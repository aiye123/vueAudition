## 1、你知道vue的模板语法用的是哪个web模板引擎的吗？说说你对这模板引擎的理解
mustache
## 2、v-model 原理
v-model主要提供了两个功能，view层输入值影响data的属性值，data属性值发生改变会更新view层的数值变化
## 3、 在使用计算属性的时，函数名和data数据源中的数据可以同名吗?
不能同名 因为不管是计算属性还是data还是props 都会被挂载在vm实例上，因此 这三个都不能同名
## 4、vue中data的属性可以和methods中的方法同名吗？为什么？
不可以，data中的属性和methods方法重名会优先执行data中的属性并且报错
## 5、 vue2.0不再支持v-html中使用过滤器了怎么办？
使用vue.filter 或者在method 里写方法
## 6、说一下你对闭包的理解，以及你在什么场景会用到闭包？
理解：
简单来说，闭包就是在函数里面声明函数，实际开发中主要应用于封装变量，保护变量不受外界污染，也相当于是在函数作用域里面再声明一个内部作用域，这样执行结果拿到的变量都是不同的，拿的就不是全局变量。

特性：函数内部嵌套函数

缺点：闭包容易消耗内存

注意：
子函数可以访问父函数中所有的局部变量，，但是父函数不能访问子函数的变量

创建：
创建闭包最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量，利用闭包可以突破作用域链，将函数内部的变量和方法传递到外部。
## 6、如何判断一个变量是Array类型？如何判断一个变量是Number类型
1.typeof操作符

2.instanceof操作符（这个操作符和JavaScript中面向对象有点关系，了解这个就先得了解JavaScript中的面向对象。因为这个操作符是检测对象的原型链是否指向构造函数的prototype对象的。）

var arr = [1,2,3,1];     

alert(arrinstanceof Array); // true 

3.对象的constructor属性

var arr = [1,2,3,1];     

alert(arr.constructor === Array);// true  

4.Array.isArray()

5.1.Object.prototype.toString

　　Object.prototype.toString的行为：首先，取得对象的一个内部属性[[Class]]，然后依据这个属性，返回一个类似于"[object Array]"的字符串作为结果(看过ECMA标准的应该都知道，[[]]用来表示语言内部用到的、外部不可直接访问的属性，称为“内部属性”)。利用这 个方法，再配合call，我们可以取得任何对象的内部属性[[Class]]，然后把类型检测转化为字符串比较，以达到我们的目的。

function isArrayFn (o) {    

        return Object.prototype.toString.call(o) === '[object Array]';     

}  

    var arr = [1,2,3,1];     

    alert(isArrayFn(arr));// true   

call改变toString的this引用为待检测的对象，返回此对象的字符串表示，然后对比此字符串是否是'[object Array]'，以判断其是否是Array的实例。为什么不直接o.toString()?嗯，虽然Array继承自Object，也会有 toString方法，但是这个方法有可能会被改写而达不到我们的要求，而Object.prototype则是老虎的屁股，很少有人敢去碰它的，所以能一定程度保证其“纯洁性”：)

　　JavaScript 标准文档中定义: [[Class]] 的值只可能是下面字符串中的一个： Arguments, Array, Boolean, Date, Error, Function, JSON, Math, Number, Object, RegExp, String.

　　这种方法在识别内置对象时往往十分有用，但对于自定义对象请不要使用这种方法。

## 7、怎么判断两个对象是否相等
1、通过JSON.stringify(obj)来判断两个对象转后的字符串是否相等。key值的键值对位置不同会导致出错

