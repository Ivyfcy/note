[toc]

# 单体内置对象
## Global对象 
- 不属于任何其他对象的属性和方法，最终都是它的属性和方法
- 所有在全局作用域中定义的属性和函数都是Global对象//i是Finite(),isNaN(),parseInt(),parseFloat()

### URL编码方法
- encodeURL(),encodeURLComponent()进行编码，发给浏览器
- encodeURL()主要用于整个URL；不会对本身属于URL的特殊字符进行编码，例如冒号，正斜杆，问号，井字好
- encodeURLComponent()主要用于对URL中的一段；会对它发现的任何非标准字符进行编码（会使用对应的编码替换所有非字母数字字符）；使用更多（在对查询字符串参数）
- 有效的URL不能包含某些字符，例如空格
-----
- decodeURL()：只能对使用encodeURL()替换的字符串进行解码
- decodeURLComponent()能够解码使用encodeURLComponent()编码的所有字符，级解码任何特殊字符的编码

### eval()方法
- 只接受一个参数
- 看day-2
- 在严格模式下，为eval()赋值会导致错误，在外部访问不到eval()中创建的任何变量和函数

### Global对象的属性
- 特殊值：undefined，NaN,Infinity
- 所有原生引用类型的构造函数，像Object，Function都是Global对象

### window对象
- 访问window对象即访问Global对象

## Math对象
###  min()和max()
- 最大值和最小值//var max=Math.max(2,3,6,4)
- 在数组中的最大最小值，用apply()方法// var value=[1,2,3,67,8,4];var max=Math.max.apply(Math,value)
   - 把Math对象作为apply()的第一个参数，从而正确的设置this值

### 舍入方法
- Math.ceil()向上舍入将数值`向上舍入`为最接近的整数
- Math.floor()向下舍入，对数值`向下取整`，即得到`小于或等于`该数值的最大整数
- Math.round()四舍五入
  Math.floor(-12.4)// -13
  Math.floor(-12.5)// -13
  Math.floor(-12.6)// -13

### random()
- 返回[0,1)的一个随机数
- 获取[n-m]之间整数：Math.round(Math.round()*(m-n)+n)
