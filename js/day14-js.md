[TOC]

# 创建对象
## 原型模式
### 原型与in操作符
- 单独使用in
**注意：in操作符判断`数组`时，是判断`索引`是否存在，而不是判断值，索引存在返回true，不存在返回false**
![](https://github.com/Ivyfcy/note/blob/master/img/20180612145900.png)
- 在for-in循环中使1用
- 通过`对象能够访问`给定的`属性`时，返回true,`无论该属性存在于实例中还是原型中`
- 判断该属性在对象中还是原型中：同时使用`hasOwnProperty()方法和in操作符`;只有属性存在于实例中hasOwnProperty()返回true；当in操作符返回true，hasOwnProperty()返回false，判断该属性是原型中的属性
- for-in循环时，返回所有能够通过对象访问的，可枚举的属性，包括实例和原型中的属性
![](https://github.com/Ivyfcy/note/blob/master/img/20180612150007.png)
- `Object.keys()`:要`取得对象上`(就只是传入参数的对象)所有可枚举的实例属性,接收`一个对象参数`,返回一个`字符串数组`（包含所有可枚举属性）
![](https://github.com/Ivyfcy/note/blob/master/img/20180612150050.png)
- `Object.getOwnPropertyNames()方法`:想要得到所有的实例属性，`无论是否可枚举`
![](https://github.com/Ivyfcy/note/blob/master/img/20180612150142.png)
> Object.keys()和 Object.getOwnPropertyNames()方法都可以用来替代 for-in 循环

### 更简单的原型语法
- 下图对象字面量来重写整个原型对象，constructor属性就不再指向person了，而指向Object构造函数（如下图），
- 为了保证整个构造函数-原型-对象之间的关系的合理性，在重写整个原型对象，在新的原型对象中`需要手动重新添加constructor：Person`也确保通过该属性能够访问到适当的值，原生的constructor属性时不可枚举，手动添加属性变成了可枚举
![](https://github.com/Ivyfcy/note/blob/master/img/20180612150257.png)
- Object.defineProperty()
![](https://github.com/Ivyfcy/note/blob/master/img/20180612150330.png)
