# BOM
## window对象
- BOM的核心对象是window
### 全局作用域 
-  window 对象也等于 Global 对象
- 因此所有在全局作用域中声明的变量、函数都会变成 window 对象的属性和方法
- 定义全局变量与在 window 对象上直接定义属性还 是有一点差别：`全局变量不能通过 delete 操作符删除`，而直接在 window 对象上的定义的属性可以
- 尝试访问未声明的变量会抛出错误，但是通过查询 window 对象，可以知道某个可能未声明的变量是否存在
![](https://github.com/Ivyfcy/note/blob/master/img/20180612163330.png) 
### 窗口关系及框架
- 如果页面中包含框架，则每个框架都拥有自己的window 对象，并且保存在frames 集合中
- 每个 window 对象都有一个 name 属性，其中包含框架的名称？？？
- `top 对象始终指向高（外）层的框架`，也就是浏览器窗口
- 与 top 相对的另一个 window 对象是parent,parent（父）对象始终指向当前框架的直接上层框架。parent 有可能等于 top；但在没有框架的情况下，parent 一定等于 top（此时它们都等于 window）
> 除非高层窗口是通过 window.open()打开的,否则其 window 对象 的 name 属性不会包含任何值

- 与框架有关的后一个对象是 self，它始终指向 window,实际上，self 和 window 对象可以互 换使用。引入 self 对象的目的只是为了与 top 和 parent 对象对应起来,所有这些对象都是 window 对象的属性，可以通过 window.parent、window.top 等形式来访问
### 窗口位置
- 表示窗口相对于屏幕左边和上边的位置：screenLeft属性，screenTop 属性
- 使用下列代码可以跨浏览器取得窗口左边和上边的位置
``var leftPos = (typeof window.screenLeft == "number") ? window.screenLeft :window.screenX;
var topPos = (typeof window.screenTop == "number") ?window.screenTop : window.screenY;``
- 使用 moveTo() 和 moveBy()方法倒是有可能将窗口精确地移动到一个新位置
- moveTo()接收的是新位置的 x和 y坐标值
- moveBy()接收的是在水平和垂直方向上移动的像素数
![](https://github.com/Ivyfcy/note/blob/master/img/20180612163410.png) 
