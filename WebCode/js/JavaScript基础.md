#### JavaScript基础部分
* JavaScript 基本数据类型
    - String      字符串
    - Number      数字
    - Boolean     布尔值
    - Null        空值
    - Undefined   未定义

    - Object  对象属于一种复合数据类型，可以保存多个不同的数据类型的数据

### 对象分类
*   1.内建对象 
    - 有ES标准中定义的对象，在任何的ES的实现中都可以使用
    - 比如：Math String Number Boolean Function Object
*   2.宿主对象
    - 由JS的运行环境提供的对象，比如浏览器提供的对象
    - 比如 BOM与DOM
*   3.自定义对象
    - 由开发人员自己创建的对象


> in 运算符
    - 通过该运算符可以检查一个对象中是否含有指定的属性
    - 属性 in Object

### 基本数据类型   引用数据类型
> #### JS变量
- JS中的变量都是保存到栈内存中
- 基本数据类型的值直接在栈内存中储存
- 值与值之间是独立存在的，修改一个值不会印象其他值
> JS对象
- 对象是保存到堆内存中的，每创建一个新的对象，就会在堆内存中开辟出一个新的内存空间而变量保存的是对象的内存地址（对象的引用），
如果两个变量保存的是同一个对象引用当一个通过一个变量修改属性时，另一个也会受影响
> 对象比较
- 当比较两个基本数据类型的值时，就是比较值
- 然而比较两个引用数据类型时，它比较的是对象的内存地址，如果两个对象一模一样，但是地址不同，所以返回 false
### 创建对象

* 创建一个对象
    - `var Obj = new Object()`
* 使用对象字面量创建一个对象
    - `var obj = {}`
* 使用对象字面量，可以在创建对象时，直接指定对象中的属性
    - 语法：{属性名：属性值，属性名：属性值}
    - 属性名和属性值是一组一组的名值结构，名和值之间使用 ':' 连接,多个名值对之间使用 ',' 隔开
    - `var obj = {name:'张三'}`

---
## 函数
* 函数也是一个对象
* 函数中可以封装一个功能（代码），在需要时可以执行这些功能（代码）
* 函数中可以保存一些代码在需要的时候调用
* 使用typof检查一个函数对象时，会返回function

> 创建函数（只做了解，实际开发中不推荐使用）

* 创建一个函数对象
    - 可以将要封装的代码以字符串的形式传递给构造函数
    - 封装到函数中的代码不会立即执行
    - 函数中的代码会在调用的时候执行
    - 调用函数 语法：函数名（）
    - `var fun = new Function()`
> 使用函数声明来创建一个函数
 ``` 
 function 函数名([形参一],[形参二],。。。。，[形参三]){
     语句。。。
 }
 ```
 > 使用函数表达式来创建一个函数
 ``` 
 var 函数名 = function ([形参一],[形参二],。。。。，[形参三]){
     语句。。。
 }
 ```

 > 立即执行函数

* 函数对象()
    - 立即执行函数
    - 函数执行完立即被调用，这种函数就叫做立即执行函数
    - 立即执行函数往往只执行一次
```
(function(){
    alert('我是一个匿名函数~~~')
})();
```
> 方法
* 对象的属性值可以是任何 数据类型 也可以是个 函数
* 函数也可以是对象的属性
    - 如果一个函数作为一个对象的属性保存，那么我们称这个函数是这个对象的方法
    - 调用函数就说调用对象方法（method），但是它只是名称上的区别没有其他区别
