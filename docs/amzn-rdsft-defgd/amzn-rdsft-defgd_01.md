# 前言

欢迎来到数据仓库和亚马逊 Redshift 的世界！在本书中，我们将踏上一段充满挑战和乐趣的旅程，探索亚马逊 Redshift 强大的能力以及其在现代数据仓库中的角色。无论您是数据专业人士、架构师、IT 领导，还是对数据管理和分析感兴趣的普通读者，本书旨在为您提供对使用亚马逊 Redshift 进行现代数据仓库模式的全面见解。

数据在现代业务运营中发挥着关键作用，作为推动增长的宝贵资产，支持基于信息的决策。在当今数字化时代，企业从各种来源生成和收集大量数据，包括客户互动、市场趋势、社交媒体、设备和操作过程。通过利用和分析这些数据，企业可以通过识别模式和相关性来进行基于数据驱动的决策，并推动创新，从而获得竞争优势。随着数据量、速度和多样性的急剧增长，对于企业拥有能够处理当今数据驱动世界需求的高效可扩展数据仓库解决方案变得越来越关键。

亚马逊 Redshift 作为一种完全托管的基于云的数据仓库服务，在行业中已经成为领先解决方案，使组织能够存储、分析并从其庞大数据集中获取可操作见解。凭借其灵活的架构、高性能的处理能力以及与其他亚马逊网络服务（AWS）的集成，亚马逊 Redshift 为构建强大和可扩展的数据仓库提供了平台。

亚马逊 Redshift 一直处于 Gartner 数据库管理系统（DBMS）魔力象限的前沿，本书将进一步深入探讨如何成功地在 AWS 的这一数据仓库服务上实施您的分析解决方案。亚马逊 Redshift 已经从一个独立的分析查询引擎发展为一个利用机器学习作为核心特性的 AI 驱动数据仓库服务，其功能包括自动工作负载管理、Autonomics 和 Query Editor 中的 CodeWhisperer。

在本书中，我们深入探讨了数据仓库的基本概念和原则，涵盖了数据建模、提取、转换和加载过程、性能优化以及数据治理等主题。我们探索了亚马逊 Redshift 的独特功能和优势，并指导您完成设置、配置和管理 Redshift 集群的过程。我们还讨论了数据加载、架构设计、查询优化和安全考虑的最佳实践。

本书同样适用于完全不熟悉数据仓库的人员，或者那些希望通过利用云的力量来现代化当前本地解决方案的人员。各章节首先介绍 Amazon Redshift 服务，重点转向第九章中的迁移。但我们建议对迁移到 Amazon Redshift 感兴趣的读者可以根据需要提前查阅第九章。

我们结合了使用 Amazon Redshift 的个人经验，以及与使用 Amazon Redshift 的客户的互动，这是我们从日常工作中获得的特权。同时，与实际产品团队和工程团队密切合作，帮助我们在整本书中分享一些有趣的内容。

我们花了将近一整年的时间来完成这本书。AWS 根据客户反馈不断发展其服务，每隔几个月推出新功能，我们期待看到这本书很快会“过时”，或者说，我们为此感到骄傲！

随着每一章的进展，您将更深入地了解如何利用 Amazon Redshift 的强大功能构建现代化数据仓库，支持大数据量、复杂分析查询，并促进实时洞察。我们提供实际示例、代码片段和现实场景，帮助您将概念和技术应用到自己的数据仓库项目中。

请注意，本书假设读者对 Amazon Redshift 或数据仓库概念没有先前的了解。我们从基础知识开始，逐步深入，确保各个层次的读者都能从这本全面指南中受益。无论您是刚开始数据仓库之旅，还是希望增强现有知识，本书都将作为宝贵的资源和参考资料。

不多说了，让我们一起踏上这段充满激情的 Amazon Redshift 数据仓库之旅吧。愿本书成为您的忠实伴侣，为您提供构建可扩展、高性能数据仓库所需的知识和工具，将您组织的数据转化为战略资产。

