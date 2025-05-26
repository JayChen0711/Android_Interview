# Flow
- 在协程中，一种可以依序发送多个数据的流。
- 每个数据的计算可以是异步的。
- 类似于迭代器，不同点是它使用挂起函数让生产与消费的过程变成异步的。

# 创建Flow
- flow builder

    val flows:Flow<Int> = flow{ emit(1) }
- 