> 枚举对象中的属性
```
var obj = {
    name:'张三',
    age:18,
    gender:'男'
}
```
* 枚举对象中的属性使用：for...in...
```
for(var n in obj){
    console.log("属性名"+n) // 取属性名
    console.log("属性值" + obj[n] ) // 取属性值
}

```
> 作用域
 * 作用域指一个变量的作用范围

    - 全局作用域
        + 直接编写在script标签中的代码，都在全局作用域中
        + 全局作用域在页面打开时创建，在页面关闭是销毁
        + 在全局作用域中有一个全局作用域 `Window` ，它代表是一个浏览器窗口，它由浏览器创建我们可以直接使用
        + 在全局作用域中创建的变量都会作为`window`对象的属性保存，创建的函数都会作为`window`的方法保存
    - 变量的声明提前
        + 使用`var`关键字声明的变量，会在所有的代码执行前被声明(但是不会被赋值)，但是如果声明变量时不适用`var`关键字，则变量不会被声明提前
    - 函数的声明提前
        + 使用函数声明式创建的函数：`function 函数名(){}`,他会在所有代码执行前就被创建，所以我们可以在函数声明前调用
        + 使用函数表达式创建的函数：`var fun = function (){}`,他不会被声明提前，他只是声明的变量fun，并没有赋值，所以没有被声明提前
    - 函数作用域
        + 调用函数，创建函数作用域，函数执行完毕以后，函数作用域销毁
        + 没调用一次函数就会创建一个函数作用域，他们之间是相互独立的
        + 函数作用域中可以访问到全局作用域的变量,在全局作用域中无法访问函数作用域中的变量
        + 当在函数作用域中操作一个变量时，他会先在自身作用域查找，如果有就直接用，没有则向上一级作用域寻找，直到找到全局作用域，如果全局作用域都没有怎报错 `ReferenceError`
        + 在函数中要访问全局变量，可以使用`window`对象查找
        + 在函数中也有声明提前的特性，使用 `var` 关键字声明变量，会在函数中所有的代码执行前被声明函数声明也会在函数中所有的代码被执行前声明，
        + 在函数中，不使用 `var` 声明的变量会变成全局变量
        + 定义形参就相当于在函数作用域中声明了变量
        ```
        var a = 10;
        function fun(a){
            console.log(a)
        } 
        fun(); // 输出 undefined
        ```
> this
* 解析器在调用函数每次都会向内部传递一个隐含的参数，这个隐含的参数就是`this`
    - `this` 指向的是一个对象，这个对象我们称为函数的上下文对象
    - 根据函数的调用方式不同，this会指向不同的对象
        + 1、以函数形式调用时 `fun()` ; `this` 永远指向 `windo`
        + 2、以方法形式调用时 `obj.sayName()` ; `this`指向的就是调用方法的那个对象（谁调用指向谁）
        + 3、当以构造函数调用时，this指向的就是新创建的那个对象
    ```
    function fun (a,b){
        console.log("a = "+a+",b = " + b )
        console.log(this) // 此时输出 [object window]
    }
    fun()
     
     // 创建一个对象
    var obj = {
        name:'孙悟空',
        sayName:fun
    }
    console.log(obj.sayName == fun) /// true

    obj.sayName() // [object object] // 此时fun 函数中的this  指向 obj

    ```
> 工厂方法创建对象

