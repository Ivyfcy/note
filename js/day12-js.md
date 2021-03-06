[TOC]

# 创捷对象

### 工厂模式
> Object构造函数和对象字面量都可以创建单个对象，缺点：使用同一个接口创建很多对象，会产生大量的重复代码

- 用函数来封装以特定接口创建对象
- 缺点：没有解决对象识别的问题
![](https://github.com/Ivyfcy/note/blob/master/img/20180612115434.png)

### 构造函数
- 构造函数是用来初始化对象的（创建对象的）
- 任何函数使用`new操作`符来调用，就是构造函数（构造函数和普通函数的唯一区别：调用方式不同）
- 构造函数没有return语句，但是默认返回值是新对象(如果是普通函数没有return语句会返回undefined)
- 直接将属性和方法赋给了this对象
- 大写字母开头
- 在构造函数的属性和方法后面添加return xx，会默认返回新对象，无视return后面的值，如果是Object类型的值return {}，将不会返回新创建的对象，而返回return 后面的值
![](https://github.com/Ivyfcy/note/blob/master/img/20180612115600.png)

- 缺点：每个方法都要在每个实例上重新创建一遍，person1 和 person2 都有一个名为 sayName()的方法，两个方法不是同一个 Function 的实例。函数是对象，因此每定义一个 函数，也就是实例化了一个对象(`不同实例上的同名函数是不相等的`，如果`比较运行结果是会相等的`，如下图)
![](https://github.com/Ivyfcy/note/blob/master/img/20180612115642.png)
#### 当普通函数调用
- 普通函数调用时，函数里this指向window
![](https://github.com/Ivyfcy/note/blob/master/img/20180612115713.png)
