[TOC]

# 基本包装类型
- 3个特殊的引用类型：Boolean，Number，String
- 主要区别：对象的生存期
- 引用类型的对象：使用new操作符创建的引用类型实例，在执行流离开当前作用域之前一直保存在内存中
- 基本包装类型的对象：只存在于一行代码的执行瞬间，然后被销毁。所以我们`不能为基本包装类型值添加属性和方法`
- 使用`new`调用基本包装类型的构造函数，与直接调用同名的`转型函数`是不一样的
![](https://github.com/Ivyfcy/note/blob/master/img/d0dde125-9e80-4397-a7a3-651a8636b446.png)
- 会重写valueOf(),toString(),toLocaleString()；因为所有的对象都继承了Object.prototype 的 valueOf方法，但是Boolean，Number，String改变了valueOf（）方法
![](https://github.com/Ivyfcy/note/blob/master/img/20180612170254.png)
> 如果Number没有重写valueof方法返回的应该是'object'而不是'number' 
![](https://github.com/Ivyfcy/note/blob/master/img/20180612170405.png)
## Boolean类型
- Boolean类型是布尔值对应的引用类型
- typeof操作符对基本类型返回"boolean"，而对引用类型返回"object"
- 布尔表达式中的`所有对象`都会被转换为true
![](https://github.com/Ivyfcy/note/blob/master/img/b0aff54f-2165-48a0-ab09-b043810b2b84.png)
- 最好永远不要使用Boolean对象

## Number类型
-  Number类型是数字值对应的引用类型，创建Number对象,调用Number构造函数时向其中传递相应的数值//var aa=new Number(10)
- toFixed():会按照指定的小数位返回数值的`字符串`表示
![](https://github.com/Ivyfcy/note/blob/master/img/cb65ca05-2a23-4ca6-ab93-7681ba9859aa.png)
- toExponential():返回以`指数表达法`,小数前只有一位，小数后的位数则有参数指定（有效数字位数比指定的位数要多一位）//var n=123456.789;n.toExponential(1)//"1.2e+5"
- toPrecision（）：根据指定的有效数字位数将数字转换字符串 

## String类型
- String 类型是字符串的对象包装类型//var str = new String("hello")

### 字符方法
- charAt()，charCodeAt()接收一个参数，即基于 0 的字符位置。
- charAt()：得到字符
- charCodeAt()：得到字符编码
- []:访问个别字符的方法
![](https://github.com/Ivyfcy/note/blob/master/img/4d196d60-6db9-48f2-aaf7-ea806ca6c7ec.png)

### 字符串操作方法(不会改变原字符串)
- concat():将一个或多个字符串拼接，返回新的字符串//大多情况使用`+`
- 字符串截取有三种：slice()，substr()，substring()
- slice()：看js-day2
- substr()：从索引start开始截取length个字符//substr(start [length ])
  - 返回一个从`指定位置开始的指定长度`的子字符串。
  - 传递`一个负值参数时`，它们的行为相同。
  - 如果start为负数，则start=str.length+start
  - 如果 `length 为 0 或负数`，将返回一个`空字符串`
- substring()：从索引start开始，找到索引end处（不包含end），将找到的字符串返回//substring(start,end):
  - 参数必须是`非负的整数`，或者转换为0
  - 2个参数，会将较小的数作为开始位置，将较大的数作为结束位置

### 字符串位置方法
- 返回字符串的位置索引indexOf()，lastIndexOf()：跟day6-js数组位置方法一样
![](https://github.com/Ivyfcy/note/blob/master/img/dcbfbec2-e8b5-4012-8fd8-1ca633f86c41.png)

## trim()方法
- 会创建一个字符串的副本，`删除`前置及后缀的`所有空格`，然后返回结果（不改变原数组）

### 大小写转换
- toLowerCase()，toUpperCase()：通用方法；
- toLocaleLowerCase()，toLocaleUpperCase()：针对特定地区的实现

###  字符串的模式匹配方法（与day-7 String对象方法一样）
- match(),search(),replace(),split()

### localeCompare()方法
- 比较两个字符串
- 如果字符串在字母表中应该排在字符串参数之前，则返回一个负数（大多数情况下是-1，具体的值要视实现而定）
- 如果字符串等于字符串参数，则返回 0
- 如果字符串在字母表中应该排在字符串参数之后，则返回一个正数（大多数情况下是 1，具体的值同样要视实现而定）
![](https://github.com/Ivyfcy/note/blob/master/img/bdd29f85-731e-48c9-9175-37d431f831c8.png)

### fromCharCode()方法
- 是String 构造函数本身静态方法，与charCodeAt()执行的是相反的操作
![](https://github.com/Ivyfcy/note/blob/master/img/b978ae5e-ac77-4533-b784-4646250bf817.png)
