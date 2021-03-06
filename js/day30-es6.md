# 数组的扩展
## 扩展运算符
- 含义：三个点（...）,如同rest参数的逆运算，可以将一个数组变为参数序列
- 扩展运算符与正常的函数参数可以结合使用
- 如果扩展运算符后面是一个空数组，则不产生任何效果
``- console.log(...[1,2,3])//1 2 3
   - function f（v,w,x,y,z）{
     var args=[0,1];
       f(-1,...args,...[3])
    }
   - [...[],1]//[1]
   
  ``
  >没有Iterator接口的类似数组的对象，扩展运算符就无法将其转为真正的数组 
  
## 替代数组的apply方法
- 由于扩展运算符可以展开数组，所以不再需要使用apply方法将数组转为函数的参数
`` Math.max.apply(null,[12,1,2])//es5的写法
    Math.max（...[12,1,2]）//es6的写法
    等同于Math.max(12,1,2)
``
- push()方法的参数不可以是数组，只能通过apply方法变通使用push方法，有了扩展运算符，可以直接将数组传入push方法
``
   var arr1=[1,2,3];
   var arr2=[4,5,6];
   Array.prototype.push.apply(arr1,arr2)//es5
   arr1.push(...arr2)//es6
``
## 合并数组
- es5写法[1,2]concat(more)
- es6写法[1,2,...more]
## 与解构赋值结合
- 扩展运算符与解构赋值结合，用于生产数组
``
   const [first,...rest]=[1,2,3,4,5];
    first//1
    rest//[2,3,4,5]
``
> 如果将扩展运算符用于数组赋值，只能将其放在参数的最后一位，否则报错

## 字符串
- 扩展运算符可以将字符串转为真正的数组
``
   [...'hi']//['h','i']
``
- 以上写法有一个重要的好处，能够正确识别32位Unicode字符
``'x\uD83D\uDE80y'.length//4;JavaScript会将32位Unicode字符识别为2个字符
[...'x\uD83D\uDE80y'].length//3``

## 实现了Iterator接口的对象
- 原型部署了Iterator接口的数据结构有三种，具体包含四种，分别是数组，类似数组的对象，Set和Map结构
## Array.from（）
- 可以将类似数组的对象和可遍历对象转为真正的数组