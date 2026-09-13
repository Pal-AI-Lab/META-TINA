# 准入面谈记录 — cortico-extension-creator

状态:进行中。下面各项是我按 Cortico 仓库与前期讨论预填的理解,每条带来源标签;
专家逐条确认或改正后才算面谈完成。

## 1. 产物(Artifact)
[DRAFTED, PENDING CONFIRMATION] 一个符合 Cortico 扩展契约的 npm 包:`package.json` 带
`cortico: { kind, api }` 块与关键字,`src/index.ts` 默认导出 `WorldDefinition` 或
`ProviderModule`,可选控制台面板(`src/console/client.ts` → `dist/console.js`),tests/,
README,tsconfig 的 `paths` 指向 Cortico checkout。范例:cortico-world-asr。
[EXPERT'S OWN WORDS] kind 三种都做:world、provider、bot。
[DRAFTED, PENDING CONFIRMATION](0912 据代码核实,Cortico 71d29bb)前置已满足:`EXTENSION_KINDS` =
world / provider / bot,`EXTENSION_API_VERSION` = 3;三种 kind 共用一份 manifest 与一条装载线,
`pnpm check:extension <目录>` 三种都查。bot 包:`deployment.json` 的 `bot` 字段填包名即启用,仓内
`bots/<同名>/` 赢,bot id 不得与仓内 `bots/` 目录同名,包目录只读(promptDocs 没给 `deploymentPath`
的模板能看不能存)。
[DRAFTED, PENDING CONFIRMATION] bot 线的一个缺口:扩展包只能以 `cortico/<src 下路径>` import 框架,
仓内 `bots/cormini/` 不在 `src/` 下,所以扩展 bot **不能继承 Cormini**,只剩「复制 cormini 再改」一条路。

## 2. 用户(Users)
[DRAFTED, PENDING CONFIRMATION] 带着 coding agent 的开发者,想把 Cortico 接到一个新平台
或新端点方言。懂 TypeScript / Node 与目标平台的 API;不懂 Cortico 的四层边界、事件/工具契约、
面板契约、manifest。代码主要由 agent 写,开发者审。
[EXPERT'S OWN WORDS] 按 kind 分层:provider 是比较有开发经验的人才会做的;World 和 bot 那边纯爱好者很多。

## 3. 验证(Verification)
[DRAFTED, PENDING CONFIRMATION] 三级:包内 `pnpm typecheck` + `pnpm test` 绿,且在 Cortico clone 下
`pnpm check:extension <包目录>` 通过;装进真实实例后扩展页卡片显示「已加载」;行为确认(事件进上下文 /
工具可调用)由开发者在自己的实例上目视。
[CONFIRMED](专家 0912 拍板「改 Cortico」,已落地 688e11f)第二级由 `check:extension` 的干装载覆盖:World 在假部署下
`create()`、跑 `tools()` / `envPromptVars()` / `console()`、对照 Core 保留名与内建 World 工具名;provider 按假端点
`create()`;bot 按假部署 `build()`。agent 自己能闭环的到此为止;真实实例只剩第三级行为目击。

## 4. 失败代价(Cost of failure)
[DRAFTED, PENDING CONFIRMATION] 低:装载失败卡片写明原因,重做只花时间。唯一要防的不可逆
风险是密钥进包(应在部署 `.env`)后被发布到 npm。

## 5. 节奏(Cadence)
[DRAFTED, PENDING CONFIRMATION] 一个项目一个扩展,数小时到数天,反复迭代;每步分钟级
(install、测试)可接受。

## 6. 环境(Environment)
[DRAFTED, PENDING CONFIRMATION] Node 22、corepack pnpm、git、网络(仅 clone Cortico 与
pnpm install);工作区内的 Cortico clone 做构建期依赖;开发者自己跑着的 Cortico 实例做行为
验证;目标平台的测试账号 / 凭证。

## 7. 可文本化测试(Textualization)
待专家口述:写扩展时最常在哪里纠正人或 agent,依据是什么。
[DRAFTED, PENDING CONFIRMATION] 我从 AGENTS.md §3、PHILOSOPHY 与 World 契约注释里摘的候选,供专家
勾选、排序、补充(依据在括号里):
1. 事件正文或工具回执掺启发式推论、替模型下判断(诚实认知论;`WorldHost.pushEvent` 注释「严禁转录认证不了来源的外部内容」)
2. World 越界:碰 Memory、绑 Persona 工具、与 Persona 直接调用(边界 3)
3. 用硬编码流程替代语义指令,或为当前模型的短板写死机制而不标成 fallback(设计准则 1、2)
4. 命名:工具无 `<id>_` 前缀、事件 `type` 段内带连字符、时长键不带单位、`Opts`/`Ctx`(§2 约定)
5. 代码里产出前缀文本,而不是只在 `envPromptVars()` 报值(`template.ts` 头注:前缀每个字都来自模板)
6. 密钥写进包、运行时往包目录写文件(包目录只读;`.env` 在部署)
7. 面板 bundle 里对 `cortico/*` 做运行时 import(浏览器侧只许 `import type`)
8. 防御性代码、断言 mock 被调用的测试(§4、§5)

## 分类
待定。

## 六项通过标准
待定。
