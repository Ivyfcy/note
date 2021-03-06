## 闭包与变量
-闭包只能取得包含函数中任何变量的最后一个值
- 闭包所保存的是整个变量对象，而不是某个特殊的变量；如下代码：
 ``function aa(){
var result=new Array();
for(var i=0;i<10;i++){
   result[i]=function(){
     console.log(i)
     return i;
   };
  }
   return result;
   };aa()
// 返回一个函数数组,length=10,**[f(),f().....]**
// aa()[0]();数组里每个函数返回的都是**10**；因为数组里每个函数的作用域链中都保存着 aa()函数的活动对象i，所以它们引用的都是同一个变量 i。当 aa()函数返回后，变量 i 的值是 10，所以数组里的函数返回的值同时变化了都为10
``
- 但是，可以通过`创建另一个匿名函数`强制让闭包的行为返回各自不同的索引值;思想：定义了一个匿名函数，并将`立即执行该匿名函数的结果赋给数组`
``
function aa(){
var result = new Array(); 
for (var i=0; i < 10; i++){
** result[i] = function(num){          return function(){
return num;
 };
 }(i);**
 }
 return result; 
 }
``
> 将i赋值给num，立即执行匿名函数并赋值给result[i] (将立即执行该匿名函数的结果赋 给数组);匿名函数有一个参数 num，也就是终的函数要返回的值。在调用每个匿名函数时，我 们传入了变量 i由于函数参数是`按值传递的`，所以就会将变量 i 的当前值复制给参数 num

？？？？？
## this对象
- 在闭包中使用 this 对象也可能会导致一些问题，，`匿名函数的执行环境具有全局性`，因此其 this 对象通常指向 window
- this对象在运行时基于函数的执行环境绑定的（通过call（），apply（）可以改变函数执行环境，，this 就会指向其他对象）
- 每个函数在被调用时都会自动取得两个特殊变量：this 和 arguments
- 在自定义对象里定义匿名函数之前，把this对象赋值给了一个名叫that的变量（var that=this），在定义了闭包之后，闭包可以访问这个变量that.name,这时候that.name指向的是定义的对象，不再是全局对象
- 如果在全局里把对象的方法通过赋值语句赋值给变量后，再执行该方法，该方法里的this指向window//（object.say=object.say)();object里的对象指向window
- 内部函数在搜索变量时，只会搜索到其活动对象为止；看下图
 ![](https://github.com/Ivyfcy/note/blob/master/img/20180612161812.png) 
