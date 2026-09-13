# 知识笔记 — cortico-extension-creator

结构:3 × N。三种 kind(world / provider / bot)各一节,每节按专家给的切面分小节;每行带来源标签
[EXPERT'S OWN WORDS] / [DRAFTED, PENDING CONFIRMATION] / [CONFIRMED]。World 线先做(专家 0912 定)。

## 取舍标准(全局)

[EXPERT'S OWN WORDS] 只写 coding agent 常识决定不了的、Cortico 特有的判断。例:「要不要开引擎子进程」不写,agent 自己会定。

## 知识放哪(本项目特有,专家 0912 定)

[EXPERT'S OWN WORDS] 尽量从文档自动发现设计原则,写进 Creator 反而容易漂移。(只对这个项目;Meta TINA 不用为此改。)

[DRAFTED, PENDING CONFIRMATION] 推论:Creator 只带两样——一张进 clone 的阅读地图(哪条原则在哪份文件),和 Creator 自己的行为规则(验证回路、内置支持提醒之类);抽出来却不在 Cortico 文档里的原则,写进 Cortico 文档而不是 Creator。

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

## 文档覆盖对账(0912,Cortico daa7df9)

| 已抽的原则 | 文档里有 | 位置 |
|---|---|---|
| 回执 / 事件只陈述事实 | 有 | PHILOSOPHY 诚实的认知论;docs/worlds.md 事件段 |
| 语义状态归 Memory 经 PWSR | 有 | docs/worlds.md PWSR 节 |
| 不绕开 providers/transport | 有 | src/providers/README.md「唯一的 HTTP/SSE 引擎」 |
| bot 三条 | 有 | PHILOSOPHY.md |
| 提示词 vs 工具 description 的分工 | 无 | 只有 types.ts 一句「更长的用法写进环境提示词模板」 |
| World 内部状态生命周期变化要投事件 | 无 | |
| 事件还是工具、即时还是发车刻成文、走哪档 | 半 | docs/worlds.md 列了档位,没写选择依据 |
| 内置支持够用时提醒 | 不该在文档 | Creator 自己的行为 |
