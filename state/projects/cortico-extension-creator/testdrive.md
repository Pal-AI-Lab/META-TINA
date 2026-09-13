# 试驾记录 — cortico-extension-creator

## 第一趟(2026-09-12,方法 A:专家在全新会话里打开 workspace/)

跑到的地方:首次运行。环境自检(Node 22.23.2、corepack、pnpm 11.5.0、git、GitHub 可达)通过,建了存档,从 GitHub clone 了 Cortico 并 `corepack pnpm install` 成功,写了第一条日志。未进入任何入口。

发现:

- **degraded** — clone 到的 GitHub master 停在 eb5fd26,今天 Cortico 本地的五笔(templates/extension、check:extension 干装载、docs 三条 World 规则、PWSR、仓库地址)还没推,阅读地图指的 `templates/extension/` 在那份里不存在;走到复制模板会断。处置:下一趟取 Cortico 时给本地路径 `C:\Users\13079\Desktop\BOT`(facts.md 已写这条路),或专家先推 master。
- **流程** — 试驾在 workspace/ 里建了 `.git`,外层 git 从此看不见 workspace/ 内的改动。专家定为预期行为,收尾时直接清掉;Meta TINA 的 5-testdrive.md 已加「清场」一节。本趟的 .git、clone、日志条目已清,workspace/ 回到干净状态。

未验:开场白(改动晚于本趟)、任一入口、三级验证、卡住协议。

## 第二趟(待跑)

从「开始」重来,选「编写 Cortico 的扩展」→ World,做一个小 World 走到第三级;取 Cortico 时给本地路径。

## 第二趟(2026-09-12 晚,方法 A)

跑到的地方:选了 World 入口,读完了阅读地图指的文件,还没定包。日志条目一度被外层 git 收进提交,已恢复模板。

发现:

- **degraded** — 开场白没有逐字说,被转述成自己的话(「你好啊,我是 Cortina,陪你给 Cortico 写扩展……」),菜单也改了措辞。处置:开场白原文移到 `app/opening.md`,AGENTS.md 首次运行与启动序列都改成「原样输出这个文件」,加应用不变量 C8「开场白逐字」。
- **degraded** — 又从 GitHub 取了旧的 master,`templates/extension/` 不在;agent 如实写进日志、没有假称复制了模板,这一点合格。根因同第一趟:本地五笔未推。
- **polish** — agent 找不到 websearch 与 terminal 的 README:Cortico 的 docs/worlds.md 写「每个 World 目录有自己的 README」,实际只有 bilibili 与 minecraft 有。已改 docs/worlds.md 的措辞。

专家决定:其余不再测,等与 Cortico 一起开源后按反馈迭代。本趟残留(clone、日志)已清。
