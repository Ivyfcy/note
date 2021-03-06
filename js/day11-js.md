
# 面对对象的程序设计（第6章）
## 理解对象-属性类型
- 每个对象都是基于一个引用类型创建的
### 数据类型
- 数据属性包含一个数据值的位置，可以读取和写入值。4个特性：
  - [[Configurable]]：表示能否通过 delete 删除属性从而重新定义属性
  - [[Enumerable]]：表示能否通过 for-in 循环返回属性
  - [[Writable]]：表示能否修改属性的值
  - [[Value]]：包含这个属性的数据值。读取属性值的时候，从这个位置读；写入属性值的时候， 把新值保存在这个位置。这个特性的默认值为 undefined
- 要`修改属性默认的特性`，必须使用`Object.defineProperty()`方法有3个参:数属性所在的对象,属性的名字,一个描述符对象(configurable、enumerable、writable 和 value)
  - 在调用Object.defineProperty（）方法时，如果不指定，configure，enumerable和writable特性的默认值都是false
![](https://github.com/Ivyfcy/note/blob/master/img/20180612115134.png)

  - 以上图片分析：在严格模式下, name 的属性只读的，不可修改的，如果尝试为它指定新值,会报错
  - 非严格模式下，赋值操作将被忽略
-  configurable 设置为 false，表示不能从对象中删除属性。如果对这个属性调用 delete，则 在非严格模式下什么也不会发生，而在严格模式下会导致错误。
- writable一旦定义为不可配置的， 就不能再把它变回可配置了。此时，再调用 Object.defineProperty()方法修改除 writable之外的特性(包括自身)，都会报错
**注意**只能在 DOM 对象上使用这个方法，多数情况下，可能都没有必要利用 Object.defineProperty()

### 访问器属性
- getter和 setter函数，4个特性：
- [[Configurable]]：表示能否通过 delete 删除属性从而重新定义属性，能否修改属性的特 性，或者能否把属性修改为数据属性
- [[Enumerable]]：表示能否通过 for-in 循环返回属性
-  [[Get]]：在读取属性时调用的函数。默认值为 undefined
- [[Set]]：在写入属性时调用的函数。默认值为 undefined。 
- 访问器属性不能直接定义，必须使用 `Object.defineProperty()`来定义
- 设置一个属性的值会导致其他属性发生变化。 
![](https://github.com/Ivyfcy/note/blob/master/img/20180612115230.png)

## 定义多个属性
- 一次为对象定义多个属性: Object.definePro- perties()方法：两个对象参数：对象，添加或修改的属性
## 读取属性的特性 
-  Object.getOwnPropertyDescriptor()
## 获取属性的值
- 点（.）：属性名用一个标识符来表示，标识符必须直接出现在JavaScript程序中，他们不是数据类型，程序无法修改他们
- 方括号（[表达式]）:表达式必须返回字符串（或返回一个可以转换为字符串的值）；属性名通过字符串来表示，字符串是JavaScript的数据类型，在程序运行时可以修改和创建它们。//customer["adress"+i]