# Demo Intake Skill Platform Routing

这个文件定义 `demo-intake-skill` 在 Web 和 Mobile 之间的分流规则。

目标是确保需求在进入下游 UI skill 之前，已经被明确路由到正确的平台。

## Core Rule

在输出最终 brief 前，必须明确 `Platform`。

允许的值只有：

- Web
- Mobile

如果平台仍然不明确，不应直接进入页面生成阶段。

## When To Ask Platform Early

如果用户的原始需求没有显式说明平台，应优先判断平台，尤其是在这些情况下：

- 用户只说“设计一个页面”或“做一个原型”
- 业务对象同时可能出现在 Web 和 Mobile
- 页面结构和交互会因为平台不同而明显变化
- 同一个业务场景既可能是后台，也可能是 App

典型高风险模糊需求：

- 设计一个配送单管理原型
- 做一个签收页面
- 设计一个异常处理页面
- 做一个任务看板

这些请求都应该尽早确认平台。

## Platform Decision Guidance

### Route to Web when

更符合以下特征时，优先判断为 Web：

- 企业后台或管理后台
- 以筛选、表格、分页、批量操作为主
- 需要高信息密度
- 页面主要给运营、调度、财务、管理员使用
- 以列表管理、配置管理、审核管理、数据管理为主

推荐下游 skill：

- `th-b-web-ui-skill`

### Route to Mobile when

更符合以下特征时，优先判断为 Mobile：

- 企业 App 或移动作业场景
- 以任务处理、提交、签到、扫码、拍照、跟踪为主
- 需要底部操作区、卡片流、单列结构
- 页面主要给司机、仓管员、现场人员、移动端操作角色使用
- 以即时处理任务、结果提交、移动查看为主

推荐下游 skill：

- `th-b-mobile-ui-skill`

## If the User Already Specified Platform

如果用户已经明确说了：

- Web
- PC
- 后台
- 管理端

则默认按 Web 处理。

如果用户已经明确说了：

- Mobile
- App
- 移动端
- 手机端

则默认按 Mobile 处理。

## If the User Did Not Specify Platform

优先问：

- 这个原型是给 Web 端还是 Mobile 端使用？

如果用户回答仍然模糊，再根据用户角色和核心任务继续判断。

## Output Rule

最终输出的 requirement brief 中必须包含：

- Platform
- Recommended downstream skill

对应关系固定为：

- `Platform: Web` -> `Recommended downstream skill: th-b-web-ui-skill`
- `Platform: Mobile` -> `Recommended downstream skill: th-b-mobile-ui-skill`

## Avoid

- 不要在平台未明确时直接输出页面方案
- 不要把 Web 和 Mobile 混在一个 brief 里
- 不要在同一轮里同时问平台和多个结构问题
- 不要因为用户提到“系统”就默认一定是 Web
- 不要因为用户提到“页面”就忽略 Mobile 的可能性
