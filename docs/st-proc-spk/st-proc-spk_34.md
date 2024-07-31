# 第四部分：高级 Spark Streaming 技术

在本部分中，我们将检查一些更高级的应用，您可以使用 Spark Streaming 创建这些应用，即近似算法和机器学习算法。¹

近似算法为推动 Spark 的可扩展性提供了一扇窗口，并且在数据吞吐量超过部署能力时，提供了一种优雅降级的技术。在本部分中，我们涵盖：

+   哈希函数及其在草图构建块中的使用

+   HyperLogLog 算法，用于计算不同元素的数量

+   Count-Min-Sketch 算法，用于回答关于结构顶部元素的查询

我们还介绍了 T-Digest，这是一个有用的估计器，允许我们使用聚类技术对值分布进行简洁表示。

机器学习模型提供了一些新技术，能够在不断变化的数据流上产生相关且准确的结果。在接下来的章节中，我们将看到如何调整已知的批处理算法，例如朴素贝叶斯分类、决策树和 K-Means 聚类，使其适应流式处理。这将使我们依次涵盖：

+   在线朴素贝叶斯

+   Hoeffding 树

+   在线*K*-均值聚类

这些算法将形成他们在批处理形式下处理 Spark 中的流的补充，在[[Laserson2017]](app04.xhtml#Laserson2017)中。这将为您提供强大的技术，用于对数据流的元素进行分类或聚类。

¹ 虽然我们重点介绍 Spark Streaming，但我们描述的一些算法（如 HyperLogLog）已经作为 Spark 的一部分内置函数存在，例如 `approxCountDistinct`，它们作为 DataFrames API 的一部分。