* 通过该方法可以大批量创建对象
     
        ```
        function createPerson(name , age , gender){
            var obj = new Object();
            obj.name = name;
            obj.age = age;
            obj.gender = gender;
            obj.sayName = function(){
                alert(this.name)
            }
            return obj;
        }

        var obj1 = createPerson('张三',18,'男')
 
    - 构造函数
        + 构造函数和普通函数的区别就是调用的方式不同
        + 普通函数是直接调用，构造函数需要使用 `new` 关键字来调用
        + 构造函数调用流程：`new` 之后发生了什么：
            - 1、立刻创建一个新对象
            - 2、将新建的对象设置为函数中的 `this`，在构造函数中可以使用 `this` 来引用新建的对象
            - 3、逐行执行函数中的代码
            - 4、将新建的对象作为返回值返回   
    
        ```
        function person(){
            this.name = name;
            this.age = age
        }

        var per = new person()

        console.log(per) // [object object] //此时的 `this` 指向的是对象per
        ```
    - 使用同一个构造函数创建的对象，我们称为一类对象，也将一个构造函数称为一个类
        + 我们将通过一个构建函数创建的对象，称为该构造函数的实例 
        + 使用 `instanceof` 可以检查一个对象是否是一个类(构造函数)的实例
            - 语法：对象 `instanceof` 构造函数
            - 所有对象都是 `Object` 的后代，任何对象在和 `Object` 做 `instanceof`检查是返回的都是`true` 
    - 原型对象 ：`prototype`
        + 我们所创建的每一个函数，解析器都会为函数添加一个`prototype`,这个属性对应着一个对象，这个对象就是我们的原型对象
        + 如果我们的函数只是作为普通函数调用 `prototype` 没有任何作用
        + 当函数以构造函数方式调用时 `new` ,他所创建的对象中都会有一个隐式的属性 `__proto__`,指向该函数的原型对象
        ```
        function MyClass(){

        }                        // 解析器给 MyClass 函数添加了一个 原型属性 prototype 
        
        var mc = new MyClass() ; // 构造方式调用，因为new的时候会创建对象，这个对象中有一个隐含属性 __proto__,而这个隐含属性指向的就是MyClass函数中的prototype对象
                                 //  所以 MyClass.prototype == mc.__proto__   
        ```
        + 原型对象就相当于一个公共区域，所有同一个函数（类）的实例都可以访问到这个原型对象 ，我们可以将对象中共有的内容，统一设置到原型对象中
        + 当我们访问对象的一个属性或者方法时，他会先在对象自身中查找有没有，如果有则直接使用，如果没有则会原型对象中查找
        + 以后我们创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中，这样不用分别为每一个对象添加，也不会影响到全局作用域，就可以使没个对象都具有这个属性跟方法
        ```
        function Class(){

        }
        Class.prototype.name = "我是原型中的name"

        var cl = new Class()

        console.log("name" in cl)  // 使用in 检查的是对象中有没有该属性，如果没有也会向上查找

        cl.hasOwnProperty('name') // 该方法是检查自身有没有该属性，如果没有则返回 false

        ```

    - 原型对象也是对象，所以他也有原型 `__proto__`
        + 当我们使用一个对象的属性方法时，会在自身中查找，如果有则使用，如果没有，则在原型中查找
        + 在原型中查找如果有，则使用，如果没有，则在原型的原型（Object）中查找，直到找到Object原型，Object对象的原型没有原型,所以返回`NUll`，如果在Object中属性还没找到，则返回`undefined`

    - `toSting()` 方法修改

        ```
        function Person(name,age,gender){
            this.name = name;
            this.age = age;
            this.gender = gender;
        }

        var person = new Person('张三',12,'男')

        console.log(person) // 此时调试输出的是 [object object] 
        // 如需修改怎么办？

        Person.prototype.toString = function(){
            return "[name="+this.name+"agesss="+this.age+"gender="+this.gender+"]"
        }

        var person2= new Person('李四',18,'男')

        console.log(person2.toString()) // [name="李四",age=18,gender='男']
        ```
---
## 数组(Array)

* 数组也是一个对象，它和普通对象功能类似、也是用来存储一些值、不同的是普通对象是使用字符串  
>数组方法
* push()
    - 该方法可以向数组的末尾添加一个或多个元素，并返回数组长度
    - 可以将要添加的元素作为方法的参数传递，这些元素可以自动添加到数组的末尾
    - 该方法会将新数组的长度作为返回值返回
    ```
    var arr = [];
    arr.push('张三','李四')
    console.log(arr) //  ['张三','李四']
    ```
* pop()
    - 该方法可以删除数组中最后一个元素
    ```
    var arr = ['1','2','3']
    arr.pop()
    console.log(arr) // ['1','2']
    ```
* unshift()
    - 该方法是向数组的开头添加一个或多个元素，并返回新的数组长度
    - 向前插入元素以后，其他的元素索引会依次调整
    ```
    var arr = [4,5,6]
    arr.unshift(1,2,3)
    console.log(arr) //[1,2,3,4,5,6]
    ```
* shift()
    - 该方法可以删除数组的第一个元素，并将删除的元素作为返回值返回
    ```
    var arr = [1,2,3,4,5,6]
    var result = arr.shift()
    console.log(result) // 返回  1
    console.log(arr) // [2,3,4,5,6]
    ```
>数组遍历
* for循环遍历
    ```
    var arr = [1,2,3,4,5,6]
    for(var i = 0; i<arr.length;i++){
        console.log(arr[i])
    }
    ```
* forEach 遍历 (ie9 以下不支持)
    - forEach() 方法需要一个函数作为参数
    - 像这种函数，由我们创建但是不由我们调用，我们称之为回调函数
    - 数组中有几个元素、函数就会执行几次，每次执行时，浏览器会将遍历的元素以实参的形式传递进来
    - 第一个实参为数组元素，第一个实参为数组的下标，第三个实参为数组对象
    - 索引值还可以传入一个负值，则从后往前计算
    ```
    var arr = [1,2,3,4,5,6]
    
    arr.forEach(function(element,length,arr){

    })
    ```
* slice 从某个已有的数组中返回选定的元素
    - 参数：截取开始的索引；截取结束的索引（可选）
    - 该方法不会影响原数组，而是将截取的封装到新的数组
    - 返回的新数组 包含开始索引，不包含结束索引
    ```
    var arr = [1,2,3,4,5,6]
    var newArr = arr.slice(1,2)
    console.log(arr) // 返回的还是原数组
    console.log(newArr) // 截取后的数组 [2]

    ```
* splice 可以用于删除数组中指定位置的元素
    - 使用splice（）会影响原数组，会将指定位置元素从原数组中删除，并将删除的元素作为返回值返回
    - 参数：1、表示开始位置的索引 2、表示删除的数量 第三个及以后 可以传递新元素，并将这些元素插入到开始索引的前面
    ```
    var arr = [1,2,3,4,5]
    arr.splice(0,2) 
    console.log(arr) // 返回 [3,4,5]

    arr.splice(0,1,1,2,3)
    console.log(arr) // 返回[1,2,3,4,5]

    ```
    ```
    // 数组去重
    var arr = [1, 2, 2, 3, 3, 3, 4, 4, 5, 6, 6, 4, 7]

    function arrSplice(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(j, 1)
                j--;
            }
        }
    }
    return arr;
    }
    var result = arrSplice(arr)
    console.log(result)
    ```
* concat() 
    - 可以连接两个或多个数组，并将新的数组返回
    - 该方法不会对原数组产生影响
    ```
    var arr1 = [1,2,3]
    var arr2 = [4,5,6]

    var result = arr1.concat(arr2)
    console.log(result) // 返回 [1,2,3,4,5,6]

    ```
* join()
    - 该方法可以将数组转换成字符串
    - 该方法不会对原数组产生影响，而是将转换后的字符串作为结果返回
    - 在join（）中可以指定一个字符串作为参数，这个字符串将会成为数组中元素的连接符，如果不指定，则默认使用 “，” 逗号连接
    ```
    var arr =[1,2,3]
    var result = arr.join()
    console.log(result) //  “1,2,3”

    ```
* reverse()
    - 该方法用来反转数组（前后颠倒）
    - 该方法回修改原来的数组
    ```
    var arr = [1,2,3,4,5]
    var result = arr.reverse()
    console.log(result) // [5,4,3,2,1]
    console.log(arr) // [5,4,3,2,1]
    ```
* sort()
    - 可以用来对数组进行排序
    - 该方法会修改原数组
    - 默认按照Unicode编码进行排序，所以对数字进行排序时可能会出错
    - 可以在sort()中添加回调函数来指定排序规则，
        + 回调函数中需要定义另个形参，
        + 浏览器将会分别使用数组中的元素作为实参去调用回调函数
        + 使用哪个元素调用不确定，但肯定的是数组中a一定在b前面，
        + 浏览器会根据回调函数的返回值来决定元素的顺序
        + 如果返回一个大于0的值，则两元素交换位置
        + 如果返回一个小于0的值，则两元素位置不变
        + 如果返回一个 0 ，则认为两个元素相等，也不交换
    - 如果需要升序，则  return a-b;
    - 如果需要降序，则  return b-a;
    ```
    var arr = [5,4,3,7,8,9,0,1,2,6]
    arr.sort()
    console.log(arr) // [0,1,2,3,4,5,6,7,8,9]
    // 传参

    arr.sort(function(a,b){
        return a- b;
    })
    console.log(arr) // [0,1,2,3,4,5,6,7,8,9]
    ```
## 函数的方法
* call()与apply()
    - 这两个方法都是函数对象的方法，需要通过函数对象来调用
    - 当对函数调用call()和apply()都会调用函数执行
    - 在调用call() 和 apply() 可以将一个对象指定为第一个参数 ，此时这个对象是谁函数中的`this` 就指向的是谁
    ```
    function fun (){
        console.log(this.name)
    }
    var obj ={name:"obj"}
    var obj2 = {name:'obj2'}
    fun.call(obj) // 此时输出 obj
    fun.call(obj2) // 此时输出 obj2
    fun() // 此时输出 undefined
    ```
    - call() 方法可以将实参在对象之后依次传递
    - apply() 方法需要将要传递的实参封装到一个数组中传递

    ```
    function fun(a,b){
        console.log(this.name,a,b)
    }
    var obj ={name:"obj"}
    fun.call(obj,1,2) // 输出： “obj”,1,2

    fun.apply(obj,1,2) // 输出：“Arguments list has wrong type”

    fun.apply(obj,[1,2]) // 输出：“obj,1,2”

    ```
###  this 再总结
* 1、以函数形式调用时，this永远指向window
* 2、以方法的形式调用时，this是调用方法的对象（谁调用指向谁）
* 3、以构造函数的形式调用时，this是新创建的对象（new的是谁，this指向的是谁）
* 4、使用call和apply调用时，第一个参数是谁，this指向的就是谁

> arguments 
* 在调用函数时，浏览器每次都会传递进两个隐含的参数；
    - 1、函数的上下文对象 `this`
    - 2、封装实参的对象 `arguments`
        + `arguments` 是一个类数组对象，它也可以通过索引来操作数据，也可以获取长度，在调用时，我们所传递的实参都会封装到`anguments`中
    - 它里面有一个属性叫做 `callee`
        + 这个属性对应一个函数对象，就是当前正在执行的函数的对象
    ```
    function fun(a, b) {
    console.log(arguments instanceof Array); // false
    console.log(Array.isArray(arguments)); // false
    console.log(arguments[1]); // true
    console.log(arguments.length);// 2
    console.log(arguments.callee); // [Function:fun]
    }   
    fun('hello', true)
    ```
> Date 对象   日期
* 在JS中使用Date对象来表示一个时间
    - 创建一个Date()
    - 直接使用构造函数调用创建一个Date对象,则会封装为当前代码执行时间
    ```
    var d = new Date()
    console.log(d) // 返回当前时间
    ```
    - 创建一个指定时间
    ```
    var d2 = new Date("12/03/2020 11:30:23")
    console.log(d2) // Thu Dec 03 2020 00:00:00 GMT+0800 (中国标准时间)
    ```
    - Date.getTime() 获取当前日期对象的时间戳，时间戳：从格林威治1970年1月1日,0时0分0秒起到当前的时间毫秒值（1秒=1000毫秒）
    ```
    var d = new Date()
    var time = d.getTime()
    console.log(time)
    ```
    - Date() 对象还有很多方法，查阅相关手册
> Math 
* Math和其他函数不同，它不是一个构造函数，它属于一个工具类不用创建对象，它里面封装了数学运算的相关方法
```
Math.abs(1) // 返回绝对值
Math.PI //圆周率
Math.ceil // 向上取整 1.1 得 2
Math.floor // 向下取整 1.9 得 1
Math.round // 四舍五入取整
Math.random 
// 生成随机数0-1之间
Math.random()
// 生成0-x 之间
Manth.round(Math.random()*x) 
// 生成 x-y 之间
Manth.round(Math.random() * (y-x) ) + x
```
* 相关方法可以查阅相关手册
> 包装类
* 基本数据类型
    - String Number Boolean Null Undefined
* 引用数据类型
    - Object
* 在JS中为我们提供了三个包装类，通过这三个包装类可以将基本的数据类型转换为对象
    - String()
        + 可以将基本数据类型字符串转换为String对象
    - Number()
        + 可以将基本数据类型数字转换为Number对象
    - Boolean()
        + 可以将基本数据类型布尔值转换为Boolean对象
    - 但是注意 在我们实际开发中不会使用基本数据类型对象，如果使用基本数据类型的对象，在做一些比较时可能会带来一些不可预料的结果
    ```
    var num = new Number(2)
    var str = new String("hello")
    var bool = new Boolean(true)

    console.log(typeof num) // object
    console.log(typeof str) // object
    console.log(typeof bool) // object

    ```
    - 当我们对一些基本数据类型的值调用属性和方法时，浏览器临时使用包装类将其转换为对象，然后再调用方法
    ```
    var s = 123 ;
    s.toString();
    console.log(s) ;// 输出 “123”
    console.log(typeof s) // 输出string

    ```
> string 方法
* 在底层字符串是以字符数组的形式保存的“hello” ，是以['h','e','l','l','o']
* length 可以用来获取字符串长度
* charAt()
    - 可以返回字符串指定位置字符
    - 根据索引获取指定的字符，从0开始
    ```
    str = "hello string"
    var result = str.charAt(0)
    console.log(result) // 输出：h
    ```
* charCodeAt()
    - 返回 Unicode编码
* fromCharCode()
    - 可以根据字符编码获取字符
    ```
    // 必须使用string调用
    result = String.fromCharCode(72); // 输出 “H”
    ```
* concat()
    - 可以连接两个或多个字符串
    - 作用与 “+” 号一样
* indexof()
    - 该方法可以检索一个字符串是否包含指定内容
    - 如果该字符串中含有该内容，则会返回其第一次出现的索引
* 其余方法查找手册

### 正则表达式
* 用于定义一些字符串的规则，计算机可以根据正则表达式，来检查一个字符串是否符合规则，获取将字符串中符合规则的内容提取出来
    ```
    // 创建正则表达式
        /**
         * 语法：var 变量 = new RegExp("正则表达式","匹配模式")
         * 在构造函数中可以传递一个匹配模式作为第二个参数：i 表示忽略大小写；g 表示全局匹配
         */
        var reg = new RegExp(); // 正则表达式也是一个对象
    ```
* 使用字面量来创建正则表达式
    - 使用字面量创建更加方便；使用构造函数创建更加灵活
    - “ | ” 表示或者的意思
    - " [] " 表示的也是或的意思
    - " [a-z] " 表示a----z
    - " [^ ] " 表示除了什么 匹配
    - “ [ 0-9 ] ” 匹配数字
    - “ \ ” 表示转义字符
    ```
    // 语法 ： var 变量 = /正则表达式/匹配模式
    // 创建一个正则表达式，检查一个字符出中有a或b

        var reg = /a|b/;
        reg.test('bacd')    

    // 创建一个表达式检查一个字符串中是否有字母
        var reg = /[a-z]/i
    // 检查一个字符中是否含有 abc 或 adc 或 zec
        var reg = /a[bde]c/
    // [^ ]除了什么匹配
