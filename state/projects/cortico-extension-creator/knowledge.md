# 知识笔记 — cortico-extension-creator

结构:3 × N。三种 kind(world / provider / bot)各一节,每节按专家给的切面分小节;每行带来源标签
[EXPERT'S OWN WORDS] / [DRAFTED, PENDING CONFIRMATION] / [CONFIRMED]。World 线先做(专家 0912 定)。

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

(待做)

## bot

(待做)