祝阅读愉快，愿您的数据工作取得成功！

# 本书中使用的约定

本书使用以下排版约定：

*斜体*

指示新术语、URL、电子邮件地址、文件名和文件扩展名。

`常量宽度`

用于程序列表以及段落中引用程序元素，例如变量或函数名称、数据库、数据类型、环境变量、语句和关键字。

**`常量宽度加粗`**

显示用户应按照字面意义输入的命令或其他文本。

*`常量宽度斜体`*

显示应由用户提供值或由上下文确定值的文本。

此元素表示提示或建议。

此元素表示一般说明。

此元素指示警告或注意事项。

# 使用代码示例

补充资料（代码示例，练习等）可在[*https://resources.oreilly.com/examples/0636920746867*](https://resources.oreilly.com/examples/0636920746867)下载。

如果您有技术问题或使用代码示例的问题，请发送电子邮件至*bookquestions@oreilly.com*。

本书旨在帮助您完成工作。通常情况下，如果本书提供示例代码，您可以在您的程序和文档中使用它。除非您复制了大部分代码，否则无需征得我们的许可。例如，编写一个使用本书多个代码片段的程序不需要许可。销售或分发 O’Reilly 书籍中的示例需要许可。引用本书并引用示例代码来回答问题不需要许可。将本书中大量示例代码整合到产品文档中需要许可。

我们欣赏但通常不需要署名。署名通常包括标题，作者，出版商和 ISBN。例如：“*Amazon Redshift: The Definitive Guide* by Rajesh Francis, Rajiv Gupta, and Milind Oke (O’Reilly). Copyright 2024 Rajesh Francis, Rajiv Gupta, and Milind Oke, 978-1-098-13530-0.”

如果您认为您对示例代码的使用超出了合理使用范围或上述许可，请随时与我们联系*permissions@oreilly.com*。

# O’Reilly 在线学习

40 多年来，[*O’Reilly Media*](https://oreilly.com)提供技术和商业培训，知识和见解，帮助公司取得成功。

我们独特的专家和创新者网络通过书籍、文章和我们的在线学习平台分享他们的知识和专长。O’Reilly 的在线学习平台为您提供按需访问的现场培训课程，深入学习路径，交互式编码环境，以及来自 O’Reilly 和 200 多个其他出版商的大量文本和视频。更多信息，请访问[*https://oreilly.com*](https://oreilly.com)。

# 如何联系我们

请就本书的评论和问题联系出版商：

+   O’Reilly Media, Inc.

+   1005 Gravenstein Highway North

+   Sebastopol, CA 95472

+   800-889-8969（美国或加拿大）

+   707-829-7019（国际或本地）

+   707-829-0104（传真）

+   *support@oreilly.com*

+   [*https://www.oreilly.com/about/contact.html*](https://www.oreilly.com/about/contact.html)

我们为本书设有网页，列出勘误、示例和任何额外信息。您可以访问[*https://oreil.ly/amazon-redshift-definitive-guide*](https://oreil.ly/amazon-redshift-definitive-guide)。

关于我们的图书和课程的新闻和信息，请访问[*https://oreilly.com*](https://oreilly.com)。

在 LinkedIn 上找到我们：[*https://linkedin.com/company/oreilly-media*](https://linkedin.com/company/oreilly-media)。

关注我们的 Twitter：[*https://twitter.com/oreillymedia*](https://twitter.com/oreillymedia)。

在 YouTube 上观看我们：[*https://youtube.com/oreillymedia*](https://youtube.com/oreillymedia)。

# 致谢

我们要感谢整个亚马逊 Redshift 客户群体，致力于开发这项服务的各个 AWS 团队，产品经理们，工程师们，解决方案架构师团队，以及产品营销团队。没有所有这些团队的支持，这一努力将根本不可能实现！