2018-05-06 17:07:26 星期日
# 基本概念
## 语法
### 标识符
- 标识符就是指变量，函数，属性的名字，或者函数的参数
- 规则：第一个字母必须是：字母，下划线，美元符号（$），其他字符可以是字母，下划线，美元符号（$）或数字
- 格式：采用驼峰大小写（第一个字母小写，剩下的每个单词的首字母大写）
- 命名规则
  - 第一个字符不能是数字，必须是字母或下划线
  - 区分大小写
  - 不能是保留字，关键字

### 严格模式
- 严格模式是为js定义了一种不同的解析与执行模型
- 一些js糟糕的特性都会被禁用，比如不能用with
- 严格模式中对函数有一些限制（把函数或参数命名为eval或arguments；不能出现两个命名参数同名）？
- 严格模式中，不能为函数的caller属性赋值，否则会导致错误
- 严格模式中，函数访问arguments.callee会导致错误
- 严格模式中，（初始化未经声明的变量会导致错误）所有的变量都要先声明，如果给一个未声明的变量，函数，函数参数，catch从句参数或全局对象的属性赋值，将会抛出一个引用错误；
  在非严格模式中，这种隐式声明的全局变量的方法是给全局对象新添加一个新属性
- 在严格模式中，delete运算符后跟随非法的标识符时，会抛出一个语法错误异常，试图删除一个不可配置的属性将抛出一个类型错误异常
- 在严格模式中，在一个对象中存在两个或多个同名属性将产生一个语法错误（非严格模式中不会报错）
- 在严格模式中，调用的函数（不是方法）中的一个this值是undefined；在非严格模式中，调用的函数中的this值总是全局对象
![](https://github.com/Ivyfcy/note/blob/master/img/20180612105023.png)

## 关键字和保留字
- 关键字：可用于表示控制语句的开始或结束，或者用于执行特定操作等
- 保留字：在js里现在还没特定的用途，但有可能在将来被用作关键字
- 不能用作标识符

## 变量
- 变量是松散类型的（用来保存任何类型的数据），每个变量仅仅是一个用来保存值的占位符而已
- 未经过初始化的变量，会保存一个特殊值-undefined

## 数据类型（参考day1-js）
>  数据类型转换的规则：如果是一个值，判断真假，遵循：只有0 NaN null "" undefined 这个5个是假的，其余都是真的

### Number类型（正数，负数，0，NaN）
- 不要测试某个特定的浮点数值
  - 例子：(如果这两个数是0.1和0.2，那么测试将无法通过，如果是0.05和0.25等不会有问题)
        if（a+b==0.3）{
        alert（"you got 0.3"）
        }
- 数值范围
  - Infinity（正无穷大）不能参与计算
  - -Infinity（负无穷大）不能参与计算
  - 想确定数值是不是有穷的，使用isFinite（）函数
  - NaN(不是一个有效的数字)
  - isNaN（）函数，判断是`有效数值`返回false，不是返回true。if检查的不是number类型的值，浏览器会默认的把它转化成number类型，然后再判断是否为有效数字
- 数值转换
  - 强制转化：Number（）
  - 非强制转换：`parseInt（）`识别各种整数格式：十进制，八进制等等（有`两个参数`parseInt(string, radix)）；`parseFloat（）`只解析十进制（只有`一个参数`parseFloat（string））,其他都为NaN；转换原理：从左到右，一个个字符查找，把是数字的转换为有效的数字，中途遇到了一个非有效数字，就不再继续查找。
   **注意：**parseInt（）将字`符串转`换成数字（传入的第一参数一定会被转换为字符串，然后再转Number）
![](https://github.com/Ivyfcy/note/blob/master/img/00b3a63f-6cc5-4808-849b-8773754bb208.png)
  - parseInt（''）//NaN；parseFloat（''）//NaN
  - Number('')//0
  - if两个值比较是否相等（==会进行默认的数据类型转换）
    - 对象==对象 //如果是两个独立的对象永远不相等，除非赋值再比较如下图（对象的地址相比较对象的地址相比较），
    ![](https://github.com/Ivyfcy/note/blob/master/img/93c5129e-afb6-4be8-9014-4bbcf5653646.png)
    - 对象==字符串//先将对象转换为字符串（toString（））再比较
    - 对象==布尔类型//先将对象转换为字符串（toString（））然后再转换为数字；布尔类型转换成数字
    - 对象==数字//先将对象转换为字符串然后再转换为数字
  - Number（）函数转换规则：
 - 如果对象：调用对象的valueOf()，然后按规则转换返回值。如果结果NaN,则调用对象的toString(),然后再按规则转换返回的字符串值

### String类型
- 转换为字符串
- toString()数值，布尔值，对象和字符串值都有toString（）方法。但是`null和undefined值没有这个方法`，如果用了就会报错。解决方法：在不知道要转换的值是不是null或undefined时，可以先使用转型函数String()，String()能够将任何类型的值转换为字符串
- 调用`数值`的 toString()方法时，可以传递`一个参数`/toString(2),toString(8),toString(16)...转换成相对应进制的字符串；被转的字符不为数字，参数无效等于toString()
- ""+value
- JSON.stringify(jsonobj) //可以将json对象转换成json字符串
- JSON.parse(jsonstr); //可以将json字符串转换成json对象
- 字符字面量
  - String 数据类型包含一些`特殊的字符字面量`，也叫`转义序列`
    ![](https://github.com/Ivyfcy/note/blob/master/img/6601d501-cff0-4830-b347-2225534a8450.png)
  - 字符字面量可以出现在字符串中的任意位置，而且也将被作为`一个字符`来解析(在算字符串长度length时，+1)
      ![](https://github.com/Ivyfcy/note/blob/master/img/2cfd92db-dfcf-47b3-a84c-a2571f24426f.png)
    **注意**：点和空格（. ）算一个字符；即使点在转义字符后面也算一个字符
    ![](https://github.com/Ivyfcy/note/blob/master/img/5954e05b-7c91-4aee-89c0-1b97330fcc62.png)
  - 如果字符串中包含`双字节字符`，那么 length 属性可能不会精确地返回字符串中的字符数目。
### Object类型
- valueOf():获取当前对象的值
- toString():获取当前对象字符串表示的值
- toLocaleString()：返回一个 String 对象，这个对象中包含了用当前区域设置的默认格式表示的日期。返回的结果是随机器不同而不同的
## 操作符
- 一元操作符
  - 递增和递减操作符
    - 前置型：先+-再执行：++age
    - 后置型：先执行再+-；age++
  - 一元加和减操作符
    - +就会像Number()转型函数一样对这个值执行转换
    - 位操作符  > ？需要了解吗   

## eval()是做什么的
- 将字符串转换成js代码并运行，返回执行结果
- 将Json字符串转换成Json对象:eval('(' + jsonstr + ')')注意：json字符外包裹一对小括号;不推荐，因为这种方式不安全eval会执行json串中的表达式。

## 数组
- 数组的项数保存在其length属性中
- 为数组`添加类属性`，但是并没有添加到数组的项数中，而且只能用AA[name]访问到属性值
![](https://github.com/Ivyfcy/note/blob/master/img/20180612111338.png)
- 为数组添加类属性值，toString（），valueOf（）的方法返回值不一样，toString（）会返回由数组中每个值的字符串形式拼接而成的一个一逗号分隔的字符串；valueOf（）返回的数组的本身（指针）
![](https://github.com/Ivyfcy/note/blob/master/img/20180612112100.png)
- 所以在数组比较的时候toString（）跟数组中的每个项数值有关，跟数组类属性无关；valueOf（）跟数组的本身有关
![](https://github.com/Ivyfcy/note/blob/master/img/20180612113545.png)
### 创捷数组基本方式两种：
  - 使用Array构造函数，
  - 数组字面量表示法
- 检测某个值是否为数组：Arrary.isArrary(value)//Array.isArray(arr) === true;

### length属性
- length属性是不可枚举的属性（for-in语句是用来遍历对象的每一个属性名和属性值，获取属性值只能通过对象名[key]来获取），它不是只读的，可以从数组末尾移除项或向数组添加新项
### 数组操作方法
- concat()连接产生新的数组（`原数组保持不变`）；没传递参数时，只是复制当前数组并返回副本；有参数时，每一项添加到结果数组
- slice()返回一个数组的子集（新数组），slice(start，end)返回数组`不包含结束处的元素（原数组保持不变）`；参数可以为负数，则用数组长度加上该数来确定相应的位置。//5项的数组：slice(-2,-1)=slice(3,4)
- join(',')只接受一个参数（分隔符），不传参时默认是逗号分隔符join（）=join（","），`只用于数组`;返回从数组创建的字符串（从数组元素生成一个`字符串`） [1,2]->['1','2'];`原数组不变`，返回`字符串`
> ![](https://github.com/Ivyfcy/note/blob/master/img/20180612112715.png)
> 如果数组中某一项的值式nll，undefined ，那么该值在join(),toString(),toLocaleString(),valueOf()方法回来的结果中以空字符串表示 
- Array.valueOf()方法:如果希望返回一个数组元素，但又不想让它们转化成字符串
- 栈方法：后进先出 push(),pop()
- 队列方法：先进先出 push(),shift()
  - pop()移走最后一个元素，并且`返回该元素`的值->就是`移除的项`（不返回一个新的数组，`改变已有的数组`）
  - push()加入到数组后面的值，`返回修改后数组的长度`（不返回一个新的数组，`改变已有的数组`）
  - shift()移除第一个元素，并`返回它的值(移除的项)`，同时将数组的长度减1
  - unshift()在数组的前端添加任意项并`返回新数组的长度`

### 重排序方法
 - reverse() 数组元素的顺序求反`(改变原数组)`
 - sort()`(改变原数组)`，为数组排序sort(Function)
  - Function可选，函数名if省略（如果没有参数，调用每个数组的`toString()`方法，比较·`字符串`），数组元素按字母顺序排序
  - Function函数要有2个参数
  - 必须定义一个返回数字值的表达式
    - 正序:element1排element2之前，函数返回一个负数（return -1）
    - 倒序:element1排element2之后，函数返回一个正数（return 1）
    -  element1，element2相等，返回0

### splice()删除，取代，插入元素（改变原数组）
- `返回一个数组(删除的项)`,该数组中包含从原始数组中删除的项（if没有删除项，则返回空数组）
- splice(start，element-to-delete，value1，value2...)
- start:一个数字（数组索引值）：删除第一项的位置
- element-to-delete（可选）从start处开始要删除元素的个数，if省略，则从start处开始到数组的最后 全删
- value1...插入数组的值

