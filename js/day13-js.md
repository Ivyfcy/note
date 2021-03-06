[TOC]

# 创建对象
## 原型模式
- `每个函数`都有一个 `prototype`（原型）属性,这个属性是一个`指针`，指向一个对象(原型对象包含所有实例共享的属性和方法。)
- 好处：让所有对象实例共享它所包含的属性和方法
### 理解原型对象
- 每个实例都包含了一个内部属性，该属性仅仅指向了Person.prototype(实例与构造函数没有直接的关系)
- 所有原型对象都会自动获得一个`constructor` （构造函数）属性，这个属性包含一个指向 prototype属性所在`函数的指针`(Person.prototype.constructor指向Person)。
- 当调用构造函数`创建一个新实例`后，该实例的内部将`包含一个指针`，指向`构造函数的原型对象`；这个指针叫[[Prototype]]。

**注意：**虽然在脚本中 没有标准的方式访问[[Prototype]],只有浏览器必须部署这个属性，其他运行环境不一定要部署，最好不要使用这个属性；在`每个对象上`都支持一个属性` __proto__`；存在于`实例`与构造函数的`原型对象`之间
- ` __proto__`属性：用来读取或设置当前对象的prototype对象
- 无法访问到[[Prototype]]，可以通过 `isPrototypeOf()方法`来确定对象之间是否存在这种关系，[[Prototype]]]是否指向调用`isPrototypeOf()`方法的对象（Person.prototype），是的话方法就`返回true` //Person.prototype.isPrototypeOf(person1）；返回true：因为person1内部有一个指向 Person.prototype 的指针(因为person1是Person构造函数的实例)
-  ECMAScript 5新增`Object.getPrototypeOf()`，在所有支持的实现中，这个 方法`返回[[Prototype]]的值`
![](https://github.com/Ivyfcy/note/blob/master/img/20180612145006.png)

**Object.setPrototypeOf(object，prototype)(写操作)，Object.getPrototypeOf(obj)(读操作)，Object.create（）（生成操作）来代替**
- Object.setPrototypeOf(object，prototype):设置一个对象的prototype对象，返回的是第一个参数本身；
![](https://github.com/Ivyfcy/note/blob/master/img/20180612144904.png)
- Object.getPrototypeOf(obj):用于读取一个对象的prototype对象
![](https://github.com/Ivyfcy/note/blob/master/img/20180612145035.png)
> 以上两个方法：第一个参数不是对象，会自动转为对象；由于`undefined和null无法转为对象`，所以第一个对象是undefined和null`会报错`

![](https://github.com/Ivyfcy/note/blob/master/img/20180612145153.png)
- 不能通过实例重写原型中的值，会先访问实例的值
- 使用`delete操作`可以完全`删除`实例属性，从而能够重新访问原型中的属性
- `hasOwnProperty()`
(从 Object 继承来的)该方法检测一个属性存在实例中还是原型中，存在`对象实例`中返回`true`,否则返会false


