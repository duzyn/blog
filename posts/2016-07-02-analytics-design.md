---
title: 统计分析设计
author: David Peng
date: 2016-07-02
---

​统计分析系统的主要功能是产品运营数据的采集、存储、处理和展示。整个流程一般是由客户端采集，采集完成后的数据存储在数据仓库，再对数据进行清洗、聚合等处理，存储到关系型数据库中，然后将这些数据以交互大盘的形式在网页上或者应用上展示，展示的形式有数据图和数据表。最终实现将产品的运营情况以直观、简介、可视化的方式展现给用户，实现数据的价值。

运营统计的指标常见的有以下几个：新增用户、活跃用户、累计用户、安装量、更新量、留存率、崩溃日志、崩溃率、各种事件的统计次数、页面停留时间、转换率等。各指标的定义可以见下文的术语解释。

在统计一个产品时，很重要的几个产品方面包括：渠道、版本、区域、语言、操作系统、硬件。渠道可以表示产品发行渠道的质量，版本可以统计产品的不同版本之间的用户使用情况，区域可以分析产品的用户的地理位置，语言在国际化的产品中可以统计用户的地理分布，操作系统可以统计用户所使用的操作系统平台的比例，硬件可以统计用户使用最多的硬件是什么，应用对硬件做针对性的优化。这其中尤为关键的两个方面是渠道和版本。

# 术语解释

指标
:   又叫统计指标，是反映同类现象总体数量特征的概念及其具体数值。

过滤器
:   从各项分类中选出特定分类的数据，并展示其图表。

新增用户
:   新增用户是在指定的时间段内安装并启动了应用的新用户，而不是仅仅安装了应用的用户。新增用户由唯一的设备 ID 识别（不同的设备有不同的设备 ID）。新增用户是应用的用户增长情况的重要表征，如果一个渠道的新增用户量/下载量的数值很小，说明此渠道的质量不佳。在很多情况下，好视通统计分析中的“新增用户”等于“激活用户”。

    卸载再安装的设备，不会算作一个新增用户。

累计用户
:   此数值统计了到某时间启动过应用的所有用户数量，即截止到该时期所有的新用户数。累计用户数是表征应用的用户数量的重要指标。但是此数据并不能表示一段时间内的活跃用户数量；流失用户数 = 累计用户 – 活跃用户数。

活跃用户
:   活跃用户是指在指定日期时间段内至少启动了应用一次的用户。如果时间段大于一天，并且某个用户在这个时间段启动应用若干次，那么这个用户将会被记为这个时间段内一个活跃用户。这种去掉重复用户的过程称为去重，去重的依据是设备 ID。活跃用户的数量反应了应用对于用户的粘度，一般情况下，这个数字越高说明用户越依赖于此应用。

    活跃用户一般有以下几种：日活跃用户（简称日活）、周活跃用户（简称周活）、月活跃用户（简称月活）。

版本
:   软件开发者用于标识程序处于某个阶段的数字。版本号随着公开放行后不断增大。

    每个渠道下面都有不同的版本。

事件
:   事件是一个操作行为，需在代码中定义此行为。（来自友盟术语解释）

今日
:   从当天 00:00 至 23:59 的时间段。

本周
:   从当周的周一 00:00 至 周日 23:59 的时间段。周的开始日期可能是周一或周日。在好视通分析中周的开始日是周一。

本月
:   从当月的 1 日 00:00 至 月末 23:59 的时间段。月末日可能是 28、29、30、31 日。

过去 7 天
:   从 7 天前的 00:00 至当前时间的时间段。比如现在是 12 月 23 日 10:50，则过去 7 天指 12 月 17 日 00:00 至 12 月 23 日 10:50。

过去 30 天
:   从 30 天前的 00:00 至当前时间的时间段。比如现在是 12 月 23 日 10:50，则过去 30 天指 11 月 24 日 00:00 至 12 月 23 日 10:50。

上周
:   从上周的周一 00:00 至 周日 23:59 的时间段。周的开始日期可能是周一或周日。在好视通分析中周的开始日是周一。

上月
:   从上月的 1 日 00:00 至 月末 23:59 的时间段。

# 产品的目标

产品的目标是改善客户端和服务器应用的端到端的用户体验，提高用户满意度，提升产品竞争力。

# 产品的定位

产品的定位是内部 IT 系统和工具，用于辅助产品开发团队根据用户反馈解决应用的性能问题，提高客户满意度。