### 什么是DOM
* DOM 全称 Document Object Model文档对象模型
* JS通过DOM来对HTML文档进行操作，只要了解了DOM就可以随心所欲的操作WEB页面

    |     | nodeName  |nodeType|nodeValue|
    |  :-:  | :-:  |:-:|:-:|
    | 文档节点 | #document |9|null|
    | 元素节点 | 标签名 | 1 | null |
    | 属性节点 | 属性名 | 2 | 属性值|
    | 文本节点 | #text | 3 | ⭐️文本内容|


> 事件
* 事件，就是文档或浏览器窗口中发生的一些特定的交互瞬间
* JavaScript与HTML之间的交互是通过事件来实现的
* 比如：点击按钮、鼠标移动、关闭窗口
 ```
 // 绑定单击事件
 var btn = document.getElementById('btn')
 btn.onclick=function(){
     alart('鼠标点击事件')
 }
 ```
* 浏览器加载顺序：是按照自上向下的顺序加载，读取到一行就运行一行，如果将Script标签写到页面上面时，页面还没有加载，事件无法响应报错
* 如果想把js代码写在页面首部，可以添加window.onload事件；onload事件会在整个页面加载完之后才触发; 可以确保HTML DOM对象加载完毕再执行函数
```
// onload
window.onload=function(){
    // 代码区域
}
```
* document.querySelector() // Css 选择器查找

