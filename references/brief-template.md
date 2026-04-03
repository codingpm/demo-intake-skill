# Demo Intake Skill Brief Template

这个文件定义 `demo-intake-skill` 的标准输出格式。

目标是让澄清后的需求可以直接交给 `th-b-web-ui-skill` 或 `th-b-mobile-ui-skill`，而不需要再次解释上下文。

## Standard Requirement Brief

使用下面这个模板作为默认输出：

```md
## Requirement Brief

- Platform:
- Business domain:
- Page or screen type:
- Target users:
- Core business object:
- Primary goal:
- Key actions:
- Key information or fields:
- Important statuses or workflow notes:
- Constraints or preferences:
- Recommended downstream skill:
- Assumptions used:
```

## Field Guidance

### Platform

只填写：

- Web
- Mobile

如果仍不明确，应优先继续提问，而不是跳过。

### Business domain

填写业务领域，例如：

- TMS
- WMS
- OMS
- 财务
- 客服
- 供应链

### Page or screen type

描述结构类型，而不是泛泛地写“一个页面”。

例如：

- 配送单列表页
- 订单详情页
- 审批表单页
- 司机任务详情 screen
- 仓库作业提交页

### Target users

描述主要用户角色，例如：

- 调度员
- 运营
- 仓管员
- 司机
- 财务专员

### Core business object

描述页面围绕的核心对象，例如：

- 配送单
- 运单
- 审批记录
- 司机签到任务
- 入库作业单

### Primary goal

写一句清晰的话，说明这个页面最重要的目标。

例如：

- 帮助调度员快速筛选和分配配送单
- 帮助司机查看任务详情并完成签到
- 帮助仓管员提交入库作业结果

### Key actions

列出最重要的操作，优先保留 2 到 5 个。

例如：

- 查询
- 重置
- 分配司机
- 导出
- 查看详情

### Key information or fields

列出页面必须优先展示的字段或信息块。

例如：

- 配送单号
- 状态
- 承运商
- 配送时间
- 司机
- 异常标记

### Important statuses or workflow notes

记录重要状态或流程特征。

例如：

- 待分配、配送中、已签收、异常
- 存在批量分配流程
- 存在异常单高亮需求
- 存在审批驳回流程

### Constraints or preferences

记录对输出有明显影响的约束。

例如：

- 需要紧凑型后台布局
- 需要固定底部操作区
- 需要批量操作
- 需要突出异常订单

### Recommended downstream skill

根据 platform 输出：

- `th-b-web-ui-skill`
- `th-b-mobile-ui-skill`

### Assumptions used

明确写出未说明但被默认采用的内容。

例如：

- 默认采用企业后台紧凑布局
- 默认详情操作放在右上或底部操作区
- 默认使用状态标签表达流程状态

## Good Example

```md
## Requirement Brief

- Platform: Web
- Business domain: TMS
- Page or screen type: 配送单列表页
- Target users: 调度员
- Core business object: 配送单
- Primary goal: 帮助调度员快速筛选、查看并分配配送单
- Key actions: 查询、重置、分配司机、导出、查看详情
- Key information or fields: 配送单号、配送状态、线路、承运商、司机、计划配送时间、异常标记
- Important statuses or workflow notes: 状态包含待分配、配送中、已签收、异常；需要支持异常单高亮和批量分配
- Constraints or preferences: 页面偏紧凑，主内容应以表格为中心
- Recommended downstream skill: `th-b-web-ui-skill`
- Assumptions used: 默认采用企业后台列表页结构，包含筛选区、操作区、表格和分页
```

## Output Rules

- brief 应短而完整，不要写成长篇分析
- 用结构化字段，不用松散段落
- 不要附带完整提问过程
- 不要混入与页面结构无关的泛泛描述
- brief 应能被下游 skill 直接使用