产品可以量化反映应用的用户体验，可供相关角色的用户查看，帮助开发人员分析问题，并指导开发团队改进产品。

# 目标用户和需求

产品的目标用户是公司内部的高层、客户成功、运维、产品经理、开发团队。见

|   角色   |                                                                         需求                                                                         |
| -------- | --------------------------------------------------- |
| 高层     | 了解各个应用的整体的用户体验情况，查看应用的指标按版本、按时间是否有改善。                                                                           |
| 客户成功 | 在客户反馈问题时，可以通过系统去搜索客户对应的问题，并做基本的分析后回复客户。不能解决的问题转给研发处理。                                           |
| 运维     | 了解和监控服务器应用的性能指标的情况。在客户反馈问题时，可以通过系统去搜索客户对应的问题，并做基本的分析后回复客户。不能解决的问题转给研发处理。     |
| 产品经理 | 了解自己负责的应用的整体的用户体验情况，查看应用的指标按版本按时间是否有改善。制定指标目标，规划版本以提升。                                         |
| 开发团队 | 根据高层、产品经理规划的指标目标，分析当前的指标现状的原因，编写代码改善指标。对客户成功和运维反馈的问题，筛选出来，查看上传的日志并分析和解决问题。 |

:   目标用户角色和需求

# 指标分类

指标的来源是本产品的用户提出的需求，这些需求由产品经理带领团队提炼成可量化的指标。

应用的指标按端可分为客户端应用（C或B）和服务器应用（S）。每个应用的指标又可以分为业务指标、性能指标和音视频指标。业务指标是衡量跨多个应用的业务的指标，例如登录进会议室的业务，需要使用链路追踪来提升。性能指标是衡量应用本身的指标，例如应用的崩溃和页面加载性能，需要使用应用监控来提升。音视频指标是衡量跨多个应用的 *音视频业务* 的指标，例如视频的丢包，需要自研来提升。

# 指标的业务流程

描述每个指标的端到端闭环流程，如何帮助开发团队发现问题、分析问题、解决问题、验证
问题是否解决。

整个流程大致如下：在产品中植入采集SDK → 采集数据到数据仓库 → 清洗数据 → 分析数据 → 用户在 Web 前端查看数据、对比指标、制作报表 → 设置指标告警规则 → 收到告警邮件 → 产品带领开发团队查看、分析问题 → 解决问题 → 发布新版本 → 优化或者新增数据采集 → 采集数据到数据仓库。

指标制定后，需要在日常工作中执行下去。产品经理可以将关键的指标纳入季度规划，做为关键任务或非关键任务。QA 跟踪检查指标的达成情况，并统计后做为绩效考核的依据。

# 设计

系统的信息架构见：

![系统的信息架构](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/系统信息架构.png)

统计分析系统的页面设计总体最简的信息架构包含：

- 登录页：系统的用户登录系统用。应用运营数据是企业机密信息，应有登录授权的用户才能访问。
- 概览页：展示系统整体的各项指标和应用的各项指标的概况。点击概览指标可以查看具体的指标。
- 统计分析页：具体查看应用的指标情况和设置应用的信息。
- 设置：系统设置，包括账号、应用、渠道等。
- 告警通知：指标在触发告警规则后发送告警通知，在系统在可以接收、查看和处理通知。
- 帮助：帮助手册，用于新用户学习使用。

## 概览页

![概览](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/概览.png)

在概览页的上方显示应用用户指标、应用业务指标、应用性能指标的日/周/月的*各应用整体平均值*，同时显示日/周/月的同比增降百分比情况，上升使用红色的箭头，下降使用绿色的箭头，这是借鉴股价涨跌的颜色表示方法。点击概览的指标可以跳到*第一个*应用的具体指标页查看。

在概览页的下方显示各应用的各指标的日/周/月的*应用整体平均值*，同时显示日/周/月的同比增降百分比情况。点击应用的具体的值，可以跳到该应用的具体指标页查看。

点击“日/周/月”的切换器可以查看整体和各应用的各指标的情况。

## 指标页

一个指标页面的页面结构见：

![页面结构](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/页面结构.png)

以登录入会时长为例，其他指标的基本规则和此指标类似。

指标页是重中之重，是系统的主要内容。指标页的页面结构分为上中下三层，中间为主要内容区，上方页眉为系统级的主导航区（主导航），下方页脚为辅助信息，是非必要的。

指标页的内容区的左侧为应用级的导航区（次导航），分为各应用指标类和应用设置。右侧为指标的展示，指标的展示主体内容为图和表，再辅以必需的页面标题、数据的工具栏、图标题、图示例、表格和翻页工具栏。

