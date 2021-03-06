# 闭包
- `作用域链`本质上是一个`指向变量对象的指针列表`，它只 引用但不实际包含变量对象
- 解除对闭包里的匿名函数的引用：`compareNames = null`；因为函数在执行完毕后，匿名函数（闭包）的作用域链仍然在引用外部函数活动对象，所以活动对象不会被销毁；换句话说，当 createComparisonFunction()函数返回后，其执行环境的`作用域链会被销毁`，但它的`活动对象仍然会留在内存中`；`直到匿名函数被销毁后`，createComparisonFunction()的活动对象才会被销毁
- compareNames = null:解除该函数的引用，就等于通知垃圾回收例程将其清除。随着匿名函数的作用域链被销毁，其他作用域 （除了全局作用域）也都可以安全地销毁了
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612161532.png)

- 自调用函数/匿名函数/立即执行函数：（function(){}）()
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612161611.png) 
- 慎重使用闭包：闭包会携带包含它的函数的作用域，占用更多的内存

