[TOC]

# Function类型

## 定义函数方式
- 定义函数的方式有3种：函数声明；函数表达式；构造函数
## 函数表达式
- 函数表达式：var sum =function (num1,num2){return num1+num2};//`;`一定要有(就像声明其他变量一样)，通过变量sum即可以引用函数（`函数名是指针`）
## 函数指针
- 定义了sum()的函数(funtion sum(num1,num2){return num1+num2})，又声明了变量anotherSum，将sum的值赋值给anotherSum（var anotherSum=sum）这样`anotherSum`和`sum`就都`指向同一个函数`，即使`sum=null，但anotherSum仍然可以正常调用`，sum:不带圆括号的函数名是`访问函数指针`(函数本身)，sum():函数执行的目的就是把函数之前存储的字符串变为js代码。
## 函数声明和函数表达式
- 函数声明和函数表达式`不同点`:函数声明能通过变量访问函数（函数声明提升），而函数表达式会报错
## 函数内部属性
- arguments：类数组对象，保存函数参数。
 - callee属性（指针），指向拥有这个arguments对象的函数；
 - `arguments.callee`(代表函数本身):通常用于阶乘函数;如果在函数中用函数名(),之后函数名=重写函数则运行重写的函数，而我们要的是置型自身函数而不是执行重写函数；目的：为了`解除函数体内的代码与函数名的耦合`P114
 - 严格模式下，函数访问arguments.callee会导致错误
- this:引用的是函数据以执行的环境对象
- caller（函数名.caller）：是调用当前函数的函数引用；哪个函数调用了它，函数名.caller就指向那个函数的引用
 - 为了实现更松散的耦合:可以通过`arguments.callee.caller`来访问相同的信息
 - 严格模式下，不能为函数的caller属性赋值，否则会导致错误
## 函数属性和方法
- length：表示函数希望接收的命名参数的个数
- prototype属性不可枚举的，因此for-in无法发现（第六章详细介绍）
- 两个非继承而来的方法：apply(),call()；看day1-js
- bind():会创捷一个函数的实例，其this值会被绑定到传给bind()函数的值//var aa=say.bind(o)