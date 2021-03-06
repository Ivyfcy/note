# 模块模式 
- 是为单例(只有一个实例的对象)创建私有变量和特权方法
- 通常以对象字面量的方式来创建单例对象
- 模块模式语法
- ``var singleton = function(){
    //私有变量和私有函数
    var privateVariable = 10;function privateFunction(){
    return false;
    }
    //特权/公有方法和属性
    return {publicProperty: true, publicMethod : function(){                    privateVariable++;return privateFunction();}
    }; }();``
>这种模式在需要对单例进行某些初始化，同时又需要维护其私有 变量时是非常有用的

- 例如：
- ``var application = function(){ 
    //私有变量和函数     var components = new Array(); 
    //初始化     components.push(new BaseComponent()); 
    //公共     return {         getComponentCount : function(){             return components.length;         }, 
        registerComponent : function(component){             if (typeof component == "object"){                 components.push(component);             }         }     }; }();``
        
- 如果必须创建一个对象并以某些数据对其进行初始化，同时还要公开一些能够访问这些私有 数据的方法，那么就可以使用模块模式

# 增强的模块模式 
- 进一步改进了模块模式,适合那些单例`必须是某种类型的实例`，同时还必须添加某些属性和（或）方法对其加以增强的情况
- 例子
- ``
   var singleton = function(){ 
    //私有变量和私有函数     var privateVariable = 10; 
    function privateFunction(){         return false;     } 
    //创建对象     var object = new CustomType(); 
    //添加特权/公有属性和方法     object.publicProperty = true; 
    object.publicMethod = function(){         privateVariable++;         return privateFunction();     }; 
    //返回这个对象     return object; }();
``