# 知识笔记 — cortico-extension-creator

结构:3 × N。三种 kind(world / provider / bot)各一节,每节按专家给的切面分小节;每行带来源标签
[EXPERT'S OWN WORDS] / [DRAFTED, PENDING CONFIRMATION] / [CONFIRMED]。World 线先做(专家 0912 定)。

## 取舍标准(全局)

[EXPERT'S OWN WORDS] 只写 coding agent 常识决定不了的、Cortico 特有的判断。例:「要不要开引擎子进程」不写,agent 自己会定。

## 知识放哪(本项目特有,专家 0912 定)

[EXPERT'S OWN WORDS] 尽量从文档自动发现设计原则,写进 Creator 反而容易漂移。(只对这个项目;Meta TINA 不用为此改。)

[DRAFTED, PENDING CONFIRMATION] 推论:Creator 只带两样——一张进 clone 的阅读地图(哪条原则在哪份文件),和 Creator 自己的行为规则(验证回路、内置支持提醒之类);抽出来却不在 Cortico 文档里的原则,写进 Cortico 文档而不是 Creator。

## Creator 的形状(逐项拍板)

[CONFIRMED](专家 0912)扩展包从第一天起是独立 git 仓库,在 Creator 工作区里 gitignored;Creator 的 git 只存档自己的设计记录与日志。理由:Creator 开发完之后正好接着作为维护目录长期存在。

[DRAFTED, PENDING CONFIRMATION] 一个工作区允许多个包(bot 常配一个 World)。

[CONFIRMED](专家 0912「用 Pi 的做法」)起步文件由 Cortico 提供:templates/extension/{world,provider,bot}/ 各一个能装的最小真包,仓库测试对它们做干装载;不加脚手架命令。Creator 从 clone 里复制。已落地(Cortico 提交见 JOURNAL)。

[CONFIRMED](专家 0912)Creator 的文字用中文;协议不变量按规范保留英文原文。英文版是后一遍。

[CONFIRMED](专家 0912)Cortico 来源:https://github.com/Pal-AI-Lab/Cortico,直接跟 master、不钉版本——Creator 里没有能过时的东西(原则、模板、校验脚本全在 clone 里现读)。仓库暂未公开,专家之后会改;公开前 clone 需要专家自己的凭证或本地路径覆盖。

[DRAFTED, PENDING CONFIRMATION] 参考了 Pi(仓内示例目录)、OpenClaw(CLI 脚手架)、AstrBot(独立模板仓)、Hermes(文档手写 + 示例仓);没有一家在主仓放 templates/。

## 第四种入口:迁移现有 bot 到 Cortico

[EXPERT'S OWN WORDS] 除了三个扩展模式,用户第一次输入之后提供的选项还有一个:迁移现有的 bot 到 Cortico 下。此时 coding agent 应该要求用户提供对应目录,然后进去搞清楚上下文的组织方式、内部语义信息持久化的方式(映射到 Memory)、外部 IO(映射到 World)、会话生命周期一类的基础信息,然后提出一个迁移预案,可能包含实现一个 bot + 一种 Memory + 一个或多个 World。

[EXPERT'S OWN WORDS] 迁移的第一目标是还原,所以为旧模型局限写的机制要保留(标 fallback),不在迁移时去掉。

[EXPERT'S OWN WORDS] 历史数据(记忆、对话记录)的迁移也要注意,预案里要答。完成判据不用单列行为清单:开发者自己发现不对了会跟进,这种冗余不需要。各包仍各自走三级验证。

## 身份与开场白

[EXPERT'S OWN WORDS](0912)加个简单的小 RP,叫 Cortina。固定开场白原文进 AGENTS.md 首次运行第 1 步:自报型号名 + TINA 规范链接 https://github.com/Pal-AI-Lab/ThereIsNoApp;三个选项:编写扩展(World/Provider/Bot)、迁移现有的 Bot/人格 AI 框架、我还是不太懂。

## 用户按 kind 分层

[EXPERT'S OWN WORDS] provider 是比较有开发经验的人才会做的;World 和 bot 那边纯爱好者很多。

## World

专家的切分:模型可见的一侧(提示词、工具列表描述、工具、工具回执、事件)与模型不可见的一侧(World 内部)。

### 模型可见的一侧:不熟悉的人容易出的问题

[EXPERT'S OWN WORDS] 提示词和工具的 description 重复了,或没有分对。好的实践:使用时机、模型应该回避的
错误模式这类比较模糊、需要放在一起说明的内容放在提示词;具体每个工具的定义、用法放在 description。
提示词应该放整体性、语义化、需要被看到而且容易变动的内容;工具 description 应该放独立的、机械的
(工具本身的 exec 代码应该可以看出来的)、对迭代比较稳定的内容。

[EXPERT'S OWN WORDS] 事件 / 工具回执里包含启发式结构导出的推论和引导,没有严格一比一贴合实际可以
判定的事实。

[EXPERT'S OWN WORDS] 放了一些应该用事件流机制实现的工具:例如被动的状态同步用轮询工具实现,实际上
应该用 snapshot 类事件实现。

### 模型可见的一侧:决策依据

[CONFIRMED](我拟、专家 0912 确认「你猜的是对的」)一件外界变化怎么进 bot 的上下文:被动发生的是事件,bot 主动要看的是工具;描述「此刻状态」的快照在发车刻成文(pushDeferred),只搭车不发车(piggyback);需要 bot 立刻停手的才打断(preempt)。

### 模型不可见的一侧(World 内部):与 Cortico 有关、要避免的问题

[EXPERT'S OWN WORDS] 这里有很多和 Cortico 无关的错误模式;有关的主要是下面两条。

[EXPERT'S OWN WORDS] 注意管理 World 内部状态的生命周期,并确保在各种合适的时机以事件投递通知 bot。
例如 Minecraft 的服务器启动、切换世界,都应该投递事件告知 bot,避免静默切换导致两边状态不对齐,
bot 以为自己还在旧状态。

[EXPERT'S OWN WORDS] 注意尽量避免在 World 内部存储持久化的语义化内容(不是存档这类机械数据内容)。
例如 bot 自己记录的游戏地图,这种应该放在 Memory 里存储,并使用 PWSR 来同步给 World 侧。

[DRAFTED, PENDING CONFIRMATION] PWSR = Persona–World State Reconciliation。契约文本此刻没有活的
出处:准则原在 DESIGN.md §2.6,该文件 0911 退役到 deprecated/(不进版本控制);仓内只剩
src/worlds/minecraft/README.md 一处指向它的悬空引用与 world.ts / executor.ts 的注释。Creator 要教
这条,得先给它一个活的家。

## provider

### 不熟悉的人容易出的问题

[CONFIRMED](我拟、专家 0912 确认)绕开 providers/transport/ 自己写 HTTP、SSE 和重试,结果计量、超时、runaway 判定全没有。

[EXPERT'S OWN WORDS] 不写的:厂商事实硬编码进模块、终态造假(截断 / 取消包装成 completed)——这些是基本开发知识,coding agent 自己会定。

### 该不该写 provider

[EXPERT'S OWN WORDS] 背后的问题是用 Creator 的人有没有试过内置支持。提醒一下「这个内置支持可以做」就行,不要出现拦截或告诉你不值得的情况。不需要明确的边界,runtime 自己判断内置支持足够的时候提醒一下就行。

## bot

### 不熟悉的人容易出的问题(三条都在 PHILOSOPHY.md,Creator 不复制)

[CONFIRMED] 把人格写进代码,而它该在 Memory 里 —— PHILOSOPHY.md「Memory 即人格」。

[CONFIRMED] 用机械规则逼 bot 行动,而默认该是不行为 —— PHILOSOPHY.md「主动性和自由性优先」。

[CONFIRMED] Persona 伸手进 World —— PHILOSOPHY.md World 段「不能调用彼此的程序接口」。

[EXPERT'S OWN WORDS](0912)扩展 bot 不能继承 cormini 这个缺口不补:Cortico 之后会发布 npm 包,到时由包的 exports 接管。bot 线现在按「复制 cormini 再改」写。

## 文档覆盖对账(0912,Cortico daa7df9)

| 已抽的原则 | 文档里有 | 位置 |
|---|---|---|
| 回执 / 事件只陈述事实 | 有 | PHILOSOPHY 诚实的认知论;docs/worlds.md 事件段 |
| 语义状态归 Memory 经 PWSR | 有 | docs/worlds.md PWSR 节 |
| 不绕开 providers/transport | 有 | src/providers/README.md「唯一的 HTTP/SSE 引擎」 |
| bot 三条 | 有 | PHILOSOPHY.md |
| 提示词 vs 工具 description 的分工 | 有(0912 补) | docs/worlds.md 环境提示词节;types.ts tools() 注释 |
| World 内部状态生命周期变化要投事件 | 有(0912 补) | docs/worlds.md 契约节 |
| 事件还是工具、即时还是发车刻成文、走哪档 | 有(0912 补) | docs/worlds.md 契约节,触发档位下一段 |
| 内置支持够用时提醒 | 不该在文档 | Creator 自己的行为 |
