# Demo Intake Skill

`demo-intake-skill` 是一个面向原型需求澄清的 skill。

它的目标不是直接生成页面，而是帮助 AI 在需求信息不足时，先把关键问题问清楚，再整理成结构化 brief，交给下游的 Web 或 Mobile 设计 skill 继续生成。

## 适合做什么

- 澄清只有一句话描述的原型需求
- 帮助判断目标是 Web 还是 Mobile
- 补齐页面类型、用户角色、业务对象和核心目标
- 在生成前补齐关键字段、关键操作和特殊约束
- 作为 `th-b-web-ui-skill` 和 `th-b-mobile-ui-skill` 的前置需求收集层

## 这个 Skill 的核心价值

它会引导 AI 优先做这些事情：

- 先判断信息是否足够，而不是直接猜页面
- 一次只问一个问题，降低用户回答负担
- 根据用户上一轮回答动态追问，而不是固定问卷
- 优先补齐最影响页面结构的高价值信息
- 在最多 8 轮内收敛，避免无限追问
- 输出结构化 requirement brief，方便后续页面生成

它解决的核心问题是：

- 用户说得太少
- AI 脑补太多
- 第一版页面偏差大

## 不做什么

这个 skill 不负责沉淀具体的 Web 或 Mobile 视觉规范，也不负责直接定义页面样式细节。

它更适合做：

- 需求澄清
- 结构化信息收集
- 平台判断
- brief 生成

它不替代下游页面设计 skill，而是为它们提供更好的输入。

## 推荐使用方式

最简单的调用方式：

```text
请用 $demo-intake-skill 帮我澄清一个原型需求，在给方案前先逐轮问我问题。
```

更推荐的调用方式：

```text
请用 $demo-intake-skill 帮我梳理一个配送单管理原型需求。

要求：
- 在给方案前先提问
- 一次只问一个问题
- 根据我的回答继续追问
- 最多问 8 个问题
- 最后整理成结构化 brief
```

## 适合补充给 AI 的信息

为了让澄清更快收口，建议尽量补充：

- 平台：Web 或 Mobile
- 页面类型：列表页、详情页、表单页、任务页、Dashboard
- 目标用户：调度员、运营、司机、仓管、管理员等
- 主要业务对象：配送单、运单、仓库任务、签收记录等
- 核心目标：查询、分配、审核、跟踪、上报、导出等
- 关键字段
- 关键操作
- 特殊约束或偏好

## 推荐搭配

- `demo-intake-skill` + `th-b-web-ui-skill`
- `demo-intake-skill` + `th-b-mobile-ui-skill`

推荐流程：

1. 先用 intake skill 补齐需求
2. 生成结构化 brief
3. 再交给对应的 UI skill 生成页面

## 目录说明

- [SKILL.md](/Users/mashaoguang/Documents/New project/demo-intake-skill/SKILL.md)
  skill 的核心规则定义
- [README.md](/Users/mashaoguang/Documents/New project/demo-intake-skill/README.md)
  仓库级说明文档
- [openai.yaml](/Users/mashaoguang/Documents/New project/demo-intake-skill/agents/openai.yaml)
  skills 平台展示信息和默认 prompt
- [publishing-kit.md](/Users/mashaoguang/Documents/New project/demo-intake-skill/references/publishing-kit.md)
  对外发布文案和示例 prompt

## 一句话总结

如果你的目标是“先把原型需求问清楚，再提高首版页面命中率”，那就用 `demo-intake-skill`。
