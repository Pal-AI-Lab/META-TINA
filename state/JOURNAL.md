# Meta TINA Journal

[Format note: each entry as below. Append at milestones or before a
session ends; write the first entry during the first run. As long as
this file has no dated entries, it is treated as the first run.]

    ## YYYY-MM-DD — one-line title
    - What was done this time:
    - What was decided, and why:
    - Next step:

## 2026-09-11 — 首次运行,开项目 cortico-extension-creator
- What was done this time: 首次运行;开出项目文件夹;按仓库与前期讨论预填准入面谈七项,全部标 PENDING。
- What was decided, and why: 发布形式先定(独立仓库、内部 clone Cortico),因为它影响能力声明与环境自检的写法。
- Next step: 专家确认或改正预填项,补第 7 项;写分类与六项标准;转 extraction。

## 2026-09-12 — 续做准入:按 Cortico 71d29bb 核实预填事实
- What was done this time: 通读 Meta TINA 全部 app/ 文档与 Cortico 侧扩展契约(manifest、装载器、check 脚本、三个扩展点的类型、五个外部扩展包的工具链文件、夹具);改正 admission.md 第 1、3 项里过时的前置事实;给第 7 项列了 8 条候选供专家勾选。
- What was decided, and why: 无新拍板。发现两处影响设计的框架事实:扩展 bot 不能 import 仓内 bots/cormini(只能复制);第二级验证(装载)今天只有真实实例能证明。
- Next step: 专家答第 7 项与拍板清单(分类、知识来源、工作区布局、验证回路、bot 线、语言、钉 commit、范围);写六项标准;转 extraction。

## 2026-09-12 — 准入与抽取同日结案,转起草
- What was done this time: 按 3 × N 抽完三条线的坑与依据;Creator 形状逐项拍板(包自带 git、模板在 Cortico、验证第二级用干装载、中文、跟 master、第四入口迁移);两处摩擦回写进 Meta TINA(准入第 7 问改问法、builder 产物自带 git);Cortico 侧落了四笔(PWSR 进 docs、三条 World 规则进 docs、check:extension 干装载、templates/extension 三个包)。
- What was decided, and why: 原则不复制进 Creator、从 Cortico 文档现读,因为复制会漂;Creator 只剩阅读地图与行为规则。
- Next step: 起草文档清单给专家过,然后逐份写。

## 2026-09-12 — 一次写完整个工作区
- What was done this time: 专家过了文档清单,要求直接全部写完;起草与装配合并,写出 workspace/ 全部 15 个文件;协议不变量逐字拷入并 diff 核对;装配检查单全过,只剩两处 PENDING 标签待专家确认。
- What was decided, and why: 不开「扩展 bot 继承 cormini」的路,等 Cortico 发 npm 包;Creator 的 bot 线按复制写。
- Next step: 专家评审;试驾(全新会话,方法 A)。

## 2026-09-12 — 声明远程存档,推送到 GitHub
- What was done this time: 应用户明确要求,把本工作区推送到 https://github.com/Pal-AI-Lab/META-TINA(私有仓库),分支 master 改名 main。按 I6 记录一次绕过:AGENTS.md 原承诺「不连接远程 git 仓库」、存档策略「无偏离」,用户的明确指令覆盖了它;已把远程写进 AGENTS.md 的存档策略与能力声明(I4 改动,单独一笔提交)。另把 app/spec/TINA-SPEC-0.1.md 逐字复制为独立规范仓库 https://github.com/Pal-AI-Lab/ThereIsNoApp,两边 diff 一致。
- What was decided, and why: 远程只做存档镜像,只在用户明确要求时推送;规范以 Meta TINA 内 app/spec 的文本为准,规范仓库是它的发布副本。
- Next step: cortico-extension-creator 试驾继续(workspace 已完成首次启动)。
