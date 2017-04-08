# ECMA6
最常用的ES6特性：
1.声明：let, const, 
2.类：class, extends, super,
3.箭头函数： arrow functions,
4.字符模板： template string, 
5.解构：destructuring, 
6.参数默认值：default, rest arguments

========================================================================================================================================================================



一.let和const声明：

1.let声明：此声明是有块级作用域的，并且此方法不存在变量提升现象，变量一定要在声明后使用。

{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1

for循环的计数器，就很合适使用let命令。
for (let i = 0; i < 10; i++) {}

console.log(i);
//ReferenceError: i is not defined

2.const声明：声明一个只读的常量。一旦声明，常量的值就不能改变。
const PI = 3.1415;
PI // 3.1415

PI = 3;
// TypeError: Assignment to constant variable. //上面一旦声明就不能改变否则报错。

=========================================================================================================================================================
二.变量的赋值

1.数组的赋值：

以前：
var a = 1;
var b = 2;
var c = 3;

现在：
var [a, b, c] = [1, 2, 3];

==========================================================================================================================================================

三.class，类的概念:

class Animal {
    constructor(){    //constructor 里面定义的属性和方法是自己的 ，而这个之外定义的属性方法是可以共享的。
        this.type = 'animal'
    }
    says(say){
        console.log(this.type + ' says ' + say)
    }
}

let animail = new Animal（）； 构造函数

animal.says('hello') //animal says hello。。。

class Cat extends Animal {   //extends 这个方法可以是Cat 继承 Animal 上的属性和方法。。
    constructor(){
        super()
        this.type = 'cat'
    }
}

let cat = new Cat()
cat.says('hello') //cat says hello

=========================================================================================================================================================

四.arrow function：箭头函数

ES5：function(i){ return i + 1; }；      function(x, y) { 
                                                     x++;
                                                     y--;
                                                     return x + y;
                                                          }；


ES6：(i) => i + 1；                      (x, y) => {x++; y--; return x+y}；

超级无敌特性 无需在意this指向 因为ES6箭头函数没有自己的this，它的this是通过继承得来的

ES5： class Animal {
    constructor(){
        this.type = 'animal'
    }
    says(say){
        setTimeout(function(){
            console.log(this.type + ' says ' + say)    //这个构造函数会报错 因为setTimeout的this指向全局，以往方法会用到var that = this；而ES6就不必这样麻烦了。
        }, 1000)
    }
}

 var animal = new Animal()
 animal.says('hi')   //undefined says hi


ES6：class Animal {
    constructor(){
        this.type = 'animal'
    }
    says(say){
        setTimeout( () => {
            console.log(this.type + ' says ' + say)
        }, 1000)
    }
}
 var animal = new Animal()
 animal.says('hi')  //animal says hi

=============================================================================================================================================================


五.template string:模板字符串 ``反引号和${ };代替繁琐的+号引用变量

ES5:  $("#result").append(
      "There are <b>" + basket.count + "</b> " +
       "items in your basket, " +
       "<em>" + basket.onSale +
       "</em> are on sale!"
);

ES6:  $("#result").append(`
        There are <b>${basket.count}</b> items
        in your basket, <em>${basket.onSale}</em>
        are on sale!
`);

==============================================================================================================================================================

六.destructuring ：ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构

ES5 : 
let cat = 'ken'
let dog = 'lili'
let zoo = {cat: cat, dog: dog}
console.log(zoo)  //Object {cat: "ken", dog: "lili"};

ES6: 
let cat = 'ken'                                           
let dog = 'lili'
let zoo = {cat, dog}
console.log(zoo)  //Object {cat: "ken", dog: "lili"};
也可以这样：
let dog = {type: 'animal', many: 2}
let { type, many} = dog
console.log(type, many)   //animal 2

============================================================================================================================================================

七.函数参数默认值：default, rest

ES5：
function animal(type){
    type = type || 'cat'  
    console.log(type)
}
animal()；

ES6：
function animal(type = 'cat'){  //直接在这里写默认值
    console.log(type)
}
animal()；

rest语法也很简单，直接看例子：

function animals(...types){
    console.log(types)
}
animals('cat', 'dog', 'fish') //["cat", "dog", "fish"]  //直接传几个参数 返回一个数组

