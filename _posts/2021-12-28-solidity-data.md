# Solidity Data Location and Data Type



通常在contract中会发现，一些function中定义变量使用`memory`进行限定，这有怎样的作用？

One of the most confusing concepts in solidity is how to effective use memory and storage.



The EVM has 4 areas where it can store items.

`memory,storage,stack,calldata`

主要涉及生命周期，持久性，value和消耗gas的情况区别。

`Memory`按照字面意思也是`temporary values`，只有在调用function才创建，function执行结束就销毁,cheaper to use.

`Storage`是用来`hold permanent values`,所有的`contract state variables` 都将stored in storage,expensive to use.

那么什么是`contract state variables`？



Stack 通常用于hold small local variables，free to use.

Calldata: This is where all incoming function execution data, including function arguments, is stored. This is a non-modifiable memory location



一般情况下：

- state variables are always in storage
- function arguments are always in memory
- local variables of struct，array or mapping type reference storage by default
- local variables of value type are stored in the stack



Why need interface in contract,what's differents like interface,libray,inhert?how to use it?

Interface just defined functions,where use position will create with address,to call interface function.

so what is library, how to use it?

没有适合的文档解释清楚这几者的关系，以及何时选择使用哪种方式？

