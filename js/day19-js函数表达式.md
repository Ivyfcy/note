[TOC]

# 函数表达式
- 定义函数的 方式有两种：一种是函数声明，另一种就是函数表达式
- 函数声明，重要特征就是函数声明提升（sayHi(); function sayHi(){alert("Hi!")}；//可以把函数声明放在调用它的语句后面）
- 函数表达式，没有函数声明提升，与其他表达式一样，在使用前必须先赋值
- 函数体内变量提升：如果全局有声明a变量函数体内在最好也声明了a变量，在函数体内先打印a则为undefined
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612160959.png)
## 递归
- 递归函数是在一个函数通过名字调用自身（处理中：每次处理的对象，都是前一次返回的值）
- 在递归函数调用自身函数，调用函数变量名，耦合性太强很危险
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612161036.png)
> 如果像 return num * factorial(num-1);调用自身函数名，如果在代码中重新声明一个变量a，这个变量等于factorial（指针指向factorial）；然后再设置factorial=null时，再调用a(4)会报错

- 解决递归函数调用自身函数的问题
  - arguments.callee 是一个指向正在执行的函数的指针（严格模式下不能访问arguments.callee）
  - 使用命名函数表达式；创建了f()的命名函数表达式，将它赋值给变量 factorial。即便把函数赋值给了另一个变量，函数的名字 f 仍然有效，所以递归调用照样能正确完成。
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612161103.png)
 