对数据的整体操作体现在工具栏上。工具栏分为左右两侧，左侧为对数据指标进行不同查看方式的处理，包括查看依据、过滤器和导出数据，右侧为指标的按时间显示方式，包括按日/周/月显示和选择起止日期。

查看依据是指标的不同维度，这些维度都是查看指标的方式，以新增用户为例，维度有渠道、版本、区域、语言、操作系统、硬件等，以登录入会时长为例，维度有版本、企业 ID。

查看依据：在查看依据中显示的是指标的维度，可以以此聚合数据。聚合后的数据，值从大到小排列，默认在图上显示前 3 个。如下图是以版本查看登录入会时长的数据情况。在下方的表中可以选择更多查看依据的值，勾中一个则在图中显示一条线。

下例中，展示了应用的崩溃次数整体情况，展示了以版本为查看依据查看登录入会时长。

![崩溃次数](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/崩溃次数.png)

![以版本为查看依据查看登录入会时长](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/登录入会时长.png)

过滤器：可以以维度为过滤器来查看图表，点击“添加过滤器”添加一个过滤器，如下图是以一个版本为过滤器。在添加一个过滤器后，还可以添加其他过滤器。见

![以版本为过滤器](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/过滤器.png)

在过滤后显示结果的图表。点击“X”可以移除过滤器。见

![过滤版本 3.30 的登录入会时长](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/过滤器结果.png)

导出：所有图表都支持导出数据为 CSV 文件。导出文件的内容和下方的表一样。

## 查询页

以调用链查询页为例，其他指标的查询页与此类似。

查询页是对结构化的数据进行查询的页面，用于用户对数据的检索。查询页的设计上方是筛选区，可以按所有字段进行数据的筛选，下方是表格，展示每条数据的详细信息。

应用业务指标需要使用链路追踪来改进，提供一个统一的地方查询调用链。开发人员可以根据用户反馈的问题情况查找相应的调用链，并分析问题。

调用链表格的字段有以下，且支持以这些字段筛选：

- TraceID
- 时间
- Span 名称
- 耗时（毫秒）
- IP
- 应用名称
- 应用版本
- 用户 ID
- 企业 ID

下例中，展示了调用链查询，展示了崩溃查询。

![调用链查询](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/调用链查询.png)

![崩溃查询](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/崩溃查询.png)

## 详情页

以调用链详情页为例，其他指标的查询页与此类似。

点击表格中的主要属性（例如 TraceID）可以查看详情，字段有：

- 应用名称
- Span 名称
- 日志产生时间
- 状态
- IP
- 时间轴（耗时）

下例中，展示了调用链详情，展示了崩溃详情。

![调用链详情](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/调用链详情.png)

![崩溃详情](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/崩溃详情.png)

查看 Span 详情：鼠标悬浮在 Span 名称上可以查看 Span 的详情，字段有：

## 告警设置

以登录入会时长为例，其他指标的基本规则和此指标类似。

在应用设置中点击“告警设置”，打开告警设置。如

![告警设置](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/告警设置.png)

添加告警规则：点击“添加告警规则”，填写告警规则，设定好后系统在触发规则后，*实时*自动发送*邮件*给通知对象。

- 应用名称
- 告警名称：自己输一个和规则相关的告警名称，不能重复
- 告警规则：选择“同时满足以下规则”或“满足以下任一规则”中的一个，即是“与”和“或”的差别。

    告警规则可以添加一个或多个。每个规则有以下字段：

    - 最近 N 分钟：数字
    - 指标：已人为定义好的可选的指标
    - 计算方式：求和、平均值等，根据实际情况来
    - 操作符：有 $=$, $<$, $>$, $\leq$, $\geq$, $\neq$ 等
    - 阈值：数字

- 通知对象：输入邮箱，多个邮箱以换行分隔

![添加告警规则](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/添加告警规则.png)

在添加告警规则后，点击“运行”即可开启告警监控。再点击“停止”即可停止告警监控。

查看告警记录：点击“查看告警记录”可以打开查看此告警规则触发告警的记录。字段有：

- 发生时间：YYYY-MM-DD HH:MM:SS
- 告警内容：触发的值以红色标出
- 告警名称：
- 告警规则：

![查看告警记录](https://cdn.jsdelivr.net/gh/duzyn/img/images/2016-07-02-analytics-design/查看告警记录.png)