<!--
 * @Author: your name
 * @Date: 2020-06-28 21:42:29
 * @LastEditTime : 2020-08-04 16:00:27
 * @LastEditors  : Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /笔记/JavaScript高级.md
--> 
### JS基础总结
> 数据类型
* 基本类型（值类型）
    - String ：任意字符串
    - Number ：任意数字
    - boolean ：true/false
    - undefined ：undefined
    - null ：null
* 对象（引用）类型
    - Object ：任意对象
    - Function ：一种特别的对象（可以执行）
    - Array ：一种特别的对象（数值下标，内部数据是有序的）
> 判断数据类型
* typeof
    - 可以判断 ： undefined / 数值 / boolean / String / function
    - 不能判断 ：null / object   object与array
* instanceof ： 判断对象的具体类型
* === / ==
    - 可以判断 ：undefined / null

> 判断对象类型


```
    var b1 = {
    b2:[1,'abc',console.log]
    b3:function(){
        console.log('b3')
    }
}
console.log(b1 instanceof Object,b1 instanceof Array) //true false
console.log(b1.b2 instanceof Array,b1.b2 instanceof Object) // true true

```
>相关问题
* `undefined` 与 `null `的区别？
    - `undefined` 代表定义但是没有赋值
    - `null` 代表定义了并且赋值，且值为 `null`
* 什么时候给变量赋值为 `null`呢？
    - 初始赋值，表明将要赋值的为对象
    - 结束前，让对象成为垃圾对象从而被垃圾对象回收
* 严格区别变量类型与数据类型
    - 数据的类型
        + 基本类型
        + 对象类型
    - 变量的类型（变量内存值的类型）
        + 基本类型 ：保存的就是基本类型的数据
        + 引用类型 ：保存的是地址值
> 数据、变量、内存
* 什么是数据？
    - 存储在内存中代表特定信息的‘东西’，本质上就是 `010101`
    - 数据的特点：可传递，可运算
    - 一切皆数据
    - 内存中所有操作的目标：数据
        + 算术运算
        + 赋值
        + 运行函数
* 什么是内存？
    - 内存条通电后产生的可存储数据的空间
    - 一块小内存的2个数据
        + 内部储存的数据
        + 地址值
    - 内存分类
        + 栈 ：全局变量 / 局部变量
        + 堆 ：对象
* 什么是变量？
    - 可变化的数据，变量名与变量值组成
    - 每个变量对应着一块小内存，变量名用来查找对应的内存，变量值就是内存中保存的数据
* 内存，数据，变量三者之间的关系？
    - 内存是用来存储数据的空间
* 问题：
    - `var a = xxx` a内存中到底保存的是什么？
        + xxx是基本数据，保存的就是这个数据
        + xxx是对象，保存的就是对象的地址值
        + xxx是变量，保存的xxx的内存内容（可能是基本数据，也可能是地址值）
    - 关于引用变量赋值问题
        + n个引用变量指向同一个对象，通过一个变量修改对象内部数据，另一个变量看到的是修改之后的数据
        + 2个引用变量指向同一个对象，让其中一个引用变量指向另一个对象，另一个引用变量依然指向前一个对象
        ```
        var obj = {'name':'张三'}
        var a = obj; // 这是只是给a赋值了obj在堆内存中的地址值
        a.name = "李四"; 
        console.log(obj.name) // 此时输出的是李四
        ```
    - 在js调用函数时传递变量参数时，是值传递还是引用传递？
    ```
    var a = 3
    function fn(a){
        a = a+1;
    }
    fn(a)
    console.log(a) // 此时的值是 3
    ```
    - 理解1：都是值（基本值/地址值）传递
    - 理解2：可能是值传递，也可能是引用传递（地址值）
    - JS引擎如何进行内存管理？
        + 内存生命周期
            - 分配空间，得到使用权
            - 存储数据，可以反复进行操作
            - 释放当前小内存空间
        + 释放内存
            - 局部变量：函数执行完自动释放
            - 对象： 称为垃圾对象===>垃圾回收器回收
> 对象
- 什么是对象？
    * 多个数据的封装体
    * 用来保存多个数据的容器
    * 一个对象代表现实中的一个事物
- 为什么用对象？
    * 统一管理多个数据
- 对象的组成
    * 属性：属性名（字符串）和属性值（任意）组成
    * 方法：一种特别的属性（属性值是函数）
- 如何访问对象内部数据？
    * .属性名：编码简单，有时不能用
    * [属性名]：编码复杂，能通用
        ```
        var person ={
            name:'Tom',
            age:12,
            setName:function(name){
                this.name = name
            },
            setAge:function(age){
                this.age = age
            }
        }
        console.log(person.name)
        ```
- 问题：
    * 什么时候必须使用`['属性名']`的方式?
    * 1、属性名包含特殊字符：- 空格
    * 2、变量名不确定
        ```
        var p ={}
        p.content-type = 'text/json' // 不能用
        // 推荐使用
        p['content-type'] = "text/json"
        console.log(p['content-type'])

        //2、变量名不确定
        var propName = 'myApp'
        var value = 18
        // p.propName = value // 不能使用
        p[propName] = value
        ```
> 函数
* 什么是函数？
    - 具有特定功能的n条语句的封装体
    - 只有函数时可以执行的，其他类型的数据不能执行
* 为什么要用函数？
    - 提高代码复用
    - 便于阅读交流
* 如何定义函数？
    - 函数声明
    - 表达式
