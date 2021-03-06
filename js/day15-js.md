[TOC]

# 创建对象
## 原型模式
### 原型的动态链
- 对原型对象所做的任何修改都能立即从实例上反映，不在乎是先创建实例还是先修改原型，实例依然可以访问原型上的属性和方法
- 因为`实例和原型之间的连接是一个指针`
- 如果重写原型对象:调用构造函数时会为实例添加一个指向初原型的 [[Prototype]]指针，而把`原型重写`为另外一个对象就等于`切断了构造函数与初原型之间的联系`。 **实例中的指针仅指向原型，而不指向构造函数**
  - 在调用构造函数创建`实例之前重写原型`；可以正常调用原型里的方法
    ![](https://github.com/Ivyfcy/note/blob/master/img/20180612154059.png)

  - 在调用构造函数创建`实例之后重写原型`;调用原型里的`方法会报错`，但是调用重写原型对象里的`属性得到undefined`
![](https://github.com/Ivyfcy/note/blob/master/img/20180612154148.png)
  
### 原生对象的原型
- 原型模式的重要性不仅体现在创建自定义类型方面，所有原生的引用类型（Object，Arrsy，String，等等）都在构造函数的原型上定义了方法，eg：在 Array.prototype 中可以找到 sort()方法，而在 String.prototype 中可以找到 substring()方法
- 通过原生对象的原型，不仅可以取得默认方法的引用，还可以定义新方法（但是不推荐修改原生对象原型）
![](https://github.com/Ivyfcy/note/blob/master/img/20180612154307.png)
- `安全扩展内置对象(原生对象)`:写一个函数使之原型等于原生函数的实例，这样这个函数就继承了原生对象那就可以使用原型对象的属性和方法。
eg:function MyArray(){}
    var arr =new Array();
    MyArray.prototypr=arr;
    MyArray.push(1)

### 原型对象的问题
- 缺点：
  - `省略了`为构造函数`传递初始化参数`，结果所有实例在 默认情况下都将取得相同的属性值
  - 对于包含`引用类型值的属性`来说;由于 friends 数组存在于 Person.prototype 而非 person1 中，所以person1.friends.push("Van")的修改也会通过person2.friends（与 person1.friends 指向同一个数组，都是原型对象的属性）反映出来
![](https://github.com/Ivyfcy/note/blob/master/img/20180612155159.png)

- 因为以上缺点所以很少看到有人单独使用原型模式的原因所在