> dom 增删改
* 增加节点
```
 // 1.创建一个元素节点，
 //它需要一个标签名作为参数，将会根据标签名创建元素节点对象，并将创建好的对象作为返回值返回
 
 var li = document.createElement("li") // 表示创建一个 “ li ” 节点
 
 // 2.创建一个文本节点，
 // 需要一个文本内容作为参数，将会根据该内容创建文本节点，并将新的节点返回

 var gzText = document.createTextNode('广州')

 // 3.将gzText文本设置到li元素节点上
 // 向父节点上添加一个新的子节点

 li.appendChild(gzText) // 父节点.appendChild(子节点);

```
* 在指定节点前插入新的子节点：  insertBefore()
    - 语法： 父节点.insertBefore(新节点,旧节点) 
* 替换子节点： replaceChild() 
    - 语法：父节点.replaceChild(新节点,旧节点)
* 删除节点：removeChild()
    - 语法：父节点.removeChild(子节点)
    - 常用：子节点.parentNode.removeChild(子节点)
* 相关API查阅手册
> 操作内联样式
* 通过JS修改元素的样式
    - 语法：元素.style.样式名 = 样式值
    - 通过js修改的样式为内联样式，内联样式优先级高，修改完后会立即生效
    - 但是如果样式中写了`!important`属性，则此时样式会有最高的优先级，即使通过JS也不能修改生效 
    ```
    // 1. 获取元素
    // 2. 为元素绑定事件
    // 3. 修改相应的style样式

    var box1 = document.getElementById('box1');
    var btn1 = document.getElementById('btn1');
    btn1.onclick = function(){
        box1.style.width = "300px"
        // 类似于 background-color的样式名应该采用驼峰命名
        box1.style.backgroundColor = "yellow"
    }
    ```
