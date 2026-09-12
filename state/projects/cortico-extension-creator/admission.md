# 准入面谈记录 — cortico-extension-creator

状态:进行中。下面各项是我按 Cortico 仓库与前期讨论预填的理解,每条带来源标签;
专家逐条确认或改正后才算面谈完成。

## 1. 产物(Artifact)
[DRAFTED, PENDING CONFIRMATION] 一个符合 Cortico 扩展契约的 npm 包:`package.json` 带
`cortico: { kind, api }` 块与关键字,`src/index.ts` 默认导出 `WorldDefinition` 或
`ProviderModule`,可选控制台面板(`src/console/client.ts` → `dist/console.js`),tests/,
README,tsconfig 的 `paths` 指向 Cortico checkout。范例:cortico-world-asr。
[DRAFTED, PENDING CONFIRMATION] v1 只覆盖 world 与 provider 两种 kind;bot 双轨未拍板,不写。

## 2. 用户(Users)
[DRAFTED, PENDING CONFIRMATION] 带着 coding agent 的开发者,想把 Cortico 接到一个新平台
或新端点方言。懂 TypeScript / Node 与目标平台的 API;不懂 Cortico 的四层边界、事件/工具契约、
面板契约、manifest。代码主要由 agent 写,开发者审。

## 3. 验证(Verification)
[DRAFTED, PENDING CONFIRMATION] 三级:`pnpm extension:check` 通过;装进真实实例后扩展页卡片
显示「已加载」;行为确认(事件进上下文 / 工具可调用)由开发者在自己的实例上目视。

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

## 分类
待定。

## 六项通过标准
待定。
