[TOC]

# Promise
Promise的精髓是“状态”，用维护状态、传递状态的方式来使得回调函数能够及时调用
- Promise是`异步编程`的一种解决方案，比传统的解决方案（回调函数和事件）更合理强大
- 是一个容器，保存着某个未来才会结束的事件。用于处理异步操作的，异步处理成功了就执行成功的操作，异步处理失败了就捕获错误或者停止后续操作。

## Promise 特点
- `对象的状态不受外界影响，`有三种状态：Pending（初始状态进行中），Fulfilled（已成功），Rejected（已失败）只有异步操作的结果可以决定当前是哪种状态，任何操作都无法改变这个状态。
- `一旦状态改变就不会再变,`Promise对象的状态只有两种可能：Pending->Fulfilled（操作成功）;Pending->Rejected（操作失败）
- 可以将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数
## Promise 缺点
- 无法取消Promise，一旦新建它就会立即执行（所以通常写在函数里），无法中途取消。
- 如果不设置回调函数，Promise内部抛出的错误不会反应到外部。
- 当处于Pending状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）

## Promise基本用法
- Promise对象是一个构造函数，用来生成Promise实例，还提供了 resolve 和 reject 函数让我们执行回调操作；原型上有then、catch等方法
**注意：调用resolve 和 reject并不会终结Promise的参数函数的执行**

```
function runAsync(){
var p = new Promise(function(resolve, reject){ //做一些异步操作
    setTimeout(function(){
        console.log('执行完成');
        resolve('随便什么数据');
    }, 2000);
    console.log('1111执行完成');
})
return p；// 执行了runAsync函数得到了Promise对象
}
// 使用then方法
runAsync().then(function(data){
    console.log(data); //后面可以用传过来的数据做些其他操作;data就是我们在runAsync中调用resolve时传的的参数'随便什么数据'
})
// 输出结果：
1111执行完成
执行完成
随便什么数据
```

> 执行了一个异步操作，也就是setTimeout，2秒后，输出“执行完成”，并且调用resolve方法,并将异步操作的结果作为参数传递出去,then里面的函数就跟我们平时的回调函数一个意思

### Promise.prototype.then()
- 作用：为Promise实例添加状态改变时的回调函数；then方法返回的是一个新的Promise实例；每次 then 调用都会以之前的 then 调用的返回值为参数。

> 为什么不能打印111，222

``` 
var  p=new  Promise((resolve,reject)=>
{ resolve(99+I)})
p.then((val)=>{console.log(111,val)})
.then((val)=>console.log(222,val))
.catch((err)=>console.log(333,err))

// 333 ReferenceError: I is not defined
```

    
```
var  p=new  Promise((resolve,reject)=>
{ resolve(99+I)}
)
p.catch((err)=>console.log(333,err))
.then((val)=>{console.log(111,val)})
.then((val)=>console.log(222,val))
// 333 ReferenceError: I is not defined
 111 undefined
 222 undefined
```
> catch 方法返回的还是一个Promise对象，因此后面还可以接着调用then方法，如果then方法报错与前面的catch无关了，所以可以在最后再加上catch方法捕捉then和前一个catch方法里的错误

### Promise.prototype.catch()
- 它和then的第二个参数一样，用于指定发生错误时的回调函数
- then方法指定的回调函数如果再运行中抛出错误，也会被catch方法捕获
- catch方法返回的还是一个Promise对象，因此后面还可以接着调用then方法
### Promise.all()
- 用于将多个Promise实例包装成一个新的Promise实例；
- 提供了`并行`执行异步操作的能力,并且在所有异步操作执行完后才执行回调(可以并行执行多个异步操作，并且在一个回调中处理所有的返回数据)
- all接收一个`数组参数`；参数会转化为promise实例
- 只有all的参数全部状态变为Fulfilled，参数的返回值组成一个数组，传递给回调函数
- 只要all参数里的任何一个状态变为rejected，此时第一个被rejected的实例的返回值会传递给回调函数
```
      function runAsync1(){
      return new  Promise((resolve,reject)=>{
         setTimeout(function(){
            console.log('异步任务1执行完成');
            resolve('异步执行1的数据');
        }, 1000);
          })
         };
             function runAsync2(){
       return new                  Promise((resolve,reject)=>{
         setTimeout(function(){
            console.log('异步任务2执行完成');
            resolve('异步执行2的数据');
        }, 2000);
        })
        };
        Promise
        .all([runAsync1(), runAsync2()])
         .then(function(results){
       console.log(results);
      });
      // 输出结果：
       异步执行1完成
       异步执行2完成
      ["异步执行1的数据"，"异步执行2的数据"]
```

### Promise.race()
- 用于将多个Promise实例包装成一个新的Promise实例；
- `率先`改变状态的Promise实例的返回值就会传递给回调函数（谁跑的快，以谁为准执行回调）
```
Promise
.race([runAsync1(), runAsync2()])
.then(function(results){
    console.log(results);
});
// 输出结果
异步任务1执行完成
异步执行1的数据
异步任务2执行完成
```

### Promise.resolve()
- 有时需要将现有对象转化为Promise对象
- `Promise.resolve("foot")`等价于 `new Promise
(resolve=>resolve("foot"))`
**注意：resolve的Promise对象是在本轮"事件循环"结束时，而不是在下一轮"事件循环"开始时**
```
setTimeout(function(){
console.log('3333');
},0);//时在下一轮"事件循环"开始时执行
Promise.resolve().then(()=>console.log(2222));//在本轮"事件循环"结束时执行
console.log(11111)// 立即执行
///  输出结果
11111
2222
3333
```

**对比上图**
```
setTimeout(function(){
console.log('3333');
},0);
new Promise((resolve,reject)=>{console.log(99999)})//会等Promise对象执行完再执行下面同步的代码，但是如果在then的回调函数就得等所有同步代码执行完再执行如上图
console.log(11111)
// 输出结果：
99999
11111
3333
```
### Promise.reject()
- Promise.reject()方法的参数会`原封不动`地作为reject的理由变成后续方法的参数。这与Promise.resolve方法不一致