* 获取元素样式
    - 语法：元素.style.样式名
    ```
    // 1. 获取元素
    // 2. 为元素绑定事件
    // 3. 修改相应的style样式

    var box1 = document.getElementById('box1');
    var btn1 = document.getElementById('btn1');
    btn1.onclick = function(){
        console.log( box1.style.width ) // 获取到了box1的宽度属性：
    }
    ```
* 获取元素当前的显示样式
    - 语法：元素.currentStyle.样式名（仅IE浏览器支持）
    - 它可以用来读取当前元素显示的样式
    - 在其他浏览器中getComputedStyle()来获取样式值
    - 语法：getComputedStyle(元素,null)
    - 该方法会返回一个对象，该对象封装了当前元素的一些对应样式
    ```
    // 封装一个获取样式函数
    // 参数：obj : 要获取样式的元素   name：要获取的样式名

    function getStyle(obj,name){
        return window.getComputedStyle?getComputedStyle(obj,null)[name]
    }
    ```
* 获取样式的相关API 可以参考W3Cshool手册
### 事件
* 事件对象
    - 当事件的响应函数被触发时，浏览器每次都会将一个事件对象作为实参传递进响应函数
    - 在事件对象中封装了当前事件相关的一切信息，比如：鼠标的坐标，键盘哪个按键按下，鼠标滚轮滚动的方向
    - 在IE8及以下的浏览器，event 不会被传递，是将事件对象作为window对象的属性保存，（又不支持火狐浏览器）
