# Demo Intake Skill

Demo Intake Skill 是一个用于补齐原型需求信息的可复用 skill。

它的作用不是直接生成页面，而是在用户需求过于简短、模糊或缺少关键上下文时，先通过连续追问帮助 AI 理解真实目标，再整理成结构化 brief，交给下游的 Web 或 Mobile 设计 skill 使用。

它关注的是需求澄清和信息收集，而不是具体视觉规范或某一种技术实现。

## 特性

- 支持为 Web 和 Mobile 原型生成做前置需求澄清
- 一次只问一个问题，避免多问题并发造成回答质量下降
- 最多追问 8 轮，在理解质量和对话成本之间做平衡
- 能根据用户回答动态追问，而不是固定问卷
- 输出结构化 requirement brief，方便下游 skill 继续生成页面
- 兼容 skill 平台常见结构，包含 `SKILL.md` 和 `agents/openai.yaml`
- 适合通过 GitHub 仓库进行分享、维护和发布

## 快速开始

在提示词中直接引用这个 skill：

```text
请用 $demo-intake-skill 帮我澄清一个原型需求，在给方案前先逐轮问我问题，一次只问一个，最多 8 个问题。
```

如果你已经知道要做的是 Web 还是 Mobile，也可以直接补充：

```text
请用 $demo-intake-skill 帮我澄清一个 Web 端原型需求，在输出方案前先逐轮提问。
```

```text
请用 $demo-intake-skill 帮我澄清一个移动端页面需求，一次只问一个问题，最后整理成 brief。
```

## 示例提示词

```text
请用 $demo-intake-skill 帮我梳理一个 TMS 配送单管理原型需求，先问我问题，不要直接出页面。
```

```text
请用 $demo-intake-skill 澄清一个仓库作业 App 页面需求，要求一次只问一个问题，直到你足够理解后再总结。
```

```text
请用 $demo-intake-skill 帮我补齐一个订单审核页面的需求信息，并输出成结构化页面 brief。
```

## 这个 Skill 能做什么

这个 skill 主要用于指导 AI：

- 判断当前原型需求信息是否足够
- 优先识别目标平台是 Web 还是 Mobile
- 逐轮澄清页面类型、用户角色、业务对象和核心目标
- 追问关键操作、关键字段、状态流转和特殊约束
- 在 8 轮以内尽量补齐高价值信息
- 输出适合下游设计 skill 消费的结构化 brief

## 工作方式

这个 skill 采用“先澄清，后生成”的流程。

核心规则包括：

- 在给出方案前先提问
- 一次只问一个问题
- 每一轮都基于用户上一轮回答继续追问
- 优先问最影响页面结构的问题
- 最多追问 8 次
- 当关键槽位足够清晰时提前收口
- 输出前先整理结构化 brief

这个 skill 通常会优先补齐这些信息：

- Platform
- Page or screen type
- Target users
- Business domain
- Core business object
- Primary goal
- Key actions
- Key information or fields
- Constraints or preferences

## 推荐搭配方式

这个 skill 更适合作为前置 skill，与页面生成 skill 配套使用。

推荐搭配：

- `demo-intake-skill` + `th-b-web-ui-skill`
- `demo-intake-skill` + `th-b-mobile-ui-skill`

推荐流程：

1. 先用 `demo-intake-skill` 补齐需求
2. 产出结构化 requirement brief
3. 再交给对应的 Web 或 Mobile UI skill 生成页面

## 仓库结构

```text
demo-intake-skill/
├── SKILL.md
├── README.md
└── agents/
    └── openai.yaml
```

### 主要文件

- `SKILL.md`
  skill 的核心定义、提问规则、停止条件和 brief 输出格式。

- `agents/openai.yaml`
  skill 平台展示信息和默认提示词配置。

## 这个仓库怎么用

这个仓库有几种常见用法：

1. 作为本地 skill 目录，放入兼容 Codex 的 skills 目录中使用
2. 作为 GitHub 仓库，被 skill 平台从仓库导入
3. 作为团队共享的“原型需求澄清规范”

## 适合的使用场景

- 用户只给了一句话需求，但希望首次生成更准确
- 需要先判断原型是 Web 还是 Mobile
- 业务对象明确，但页面结构还不明确
- 需要在生成前补齐角色、目标、关键字段和操作
- 想把“需求澄清”从页面设计规则中独立出来，作为通用前置层

## 发布说明

这个仓库已经按 skill 平台和 GitHub 分发的方向组织好了结构。它被设计成一层可复用的原型需求澄清能力，而不是某个具体产品的页面生成规则。

如果平台支持读取 skill 元数据，主要入口文件是：

- `SKILL.md`
- `agents/openai.yaml`
