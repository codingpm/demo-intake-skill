# Demo Intake Skill Publishing Kit

## Short Description

Clarify incomplete prototype requests before UI generation by asking one question at a time and turning vague needs into a structured brief for downstream Web or Mobile design skills.

## Value Proposition

- 提升原型首版命中率
- 避免 AI 在信息不足时过度脑补
- 将模糊需求整理成结构化 brief
- 同时支持 Web 和 Mobile 原型生成前置澄清
- 可与页面生成 skill 组合使用，形成稳定工作流

## Key Capabilities

- 判断当前需求是否足够支持页面生成
- 优先识别目标平台是 Web 还是 Mobile
- 一次只问一个问题
- 基于用户上一轮回答动态追问
- 最多追问 8 轮
- 输出结构化 requirement brief
- 推荐正确的下游 skill

## Recommended Pairings

- `demo-intake-skill` + `th-b-web-ui-skill`
- `demo-intake-skill` + `th-b-mobile-ui-skill`

## Suitable Use Cases

- 用户只给一句话原型需求
- 页面方向不明确，容易设计偏
- 需要先判断是 Web 还是 Mobile
- 需要补齐页面类型、角色、目标、字段和操作
- 想建立“需求澄清 -> 页面生成”的稳定链路

## Sample Prompts

```text
请用 $demo-intake-skill 帮我澄清一个原型需求，在给方案前先逐轮问我问题，一次只问一个。
```

```text
请用 $demo-intake-skill 帮我梳理一个 TMS 配送单管理原型需求，最多问 8 个问题，最后输出结构化 brief。
```

```text
请用 $demo-intake-skill 帮我补齐一个移动端仓库作业页面的需求信息，然后推荐我应该接哪个 UI skill。
```

## Suggested Positioning

这个 skill 适合作为“原型需求 intake 层”存在。

它不替代页面生成 skill，而是为页面生成 skill 提供更高质量的输入。

推荐定位表达：

- 一个先澄清、后生成的原型需求收集 skill
- 一个同时适用于 Web 和 Mobile 的前置需求补全 skill
- 一个帮助团队提升首版原型满意率的通用 intake skill
