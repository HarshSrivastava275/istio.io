---
title: 功能状态
description: 特性及其发布阶段的列表。
weight: 10
aliases:
    - /zh/docs/reference/release-roadmap.html
    - /zh/docs/reference/feature-stages.html
    - /zh/docs/welcome/feature-stages.html
    - /zh/docs/home/roadmap.html
    - /zh/about/feature-stages
    - /zh/latest/about/feature-stages
owner: istio/wg-docs-maintainers
test: n/a
---

<!--
Note: this contains feature status from
https://docs.google.com/spreadsheets/d/1Nbjat-juyQ8AWhkq3njLckmHM8TRL4O-sjm9Bfr9zrU/edit#gid=0
-->

本页面列出了每个 Istio 特性的相对成熟度和支持级别。请注意，
这些阶段是针对项目中的各个功能而不是整个项目。以下是对这些内容的高级描述标签。

## 功能定义阶段  {#feature-phase-definitions}

|      | Experimental                                                                                                               | Alpha                                                                                                                    | Beta                                                                                                                                                                    | Stable                                         |
|------|----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| 目的   | 该功能正在积极开发中，用户的 API 可能会发生变化。用户在部署实验性功能时应极度谨慎，最好在非生产环境中使用，因为实验版本可能需要进行迁移工作。                                                  | 用于获取有关设计或功能的反馈，或查看试探性设计的执行情况等。针对开发人员和专家用户。                                                                               | 用于审查生产中的解决方案，但没有长期承诺，以评估其可行性、性能、可用​​性等。针对所有用户。                                                                                                                          | 经过生产验证，可靠。                                     |
| 稳定性  | 可能存在错误。使用该功能可能会暴露出错误。默认不活动。                                                                                                | 可能存在错误。使用该功能可能会暴露出错误。默认不活动                                                                                               | 代码经过充分测试。该功能在生产环境中使用是安全的。                                                                                                                                               | 代码经过充分测试且稳定。在生产环境中可以安全广泛部署使用。                  |
| 性能   | 性能特征未知。启用实验性功能可能会对性能产生负面影响。                                                                                                | 性能要求作为设计的一部分进行评估。                                                                                                        | 具备性能和可扩展性的特性，但可能存在一些注意事项。                                                                                                                                               | 性能（延迟/规模）被量化并记录下来，保证不会出现退化。                    |
| 支持   | 不保证向后兼容性。Istio 社区不承诺改进、维护或完成该功能，并且该功能可能随时在后续软件版本中完全删除，恕不另行通知。                                                              | 不保证向后兼容性。Istio 不承诺完成该功能。该功能可能会随时在后续软件版本中完全删除，恕不另行通知。                                                                     | 尽管细节可能会发生变化，但整体功能不会被删除。Istio 承诺在后续的稳定版本中以某种形式完成该功能。通常这会在 3 个月内发生，但有时会更长。 版本应在至少一个受支持的发布周期（通常为 3 个月）内同时支持两个连续版本（例如 v1alpha1 和 v1beta1；或 v1beta1 和 v1），以便用户有足够的时间升级和迁移资源。 | 该功能将在许多后续版本中继续存在。                              |
| 弃用政策 | 无，功能可能随时被删除。                                                                                                               | 无，功能可以随时被删除。                                                                                                             | 弱，会提前 3 个月通知删除功能。                                                                                                                                                       | 强，该功能可以在提前 1 年通知的情况下被删除，但通常会提供支持的升级路径以替换该功能。   |
| 版本控制 | API 版本名称包含 dev（例如 v1dev1）。                                                                                                 | API 版本名称包含 alpha（例如 v1alpha1）。                                                                                           | API 版本名称包含 beta（例如 v1beta1）。                                                                                                                                            | API 版本是 `vX`，其中 X 是整数（例如 v1）。                  |
| 可用性  | 该功能可能在主 Istio 存储库中可用，也可能不可用。该功能可能会也可能不会出现在 Istio 版本中。如果它确实出现在 Istio 版本中，它将默认被禁用。除了使用该功能所需的任何配置外，该功能还需要一个显式标志来启用，以便打开开发功能。  | 该功能已提交给 Istio 存储库。该功能出现在 Istio 的官方版本中。该功能需要明确的用户操作才能使用，例如标志翻转、配置资源的使用、显式安装操作或调用的 API。当某个功能被禁用时，它不得影响系统稳定性。               | 在官方 Istio 版本中默认启用。                                                                                                                                                      | 与 Beta 版相同。                                        |
| 受众   | 其他开发人员在功能或概念验证方面密切合作。                                                                                                      | 该功能面向有兴趣提供早期反馈的开发人员和专家用户。                                                                                                | 有兴趣提供有关功能的反馈的用户。                                                                                                                                                        | 所有用户。                                          |
| 完整性  | 功能的兼容性有限。此功能可以作为概念证明。                                                                                                      | 某些 API 操作或 CLI 命令可能无法实现。该功能不需要进行 API 审查（在正常的代码审查之上对 API 进行深入且有针对性的审查）。                                                   | 应实现所有 API 操作和 CLI 命令。端到端测试完整且可靠。该 API 已经过彻底的 API 审查，并且被认为是完整的，尽管在测试期间使用经常会出现审查期间未考虑到的 API 问题。                                                                           | 与 Beta 版相同。                                    |
| 文档   | 实验性功能在自动生成的参考文档中被标记为实验性或不公开。                                                                                               | Alpha 功能在自动生成的参考文档中标记为 alpha。描述该功能的作用、如何启用它、限制和警告的基本文档，以及指向该功能所基于的问题或设计文档的指针。                                            | 发布到 Istio.io 的完整功能文档 除了基本的 alpha 级文档，beta 文档还包括示例、教程、术语表条目等。                                                                                                            | 与 Beta 版相同。                                        |
| 可升级性 | 实验性功能的架构和语义可能会在较新版本中发生变化，但无法保证在升级期间需要更改配置的向后兼容性。API 版本的增加速度可能比发布节奏快，开发人员无需维护多个版本以实现向后兼容性。当架构或语义以不兼容的方式更改时，鼓励开发人员增加 API 版本。 | Alpha 功能的架构和语义可能会在后续软件版本中发生变化，而无需在现有 Istio 安装中保留配置对象。API 版本的增加速度可能快于发布节奏，并且开发人员无需维护多个版本。当架构或语义以不兼容的方式更改时，开发人员应增加 API 版本。 | 架构和语义可能会在以后的软件版本中发生变化。发生这种情况时，将记录升级路径。在某些情况下，对象将自动转换为新版本。在其他情况下，可能需要手动升级。手动升级可能需要对依赖新功能的任何内容进行停机，并且可能需要将对象手动转换为新版本。当需要手动转换时，项目将提供有关该过程的文档。                              | 在随后的软件版本中只允许严格兼容的更改。                           |
| 测试   | 该功能的存在不得影响任何已发布的功能。                                                                                                        | 该功能由单元测试和集成测试覆盖，其中启用了该功能并且测试是稳定的。测试可能无法涵盖所有​​极端情况，但已经涵盖了最常见的情况。测试代码覆盖率 >= 70%。当该功能被禁用时，它不会降低系统的性能。                       | 集成测试涵盖边缘情况以及常见用例。集成测试涵盖了该功能上报告的所有问题。该功能具有涵盖该功能示例/教程的端到端测试。测试代码覆盖率 >= 80%。                                                                                               | Beta 的超集，包括对 Beta 期间发现的任何问题的测试。测试代码覆盖率 >= 90%。 |
| 可靠性  | 用户不应期望可靠的功能可能未经测试。                                                                                                         | 由于该功能相对较新，并且可能缺乏完整的端到端测试，因此通过标志启用该功能可能会暴露导致 Istio 不稳定的错误（例如，控制循环中的错误可能会迅速创建过多的对象，耗尽 API 存储空间） .                          | 由于该功能具有 e2e 测试，因此启用该功能不应在不相关的功能中产生新的错误。由于该功能相对较新，因此可能存在小错误。                                                                                                             | 高的。该功能经过充分测试，适用于所有用途，稳定可靠。                     |
| 推荐用例 | 在短期开发或测试环境中，旨在征求用户的早期反馈以制定开发工作。                                                                                            | 在短期开发或测试环境中，由于可升级性的复杂性和缺乏长期支持。                                                                                           | 在开发或测试环境中。在生产环境中作为功能评估的一部分以提供反馈。                                                                                                                                        | 任何。                                            |

## Istio 特性  {#Istio-features}

以下是我们现有功能及其当前阶段的列表。此信息将在每次发布后更新。

### 流量管理  {#traffic-management}

{{< features section="Traffic Management" >}}

### 可观测性  {#observability}

{{< features section="Observability" >}}

### 可扩展性  {#extensibility}

{{< features section="Extensibility" >}}

### 安全和政策执行  {#security-and-policy-enforcement}

{{< features section="Security and policy enforcement" >}}

### 核心  {#core}

{{< features section="Core" >}}

### Ambient 模式 {#ambient-mode}

{{< features section="Ambient 模式" >}}

{{< idea >}}
如果您希望在我们的未来版本中看到某些功能，
请通过[加入我们的社区](/zh/get-involved/)与我们联系！
{{< /idea >}}