* onmousemove  鼠标在元素中移动触发
```
element.onmousemove = function(event){
    // 触发之后的代码
    // clientX 可以获取鼠标指针的 X 轴坐标
    // clientY 可以获取鼠标指针的 Y 轴坐标
}
```
* 使div跟随鼠标移动
```
var box1 = document.getElementById('box1')
box1.onmousemove = function(event){
    // 兼容性
    event = event || window.event
    // 获取鼠标坐标
    var left = event.pageX;
    var top = event.pageY;
    // 设置div偏移量
    box1.style.left = left+"px";
    box.style.top = top+"px";
}
```
* 事件冒泡
    - 所谓的冒泡指的就是事件的向上传导，当后代元素上的事件被触发时，其祖先元素的相同事件也会被触发
    - 可以使用事件对象取消冒泡
    `event.cancelBubble = true` //  取消冒泡 
* 事件委托
    - 指将事件统一绑定给元素的共同的祖先元素，这样后代元素上的事件触发时，会一直冒泡到祖先元素，从而通过祖先元素的响应函数来处理事件
    - 事件委派是利用了冒泡函数，通过委派可以减少事件绑定次数
* 事件绑定
    - 使用  对象.事件 = 响应函数 ； 这种方法它只能同时为一个元素的一个事件绑定一个响应函数，不能绑定多个，绑定多个后面的会把前面的覆盖掉
    - 通过 addEventListener() 事件监听绑定函数
        + 参数：1.事件字符串，不要on ；
        +   2、回调函数，当事件调用时该函数会被调用
        +   3、是否在捕获阶段触发、需要一个布尔值，一般都传false
        ```
        btn.addEventListener("click",function(){
            alart(1)
        },false)
        ```
    - 使用addEventListener()可以同时为一个元素的相同事件同时绑定多个响应函数，这样当响应事件执行时，响应函数会根据绑定的顺序依次执行
    - 该方法IE8及以下不支持（使用attchEvent代替）
