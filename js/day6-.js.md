> 由于昨天看了电视剧导致学习时间不够，整理笔记不够5个知识点，而且今早也没背单词，为了作为惩罚发红包给大神

[TOC]

# Array类型
## 位置方法
- 位置方法：indexOf()，lastIndexOf()，接收两个参数（要查找的项，查找起点位置的索引(可选)）；返回查找的项在数组中的位置，没有找到返回-1；
- 查找时的比较`严格等于`(===)
- indexOf()，从数组的开头开始向后找
- lastIndexOf()，从数组的末尾开始向前找
- 意外：indexOf()结合for循环可以实现数组去重
![](https://github.com/Ivyfcy/note/blob/master/img/4919eaa1-3628-4713-916e-76f1d3ab5a8e.png)
## 迭代方法，归并方法
- 数组有5种迭代的方法；接收两个参数(函数，函数的作用域对象(影响this的值)(可选))；不会修改数组的值
- 传入的函数接收`三个参数`：数组项的值，该项在数组中的位置，数组对象的本身
 - forEach()：`没有返回值`,本质上和for循环迭代数组一样
 - map():让数组通过某种计算产生一个`新数组`(返回函数每次调用的结果组成的数组)
 - filter():筛选出数组中符合条件的项(因为传入的函数对符合项返回true)，组成`新数组`
 - every():检测数组`每一项是否`符合条件，对`每一项都返回true`，则结果返回true
 - some():检测数组`是否有些项`符合条件，`某一项返回true`，则结果返回true
- 2种归并数组的方法
 - reduce():接收一个函数作为累加器，数组中的每个值(从左到右)开始缩减，最终为一个值；传入的函数接收`四个参数`:前一个值，当前值，项的索引，数组对象。
 - reduceRight():则从数组的最后一项开始，向前遍历到第一项

![](https://github.com/Ivyfcy/note/blob/master/img/20170207110723394.png)

## toString()
- 返回一个反映这个对象的字符串
![](https://github.com/Ivyfcy/note/blob/master/img/f3e505a7-1dad-48ad-9eee-ca31d3691220.jpg)
- 打印的值是30；因为toString方法被重写了,打印30是Number，不是字符串

# Date 类型
- new 操作符创建一个日期对象；不传递参数的情况下，获得当前的日期和时间；var date = new Date();如果参数时`数值`，年份，月份...
- 转日期毫秒数：Date.parse()，Date.UTC()；最好用**moment.js** 这类工具去处理。
- `+ 操作符`可以把Date对象转换日期毫秒数;与`Date.now()`方法一样作用；![](https://github.com/Ivyfcy/note/blob/master/img/c83a2e6a-05ef-4458-8d69-e857b8309e6a.png)
 - Date.parse():接收一个参数：`日期的字符串`；无法识别参数返回NaN;Date.parse(new Date())也是可以
 - 直接将日期的字符串(数值)传递给Date构造函数，在后台会调用Date.parse()（Date.UTC()）//new Date('May 25,2004')===new Date(Date.parse('May 25,2004'))
 - Date.UTC()，参数(`数值`)：年，月(基于0的月份)，日
- Date类型的valueOf();返回当期日期和时间的毫秒
## 日期/时间组件方法
- getTime()，返回毫秒数，与valueOf()方法返回的值相同
- getFullYear()，返回年份
- getMonth()，返回月份，0~11
- getDate()，返回天数，1~31
- getDay()，返回星期几，0~6（星期日为0）
- getHours()，返回小时数，0~23（14：30返回14）
- getMinutes()，返回分钟数，0~59
- getSeconds()，返回秒数，0~59
- getMilliseconds()，返回毫秒数



