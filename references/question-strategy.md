# Demo Intake Skill Question Strategy

这个文件用于补充 `demo-intake-skill` 的提问策略，帮助 AI 在需求不完整时，以更稳定的方式逐轮澄清原型需求。

## 目标

提问的目标不是把用户变成 PRD 编写者，而是用尽量少的问题补齐最影响页面结构的关键信息。

提问应当服务于以下结果：

- 判断平台是 Web 还是 Mobile
- 判断页面或 screen 类型
- 理解核心用户和任务目标
- 找到关键字段、关键操作和主要状态
- 整理出可供下游 UI skill 使用的结构化 brief

## 总原则

- 在给方案前先提问
- 一次只问一个问题
- 每个问题都要基于上一轮回答
- 优先问最影响结构的问题
- 不问低价值细节
- 最多追问 8 轮
- 当主要结构信息足够时提前收口

## 推荐提问顺序

通常按下面顺序判断下一问最有价值：

1. Platform
2. Page or screen type
3. Target users
4. Primary goal
5. Core business object
6. Key actions
7. Key fields or information blocks
8. Important statuses, exceptions, or constraints

不是每次都要按这个顺序机械执行。已经明确的信息不要重复问。

## 第一类问题：平台判断

如果平台未明确，应尽早提问：

- 这是 Web 端还是 Mobile 端原型？

平台一旦明确，后续问题就要贴合平台特点继续追问。

## 第二类问题：页面类型判断

如果页面结构还不清晰，优先问：

- 这是列表页、详情页、表单页、Dashboard，还是任务处理页？

对 Mobile，也可以问：

- 这是列表 screen、详情 screen、提交页、结果页，还是任务操作页？

## 第三类问题：用户和目标

这类问题帮助判断信息层级和操作重点：

- 这个页面主要给谁使用？
- 用户在这个页面最主要想完成什么？

如果只能问一个，优先问“最主要任务是什么”。

## 第四类问题：对象、字段和操作

在页面结构初步明确后，再问：

- 页面围绕的核心对象是什么？
- 哪些信息必须第一屏看到？
- 最重要的 2 到 3 个操作是什么？

不要一口气把字段、状态、操作全问完。每轮只取最有价值的一项。

## 第五类问题：状态和约束

当基础结构已经明确，可以补充：

- 是否有关键状态需要显式区分？
- 是否有异常流程、审批流、退回流、批量操作或权限差异？
- 是否有必须保留的交互偏好或界面约束？

## 适合问的问题

- 问题应当短、具体、容易回答
- 问题应当能改变页面结构或信息优先级
- 问题最好带有限定范围，降低用户回答成本

好例子：

- 这是 Web 还是 Mobile？
- 这是列表页还是详情页？
- 主要用户是谁？
- 最重要的任务是什么？
- 哪些信息必须优先展示？
- 这个页面最关键的操作是什么？

## 不适合问的问题

- 请详细描述你的业务
- 请把所有需求都写出来
- 还有别的吗
- 你还有没有其他补充
- 一轮里连续问多个问题

这类问题过于宽泛，容易让用户负担过重，也会降低回答质量。

## 收口判断

当以下多数信息已经明确，就应准备停止追问：

- platform
- page or screen type
- target users
- primary goal
- core business object
- key actions
- major information blocks or fields

如果只差少量次要细节，应使用合理默认值，而不是继续追问。

## 默认值策略

当对话接近上限但仍有少量信息缺失时：

- 对 Web 默认企业后台布局
- 对 Mobile 默认任务优先的企业移动端结构
- 字段不全时，优先保留核心识别信息、状态信息和主操作信息
- 约束未说明时，默认采用清晰、稳定、低噪音的企业产品模式

## 最终产物

提问结束后，应输出结构化 requirement brief，而不是松散总结。

brief 至少应包含：

- Platform
- Page or screen type
- Target users
- Business domain
- Core business object
- Primary goal
- Key actions
- Key information or fields
- Assumptions used