* 拖拽
    - onmousedown 鼠标按下事件
    - onmousemove 鼠标移动事件
    - onmouseup   鼠标松开事件
    ```
    // 获取元素
    var box1 = document.getElementById('box1')
    // 绑定鼠标 按下事件
    box1.onmousedown = function(event){
        // 兼容性判断
        event = event || window.event
        // 鼠标按下获取当前指针位置并计算，否则移动是鼠标指针会在div的右上角
        var ol = event.clientX - box1.offsetLeft;
        var ot = event.clientY - box1.offsetTop;

        // 因为在document 上移动所以给document绑定移动事件

        document.onmousemove = function(event){
            // 兼容性判断
            event = event || window.event
            // 获取鼠标移动位置并赋值

            var left = event.clientX - ol;
            var top = event.clientY - ot;

            //修改box1 位置
            box1.style.left = left + "px";
            box1.style.top = top + "px"
        }
        // 为document 绑定一个鼠标松开事件

        document.onmouseup = function(){
            // 当鼠标松开时，被拖拽元素固定在当前位置 onmouseup
            // 取消 document 的 onmousemove 事件
            document.onmousemove = null;
            // 取消 document 的 onmouseup 事件
            document.onmouseup = null;
        }
        // 当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容
        // 此时会导致拖拽功能失常，这个行为是浏览器的默认行为
        // 如果不希望发生这个行为，则可以通过 return false 来取消默认行为
        // IE8 不支持：使用 setCapture()与releaseCapture() 解决，但该方法只仅限于IE
        
        return false;
    }

    ```
* 鼠标滚轮事件
    - onmousewheel 滚轮事件
    - 火狐不支持该事件；改用 DOMMouseScroll,该方法需要通过addEventListener()函数绑定
    - 当滚轮滚动时，如果浏览器有滚动条，滚动条会随之滚动，这是浏览器的默认行为，如果不希望发生，则可以`return false` 取消默认行为，该方法仅支持Chrome
    - 使用`addEventListener()` 绑定的函数，取消默认行为时不能使用`return false` ;要是用`event.preventDefault()` 但是ie8 不支持；
* 键盘事件
    - onKeydown 某个按键被按下
        + ` documrnt.onKeydown = function(){}`
        + 如果按着一个按键不松手，则事件会一直触发，
        + 当连续触发时，第一次和第二次之间会间隔稍微长一点，后续会指向连续非常快，这种设计是为了防止误触发生
    - onKeyup 某个按键被松开
        + `document.onKeyup = function(){}`
        + 即某个按键松开执行
### BOM 浏览器对象模型
* BOM 可以使我们通过JS操作浏览器
* BOM 对象 `Window`,`Navigator`,`Location`,`History`,`Screen`
* Window 
    - 代表的是整个浏览器窗口，同时window也是网页中的全局对象
* Navigator 
    - 代表的当前浏览器的信息，通过该对象可以来识别不同浏览器
    - 由于历史原因，`Navigator`对象中大部分属性都已经不能帮助我们识别浏览器了
    - 一般我们只使用`UserAgent`来判断浏览器信息；`UserAgent`是一个字符串，这个字符串中包含了用来描述浏览器信息的内容，不同的浏览器会有不同的`userAgent`
    - 但是在`IE11`中已经将相关的标识移除，所以基本不能使用`UserAgent`来识别一个浏览器了
    > 如果通过 UserAgent 不能判断，还可以通过一些浏览器中持有对象，来判断浏览器信息;比如：`ActiveXObject`
    ```
    if("ActiveXObject" in window) // 进行判断
    ```
* Location
    - 代表浏览器的的地址栏信息
    - `assign()` 用来跳转到其他页面；作用和直接修改`location` 一样
    - `reload()` 用于重新加载当前页面，作用和刷新按钮一样；如果在方法中传递一个`true`,作为参数，则会强制清空缓存刷新页面
    - `replace()` 可以使用一个新的页面替换当前页面
* History
    - 代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录
    - 由于隐私的原因，该对象不能获取到具体的浏览记录，只能操作浏览器向前或者向后翻页，而且只在当次有效
    - `length`
        + 可以获取到当前的访问连接数量
    - `back()`
        + 可以用来回退到上一个页面
    - `forward()`
        + 可以跳转到下一个页面，与浏览器前进按钮相似
    - `go()`
        + 可以跳转到指定页面；参数需要一个整数
* Screen
    - 代表用户屏幕信息，通过该对象可以获取到用户的
* 定时器
    - `setInterval()`
    - 可以将函数每隔一段时间调用一次
    - 参数：1、回调函数，2、每次调用的间隔时间













 