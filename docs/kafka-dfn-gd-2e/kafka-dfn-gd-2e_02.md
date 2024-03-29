# 前言

对技术书籍的作者来说，最大的赞美是“这是我在开始学习这个主题时希望拥有的书。”这是我们在开始写这本书时为自己设定的目标。我们回顾了我们编写 Kafka、在生产环境中运行 Kafka 以及帮助许多公司使用 Kafka 构建软件架构和管理数据管道的经验，然后问自己：“我们可以与新用户分享哪些最有用的东西，让他们从初学者变成专家？”这本书反映了我们每天所做的工作：运行 Apache Kafka 并帮助他人以最佳方式使用它。

我们包括了我们认为您需要了解的内容，以便成功地在生产环境中运行 Apache Kafka 并在其上构建稳健且高性能的应用程序。我们重点介绍了流行的用例：事件驱动微服务的消息总线、流处理应用程序和大规模数据管道。我们还专注于使书籍通用和全面，以便对使用 Kafka 的任何人都有用，无论用例或架构如何。我们涵盖了实际问题，例如如何安装和配置 Kafka 以及如何使用 Kafka API，并且我们还专门介绍了 Kafka 的设计原则和可靠性保证，并探讨了 Kafka 的一些令人愉快的架构细节：复制协议、控制器和存储层。我们相信，对 Kafka 的设计和内部原理的了解不仅对那些对分布式系统感兴趣的人来说是一种有趣的阅读，而且对于那些在部署 Kafka 并设计使用 Kafka 的应用程序时寻求做出明智决策的人来说也是非常有用的。您对 Kafka 的工作原理了解得越多，您就能更多地做出关于工程中涉及的许多权衡的明智决策。

软件工程中的一个问题是，总是有多种方法可以做任何事情。诸如 Apache Kafka 之类的平台提供了很大的灵活性，这对专家来说是很好的，但对初学者来说会造成陡峭的学习曲线。很多时候，Apache Kafka 告诉您如何使用一个功能，但并没有告诉您为什么应该或不应该使用它。在可能的情况下，我们试图澄清现有的选择、涉及的权衡以及您应该何时以及不应该使用 Apache Kafka 提供的不同选项。

# 谁应该阅读这本书

*Kafka：权威指南*是为开发使用 Kafka API 的应用程序的软件工程师以及在生产环境中安装、配置、调优和监控 Kafka 的生产工程师（也称为 SRE、DevOps 或系统管理员）编写的。我们还考虑了数据架构师和数据工程师——他们负责设计和构建组织的整个数据基础设施。一些章节，特别是第[3]章、[4]章和[14]章，是针对 Java 开发人员的。这些章节假设读者熟悉 Java 编程语言的基础知识，包括异常处理和并发等主题。其他章节，特别是第[2]章、[10]章、[12]章和[13]章，假设读者具有在 Linux 上运行的经验，并对 Linux 中的存储和网络配置有一定的了解。本书的其余部分讨论了更一般的 Kafka 和软件架构，并不假设特殊知识。

另一类可能对本书感兴趣的人是那些不直接使用 Kafka 但与使用 Kafka 的人一起工作的经理和架构师。他们理解 Kafka 提供的保证以及员工和同事在构建基于 Kafka 的系统时需要做出的权衡同样重要。本书可以为希望让员工接受 Apache Kafka 培训或确保团队了解他们需要了解的内容的经理提供支持。

# 本书中使用的约定

本书使用以下排版约定：

*斜体*

指示新术语，URL，电子邮件地址，文件名和文件扩展名。

`常量宽度`

用于程序清单，以及在段落中引用程序元素，如变量或函数名称，数据库，数据类型，环境变量，语句和关键字。

**`常量宽度粗体`**

显示用户应该按照字面意思输入的命令或其他文本。

*`常量宽度斜体`*

显示应由用户提供的值或由上下文确定的值替换的文本。

###### 提示

这个元素表示提示或建议。

###### 注

这个元素表示一般说明。

###### 警告

这个元素表示警告或注意。

# 使用代码示例

如果您对代码示例有技术问题或问题，请发送电子邮件至*bookquestions@oreilly.com*。

本书旨在帮助您完成工作。一般来说，如果本书提供示例代码，您可以在程序和文档中使用它。除非您复制了代码的大部分，否则您无需联系我们以获得许可。例如，编写一个使用本书中几个代码块的程序不需要许可。出售或分发 O'Reilly 书籍中的示例需要许可。引用本书并引用示例代码来回答问题不需要许可。将本书中大量示例代码合并到产品文档中需要许可。

我们感谢您的使用，但不需要署名。署名通常包括标题，作者，出版商和 ISBN。例如：“*Kafka: The Definitive Guide* by Gwen Shapira, Todd Palino, Rajini Sivaram, and Krit Petty (O’Reilly). Copyright 2021 Chen Shapira, Todd Palino, Rajini Sivaram, and Krit Petty, 978-1-491-93616-0。”

如果您认为您使用的代码示例超出了合理使用范围或上述给出的许可，请随时通过*permissions@oreilly.com*与我们联系。


# 致谢

我们要感谢许多为 Apache Kafka 及其生态系统做出贡献的人。没有他们的工作，这本书就不会存在。特别感谢 Jay Kreps，Neha Narkhede 和 Jun Rao，以及他们的同事和领导 LinkedIn，共同创造了 Kafka 并将其贡献给 Apache 软件基金会。

许多人对书的早期版本提供了宝贵的反馈意见，我们感谢他们的时间和专业知识：Apurva Mehta，Arseniy Tashoyan，Dylan Scott，Ewen Cheslack-Postava，Grant Henke，Ismael Juma，James Cheng，Jason Gustafson，Jeff Holoman，Joel Koshy，Jonathan Seidman，Jun Rao，Matthias Sax，Michael Noll，Paolo Castagna 和 Jesse Anderson。我们还要感谢许多读者通过初稿反馈网站留下评论和反馈。

许多审阅者帮助我们，极大地提高了这本书的质量，所以留下的任何错误都是我们自己的。

我们要感谢我们的 O'Reilly 第一版编辑 Shannon Cutt，她的鼓励和耐心，远远超过了我们。我们的第二版编辑 Jess Haberman 和 Gary O'Brien 在全球挑战中帮助我们保持在正确的轨道上。与 O'Reilly 合作对于作者来说是一次很棒的经历——他们提供的支持，从工具到书签名，都是无与伦比的。我们感谢所有参与使这一切成为可能的人，我们感激他们选择与我们合作。

我们还要感谢我们的经理和同事，在写作过程中给予我们支持和鼓励。

Gwen 要感谢她的丈夫 Omer Shapira，在写作了又一本书的许多个月里给予她的支持和耐心；她的猫 Luke 和 Lea，因为它们是可爱的；以及她的父亲 Lior Shapira，教会她即使看起来艰巨，也要始终接受机会。

Todd 没有他的妻子 Marcy 和女儿 Bella 和 Kaylee 的支持，他将一事无成。他们对他写作的额外时间和长时间奔波的支持使他能够坚持下去。

Rajini 要感谢她的丈夫 Manjunath 和儿子 Tarun，感谢他们始终如一的支持和鼓励，感谢他们在周末审阅早期草稿，以及始终在她身边。

Krit 与妻子 Cecilia 和两个孩子 Lucas 和 Lizabeth 分享他的爱和感激之情。他们的爱和支持使每一天都充满了快乐，没有他们，他将无法追求自己的激情。他还要感谢他的妈妈 Cindy Petty，她灌输给 Krit 的愿望是永远成为最好的自己。
