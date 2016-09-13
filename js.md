# 参考

* 笔试面试知识整理：http://hit-alibaba.github.io/interview/index.html
* Darren_聂微东 - 关注前端技术：http://www.cnblogs.com/Darren_code/p/interview.html、http://www.cnblogs.com/Darren_code/archive/2011/08/31/JavascripDesignPatterns.html
* 聂微东github：https://github.com/nieweidong
# 一、JS 变量属性

* JS私有变量与方法
* JS特权变量与方法
* JS公共变量与方法
* JS共有静态属性与方法

***
## 1、JS私有变量与方法
   私有变量与方法，是指JS函数内部使用var定义的变量或直接在函数中定义的内联方法。其作用域为当前方法的上下文，不能在方法外部调用。
### 例：
```JS
 function myClass(){
        var private = '我是私有变量';
        function privateMethod(){
            //private可在此调用
            return '我是私有方法';
        }
        //private可在此调用
        privateMethod();//privateMethod调用
    }
```
## 2、JS特权变量与方法
  特权变量与方法，是指方法中使用关键词this定义的方法或变量。
### 特点：
* 可以访问构造器内的私有成员
### 例：
```JS
//定义
function myClass(){
    var private ='私有变量';
    this.protect='我是特权变量';
    this.protectMethod=function(){
        return '我是特权方法'+'我调用了'+private;
    }
}
//调用
var myClassObject = new myClass();
console.log(myClassObject.protect);//我是特权变量
console.log(myClassObject.protectMethod());//我是特权方法我调用了私有变量
```

## 3、JS公共变量与方法
   公共变量与方法，是指方法外使用prototype关键词定义的方法或者变量。
### 特点：
* 不可以访问构造器内的私有成员
* 可以访问特权成员
* 子类会继承所有的共有方法。(继承时阐述)
### 例：
```JS
//定义
function myClass(){
}
myClass.prototype.public='我是公共变量';
myClass.prototype.publicMethod=function(){
    return '我是公共方法'
}
//调用
var myClassObject = new myClass();
console.log(myClassObject.public);//我是公共变量
console.log(myClassObject.publicMethod());//我是公共方法
```
## 4、JS共有静态属性与方法
   共有静态属性与方法，无需实例化就可以调用的方法就叫静态方法。
### 特点：
* 无需实例化就可以调用的方法或变量
### 例：
```JS
//定义
function myClass(){
}
myClass.static='我是静态变量';
myClass.staticMethod=function(){
    return '我是静态方法'
}
//调用
var myClassObject = new myClass();
console.log(myClass.static);//我是静态变量
console.log(myClass.staticMethod());//我是静态方法
```
# 二、JS 继承
* 定义
* 继承实现方式
* 继承时公共、静态、私有、特权方法调用规则
## 1、什么是继承？
