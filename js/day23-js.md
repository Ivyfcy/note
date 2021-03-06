# 内存泄漏
- 闭包会引用包含函数 的整个活动对象，而其中包含着 element。即使闭包不直接引用 element，包含函数的活动对象中也 仍然会保存一个引用
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612162001.png) 
> ，通过把 element.id 的一个副本保存在一个变量中，并且在闭包中引用该变量消 除了循环引用。但仅仅做到这一步，还是不能解决内存泄漏的问题,把 element 变量设置为 null。这样就能够解除对 DOM对象的引 用，顺利地减少其引用数，确保正常回收其占用的内存。

# 模仿块级作用域
- 变量 i 是定义在 ouputNumbers()的活动对象中的，从它有定义开始，就可以在函数内部随处访问它。即使像下面这样`错误地重新声明同一个变量`，也`不会改变它的值`
``function outputNumbers(count){
 for (var i=0; i < count; i++){
 console.log(i);     }
 var i;//重新声明变量。
 alert(i); } outputNumbers(5)``
- 匿名函数可以用来模仿块级作用域来避免以上问题
- 匿名函数语法：（function(){//这里就是块级作用域})()
- 不可以用函数的值直接取代函数名，function 关键字当作一个函数声明的开始，函数声明后面不能跟圆括号。然而函数表达式的后面可以跟圆括号：如下
![](https://github.com/Ivyfcy/note/blob/master/img/20180612162058.png) 