* 如何调用（执行）函数？
    - 函数名（）：直接调用
    - obj.函数名（） ：通过对象调用
    - new 函数名（）：new调用
    - 函数名.call/apply(obj) ：改变this执行调用
> 回调函数
* 什么函数才是回调函数？
    - 把一个函数A作为参数传递给函数B，当函数A执行完毕再执行B函数，这个过程就叫回调函数
    - 你定义的
    - 你没有调用
    - 但是最终执行了
    ```
    setTimeout(function(){
        console.log('这就是一个回调函数')
    },1000)
    ```
* 常见的回调函数？
    - dom事件回调函数
    - 定时器回调函数
    - ajax请求回调函数
    - 生命周期
> `IIFE`
* 全称：Immediately-Invoked Function Expression 立即调用的函数表达式
* 作用：
    - 隐藏实现
    - 不会污染外部（全部）命名空间
    - 用它来编写js模块
```
(function(){
    console.log('立即执行的匿名函数')
})()
```
> this
* this是什么？
    - 任何函数本质上都是通过某个对象来调用，如果没有直接指定就是`window`
    - 所有函数内部都有一个变量this
    - 它的值是调用函数的当前对象
* 如何确定this的值？
```
function Person(color){
    console.log(this) // window
    this.color = color
    this.getColor = function(){
         console.log(this) // 
        return this.color
    }
    this.setColor = function(color){
         console.log(this) // 
        this.color = color
    }
}
Person('red') // this 是谁？ window

var p = new Person('yellow') // this是谁？ p

p.getColor() // this是 p

var obj ={}
p.setColor.call(obj,'black') // this是obj

var test = p.setColor;
test() // this是 window

function fun1(){
    function fun2(){
        console.log(this)
    }
    fun2() // this 是 window
}
fun1()
```
### 函数高级
* 原型与原型链
    - #### 原型（prototype）
        + 函数的prototype属性
            - 每个函数都有一个 `prototype` 属性，它默认指向一个 `Object` 空对象（即称为：原型对象）
            - 原型对象中都有一个 `constructor` 属性，它指向函数对象
            ```
             // 每个函数都有一个 `prototype` 属性，它默认指向一个 `Object` 空对象（即称为：原型对象）
            console.log(Date.prototype, typeof Date.prototype);

            function fun() {

            }

            console.log(fun.prototype); // 默认指向一个object空对象（没有我们的属性）
            // 原型对象中都有一个 `constructor` 属性，它指向函数对象
            console.log(Date.prototype.constructor === Date); // true
            console.log(fun.prototype.constructor === fun); // true
            ```
        + 给原型对象添加属性（一般都是方法）
            - 作用：函数的所有实例对象自动拥有原型中的属性（方法）
        ```
         // 给原型对象添加属性（一般是方法）===> 实例对象可以访问
        Fun.prototype.test = function() {
            console.log('test()');
        }

        const fun = new Fun();
        fun.test() // 输出 test()

        ```
        + 显示原型与隐式原型
            - 每一个 `function` 都有一个 `prototype` ,即显示原型（属性）
            - 每一个实例对象都有一个 `__proto__` , 可称为隐式原型（属性）
        ```
        function Fun(params) { // 内部语句：this.proyotype = {}

        }
        // 1. 每个函数function都有一个prototype，即显示原型 ,默认指向一个空的Object对象
        console.log(Fun.prototype);
        // 2. 每个实例对象都有一个 __proto__,可称之为隐式原型
        var fun = new Fun() // 内部语句：this.__proto__ = Fn.prototype
        console.log(fun.__proto__);
        // 给原型添加方法
        Fun.prototype.test = function(params) {
            console.log('test()');

        }
        // 总结：1.定义构造函数
        //      2. 创建实例对象   
        //      3. 给原型添加方法
        //      4. 通过实例调用原型方法
        ```
        + 总结：
            - 函数的 `prototype` 属性：在定义函数时解析器自动添加，默认值是一个空`Object`对象
            - 对象的 `__proto__` 属性：在创建对象时解析器自动添加，默认值为构造函数的`prototype`属性值
            - 显示原型可以直接操作，隐式原型不能直接操作（ES6之前）
            ![图片](https://note.youdao.com/yws/api/personal/file/5A45F00880284B408A9973D1BF8AF9BB?method=download&shareKey=1a51badfec4a43940e863757ee3f7fc5)

    - #### 原型链
        + 访问一个对象的属性时，先在自身查找，
        + 如果没有则沿着`__proto__`这条链向上查找，找到则返回，
        + 如果最终没找到则返回 `undefined`
        + 别名：隐式原型链
        + 作用查找对象的属性或者方法
          ![图片](https://note.youdao.com/yws/api/personal/file/2C279829E9A443B3AAAF4C4A52A2DD30?method=download&shareKey=c93f98e39006d8f67272c51550b706a3)
        + 函数的显示原型指向的对象：默认是空 `Object` 实例对象（但Object不满足）
            ```
            console.log(Fn.prototype instanceof Object) // true
            console.log(Object.prototype instanceof Object) // false
            console.log(Function.prototype instanceof Object) // true
            ```
        + 所有函数都是 `Function` 的实例 （包括自己本身）
            ```
            console.log(Function.__proto__ === Function.prototype)
            ``` 
        + `Object`  的原型对象是原型链的尽头

            ```
            console.log(Object.prototype.__proto__) // 输出   null
            ```


* 执行上下文与执行上下文的栈
* 作用域与作用域链
* 闭包



   


