知识总结

什么是脚本语言

假设你经常从网上下东西，全都放在 D 盘那个叫做 downloads 的文件夹里。而你有分类的癖好，每周都要把下载下来的图片放到 pic 文件夹里，pdf 放到 book 文件夹里，mp3 和 wma 文件放到 music 文件夹里。手动分了一年之后你终于厌倦了，于是你打开记事本，写了以下的三行字：

copy /Y D:\download\*.jpg D:\pic\
copy /Y D:\download\*.pdf D:\book\
copy /Y D:\download\*.mp3 D:\music\

然后把它存成一个叫做 cleanupdownload.bat 的文件。想起来的时候你就双击一下这个文件，然后就发现 download 里的三类文件都被拷到它们该去的地方了。这就是个非常简单的脚本。

类似于演戏时用到的脚本，

script 其实就是一系列指令——演员看了指令就知道自己该表演什么，说什么台词；计算机看了指令就知道自己该做什么事情。所以 script 其实就是短小的、用来让计算机自动化完成一系列工作的程序，这类程序可以用文本编辑器修改，不需要编译，通常是解释运行的。

在网站前端编程的语境下，脚本通常是指在浏览器里运行的小程序，就像剧本一样，它可以用来控制网页上的各类元素该怎么表演给观众看——比如知乎主页右边那个回到页首的小箭头就是个演员，你可以用脚本告诉它只在屏幕下拉到某个特定长度的时候才出现

## javascript历史及三大组成

网景公司于1995年发布JavaScript;

ECMAScript 是标准，JavaScript是具体实现

ES6于2015.6发布

JavaScript是一种专为与网页交互而设计的脚本语言

由 ECMAScript、BOM、DOM 三大部分组成

- ECMAScript：JavaScript的语法标准。包括变量、表达式、运算符、函数、if语句、for语句等。

- **DOM**：文档对象模型（Document object Model），操作**网页上的元素**的API。比如让盒子移动、变色、轮播图等。

- **BOM**：浏览器对象模型（Browser Object Model），操作**浏览器部分功能**的API。比如让浏览器自动滚动。

ES6  - 全称是ECMAScrip2015 
ES7  - 全称是ECMAScrip2016
ES8  - 全称是ECMAScrip2017
ES9  - 全称是ECMAScrip2018
ES10 - 全称是ECMAScrip2019
ES11 - 全称是ECMAScrip2020





## javascript的书写位置

1、行内式

直接写在标签上的

2、内嵌式

用script标签包裹起来的

3、外链式

通过src属性引入外部的.js文件

## javascript的基础语法

### 变量及命名规则与规范

使用var 定义变量

变量命名规则：变量名只能由数字、字母、下划线、美元符组成，不能是数字开头，严格区分大小写，不能使用关键字和保留字

变量命名规范：尽量不要使用中文，尽量命名与其有意义的单词，尽量使用驼峰命名发，如果有两个单词以上，从第二个单词开始首字母大写

### 注释

/* */  表多行注释    // 表单行注释

### 输出

alert    弹出一个提示框

prompt 弹出一个文本框  输入你想要输入的内容 格式是字符串

console.log  在控制台打印

document.write()  显示在页面上

confirm()   弹出一个提示框  返回值是  true和false  

### 包装类

### 包装类的介绍

我们都知道，js中的数据类型包括以下几种。

- 基本数据类型：String、Number、Boolean、Null、Undefined

- 引用数据类型：Object

JS为我们提供了**三个包装类**：

- String()：将基本数据类型字符串，转换为String对象。

- Number()：将基本数据类型的数字，转换为Number对象。

- Boolean()：将基本数据类型的布尔值，转换为Boolean对象。

通过上面这这三个包装类，我们可以**将基本数据类型的数据转换为对象**。


代码举例：

```javascript
	var num = new Number(3);

	var str = new String("hello");

	var bool = new Boolean(true);

	console.log(typeof num); // 打印结果：object
```


**需要注意的是**：我们在实际应用中不会使用基本数据类型的对象。如果使用基本数据类型的对象，在做一些比较时可能会带来一些**不可预期**的结果。

比如说：

```javascript
	var boo1 = new Boolean(true);
	var boo2 = new Boolean(true);

	console.log(boo1 === boo2); // 打印结果竟然是：false
```


再比如说：

```javascript
var boo3 = new Boolean(false);

if (boo3) {
	console.log('qianguyihao'); // 这行代码竟然执行了
}
```


### 基本数据类型不能添加属性和方法

方法和属性只能添加给对象，不能添加给基本数据类型。

**注意**：当我们对一些基本数据类型的值去调用属性和方法时，浏览器会**临时使用包装类将其转换为对象**，然后在调用对象的属性和方法；调用完以后，在将其转换为基本数据类型。

代码举例：

```javascript
	var str = 123;

	str = str.toString(); // 将 number 类型转换为 string 类型
	str.hello = "千古壹号"; // 添加属性

	console.log(typeof str); // 打印结果：string
	console.log(str.hello); // 打印结果：undefined
```

再比如，String 对象的很多内置方法，也可以直接给字符串用。此时，也是临时将字符串转换为 String 对象，然后再调用内置方法。

#### js面试题：请问JavaScript中的内置对象，本地对象，宿主对象分别是什么？

本地对象为Object Function Array String Boolean Number Date RegExp Error EvalError RangeError ReferenceError SyntaxError TypeError URIError 等可以new实例化
内置对象为gload Math this,arguments,event等不可以实例化的
宿主为浏览器自带的document,window 等

### 变量的数据类型(面试题)

分为两种 一种是基本数据类型  一种是引用数据类型

基本数据类型： String Number Boolean Undefiend null 

引用数据类型： Object

**常见的内置对象有Math,String,Array,Date**

两者的区别：

        基本数据类型： 参数赋值的时候，传数值。
        引用数据类型：参数赋值的时候，传地址（修改的同一片内存空间）
```
面试题：引用数据类型有几种？
  答：只有一种，即 Object 类型。
```

### 数据类型的检测

使用typeof操作符 

对象：number string boolean undefined object/null

     概要确定一个值是哪种基本类型可以使用typeof操作符，而确定一个值是哪种引用类型可以使用instanceof操作符。   
        所有变量（包括基本类型和引用类型）都存在于一个执行环境（也称为作用域）当中，这个执行环境决定了变量的生命周期，以及哪一部分代码可以访问其中的变量。



### 数据类型的转换（重点）

分为两种  一种是 隐式转换  一种是显示转换

**隐式转换**   就是不同类型的数据，浏览器会把不同数据改成相同的数据，再进行运算，

==   ===

例：  1+“2”   意思是 数字 与 字符串2 拼接  结果就是  12

**显示转换**（也叫强制转换）：parseInt() parseFloat() Number() Number() String() toString() Boolean

### 运算符

数学运算符

逻辑运算符

```javascript
// 如果第一个运算符是真值，
// 与操作返回第二个操作数：
alert( 1 && 0 ); // 0
alert( 1 && 5 ); // 5

// 如果第一个运算符是假值，
// 与操作直接返回它。第二个操作数被忽略
alert( null && 5 ); // null
alert( 0 && "no matter what" ); // 0
```

比较(关系)运算符

===

         如果为数值的时候，左边等于右边  为 ture  反之  false
            如果是字符串数字和数字 也就是说数据类型 不统一的情况下 组合 结果 是为 false 的
三目运算符

赋值运算符

逗号运算符

自增自减运算符

### 分支结构

if分支结构

switch分支结构

### 循环结构语句（重点）

for in 可以用来循环dom集合，循环时把数组的下标作为属性名(键)

for

```
for in 和 for 的区别

相同点  两者都是作用在循环当中的，循环对象可以是变量

不同点 for in 循环也可以是 对象 for 循环，没法直接循环对象，
```

while

do while

for of

for...of 循环可以使用的范围包括：

1. 数组
2. Set
3. Map
4. 类数组对象，如 arguments 对象、DOM NodeList 对象
5. Generator 对象
6. 字符串

### 循环语句的控制

break:  可以用来结束switch语句或整个循环语句，多用于 switch里面，if里面不能用

continue:用来跳过当前循环，可用于for循环中，

```
break和continue的区别  
相同点：
	都作用于循环中
不同点：
	continue和break有点类似，区别在于continue只是终止本次循环，接着还执行下一次循环
	break用于完全结束一个循环，跳出循环体执行循环后面的语句
```

再说一下 return break continue的区别

```
 return ：直接跳出当前的方法,返回到该调用的方法的语句处,继续执行，作用于方法，结束当前方法，主要用来返回方法返回值，当方法有返回值的时候，返回对应类型的返回值，没有返回值时，可以返回空，或者不返回

 break：在循环体内结束整个循环过程， 作用于语法结构，作用于结构结束当前结构，主要多用于循环和switch结构中

 continue ：结束本次的循环，直接进行下一次的循环， 作用于语法结构，结束当前方法，结束当前结构，主要用于循环的加速

```

### 函数（重点）

#### 什么是函数

就是将一些语句进行封装，在需要使用的时候，再进行调用，

#### 特点：

**封装代码**

        封装代码   使代码更加简洁
        重复使用
        调用时机
        复用性
        模块化
        开发效率高，维护方便
#### 函数的参数、返回值及创建方式

函数的参数：  形参 实参 伪数组(arguments 当实参不确定个数的时候 用 arguments 注意它不是一个数组)

返回值：return 返回实参传递给形参的值

声明式函数： function 函数名 () {}

赋值式函数：var 函数名 = function () {}

          函数调用上的区别:       
          		声明式函数可以在声明之前调用, 也可以在声明之后调用      
                赋值式函数只能在声明之后调用, 声明之前调用会报错
#### 执行期上下文

当**函数执行**时（准确来说，是在函数发生预编译的前一刻），会创建一个执行期上下文的内部对象。一个执行期上下文定义了一个函数执行时的环境。

每调用一次函数，就会创建一个新的上下文对象，他们之间是相互独立且独一无二的。当函数执行完毕，它所产生的执行期上下文会被销毁

#### 预解析

```
预 在所有代码执行之前

解析 对代码进行通读并解释一下

预解析也叫预编译  从写代码，到代码执行

预解析什么

声明式函数： 告诉浏览器，这个名字已经被定义过了，并且是一个函数

var关键字：告诉浏览器，这个变量名已经被定义过了，但是还没有赋值

预编译做的事情：

优化代码

把需要的默认值，默认代码都加上

预编译示例：变量声明提升
```

### JavaScript 运行三部曲

- 语法分析

- 预编译

- 解释执行

### 预编译前奏

> 在讲预编译前，我们先来普及下面两个规律。

#### 两个规律

**规律1：任何变量，如果未经声明就赋值，此变量是属于 window 的属性**，而且不会做变量提升。（注意，无论在哪个作用域内赋值）

比如说，如果我们直接在代码里写 `console.log(a)`，这肯定会报错的，提示找不到 `a`。但如果我直接写 `a = 100`，这就不会报错，此时，这个 `a` 就是 `window.a`。

**规律2：一切声明的全局变量，全是window的属性**。（注意，我说的是在全局作用域内声明的全局变量，不是说局部变量）

比如说，当我定义 `var a = 200` 时，这此时这个 `a` 就是 `window.a`。

由此，我们可以看出：**window 代表了全局作用域**（是说「代表」，没说「等于」）。

#### 举例

掌握了上面两句话之后，我们再来看看下面的例子。

```javascript
function foo() {
    var a = b = 100; // 连续赋值
}

foo();

console.log(window.b); // 在全局范围内访问 b
console.log(b); // 在全局范围内访问 b，但是前面没有加 window 这个关键字

console.log(window.a); // 在全局范围内访问 a
console.log(a); // 在全局范围内访问 a，但是前面没有加 window 这个关键字

```

上方代码的打印结果：

```
100

100

undefined

（会报错，提示 Uncaught ReferenceError: a is not defined）

```

**解释**：

当执行了`foo()`函数之后， `var a = b = 100` 这行**连续赋值**的代码等价于 `var a = (b = 100)`，其执行顺序是：

（1）先把 100 赋值给 b；

（2）再声明变量 a；

（3）再把 b 的值赋值给 a。

我们可以看到，b 是未经声明的变量就被赋值了，此时，根据规律1，这个 b 是属于 `window.b`；而 a 的作用域仅限于 foo() 函数内部，不属于 window。所以也就有了这样的打印结果。

### 预编译

#### 函数预编译的步骤

> 函数预编译，发生在函数执行的前一刻。

（1）创建AO对象。AO即 Activation Object 活跃对象，其实就是「执行期上下文」。

（2）找形参和变量声明，将形参名和变量作为 AO 的属性名，值为undefined。

（3）将实参值和形参统一，实参的值赋给形参。

（4）查找函数声明，函数名作为 AO 对象的属性名，值为整个函数体。

这个地方比较难理解。但只有了解了函数的预编译，才能理解明白函数的执行顺序。

代码举例：

```javascript
function fn(a) {
    console.log(a);

    var a = 666;

    console.log(a);

    function a() {}

    console.log(a);

    var b = function() {};

    console.log(b);

    function c() {}
}

fn(1);
```

打印结果：

```
ƒ a() {}
666
666
ƒ () {}
```

#### 预解释

```
预解释也叫预声明，是提前解释声明的意思；预解释是针对变量和函数来说的；但是变量和function的的预解释是两套不同的机制；

当浏览器加载我们的HTML页面的时候，首先会提供一个供JS代码执行的环境->全局作用域global（浏览器中的全局作用域，也叫顶级作用域是window）

JS中的内存空间分为两种：栈内存、堆内存

- 栈内存；提供JS代码执行的环境，存储基本数据类型的值；->全局作用域或者私有的作用域其实都是栈内存；
- 堆内存；存储引用数据类型的值（对象是把属性名和属性值储存进去，函数是把函数体内的代码当做字符串储存进去）

在当前的作用域中，JS代码执行之前，浏览器首先会默认的把所有代var和function的进行提前的声明或者定义，->“预解释”（也叫变量提升）

【in】:检测某一个属性名是否属于这个对象(不管是私有的属性还是公有的属性,只要是当前对象的属性返回true,不是的话返回false)
```



```
预解释机制

不管条件是否成立都要进行预解释

预解释只发生在”=“的左边,只把左边的进行预解释,右边的是值是不进行预解释的

函数体中return下面的代码都不在执行了,但是下面的代码需要参加预解释；而return后面的东西是需要处理的，但是由于它是当做一个值返回的，所以不进行预解释；

匿名函数的function在全局作用域下是不进行预解释的;

在预解释的时候,如果遇到名字重复了,只声明一次,不重复的声明,但是赋值还是要重复的进行的
```

### 递归（重点）


    递过去-------------归回来    简称-------递归


总结 （递归使用的时度的把握）：
    递归函数概念
        递归就是特殊的嵌套调用
        递归就是函数自己调用自己
        递归函数中必须有一个分支是不调用自己的，要不然就 死循环了
    递归函数的特点
        跟踪比较麻烦
        执行效率低
    递归函数使用场景（度的把握）
        如果一个需求能用循环解决也能用递归解决，建议使用递归
        **再树形结构里，是必须用递归的  在设计模式中  组合模式中 写web页面的菜单 有使用到**



### 变量声明提升和函数声明提升（重点）

使用var关键字声明的变量（ 比如 `var a = 1`），**会在所有的代码执行之前被声明**（但是不会赋值），但是如果声明变量时不是用var关键字（比如直接写`a = 1`），则变量不会被声明提前

举例1：

```javascript
    console.log(a);
    var a = 123;
```


打印结果：undefined

举例2：

```javascript
    console.log(a);
    a = 123;   //此时a相当于window.a
```

程序会报错：


![](http://img.smyhvae.com/20180314_2136.png)

```javascript
console.log(a);//underfined

 var a = 1; 

console.log(b); //underfined

 var b = function(){};
```

这里就是变量提升起到的作用。我们在用var或者函数声明的方式定义一个变量时，这个变量的定义会提升到方法体的最顶端，

**函数声明和变量声明总是会被解释器悄悄地被"提升"到方法体的最顶部**

**函数声明提升的优先级高于变量声明的提升**

值得注意的是，我们使用let，const定义变量的时候，并不会发生提升，因为它存在局部（块）作用域的概念，会出现**暂时性死区**，所以在它们之前打印变量将报错

### 作用域（Scope）的概念

- **概念**：通俗来讲，作用域是一个变量或函数的作用范围。作用域在**函数定义**时，就已经确定了。

- **目的**：为了提高程序的可靠性，同时减少命名冲突。

#### 作用域的分类

在 JS 中，一共有两种作用域：（ES6 之前）

- 全局作用域：作用于整个 script 标签内部，或者作用域一个独立的 JS 文件。

- 函数作用域（局部作用域）：作用于函数内的代码环境。

#### 作用域的访问关系

在内部作用域中可以访问到外部作用域的变量，在外部作用域中无法访问到内部作用域的变量。

代码举例：

```javascript
var a = 'aaa';
function foo() {
    var b = 'bbb';
    console.log(a); // 打印结果：aaa。说明 内层作用域 可以访问 外层作用域 里的变量
}

foo();
console.log(b); // 报错：Uncaught ReferenceError: b is not defined。说明 外层作用域 无法访问 内层作用域 里的变量
```

#### 变量的作用域

根据作用域的不同，变量可以分为两类：全局变量、布局变量。

**全局变量**：

- 在全局作用域下声明的变量，叫「全局变量」。在全局作用域的任何一地方，都可以访问这个变量。

- 在全局作用域下，使用 var 声明的变量是全局变量。

- 特殊情况：在函数内不使用 var 声明的变量也是全局变量（不建议这么用）。

**局部变量**：

- 定义在函数作用域的变量，叫「局部变量」。

- 在函数内部，使用 var 声明的变量是局部变量。

- 函数的**形参**也是属于局部变量。

从执行效率来看全局变量和局部变量：

- 全局变量：只有浏览器关闭时才会被销毁，比较占内存。

- 局部变量：当其所在的代码块运行结束后，就会被销毁，比较节约内存空间。

#### 作用域的上下级关系

当在函数作用域操作一个变量时，它会先在自身作用域中寻找，如果有就直接使用（**就近原则**）。如果没有则向上一级作用域中寻找，直到找到全局作用域；如果全局作用域中依然没有找到，则会报错 ReferenceError。

在函数中要访问全局变量可以使用window对象。（比如说，全局作用域和函数作用域都定义了变量a，如果想访问全局变量，可以使用`window.a`）

#### 全局作用域

直接编写在script标签中的JS代码，都在全局作用域。

- 全局作用域在页面打开时创建，在页面关闭时销毁。

- 在全局作用域中有一个全局对象window，它代表的是一个浏览器的窗口，由浏览器创建，我们可以直接使用。

在全局作用域中：

- 创建的**变量**都会作为window对象的属性保存。比如在全局作用域内写 `var a = 100`，这里的 `a` 等价于 `window.a`。

- 创建的**函数**都会作为window对象的方法保存。


### 变量的声明提前（变量提升）

使用var关键字声明的变量（ 比如 `var a = 1`），**会在所有的代码执行之前被声明**（但是不会赋值），但是如果声明变量时不是用var关键字（比如直接写`a = 1`），则变量不会被声明提前。

**举例1**：

```javascript
    console.log(a);
    var a = 123;
```

打印结果：undefined。注意，打印结果并没有报错，而是 undefined，说明变量 a 被提前声明了，只是尚未被赋值。

**举例2**：

```javascript
    console.log(a);
    a = 123;   //此时a相当于window.a
```

程序会报错：`Uncaught ReferenceError: a is not defined`。

**举例3**：

```javascript
    a = 123;   //此时a相当于window.a
    console.log(a);
```

打印结果：123。

**举例4**：

```javascript
foo();

function foo() {
    if (false) {
        var i = 123;
    }
    console.log(i);
}
```

打印结果：undefined。注意，打印结果并没有报错，而是 undefined。这个例子，再次说明了：变量 i 在函数执行前，就被提前声明了，只是尚未被赋值。



### 函数的声明提前

**函数声明**：

使用`函数声明`的形式创建的函数`function foo(){}`，**会被声明提前**。

也就是说，整个函数会在所有的代码执行之前就被**创建完成**。所以，在代码顺序里，我们可以先调用函数，再定义函数。

代码举例：

```javascript
    fn1();  // 虽然 函数 fn1 的定义是在后面，但是因为被提前声明了， 所以此处可以调用函数

    function fn1() {
        console.log('我是函数 fn1');
    }

```

**函数表达式**：

使用`函数表达式`创建的函数`var foo = function(){}`，**不会被声明提前**，所以不能在声明前调用。

很好理解，因为此时foo被声明了（这里只是变量声明），且为undefined，并没有把 `function(){}` 赋值给 foo。

所以说，下面的例子，会报错：

![](http://img.smyhvae.com/20180314_2145.png)

### 函数作用域

**提醒1**：在函数作用域中，也有声明提前的特性：

- 函数中，使用var关键字声明的变量，会在函数中所有的代码执行之前被声明。

- 函数中，没有var声明的变量都是**全局变量**，而且并不会提前声明。

举例：

```javascript
    var a = 1;

    function foo() {
        console.log(a);
        a = 2;     // 此处的a相当于window.a
    }

    foo();
    console.log(a);   //打印结果是2

```

上方代码中，执行foo()后，函数里面的打印结果是`1`。如果去掉第一行代码，执行foo()后，函数里面的打印结果是`Uncaught ReferenceError: a is not defined`。

**提醒2**：定义形参就相当于在函数作用域中声明了变量。

```javascript
    function fun6(e) { // 这个函数中，因为有了形参 e，此时就相当于在函数内部的第一行代码里，写了 var e;
        console.log(e);
    }

    fun6();  //打印结果为 undefined
    fun6(123);//打印结果为123
```

## JavaScript 没有块级作用域（ES6之前）

在其他编程语言中（如 Java、C#等），存在块级作用域，由`{}`包括起来。比如在 Java 语言中，if 语句里创建的变量，只能在if语句内部使用：

```java
if(true){
    int num = 123;
    system.out.print(num); // 123
}
system.out.print(num); // 报错
```

但是，在 JS 中没有块级作用域（ES6之前）。举例如下：

```javascript
if(true){
var num = 123;
    console.log(123); //123
}

console.log(123); //123（可以正常打印）

```

## 作用域链

引入：

- 只要是代码，就至少有一个作用域

- 写在函数内部的局部作用域

- 如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域

基于上面几条内容，我们可以得出作用域链的概念。

**作用域链**：内部函数访问外部函数的变量，采用的是链式查找的方式来决定取哪个值，这种结构称之为作用域链。查找时，采用的是**就近原则**。

代码举例：

```javascript
var num = 10;

function fn() {
    // 外部函数
    var num = 20;

    function fun() {
        // 内部函数
        console.log(num);
    }
    fun();
}
fn();

```

打印结果：20。





#### 作用域

顶级作用域   window

```
作用域只有两种

window全局作用域

函数执行形成的私有作用域
```

{name:“”} if(){} for(){} while(){} switch(){} 这些都不会产生作用域；

ES6可以用let形成块级作用域

作用域的上下级关系    函数写在哪一个作用域里面，这个函数就是那一个作用域的子级

#### 变量的使用规则

定义规则   一定要有  var 关键字 

```
    定义在哪一个作用域里面的变量 就是 属于哪一个作用域及后代作用域使用
```

赋值规则 必须要有赋值运算    要有 = 或者 += 或者 -=     n1 = 200

```
    当你需要给一个变量赋值的时候  先在自己作用域查找，如果自己有，就给自己赋值
    如果自己没有，就去 上级  作用域查找，如果有就赋值
    如果上级作用域还没有，就再去上级查找，如果有就赋值
    一直到全局作用域都没有，那么把这个变量  定义为全局变量   再进行赋值    
```

使用规则   我需要拿到某一个变量的值       console.log(n1) 

        当你需要使用一个变量的时候
        现在自己作用域查找，如果自己有，就拿自己的用
        如果自己没有，就去  上级  作用域查找，如果有就拿来用
        如果上级作用域还没有，就去再上级查找，如果有就拿用
        一直到全局作用域都没有，那么就报错 XX is not defined


### 引用类型（重点）

引用类型也称为 对象定义  是描述一类对象是具有属性和方法的



#### 对象的的定义

```
字面量方法：var obj = {}

内置构造函数创建对象： var obj = new Object()
```

 有两种操作语法，都具有增删改查的功能

```JS
点表示法：对象.属性名
 					obj.name = 'jack' //增加对象        
                    obj.age = 20    //增加对象                        
                    delete obj.name;//删除对象                               
                    obj.name = 'Rose'; //修改对象                            
                    console.log(obj.name, obj.age); //查询对象 如果没有这个对象 就返回 undefined        
                    console.log(obj)JS

数组关联语法：对象["属性名"] = 属性值
 		var obj = {}
        obj['name'] = '李海' 添加一个  数组关联的 对象
        obj['gender'] = '男' 添加一个  数组关联的 对象     
        delete obj['gender'];删除  数组关联的 对象  
        obj['gender'] = '女'; //修改 数组关联的  对象   
        console.log(obj['gender']) // 查询 数组关联的  对象  
        console.log(obj)   

两者的区别：

相同点：访问对象属性的方法是一致的

不同点：数组关联语法可以通过变量来访问属性，如果属性中包含会导致语法错误的字符，或者属性名使用的是关键字或保留字，也可以使用它，
```

注意：通常，除非必须使用变量来访问属性，否则我们建议使用点表示法

### 内存（重点）

栈区：基本数据类型保存在栈区，会根据函数的结束而自动释放

堆区：需要手动开辟，并且需要手动释放

### Array（重点）

#### 认识数组

**内置对象是JS语言自带的对象**，提供了一些基本的功能供开发者使用。常用的内置对象有Math，String，Array，Date等。

**数组就是对象（**属性（变量）和方法（函数）的集合）

**可以存储多个不同类型的数据**

#### 数组的定义

**new**

1、在堆区开辟内存空间来存储对象

2、返回堆区对象的引用

通过栈区的引用，访问堆区的对象

var arr = new Array();

**arr  栈区 存储的是一个变量   new 之后的  放在 堆区 存储的是数组对象**

**字面量表示法**：数组字面量由一对包含数组项的方括号表示，多个数组项之间以逗号隔开

var num = []  ;  var num = [1,2,3,4,5,6];

 **构造函数模式**

var num = new Array("1","2","3")   var num = new Array(4) //表示创建包含4项的数组

#### 数组的访问

数组的访问（赋值与取值）

数组元素的访问：直接通过数组下标访问

赋值与取值：通过数组下标取值，并可以对其进行赋值

#### 数组的遍历

快速遍历：for-in

for循环遍历

forEach()遍历

#### 数组的length属性

数组的项数保存在其 length 属性中，这个属性始终会返回 0 或更大的值，

数组的 length 属性很有特点——它不是只读的。因此，通过设置这个属性，可以从数组的末尾移除项或向数组中添加新项

```
例：

var colors = ["red", "blue", "green"];  // 创建一个包含 3 个字符串的数组`

colors.length = 2;`

console.log(colors[2]);                 //undefined，此时的colors数组已经被改变了；数组 colors 一开始有 3 个值。将其 length 属性设置为 2 会移除最后一项（位置为2 的那一项），结果再访问 colors[2] 就会显示 undefined 了。`

colors.length = 10;`

console.log(colors[9]);                 //undefined,虽然 colors 数组包含 2 个项，但把它的 length 属性设置成了 10。这个数组不存在位置 9，所以访问这个位置的值就得到了特殊值 undefined 。`
```

利用 length 属性也可以方便地在数组末尾添加新项

```
`var colors = ["red", "blue", "green"]; // 创建一个包含 3 个字符串的数组`   colors[colors.length] = "black"; // （在位置 3 ）添加一种颜色`    colors[colors.length] = "brown"; // （在位置 4 )再添加一种颜色`
```

删除数组的最后一项

例：

arr.length = arr.length-1

#### 数组的操作方法

##### 改变原数组的方法

###### 添加元素

push()		向数组末尾增加新元素，返回新增后数组的长度

unshift()		向数组开头增加新元素，返回新增后数组的长度

splice()		

- splice(n,m) 从索引n开始删除m个元素，把删除的部分当作新数组返回
- splice(n,m,x) 从索引n开始删除m个元素，把删除的部分当作新数组返回，并且用x替换原来位置的内容
- splice(n,0,x) 把x添加到指定索引n之前

###### 修改元素

splice()

reverse()		将数组倒过来排序

sort()		数组排序的方法	arr.sort(function(a,b){return a-b;});来实现数组的升序排列

###### 查找元素

slice()

- slice(n,m) 从索引n开找到索引m处(不包含m)，将找到的内容放到新数组返回，原有的数组不变
- slice(n) 从索引n处一直找到数组末尾；
- slice(0) 数组克隆

###### 删除元素

pop()		 删除数组末尾的元素，返回删除的内容

shift()		删除数组第一位元素，返回删除后的内容

splice()

##### 不会改变原数组的方法

concat()		 将两个数组进行拼接

 slice()

join 将数组按照指定的分隔符拆分字符串

 var arr = [1, 2, 3];

  var str = arr.join("-");

  console.log(str);//1-2-3

  console.log(typeof str);//string

toString 将数组转化为字符串



## ES5新增的数组(高阶函数)和字符串(重点)

#### 高阶函数

##### indexof() \lastindexof()		

获取数组中某一项的索引，通常用来检测数组中是否包含某一项内容，不包含返回的是-1,这个方法在IE678下不兼容； 

lastindexof

  一个参数的时候  就是  找最后一个出现元素

两个参数时，从第二个参数 往前找 返回最近值 的索引

##### 回调函数的参数

第一个参数：数组的每个元素

第二个参数：数组的下标:可选

第三个参数：数组本身：可选

##### forEach()	

格式数组.forEach（回调函数）:把数组的每一个元素遍历一下。可以替代普通for循环

不会产生新的数组，改变原数组，这个方法在IE678不兼容，

​	ary.forEach(function(item,index,input){},cantext);第二个参数是指定函数中的this，不写默认是window

​	let arr = [1,2,3];     arr.forEach(function(item,index,arr){  arr[index] = item + 1})

##### map()	

循环数组中的每一项，然后进行相关的操作，相对于forEach来说，map有返回值，可以修改数组中某一项，

返回一个新的数组，不会改变原数组，IE678不兼容

​	ary.map(function(item,index,input){},cantext);第二个参数是指定函数中的this，不写默认是window

##### filter()

在原始数组里面进行筛选，过滤，把原始数组中每个元素满总条件的元素跳出来，放在一个新的数组中 

返回一个新的数组，不会改变原数组，IE678不兼容

##### forEach() map() filter()  的区别

```
相同点：

参数都是回调函数，回调函数里的参数也是一样的  在三个函数内部都会遍历原始数组

不同点：

forEach  遍历的意思，把原始数组的元素内容进行修改 不会产生一个新的数组

map    映射，产生一个新的数组，新的数组是原始数组进行运算后的结果，原始数组不变

filer   过滤，把原始数组中每个元素满总条件的元素跳出来，放在一个新的数组中 
```



#### 字符串

##### 定义

         构造函数的方式
                    var str new = String("hello");  //var arr = new Array(12,23,34)
                    console.log(str);
                    注意：用字符串定义的字符串是引用类型
                    console.log(typrof str)
                字面量的方式
                    var str1 = "hello"; //var arr = [12,45,67]
                    
                    console.log(str1);
                    注意：用字符串定义的字符串是基本类型
                    console.log(typrof str1)
##### 属性

字符串的长度：

字符串中的length是只读属性属性，不可更改，按各国标注字符来计算长度

##### 字符串编码

           a.  ASCLL码：让计算机认识了英文
    
        b.  GB2312码:让计算机认识了中文
    
       汉字可以作为变量名，但是不推荐

##### charAt()	

返回字符串种某个下标的字符	

##### charCodeAt()	

获取字符串种指定下标的字符对应的编码

 var str = "hallo world！";

​    console.log(str.charCodeAt(1));//97

##### String.fromCharCode()	

把编码转成字符，不需要定义字符串变量，该函数的前面写的是构造函数的名字，不是字符串变量

   var str = String.fromCharCode(97, 98, 99);

​    console.log(str);//abc

##### split()

把字符串按照指定的分隔符进行分隔，结果是数组  注：这个和 数组的join函数 是相逆的   join 是加 分隔符   而 split是 去除 指定的 分隔符

  var str = "2020-03-08";

​    var t = str.split("-");

​    console.log(t); //["2020", "03", "08"]

join

 var arr = ["2020", "03", "08"];

​    var str = arr.join("-");

​    console.log(str); //"2020-03-08"

##### subString()

截取字符串的一部分字符

##### substr()

截取字符串的一部分字符

##### subString()和substr()的区别

相同点：

都是截取字符串里面的字符

不同点：

substr 是包括 第二个参数的 索引的

substring 是不包括第二个参数的 索引的

##### toUpperCase()

把字符串中的字符转成大写

##### toLowerCase()

把字符串中的字符转成小写

##### slice()

截取字符串中的一部分；参数可以为 负数 注：如果参数是两个负数的话，其算法 与  其两个正数的算法 相反

##### slice()和subString()的区别

相同点：

都是截取字符串里面的字符

**这两个方法均不会改变原字符串**

不同点：

subString的参数只能是 0 和 正整数

slice的参数可以是 0 正整数和负数

如果说slice函数的参数都是0和正整数的话，那么就和subString是同样的意思了

##### substring,substr,slice的区别

相同点：

都是截取字符串里面的字符

不同点：

subString()   参数：  起始下标（0 和 正整数）    参数： 结束下标（不含） （0和正整数）

subStr()	参数：起始下标（0和正整数）	参数：长度（正整数）

slice()	参数：起始下标（0和正整数和负数）	参数：长度（正整数和负数）

##### concat()

把字符串和其他字符串拼接起来

##### lenght()

返回字符串的长度

##### indexof()

在字符串里查找指定的字符串，返回第一次出现的下标    如果 下标不存在 就会 报错

##### lastIndexof()

在字符串里查找指定的字符串，返回最后一次出现的下标   如果 下标不存在 就会 报错    

一个参数的时候 就是 找最后一个出现元素

两个参数时，从第二个参数 往前找返回最近值 的 索引

##### replace(oldStr, newStr)

字符串替换,默认只能替换第一次出现的oldStr,通过正则表达式可以实现全部替换

##### localeCompare()

字符串比较大小

##### trim()

这个方法会创建一个字符串的副本，删除前缀及后缀的所有空格，然后返回结果

var str = "   hello   "

consloe.log(str.trim());//"hello"

console.log(str);//"   hello   "

## 严格模式

### “use strict“

对于老版本浏览器来说，就是个普通的字符串，不会出错
新版本浏览器，看到了这个字符串后，就知道，该用严格模式了

  注:想开启严格模式，直接在代码最开始的位置写 "use strict”，如果不再最后开始写，那么不起作用 

### 不能是八进制          

### 形参不能重名

### var 关键词

### with

 如果在严格模式下  将会不起作用
        以前的with关键字可以省去重复的对象的书写 
        document.write() 可以简写为  with(document){}

### 作用域

针对一个函数：写在函数的第一行
            function fn(){
                “use strict”;//使用严格模式
                }        
            function fn1(){
                               

​			}

单个js文件：在js文件里尽量使用自运行函数,
            如果有三个 .js 文件  第一个使用了 严格模式 那么 之后的两个 会有影响
            这时 需要 使用 自运行函数
             自运行函数（立即执行函数）(function(){    "use strict";
})();

;(function() {
	'use strict'

})()

## Math(重点)

### Math.PI 不需要定义，直接使用

### Math对象的属性和官方函数

#### Math.random()

随机数  默认 0-1 不含0和1

#### Math.ceil()

向上取整

#### Math.floor() 

向下取整     

#### Math.max()

参数是多个数字，求最大数字

#### Math.min()

参数是多个数字，求最小数

#### Math.pow(底数，指数)

求幂

#### Math.sqrt(n)

 开根号

#### Math.abs() 

求绝对值    

## Date(重点)

### get相关的函数

#### getYear()

这是在最早编程语言中，使用的，获取两位年份的函数

#### getFullYear()

获取年份 full 表示 四位的年份

#### getMmonth()

获取月份 默认 从0开始

#### getDate()

获取 日期 1-31

#### getHours()

获取小时 0-23

#### getMinutes()

获取分钟 0-59

#### getSeconds()

获取秒 0-59

#### getMilliseconds()

获取 毫秒 1s = 1000ms

#### getDay()

获取的是 星期  0-6(0代表周日)

#### 获取毫秒数

getTime():  获取的是从1970年1月1日0点0分0秒到现在的毫秒数       一天 为 8640000 毫秒       1s = 1000ms 一天 24*60*60 秒    24*60*60*1000 毫秒

Date.now()

Date.parse("2020-3-28 19:23")

date.valueOf()

### set相关的官方函数

#### setYear()

改变年份

#### setMonth()

改变月份

#### setDate()

改变日期

#### setHours()

改变小时

#### setMinutes()

改变分钟

#### setSeconds()

改变秒钟

#### 注：set 函数里面没有  设置星期之说

### 把日期对象转换成字符串

var d = new Date   这个时间是当前系统的时间

跟本地相同的日期显示格式

toLocaleDateString():  根据本地时间格式，把 Date 对象的日期部分转换为字符串 

 

```
   var d = new Date(); //默认是当前计算机（系统）的时间

​    var str = d.toLocaleDateString(); //d.getFullYear()+"/"+(d.getMonth()+1)+"/"+d.getDate();

​    console.log(str); //2020/03/19

​    console.log(typeof str); //string
```

toLocaleTimeString(): 根据本地时间格式，把Time对象的时间部分转换为字符串

```
 var d = new Date(); //默认是当前计算机（系统）的时间

​    var str = d.toLocaleTimeString();

​    console.log(str); //下午12:56:11
```

toLocaleString():根据本地时间格式，把日期，时间转换为字符串

```
var d = new Date(); //默认是当前计算机（系统）的时间

​    var str = d.toLocaleString();

​    console.log(str);//2020/4/18 下午12:57:13
```



### 国际通用日期显示格式

toDataString(): 把 Date 对象的日期部分 转换为字符串

```
    var d = new Date(); //默认是当前计算机（系统）的时间

​    var str = d.toDateString();

​    console.log(str); //Sat Apr 18 2020
```

toTimeSteing():把Time对象的时间部分 转换为字符串

```
  var d = new Date(); //默认是当前计算机（系统）的时间

​    var str = d.toTimeString();

​    console.log(str);//13:01:59 GMT+0800 (中国标准时间)
```

toUTCString():  格林尼治时间，就是零时区时间

```
    var d = new Date(); //默认是当前计算机（系统）的时间

​    var str = d.toUTCString();

​    console.log(str);//Sat, 18 Apr 2020 05:02:43 GMT
```



## DOM几个级别的介绍

### DOM1级

是很早以前成为W3C标准的，由DOM核心和DOM HTML两部分组成，DOM核心规定是如何映射基于XML的文档结构，以便简化对文档中任意部分的访问和操作；DOM HTML模块则在DOM核心的基础上加以扩展，添加了针对HTML的对象和方法；主要目标是映射文档的结构；

### DOM2级

在原来的DOM1级基础上扩充了鼠标和用户界面事件等；主要包括DOM视图，DOM事件、DOM样式、DOM遍历和范围；

### DOM3级

引入了以统一方式加载和保存文档的方法（在DOM加载和保存模块中定义）；新增了验证文档的方法（在DOM验证模块中定义）；DOM3级也对DOM核心进行了扩展，开始支持XML1.0，涉及XML infoset，Xpath和XML Base。



## 事件（重点）

事件就是事情，发生在DOM对象或者BOM对象上的事情

## 事件简介

事件：就是文档或浏览器窗口中发生的一些特定的交互瞬间。对于 Web 应用来说，有下面这些代表性的事件：点击某个元素、将鼠标移动至某个元素上方、关闭弹窗等等。

JavaScript 是以**事件驱动为核心**的一门语言。JavaScript 与 HTML 之间的交互是通过事件实现的。

### 事件的三要素

**事件的三要素：事件源、事件、事件驱动程序**。

比如，我用手去按开关，灯亮了。这件事情里，事件源是：手。事件是：按开关。事件驱动程序是：灯开了或者关了。

再比如，网页上弹出一个广告，我点击右上角的`X`，广告就关闭了。这件事情里，事件源是：`X`。事件是：onclick。事件驱动程序是：广告关闭了。

于是我们可以总结出：谁引发的后续事件，谁就是事件源。

**总结如下：**

- 事件源：引发后续事件的html标签。

- 事件：js已经定义好了（见下图）。

- 事件驱动程序：对样式和html的操作。也就是DOM。

也就是说，我们可以在时间对应的属性中写一些js代码，当事件被触发时，这些代码将会执行。

**代码书写步骤如下：**（重要）

- （1）获取事件源：document.getElementById(“box”);   // 类似于Android里面的findViewById

- （2）绑定事件： 事件源box.事件onclick = function(){ 事件驱动程序 };

- （3）书写事件驱动程序：关于DOM的操作。

最简单的代码举例：（点击box1，然后弹框）

```html
<body>
<div id="box1"></div>

<script type="text/javascript">
    // 1、获取事件源
    var div = document.getElementById("box1");
    // 2、绑定事件
    div.onclick = function () {
        // 3、书写事件驱动程序
        alert("我是弹出的内容");
    }
</script>

</body>
```

常见的事件如下：

![](http://img.smyhvae.com/20180126_1553.png)

下面针对这事件的三要素，进行分别介绍。

#### 1、获取事件源的方式（DOM节点的获取）

获取事件源的常见方式如下：

```javascript
var div1 = document.getElementById("box1");      //方式一：通过id获取单个标签

var arr1 = document.getElementsByTagName("div");     //方式二：通过 标签名 获得 标签数组，所以有s

var arr2 = document.getElementsByClassName("hehe");  //方式三：通过 类名 获得 标签数组，所以有s
```

#### 2、绑定事件的方式

方式一：直接绑定匿名函数

```html
<div id="box1" ></div>

<script type="text/javascript">
    var div1 = document.getElementById("box1");
    //绑定事件的第一种方式
    div1.onclick = function () {
        alert("我是弹出的内容");
    }
</script>
```

方式二：先单独定义函数，再绑定

```html
 <div id="box1" ></div>

<script type="text/javascript">
    var div1 = document.getElementById("box1");
    //绑定事件的第二种方式
    div1.onclick = fn;   //注意，这里是fn，不是fn()。fn()指的是返回值。
    //单独定义函数
    function fn() {
        alert("我是弹出的内容");
    }
</script>
```

注意上方代码的注释。**绑定的时候，是写fn，不是写fn()**。fn代表的是整个函数，而fn()代表的是返回值。

方式三：行内绑定

```html
<!--行内绑定-->
<div id="box1" onclick="fn()"></div>

<script type="text/javascript">

    function fn() {
        alert("我是弹出的内容");
    }

</script>
```

注意第一行代码，绑定时，是写的`"fn()"`，不是写的`"fn"`。因为绑定的这段代码不是写在js代码里的，而是被识别成了**字符串**。

#### 3、事件驱动程序

我们在上面是拿alert举例，不仅如此，我们还可以操作标签的属性和样式。举例如下：

点击鼠标时，原本粉色的div变大了，背景变红：

```html
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: pink;
            cursor: pointer;
        }
    </style>
</head>

<body>

<div id="box1" ></div>

<script type="text/javascript">
    var div1 = document.getElementById("box1");
    //点击鼠标时，原本粉色的div变大了，背景变红了
    div1.onclick = function () {
        div1.style.width = "200px";   //属性值要写引号
        div1.style.height = "200px";
        div1.style.backgroundColor = "red";   //属性名是backgroundColor，不是background-color
    }
</script>
```

上方代码的注意事项：

- 在js里写属性值时，要用引号

- 在js里写属性名时，是`backgroundColor`，不是CSS里面的`background-color`。

实现效果如下：

![](http://img.smyhvae.com/20180126_1720.gif)

### onload事件

> onload事件比较特殊，这里单独讲一下。

**当页面加载（文本和图片）完毕的时候，触发onload事件。**

举例：

```html
<script type="text/javascript">
    window.onload = function () {
        console.log("smyhvae");  //等页面加载完毕时，打印字符串
    }
</script>
```

有一点我们要知道：**js的加载是和html同步加载的**。因此，如果使用元素在定义元素之前，容易报错。这个时候，onload事件就能派上用场了，我们可以把使用元素的代码放在onload里，就能保证这段代码是最后执行。

建议是：整个页面上所有元素加载完毕再执行js内容。所以，window.onload可以预防使用标签在定义标签之前

###   mouseover和mouseenter的区别

ouseover和mouseout:会受事件流（冒泡）的影响

mouseenter和mouseleave里，

1、不会受事件流（冒泡和捕获）的影响，

2、子盒子的区域属于父盒子的区域

3、父盒子和子盒子的事件各是各的，即：进入子盒子的区域（出发了事件）相当于进入了父盒子的区域（触发事件）

  **子盒子和父盒子有重叠区域**

    mouseover，mouseout：当从父元素进入到子元素区域时，会触发父元素的离开事件（mouseout），同时又触发了mouseover事件
    mouseenter，mouseleave：当从父元素进入到子元素区域时，不会触发父元素的离开事件（mouseleave）
    mouseover，mouseout：当从子元素进入到父元素区域时，先触发子盒子的离开事件（并冒泡到父盒子），再触发父盒子的进入事件
    mouseenter，mouseleave：当从子元素进入到父元素区域时，只触发子盒子的离开事件

**子盒子和父盒子没有重叠区域**

```
mouseover，mouseout：当进入到子元素区域时，触发子盒子的进入事件，冒泡到父盒子
mouseenter，mouseleave：当进入到子元素区域时，不触发子盒子的进入事件，冒泡到父盒子
mouseover，mouseout：当离开子元素区域时，触发了子盒子的离开事件，冒泡到父盒子
mouseenter，mouseleave：先触发了子盒子的离开事件，再触发了父盒子的离开事件（不是冒泡）
```

### 绑定事件的两种方式/DOM事件的级别

我们在之前的一篇文章《04-JavaScript/22-DOM简介和DOM操作》中已经讲过事件的概念。这里讲一下绑定（注册）事件的两种方式，我们以onclick事件为例。

#### DOM0的写法：onclick


```javascript
    element.onclick = function () {

    }
```

举例：

```html
<body>
<button>点我</button>
<script>
    var btn = document.getElementsByTagName("button")[0];

    //这种事件绑定的方式，如果绑定多个，则后面的会覆盖掉前面的
    btn.onclick = function () {
        console.log("事件1");
    }

    btn.onclick = function () {
        console.log("事件2");
    }

</script>
</body>

```

点击按钮后，上方代码的打印结果：

```html
事件2
```

我们可以看到，`DOM对象.事件 =  函数`的这种绑定事件的方式：一个元素的一个事件只能绑定一个响应函数。如果绑定了多个响应函数，则后者会覆盖前者。

#### DOM2的写法：addEventListener（高版本浏览器）

```javascript
    element.addEventListener('click', function () {

    }, false);
```


参数解释：

- 参数1：事件名的字符串(注意，没有on)

- 参数2：回调函数：当事件触发时，该函数会被执行

- 参数3：**true表示捕获阶段触发，false表示冒泡阶段触发（默认）**。如果不写，则默认为false。【重要】

举例：

```html
<body>
<button>按钮</button>
<script>
    var btn = document.getElementsByTagName("button")[0];

    // addEventListener: 事件监听器。 原事件被执行的时候，后面绑定的事件照样被执行
    // 这种写法不存在响应函数被覆盖的情况。（更适合团队开发）
    btn.addEventListener("click", fn1);
    btn.addEventListener("click", fn2);

    function fn1() {
        console.log("事件1");
    }

    function fn2() {
        console.log("事件2");
    }

</script>
</body>
```

点击按钮后，上方代码的打印结果：


```html
    事件1
    事件2
```

我们可以看到，`addEventListener()`这种绑定事件的方式：

- 一个元素的一个事件，可以绑定多个响应函数。不存在响应函数被覆盖的情况。**执行顺序是**：事件被触发时，响应函数会按照函数的绑定顺序执行。

- addEventListener()中的this，是绑定事件的对象。

- `addEventListener()`不支持 IE8 及以下的浏览器。在IE8中可以使用`attachEvent`来绑定事件（详见下一小段）。

#### DOM2的写法：attachEvent（IE8及以下版本浏览器）

```javascript
    element.attachEvent('onclick', function () {

    });

```

参数解释：

- 参数1：事件名的字符串(注意，有on)

- 参数2：回调函数：当事件触发时，该函数会被执行

举例：

```html
    <body>
        <button>按钮</button>
        <script>
            var btn = document.getElementsByTagName('button')[0];

            btn.attachEvent('onclick', function() {
                console.log('事件1');
            });

            btn.attachEvent('onclick', function() {
                console.log('事件2');
            });
        </script>
    </body>
```

在低版本的IE浏览器上，点击按钮后，上方代码的打印结果：


```html
    事件2
    事件1
```

我们可以看到，`attachEvent()`这种绑定事件的方式：

- 一个元素的一个事件，可以绑定多个响应函数。不存在响应函数被覆盖的情况。**注意**：执行顺序是，后绑定的先执行。

- attachEvent()中的this，是window

#### 兼容性写法

上面的内容里，需要强调的是：

- `addEventListener()`中的this，是绑定事件的对象。

- `attachEvent()`中的this，是window。

既然这两个写法的`this`不同，那么，有没有一种兼容性的写法可以确保这两种绑定方式的this是相同的呢？我们可以封装一下。代码如下：

```html
    <body>
        <button>按钮</button>
        <script>
            var btn = document.getElementsByTagName('button')[0];

            myBind(btn , "click" , function(){
                alert(this);
            });



            //定义一个函数，用来为指定元素绑定响应函数
            /*
             * addEventListener()中的this，是绑定事件的对象
             * attachEvent()中的this，是window
             *  需要统一两个方法this
             */
            /*
             * 参数：
             *  element 要绑定事件的对象
             *  eventStr 事件的字符串(不要on)
             *  callback 回调函数
             */
            function myBind(element , eventStr , callback){
                if(element.addEventListener){
                    //大部分浏览器兼容的方式
                    element.addEventListener(eventStr , callback , false);
                }else{
                    /*
                     * this是谁，由调用方式决定
                     * callback.call(element)
                     */
                    //IE8及以下
                    element.attachEvent("on"+eventStr , function(){
                        //在匿名函数 function 中调用回调函数callback
                        callback.call(element);
                    });
                }
            }

        </script>
    </body>
```


### 事件对象

当事件的响应函数被触发时，会产生一个事件对象`event`。浏览器每次都会将这个事件`event`作为实参传进之前的响应函数。

这个对象中包含了与当前事件相关的一切信息。比如鼠标的坐标、键盘的哪个按键被按下、鼠标滚轮滚动的方向等。

#### 获取 event 对象（兼容性问题）

所有浏览器都支持event对象，但支持的方式不同。如下。

（1）普通浏览器的写法是 `event`。比如：

![](http://img.smyhvae.com/20180203_1735.png)

（2）ie 678 的写法是 `window.event`。此时，事件对象 event 是作为window对象的属性保存的。

于是，我们可以采取一种兼容性的写法。如下：

```javascript
    event = event || window.event; // 兼容性写法
```

代码举例：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
<script>
    //点击页面的任何部分
    document.onclick = function (event) {
        event = event || window.event; ////兼容性写法

        console.log(event);
        console.log(event.timeStamp);
        console.log(event.bubbles);
        console.log(event.button);
        console.log(event.pageX);
        console.log(event.pageY);
        console.log(event.screenX);
        console.log(event.screenY);
        console.log(event.target);
        console.log(event.type);
        console.log(event.clientX);
        console.log(event.clientY);
    }
</script>
</body>
</html>
```

#### event 属性

event 有很多属性，比如：

![](http://img.smyhvae.com/20180203_1739.png)

由于pageX 和 pageY的兼容性不好，我们可以这样做：

- 鼠标在页面的位置 = 滚动条滚动的距离 + 可视区域的坐标。

#### Event举例

##### 举例1：使 div 跟随鼠标移动

代码实现：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title></title>
    <style type="text/css">
      #box1 {
        width: 100px;
        height: 100px;
        background-color: red;
        /*
        * 开启box1的绝对定位
        */
        position: absolute;
      }
    </style>

    <script type="text/javascript">
      window.onload = function() {
        /*
         * 使div可以跟随鼠标移动
         */

        //获取box1
        var box1 = document.getElementById("box1");

        //给整个页面绑定：鼠标移动事件
        document.onmousemove = function(event) {
          //兼容的方式获取event对象
          event = event || window.event;

          // 鼠标在页面的位置 = 滚动条滚动的距离 + 可视区域的坐标。
          var pagex = event.pageX || scroll().left + event.clientX;
          var pagey = event.pageY || scroll().top + event.clientY;

          //   设置div的偏移量（相对于整个页面）
          // 注意，如果想通过 style.left 来设置属性，一定要给 box1开启绝对定位。
          box1.style.left = pagex + "px";
          box1.style.top = pagey + "px";
        };
      };

      // scroll 函数封装
      function scroll() {
        return {
          //此函数的返回值是对象
          left: window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop,
          right:
            window.pageXOffset || document.body.scrollLeft || document.documentElement.scrollLeft
        };
      }
    </script>
  </head>
  <body style="height: 1000px;width: 2000px;">
    <div id="box1"></div>
  </body>
</html>
```

##### 举例2：获取鼠标距离所在盒子的距离

关键点：

```
    鼠标距离所在盒子的距离 = 鼠标在整个页面的位置 - 所在盒子在整个页面的位置
```

代码演示：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        .box {
            width: 300px;
            height: 200px;
            padding-top: 100px;
            background-color: pink;
            margin: 100px;
            text-align: center;
            font: 18px/30px "simsun";
            cursor: pointer;
        }
    </style>
</head>
<body>
<div class="box">

</div>

<script src="animate.js"></script>
<script>
    //需求：鼠标进入盒子之后只要移动，哪怕1像素，随时显示鼠标在盒子中的坐标。
    //技术点：新事件，onmousemove：在事件源上，哪怕鼠标移动1像素也会触动这个事件。
    //一定程度上，模拟了定时器
    //步骤：
    //1.老三步和新五步
    //2.获取鼠标在整个页面的位置
    //3.获取盒子在整个页面的位置
    //4.用鼠标的位置减去盒子的位置赋值给盒子的内容。

    //1.老三步和新五步
    var div = document.getElementsByTagName("div")[0];

    div.onmousemove = function (event) {

        event = event || window.event;
        //2.获取鼠标在整个页面的位置
        var pagex = event.pageX || scroll().left + event.clientX;
        var pagey = event.pageY || scroll().top + event.clientY;
        //3.获取盒子在整个页面的位置
        // var xx =
        // var yy =
        //4.用鼠标的位置减去盒子的位置赋值给盒子的内容。
        var targetx = pagex - div.offsetLeft;
        var targety = pagey - div.offsetTop;
        this.innerHTML = "鼠标在盒子中的X坐标为：" + targetx + "px;<br>鼠标在盒子中的Y坐标为：" + targety + "px;"
    }

</script>
</body>
</html>
```

实现效果：

![](http://img.smyhvae.com/20180203_1828.gif)

##### 举例3：商品放大镜

代码实现：

（1）index.html:

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        .box {
            width: 350px;
            height: 350px;
            margin: 100px;
            border: 1px solid #ccc;
            position: relative;
        }

        .big {
            width: 400px;
            height: 400px;
            position: absolute;
            top: 0;
            left: 360px;
            border: 1px solid #ccc;
            overflow: hidden;
            display: none;
        }

        /*mask的中文是：遮罩*/
        .mask {
            width: 175px;
            height: 175px;
            background: rgba(255, 255, 0, 0.4);
            position: absolute;
            top: 0;
            left: 0;
            cursor: move;
            display: none;
        }

        .small {
            position: relative;
        }

        img {
            vertical-align: top;
        }
    </style>

    <script src="tools.js"></script>
    <script>
        window.onload = function () {
            //需求：鼠标放到小盒子上，让大盒子里面的图片和我们同步等比例移动。
            //技术点：onmouseenter==onmouseover 第一个不冒泡
            //技术点：onmouseleave==onmouseout  第一个不冒泡
            //步骤：
            //1.鼠标放上去显示盒子，移开隐藏盒子。
            //2.老三步和新五步（黄盒子跟随移动）
            //3.右侧的大图片，等比例移动。

            //0.获取相关元素
            var box = document.getElementsByClassName("box")[0];
            var small = box.firstElementChild || box.firstChild;
            var big = box.children[1];
            var mask = small.children[1];
            var bigImg = big.children[0];

            //1.鼠标放上去显示盒子，移开隐藏盒子。(为小盒子绑定事件)
            small.onmouseenter = function () {
                //封装好方法调用：显示元素
                show(mask);
                show(big);
            }
            small.onmouseleave = function () {
                //封装好方法调用：隐藏元素
                hide(mask);
                hide(big);
            }

            //2.老三步和新五步（黄盒子跟随移动）
            //绑定的事件是onmousemove，而事件源是small(只要在小盒子上移动1像素，黄盒子也要跟随)
            small.onmousemove = function (event) {
                //新五步
                event = event || window.event;

                //想要移动黄盒子，必须要知道鼠标在small小图中的位置。
                var pagex = event.pageX || scroll().left + event.clientX;
                var pagey = event.pageY || scroll().top + event.clientY;

                //x：mask的left值，y：mask的top值。
                var x = pagex - box.offsetLeft - mask.offsetWidth / 2; //除以2，可以保证鼠标mask的中间
                var y = pagey - box.offsetTop - mask.offsetHeight / 2;

                //限制换盒子的范围
                //left取值为大于0，小盒子的宽-mask的宽。
                if (x < 0) {
                    x = 0;
                }
                if (x > small.offsetWidth - mask.offsetWidth) {
                    x = small.offsetWidth - mask.offsetWidth;
                }
                //top同理。
                if (y < 0) {
                    y = 0;
                }
                if (y > small.offsetHeight - mask.offsetHeight) {
                    y = small.offsetHeight - mask.offsetHeight;
                }

                //移动黄盒子
                console.log(small.offsetHeight);
                mask.style.left = x + "px";
                mask.style.top = y + "px";

                //3.右侧的大图片，等比例移动。
                //如何移动大图片？等比例移动。
                //    大图片/大盒子 = 小图片/mask盒子
                //    大图片走的距离/mask走的距离 = （大图片-大盒子）/（小图片-黄盒子）
//                var bili = (bigImg.offsetWidth-big.offsetWidth)/(small.offsetWidth-mask.offsetWidth);

                //大图片走的距离/mask盒子都的距离 = 大图片/小图片
                var bili = bigImg.offsetWidth / small.offsetWidth;

                var xx = bili * x;  //知道比例，就可以移动大图片了
                var yy = bili * y;

                bigImg.style.marginTop = -yy + "px";
                bigImg.style.marginLeft = -xx + "px";
            }
        }
    </script>
</head>
<body>
<div class="box">
    <div class="small">
        <img src="images/001.jpg" alt=""/>
        <div class="mask"></div>
    </div>
    <div class="big">
        <img src="images/0001.jpg" alt=""/>
    </div>
</div>
</body>
</html>
```

（2）tools.js:

```javascript
/**
 * Created by smyhvae on 2018/02/03.
 */

//显示和隐藏
function show(ele) {
    ele.style.display = "block";
}

function hide(ele) {
    ele.style.display = "none";
}

function scroll() {  // 开始封装自己的scrollTop
    if (window.pageYOffset != null) {  // ie9+ 高版本浏览器
        // 因为 window.pageYOffset 默认的是  0  所以这里需要判断
        return {
            left: window.pageXOffset,
            top: window.pageYOffset
        }
    }
    else if (document.compatMode === "CSS1Compat") {    // 标准浏览器   来判断有没有声明DTD
        return {
            left: document.documentElement.scrollLeft,
            top: document.documentElement.scrollTop
        }
    }
    return {   // 未声明 DTD
        left: document.body.scrollLeft,
        top: document.body.scrollTop
    }
}

```

效果演示：

![](http://img.smyhvae.com/20180203_1920.gif)

### DOM事件流

事件传播的三个阶段是：事件捕获、事件冒泡和目标。

- 事件捕获阶段：事件从祖先元素往子元素查找（DOM树结构），直到捕获到事件目标 target。在这个过程中，默认情况下，事件相应的监听函数是不会被触发的。

- 事件目标：当到达目标元素之后，执行目标元素该事件相应的处理函数。如果没有绑定监听函数，那就不执行。

- 事件冒泡阶段：事件从事件目标 target 开始，从子元素往冒泡祖先元素冒泡，直到页面的最上一级标签。

如下图所示：

![](http://img.smyhvae.com/20180204_1218.jpg)

PS：这个概念类似于 Android 里的 **touch 事件传递**。

#### 事件捕获

addEventListener可以捕获事件：

```javascript
    box1.addEventListener("click", function () {
        alert("捕获 box3");
    }, true);
```

上面的方法中，参数为true，代表事件在捕获阶段执行。

代码演示：

```javascript
    //参数为true，代表事件在「捕获」阶段触发；参数为false或者不写参数，代表事件在「冒泡」阶段触发
    box3.addEventListener("click", function () {
        alert("捕获 child");
    }, true);

    box2.addEventListener("click", function () {
        alert("捕获 father");
    }, true);

    box1.addEventListener("click", function () {
        alert("捕获 grandfather");
    }, true);

    document.addEventListener("click", function () {
        alert("捕获 body");
    }, true);
```

效果演示：

![](http://img.smyhvae.com/20180204_1101.gif)

（如果上面的图片打不开，请点击：<http://img.smyhvae.com/20180204_1101.gif>）

**重点**：捕获阶段，事件依次传递的顺序是：window --> document --> html--> body --> 父元素、子元素、目标元素。

这几个元素在事件捕获阶段的完整写法是：

```javascript
    window.addEventListener("click", function () {
        alert("捕获 window");
    }, true);

    document.addEventListener("click", function () {
        alert("捕获 document");
    }, true);

    document.documentElement.addEventListener("click", function () {
        alert("捕获 html");
    }, true);

    document.body.addEventListener("click", function () {
        alert("捕获 body");
    }, true);

    fatherBox.addEventListener("click", function () {
        alert("捕获 father");
    }, true);

    childBox.addEventListener("click", function () {
        alert("捕获 child");
    }, true);

```

说明：

（1）第一个接收到事件的对象是 **window**（有人会说body，有人会说html，这都是错误的）。

（2）JS中涉及到DOM对象时，有两个对象最常用：window、doucument。它们俩是最先获取到事件的。

**补充一个知识点：**

在 js中：

- 如果想获取 `html`节点，方法是`document.documentElement`。

- 如果想获取 `body` 节点，方法是：`document.body`。

二者不要混淆了。

#### 事件冒泡

**事件冒泡**: 当一个元素上的事件被触发的时候（比如说鼠标点击了一个按钮），同样的事件将会在那个元素的所有**祖先元素**中被触发。这一过程被称为事件冒泡；这个事件从原始元素开始一直冒泡到DOM树的最上层。

通俗来讲，冒泡指的是：**子元素的事件被触发时，父元素的同样的事件也会被触发**。取消冒泡就是取消这种机制。

代码演示：

```javascript
    //事件冒泡
    box3.onclick = function () {
        alert("child");
    }

    box2.onclick = function () {
        alert("father");
    }

    box1.onclick = function () {
        alert("grandfather");
    }

    document.onclick = function () {
        alert("body");
    }

```

![](http://img.smyhvae.com/20180204_1028.gif)

（如果上面的图片打不开，请点击：<http://img.smyhvae.com/20180204_1028.gif>）

上图显示，当我点击子元素 box3 的时候，它的父元素box2、box1、body都依次被触发了。即使我改变代码的顺序，也不会影响效果的顺序。

当然，上面的代码中，我们用 addEventListener 这种 DOM2的写法也是可以的，但是第三个参数要写 false，或者不写。

**冒泡顺序**：

一般的浏览器: （除IE6.0之外的浏览器）

- div -> body -> html -> document -> window

IE6.0：

- div -> body -> html -> document

##### 不是所有的事件都能冒泡

以下事件不冒泡：blur、focus、load、unload、onmouseenter、onmouseleave。意思是，事件不会往父元素那里传递。

我们检查一个元素是否会冒泡，可以通过事件的以下参数：

```javascript
    event.bubbles
```

如果返回值为true，说明该事件会冒泡；反之则相反。

举例：

```javascript
    box1.onclick = function (event) {
        alert("冒泡 child");

        event = event || window.event;
        console.log(event.bubbles); //打印结果：true。说明 onclick 事件是可以冒泡的
    }
```

##### 阻止冒泡

大部分情况下，冒泡都是有益的。当然，如果你想阻止冒泡，也是可以的。可以按下面的方法阻止冒泡。

##### 阻止冒泡的方法

w3c的方法：（火狐、谷歌、IE11）

```javascript
    event.stopPropagation();
```

IE10以下则是：

```javascript
event.cancelBubble = true
```

兼容代码如下：

```javascript
   box3.onclick = function (event) {

        alert("child");

        //阻止冒泡
        event = event || window.event;

        if (event && event.stopPropagation) {
            event.stopPropagation();
        } else {
            event.cancelBubble = true;
        }
    }
```

上方代码中，我们对box3进行了阻止冒泡，产生的效果是：事件不会继续传递到 father、grandfather、body了。

##### 阻止冒泡的举例

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title></title>
        <style type="text/css">
            #box1 {
                width: 100px;
                height: 100px;
                background-color: red;
                /*
        * 开启box1的绝对定位
        */
                position: absolute;
            }
        </style>

        <script type="text/javascript">
            window.onload = function() {
                /*
                 * 使div可以跟随鼠标移动
                 */

                //获取box1
                var box1 = document.getElementById('box1');

                //给整个页面绑定：鼠标移动事件
                document.onmousemove = function(event) {
                    //兼容的方式获取event对象
                    event = event || window.event;

                    // 鼠标在页面的位置 = 滚动条滚动的距离 + 可视区域的坐标。
                    var pagex = event.pageX || scroll().left + event.clientX;
                    var pagey = event.pageY || scroll().top + event.clientY;

                    //   设置div的偏移量（相对于整个页面）
                    // 注意，如果想通过 style.left 来设置属性，一定要给 box1 开启绝对定位。
                    box1.style.left = pagex + 'px';
                    box1.style.top = pagey + 'px';
                };

                // 【重要注释】
                // 当 document.onmousemove 和 box2.onmousemove 同时触发时，通过  box2 阻止事件向 document 冒泡。
                // 也就是说，只要是在 box2 的区域，就只触发 document.onmousemove 事件
                var box2 = document.getElementById('box2');
                box2.onmousemove = function(event) {
                    //阻止冒泡
                    event = event || window.event;

                    if (event && event.stopPropagation) {
                        event.stopPropagation();
                    } else {
                        event.cancelBubble = true;
                    }
                };
            };

            // scroll 函数封装
            function scroll() {
                return {
                    //此函数的返回值是对象
                    left: window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop,
                    right: window.pageXOffset || document.body.scrollLeft || document.documentElement.scrollLeft,
                };
            }
        </script>
    </head>
    <body style="height: 1000px;width: 2000px;">
        <div id="box2" style="width: 300px; height: 300px; background-color: #bfa;"></div>
        <div id="box1"></div>
    </body>
</html>
```

关键地方可以看代码中的注释。

#### 事件委托

事件委托，通俗地来讲，就是把一个元素响应事件（click、keydown......）的函数委托到另一个元素。

比如说有一个列表 ul，列表之中有大量的列表项 `<a>`标签：

```html
<ul id="parent-list">
    <li><a href="javascript:;" class="my_link">超链接一</a></li>
    <li><a href="javascript:;" class="my_link">超链接二</a></li>
    <li><a href="javascript:;" class="my_link">超链接三</a></li>
</ul>
```

当我们的鼠标移到`<a>`标签上的时候，需要获取此`<a>`的相关信息并飘出悬浮窗以显示详细信息，或者当某个`<a>`被点击的时候需要触发相应的处理事件。我们通常的写法，是为每个`<a>`都绑定类似onMouseOver或者onClick之类的事件监听：

```javascript
    window.onload = function(){
        var parentNode = document.getElementById("parent-list");
        var aNodes = parentNode.getElementByTagName("a");
        for(var i=0, l = aNodes.length; i < l; i++){

            aNodes[i].onclick = function() {
                console.log('我是超链接 a 的单击相应函数');
            }
        }
    }
```

但是，上面的做法过于消耗内存和性能。**我们希望，只绑定一次事件，即可应用到多个元素上**，即使元素是后来添加的。

因此，比较好的方法就是把这个点击事件绑定到他的父层，也就是 `ul` 上，然后在执行事件函数的时候再去匹配判断目标元素。如下：

```html
    <!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title></title>
        <script type="text/javascript">
            window.onload = function() {

                // 获取父节点，并为它绑定click单击事件。 false 表示事件在冒泡阶段触发（默认）
                document.getElementById('parent-list').addEventListener('click', function(event) {
                    event = event || window.event;

                    // e.target 表示：触发事件的对象
                    //如果触发事件的对象是我们期望的元素，则执行否则不执行
                    if (event.target && event.target.className == 'link') {
                    // 或者写成 if (event.target && event.target.nodeName.toUpperCase() == 'A') {
                        console.log('我是ul的单击响应函数');
                    }
                }, false);
            };
        </script>
    </head>
    <body>
        <ul id="parent-list" style="background-color: #bfa;">
            <li>
                <p>我是p元素</p>
            </li>
            <li><a href="javascript:;" class="link">超链接一</a></li>
            <li><a href="javascript:;" class="link">超链接二</a></li>
            <li><a href="javascript:;" class="link">超链接三</a></li>
        </ul>
    </body>
```

上方代码，为父节点注册 click 事件，当子节点被点击的时候，click事件会从子节点开始**向父节点冒泡**。**父节点捕获到事件**之后，开始执行方法体里的内容：通过判断 event.target 拿到了被点击的子节点`<a>`。从而可以获取到相应的信息，并作处理。

换而言之，参数为false，说明事件是在冒泡阶段触发（子元素向父元素传递事件）。而父节点注册了事件函数，子节点没有注册事件函数，此时，会在父节点中执行函数体里的代码。

**总结**：事件委托是利用了冒泡机制，减少了事件绑定的次数，减少内存消耗，提高性能。

事件委托的参考链接：

- [荐 | JavaScript事件代理和委托（Delegation）](https://www.cnblogs.com/owenChen/archive/2013/02/18/2915521.html)

- [JavaScript 事件委托详解](https://zhuanlan.zhihu.com/p/26536815)

### 鼠标的拖拽事件

拖拽的流程：

（1）`onmousedown`：当鼠标在被拖拽元素上按下时，开始拖拽；

（2）`onmousemove`：当鼠标移动时被拖拽元素跟随鼠标移动；

（3）`onmouseup`：当鼠标松开时，被拖拽元素固定在当前位置。on

   (4)   oninput:           该事件类似于[onchange](https://www.w3cschool.cn/jsref/jsref-event-onchange.html) 事件。不同之处在于 oninput 事件在元素值发生变化是立即触发， onchange 在元素失去焦点时触发。另外一点不同是 onchange 事件也可以作用于 <keygen> 和 <select> 元素

### 鼠标的滚轮事件

`onmousewheel`：鼠标滚轮滚动的事件，会在滚轮滚动时触发。但是火狐不支持该属性。

`DOMMouseScroll`：在火狐中需要使用 DOMMouseScroll 来绑定滚动事件。注意该事件需要通过addEventListener()函数来绑定。

### 键盘事件

### 事件名

`onkeydown`：按键被按下。

`onkeyup`：按键被松开。


**注意**：

- 如果一直按着某一个按键不松手，那么，`onkeydown`事件会一直触发。此时，松开键盘，`onkeyup`事件会执行一次。

- 当`onkeydown`连续触发时，第一次和第二次之间会间隔稍微长一点，后续的间隔会非常快。这种设计是为了防止误操作的发生。

键盘事件一般都会绑定给一些可以获取到焦点的对象或者是document。代码举例：

```html
    <body>
        <script>
            document.onkeydown = function(event) {
                event = event || window.event;
                console.log('qianguyihao 键盘按下了');
            };

            document.onkeyup = function() {
                console.log('qianguyihao 键盘松开了');
            };
        </script>

        <input type="text" />
    </body>
```


### 判断哪个键盘被按下

可以通过`event`事件对象的`keyCode`来获取按键的编码。


此外，`event`事件对象里面还提供了以下几个属性：

- altKey

- ctrlKey

- shiftKey


上面这三个属性，可以用来判断`alt`、`ctrl`、和`shift`是否被按下。如果按下则返回true，否则返回false。代码举例：

```html
    <body>
        <script>
            document.onkeydown = function(event) {
                event = event || window.event;
                console.log('qianguyihao：键盘按下了');

                // 判断y和ctrl是否同时被按下
                if (event.ctrlKey && event.keyCode === 89) {
                    console.log('ctrl和y都被按下了');
                }
            };
        </script>
    </body>
```


**举例**：input 文本框中，禁止输入数字。代码实现：


```html
    <body>
        <input type="text" />

        <script>
            //获取input
            var input = document.getElementsByTagName('input')[0];

            input.onkeydown = function(event) {
                event = event || window.event;

                //console.log('qianguyihao:' + event.keyCode);
                //数字 48 - 57
                //使文本框中不能输入数字
                if (event.keyCode >= 48 && event.keyCode <= 57) {
                    //在文本框中输入内容，属于onkeydown的默认行为
                    return false; // 如果在onkeydown中取消了默认行为，则输入的内容，不会出现在文本框中
                }
            };
        </script>
    </body>

```


### 举例：通过键盘的方向键，移动盒子

代码实现：

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title></title>
        <style type="text/css">
            #box1 {
                width: 100px;
                height: 100px;
                background-color: red;
                position: absolute;
            }
        </style>
    </head>
    <body>
        <div id="box1"></div>

        <script type="text/javascript">
            // 使div可以根据不同的方向键向不同的方向移动
            /*
             * 按左键，div向左移
             * 按右键，div向右移
             * ...
             */

            //为document绑定一个按键按下的事件
            document.onkeydown = function(event) {
                event = event || window.event;

                //定义一个变量，来表示移动的速度
                var speed = 10;

                //当用户按了ctrl以后，速度加快
                if (event.ctrlKey) {
                    console.log('smyhvae ctrl');
                    speed = 20;
                }

                /*
                 * 37 左
                 * 38 上
                 * 39 右
                 * 40 下
                 */
                switch (event.keyCode) {
                    case 37:
                        //alert("向左"); left值减小
                        box1.style.left = box1.offsetLeft - speed + 'px'; // 在初始值的基础之上，减去 speed 大小
                        break;
                    case 39:
                        //alert("向右");
                        box1.style.left = box1.offsetLeft + speed + 'px';
                        break;
                    case 38:
                        //alert("向上");
                        box1.style.top = box1.offsetTop - speed + 'px';
                        break;
                    case 40:
                        //alert("向下");
                        box1.style.top = box1.offsetTop + speed + 'px';
                        break;
                }
            };
        </script>
    </body>
</html>


```

上方代码，待改进的地方：

（1）移动盒子时，如果要加速，需要先按`方向键`，再按`Ctrl键`。

（2）首次移动盒子时，动作较慢。后续如果学习了定时器相关的内容，可以再改进。

## BOM

 浏览器对象模型

 我们可以操作浏览器的各个部分（地址栏、历史记录），进一步说，让程序可以和浏览器之间进行通信

- 获取一些浏览器的相关信息（窗口的大小）

- 操作浏览器进行页面跳转

- 获取当前浏览器地址栏的信息

- 操作浏览器的滚动条

- 让浏览器出现一个提示框


它的核心对象是  window  window是浏览器内置的一个对象，表示浏览器窗口，里面包含着操作浏览器的方法，  window对象即是BOM对象的根，也是DOM的根

### 什么是BOM

BOM：Browser Object Model，浏览器对象模型。

**BOM的结构图：**

![](http://img.smyhvae.com/20180201_2052.png)

从上图也可以看出：

- **window对象是BOM的顶层(核心)对象**，所有对象都是通过它延伸出来的，也可以称为window的子对象。

- DOM越是BOM的一部分。

**window对象：**

- **window对象是JavaScript中的顶级对象**。

- 全局变量、自定义函数也是window对象的属性和方法。

- window对象下的属性和方法调用时，可以省略window。

下面讲一下 **BOM 的常见内置方法和内置对象**。

## 弹出系统对话框

比如说，`alert(1)`是`window.alert(1)`的简写，因为它是window的子方法。

系统对话框有三种：

```javascript
	alert();	//不同浏览器中的外观是不一样的
	confirm();  //兼容不好
	prompt();	//不推荐使用

```

## 打开窗口、关闭窗口

1、打开窗口：

```
	window.open(url,target,param)
```

**参数解释：**

- url：要打开的地址。

- target：新窗口的位置。可以是：`_blank` 、`_self`、 `_parent` 父框架。

- param：新窗口的一些设置。

- 返回值：新窗口的句柄。

**param**这个参数，可以填各种各样的参数（），比如：

- name：新窗口的名称，可以为空

- features：属性控制字符串，在此控制窗口的各种属性，属性之间以逗号隔开。

- fullscreen= { yes/no/1/0 } 是否全屏，默认no

- channelmode= { yes/no/1/0 } 是否显示频道栏，默认no

- toolbar= { yes/no/1/0 } 是否显示工具条，默认no

- location= { yes/no/1/0 } 是否显示地址栏，默认no。（有的浏览器不一定支持）

- directories = { yes/no/1/0 } 是否显示转向按钮，默认no

- status= { yes/no/1/0 } 是否显示窗口状态条，默认no

- menubar= { yes/no/1/0 } 是否显示菜单，默认no

- scrollbars= { yes/no/1/0 } 是否显示滚动条，默认yes

- resizable= { yes/no/1/0 } 是否窗口可调整大小，默认no

- width=number 窗口宽度（像素单位）

- height=number 窗口高度（像素单位）

- top=number 窗口离屏幕顶部距离（像素单位）

- left=number 窗口离屏幕左边距离（像素单位）

各个参数之间用逗号隔开就行，但我们最好是把它们统一放到json里。

2、关闭窗口：window.close()

（1）和（2）的代码举例：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
<a href="javascript:;">点击我打开一个新的页面</a>
<a href="javascript:;">点击我关闭本页面</a>
<script>
    //新窗口 = window.open(地址,是否开新窗口,新窗口的各种参数);
    var a1 = document.getElementsByTagName("a")[0];
    var a2 = document.getElementsByTagName("a")[1];
    a1.onclick = function () {
//举例1： window.open("http://www.jx.com","_blank");
        var json = {
            "name": "helloworld",
            "fullscreen": "no",
            "location": "no",
            "width": "100px",
            "height": "100px",
            "top": "100px",
            "left": "100px"
        };
        window.open("http://www.baidu.com", "_blank", json); //举例2
    }

    //关闭本页面
    a2.onclick = function () {
        window.close();
    }
</script>
</body>
</html>
```

3、新窗口相关：

- 新窗口.moveTo(5,5)

- 新窗口.moveBy()

- 新窗口.resizeTo()

- window.resizeBy()

代码举例：

```javascript
        var newWin = window.open("demo.html", "_blank", json);
        newWin.moveTo(500, 500);
```


## location对象

`window.location`可以简写成location。location相当于浏览器地址栏，可以将url解析成独立的片段。

### location对象的属性

- **href**：跳转

- hash   返回url中#后面的内容，包含#

- host    主机名，包括端口

- hostname   主机名

- pathname     url中的路径部分

- protocol    协议 一般是http、https

- search	     查询字符串

**location.href属性举例**：

**举例1：**点击盒子时，进行跳转。

```html
<body>
<div>smyhvae</div>
<script>

    var div = document.getElementsByTagName("div")[0];

    div.onclick = function () {
        location.href = "http://www.baidu.com";   //点击div时，跳转到指定链接
 //     window.open("http://www.baidu.com","_blank");  //方式二
    }

</script>
</body>
```

**举例2：5秒后自动跳转到百度**。

有时候，当我们访问一个不存在的网页时，会提示5秒后自动跳转到指定页面，此时就可以用到location。举例：

```html
<script>

    setTimeout(function () {
        location.href = "http://www.baidu.com";
    }, 5000);
</script>
```


### location对象的方法

- location.assign()：改变浏览器地址栏的地址，并记录到历史中

设置location.href  就会调用assign()。一般使用location.href 进行页面之间的跳转。

- location.replace()：替换浏览器地址栏的地址，不会记录到历史中

- location.reload()：重新加载


## navigator对象

window.navigator 的一些属性可以获取客户端的一些信息。

- userAgent：系统，浏览器)

- platform：浏览器支持的系统，win/mac/linux

举例：

```javascript
    console.log(navigator.userAgent);
    console.log(navigator.platform);
```

效果如下：

### 常见的 BOM 对象

BOM可以让我们通过JS来操作浏览器。BOM中为我们提供了一些对象，来完成对浏览器相关的操作。

常见的 BOM对象有：

- Window：代表整个浏览器的窗口，同时 window 也是网页中的全局对象。

- Navigator：代表当前浏览器的信息，通过该对象可以识别不同的浏览器。

- Location：代表当前浏览器的地址栏信息，通过 Location 可以获取地址栏信息，或者操作浏览器跳转页面。

- History：代表浏览器的历史记录，通过该对象可以操作浏览器的历史记录。由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页，而且该操作只在当次访问时有效。

- Screen：代表用户的屏幕信息，通过该对象可以获取用户的显示器的相关信息。

备注：这些 BOM 对象都是作为 window 对象的属性保存的，可以通过window对象来使用，也可以直接使用。比如说，我可以使用 `window.location.href`，也可以直接使用 `location.href`，二者是等价的。

备注2：不要忘了，之前学习过的`document`也是在`window`中保存的。

这篇文章，我们先来讲一下 几个常见的 BOM 对象。

## Navigator 和 `navigator.userAgent`

`Navigator`代表当前浏览器的信息，通过该对象可以识别不同的浏览器。

由于历史原因，Navigator对象中的大部分属性都已经不能帮助我们识别浏览器了。

**一般我们只会使用`navigator.userAgent`来获取浏览器的信息**。


userAgent 的值是一个字符串，简称 **UA**，这个字符串中包含了用来描述浏览器信息的内容，不同的浏览器会有不同的userAgent。

**代码举例**：（获取当前浏览器的UA）

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
    <body>
        <script>
            var ua = navigator.userAgent; // 获取当前浏览器的 userAgent

            console.log('qianguyihao 当前浏览器的UA是：' + ua);

            if (/firefox/i.test(ua)) {
                alert('是火狐浏览器');
            } else if (/chrome/i.test(ua)) {
                alert('是Chrome浏览器');
            } else if (/msie/i.test(ua)) {
                alert('是IE浏览器');
            } else if ('ActiveXObject' in window) {
                alert('是 IE11 浏览器');
            }
        </script>
    </body>
</html>
```

### 在电脑上模拟移动端浏览器

不同浏览器（包括微信内置的浏览器）的 userAgent 信息，是不一样的，我们可以根据 `navigator.userAgent`属性来获取。

比如说，我们在电脑浏览器上，按F12，然后在控制台输入`navigator.userAgent`，如下：

![](http://img.smyhvae.com/20180425_1656.png)

上图显示，MacOS上的Chrome浏览器的 userAgent 是：

```
"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.117 Safari/537.36"
```

我们还可以在电脑浏览器的控制台里可以添加很多设备，通过这种方式，可以模拟移动端浏览器的场景，非常有用，请务必掌握。操作如下：

（1）需要点击 edit，手动添加：

![](http://img.smyhvae.com/20191127_1903.png)

（2）添加时，根据 User agent 来识别不同的浏览器：

![](http://img.smyhvae.com/20191127_1918.png)


### 不同浏览器的 userAgent

iOS 版微信浏览器：

```
Mozilla/5.0 (iPhone; CPU iPhone OS 9_3 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13E233 MicroMessenger/6.3.15 NetType/WIFI Language/zh_CN
```

Android 版微信浏览器：

```
Mozilla/5.0 (Linux; Android 5.0.1; GT-I9502 Build/LRX22C; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/43.0.2357.121 Mobile Safari/537.36 MicroMessenger/6.1.0.78_r1129455.543 NetType/WIFI
```

iOS 版本QQ浏览器：

```
Mozilla/5.0 (iPhone; CPU iPhone OS 11_2_2 like Mac OS X) AppleWebKit/604.4.7 (KHTML, like Gecko) Mobile/15C202 QQ/7.3.5.473 V1_IPH_SQ_7.3.5_1_APP_A Pixel/1125 Core/UIWebView Device/Apple(iPhone X) NetType/WIFI QBWebViewType/1
```

Android 版 QQ浏览器：

```
Mozilla/5.0 (Linux; Android 4.4.2; PE-TL20 Build/HuaweiPE-TL20; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/57.0.2987.132 MQQBrowser/6.2 TBS/043807 Mobile Safari/537.36 V1_AND_SQ_7.3.2_762_YYB_D QQ/7.3.2.3350 NetType/WIFI WebP/0.3.0 Pixel/1080
```

**参考链接**：

## 定时器的常见方法

- setInterval()：循环调用。将一段代码，**每隔一段时间**执行一次。（循环执行）

- setTimeout()：延时调用。将一段代码，等待一段时间之后**再执行**。（只执行一次）

备注：在实际开发中，二者是可以根据需要，互相替代的。

## setInterval() 的使用

`setInterval()`：循环调用。将一段代码，**每隔一段时间**执行一次。（循环执行）

**参数**：

- 参数1：回调函数，该函数会每隔一段时间被调用一次。

- 参数2：每次调用的间隔时间，单位是毫秒。

**返回值**：返回一个Number类型的数据。这个数字用来作为定时器的**唯一标识**，方便用来清除定时器。

### 定义定时器

**方式一：**匿名函数

每间隔一秒，将 数字 加1：

```javascript
    let num = 1;
   setInterval(function () {
       num ++;
       console.log(num);
   }, 1000);
```

**方式二：**

每间隔一秒，将 数字 加1：

```javascript
    setInterval(fn,1000);

       num ++;
       console.log(num);
    }

```

### 清除定时器

定时器的返回值是作为这个定时器的**唯一标识**，可以用来清除定时器。具体方法是：假设定时器setInterval()的返回值是`参数1`，那么`clearInterval(参数1)`就可以清除定时器。

setTimeout()的道理是一样的。

代码举例：

```html
<script>
    let num = 1;

    const timer = setInterval(function () {
        console.log(num);  //每间隔一秒，打印一次num的值
        num ++;
        if(num === 5) {  //打印四次之后，就清除定时器
            clearInterval(timer);
        }

    }, 1000);
</script>

```

## setTimeout() 的使用

`setTimeout()`：延时调用。将一段代码，等待一段时间之后**再执行**。（只执行一次）

**参数**：

- 参数1：回调函数，该函数会每隔一段时间被调用一次。

- 参数2：每次调用的间隔时间，单位是毫秒。

**返回值**：返回一个Number类型的数据。这个数字用来作为定时器的**唯一标识**，方便用来清除定时器。

### 定义和清除定时器

代码举例：

```javascript
    const timer = setTimeout(function() {
        console.log(1); // 3秒之后，再执行这段代码。
    }, 3000);

    clearTimeout(timer);

```

代码举例：（箭头函数写法）

```javascript
    setTimeout(() => {
        console.log(1); // 3秒之后，再执行这段代码。
    }, 3000);
```


### setTimeout() 举例：5秒后关闭网页两侧的广告栏

假设网页两侧的广告栏为两个img标签，它们的样式为：


```html
<style>
    ...
    ...

</style>

```

5秒后关闭广告栏的js代码为：

```html
    <script>
        window.onload = function () {
            //获取相关元素
            var imgArr = document.getElementsByTagName("img");
            //设置定时器：5秒后关闭两侧的广告栏
            setTimeout(fn,5000);
            function fn(){
                imgArr[0].style.display = "none";
                imgArr[1].style.display = "none";
            }
        }
    </script>
```



## 节点

**节点**（Node）：构成 HTML 网页的最基本单元。网页中的每一个部分都可以称为是一个节点，比如：html标签、属性、文本、注释、整个文档等都是一个节点。

虽然都是节点，但是实际上他们的具体类型是不同的。常见节点分为四类：

- 文档节点（文档）：整个 HTML 文档。整个 HTML 文档就是一个文档节点。

- 元素节点（标签）：HTML标签。

- 属性节点（属性）：元素的属性。

- 文本节点（文本）：HTML标签中的文本内容（包括标签之间的空格、换行）。

节点的类型不同，属性和方法也都不尽相同。所有的节点都是Object。

## DOM

文档对象模型

文档（网页）的每一部分（标签）映射到javascript 中叫作对象（也叫dom对象）

在javaScript种操作网页上的标签,为了能让js操作html元素而指定的一个规范

DOM  就是由节点组成的，一切皆节点

#### 如果样式代码写在css里了，就可以使用className

![](../javascript-high-level/BasicSkill/编程范式/upload/image-20200423112424446.png)

**DOM**：Document Object Model，文档对象模型。DOM 为文档提供了结构化表示，并定义了如何通过脚本来访问文档结构。目的其实就是为了能让js操作html元素而制定的一个规范。

DOM就是由节点组成的。

**解析过程**：
HTML加载完毕，渲染引擎会在内存中把HTML文档，生成一个DOM树，getElementById是获取内中DOM上的元素节点。然后操作的时候修改的是该元素的**属性**。

**DOM树**：（一切都是节点）

DOM的数据结构如下：

![](http://img.smyhvae.com/20180126_2105.png)

上图可知，**在HTML当中，一切都是节点**（非常重要）。节点的分类，在上一段中，已经讲了。

整个html文档就是一个文档节点。所有的节点都是Object。

### DOM可以做什么

- 找对象（元素节点）

- 设置元素的属性值

- 设置元素的样式

- 动态创建和删除元素

- 事件的触发响应：事件源、事件、事件的驱动程序



## 元素节点的获取

DOM节点的获取方式其实就是**获取事件源的方式**。关于事件，上一篇文章中已经讲到了。

想要操作元素节点，必须首先要找到该节点。有三种方式可以获取DOM节点：

```javascript
var div1 = document.getElementById("box1"); //方式一：通过 id 获取 一个 元素节点（为什么是一个呢？因为 id 是唯一的）

var arr1 = document.getElementsByTagName("div"); //方式二：通过 标签名 获取 元素节点数组，所以有s

var arr2 = document.getElementsByClassName("hehe"); //方式三：通过 类名 获取 元素节点数组，所以有s
```

既然方式二、方式三获取的是标签数组，那么习惯性是**先遍历之后再使用**。

特殊情况：数组中的值只有1个。即便如此，这一个值也是包在数组里的。这个值的获取方式如下：

```javascript
document.getElementsByTagName("div1")[0];    //取数组中的第一个元素

document.getElementsByClassName("hehe")[0];  //取数组中的第一个元素
```

## DOM访问关系的获取

DOM的节点并不是孤立的，因此可以通过DOM节点之间的相对关系对它们进行访问。如下：

![](http://img.smyhvae.com/20180126_2140.png)

节点的访问关系，是以**属性**的方式存在的。

JS中的**父子兄**访问关系：

![](http://img.smyhvae.com/20180126_2145.png)

这里我们要重点知道**parentNode**和**children**这两个属性的用法。下面分别介绍。

### 获取父节点

调用者就是节点。一个节点只有一个父节点，调用方式就是

```javascript
	节点.parentNode
```

### 获取兄弟节点

**1、下一个节点 | 下一个元素节点**：

> Sibling的中文是**兄弟**。

（1）nextSibling：

- 火狐、谷歌、IE9+版本：都指的是下一个节点（包括标签、空文档和换行节点）。

- IE678版本：指下一个元素节点（标签）。

（2）nextElementSibling：

- 火狐、谷歌、IE9+版本：都指的是下一个元素节点（标签）。

**总结**：为了获取下一个**元素节点**，我们可以这样做：在IE678中用nextSibling，在火狐谷歌IE9+以后用nextElementSibling，于是，综合这两个属性，可以这样写：

```javascript
	下一个兄弟节点 = 节点.nextElementSibling || 节点.nextSibling
```

**2、前一个节点 | 前一个元素节点**：

> previous的中文是：前一个。

（1）previousSibling：

- 火狐、谷歌、IE9+版本：都指的是前一个节点（包括标签、空文档和换行节点）。

- IE678版本：指前一个元素节点（标签）。

（2）previousElementSibling：

- 火狐、谷歌、IE9+版本：都指的是前一个元素节点（标签）。

**总结**：为了获取前一个**元素节点**，我们可以这样做：在IE678中用previousSibling，在火狐谷歌IE9+以后用previousElementSibling，于是，综合这两个属性，可以这样写：

```javascript
	前一个兄弟节点 = 节点.previousElementSibling || 节点.previousSibling
```

**3、补充**：获得任意一个兄弟节点：

```javascript
	节点自己.parentNode.children[index];  //随意得到兄弟节点
```

### 获取单个的子节点

**1、第一个子节点 | 第一个子元素节点**：

（1）firstChild：

- 火狐、谷歌、IE9+版本：都指的是第一个子节点（包括标签、空文档和换行节点）。

- IE678版本：指第一个子元素节点（标签）。

（2）firstElementChild：

- 火狐、谷歌、IE9+版本：都指的是第一个子元素节点（标签）。

**总结**：为了获取第一个**子元素节点**，我们可以这样做：在IE678中用firstChild，在火狐谷歌IE9+以后用firstElementChild，于是，综合这两个属性，可以这样写：

```javascript
	第一个子元素节点 = 节点.firstElementChild || 节点.firstChild
```

**2、最后一个子节点 | 最后一个子元素节点**：

（1）lastChild：

- 火狐、谷歌、IE9+版本：都指的是最后一个子节点（包括标签、空文档和换行节点）。

- IE678版本：指最后一个子元素节点（标签）。

（2）lastElementChild：

- 火狐、谷歌、IE9+版本：都指的是最后一个子元素节点（标签）。

**总结**：为了获取最后一个**子元素节点**，我们可以这样做：在IE678中用lastChild，在火狐谷歌IE9+以后用lastElementChild，于是，综合这两个属性，可以这样写：

```javascript
	最后一个子元素节点 = 节点.lastElementChild || 节点.lastChild
```

### 获取所有的子节点

（1）**childNodes**：标准属性。返回的是指定元素的**子节点**的集合（包括元素节点、所有属性、文本节点）。是W3C的亲儿子。

- 火狐 谷歌等高本版会把换行也看做是子节点。

用法：

```javascript
	子节点数组 = 父节点.childNodes;   //获取所有节点。
```

（2）**children**：非标准属性。返回的是指定元素的**子元素节点**的集合。【重要】

- 它只返回HTML节点，甚至不返回文本节点。
- 在IE6/7/8中包含注释节点（在IE678中，注释节点不要写在里面）。

虽然不是标准的DOM属性，但它和innerHTML方法一样，得到了几乎所有浏览器的支持。

用法：（**用的最多**）

```javascript
	子节点数组 = 父节点.children;   //获取所有节点。用的最多。
```

## DOM节点的操作（重要）

上一段的内容：节点的**访问关系**都是**属性**。

本段的内容：节点的**操作**都是**函数**（方法）。

### 创建节点

格式如下：

```javascript
	新的标签(元素节点) = document.createElement("标签名");
```

比如，如果我们想创建一个li标签，或者是创建一个不存在的adbc标签，可以这样做：

```html
<script type="text/javascript">
    var a1 = document.createElement("li");   //创建一个li标签
    var a2 = document.createElement("adbc");   //创建一个不存在的标签

    console.log(a1);
    console.log(a2);

    console.log(typeof a1);
    console.log(typeof a2);
</script>
```

打印结果：

![](http://img.smyhvae.com/20180127_1135.png)

### 插入节点

插入节点有两种方式，它们的含义是不同的。

方式1：

```javascript
	父节点.appendChild(新的子节点);
```

解释：父节点的最后插入一个新的子节点。

方式2：

```javascript
	父节点.insertBefore(新的子节点,作为参考的子节点)
```

解释：

- 在参考节点前插入一个新的节点。
- 如果参考节点为null，那么他将在父节点里面的最后插入一个子节点。

![](http://img.smyhvae.com/20180127_1257.png)

我们可以看到，li标签确实被插入到了box1标签的里面，和box2并列了。

方式2的举例：

![](http://img.smyhvae.com/20180127_1302.png)

我们可以看到，b1标签被插入到了box1标签的里面，和a1标签并列，在a1标签的前面。


**特别强调：**

关于方式1的appendChild方法，这里要强调一下。比如，现在有下面这样一个div结构：

```html
<div class="box11">
    <div class="box12">生命壹号</div>
</div>

<div class="box21">
    <div class="box22">永不止步</div>

</div>
```


上方结构中，子盒子box12是在父亲box11里的，子盒子box22是在父亲box21里面的。现在，如果我调用方法`box11.appendChild(box22)`，**最后产生的结果是：box22会跑到box11中**（也就是说，box22不在box21里面了）。这是一个很神奇的事情：


![](http://img.smyhvae.com/20180129_2125.png)

### 删除节点

格式如下：

```javascript
	父节点.removeChild(子节点);
```

解释：**用父节点删除子节点**。必须要指定是删除哪个子节点。

如果我想删除自己这个节点，可以这么做：

```javascript
	node1.parentNode.removeChild(node1);
```

### 复制节点（克隆节点）

格式如下：

```javascript
	要复制的节点.cloneNode();       //括号里不带参数和带参数false，效果是一样的。

	要复制的节点.cloneNode(true);
```

括号里带不带参数，效果是不同的。解释如下：

- 不带参数/带参数false：只复制节点本身，不复制子节点。

- 带参数true：既复制节点本身，也复制其所有的子节点。

## 设置节点的属性

我们可以获取节点的属性值、设置节点的属性值、删除节点的属性。

我们就统一拿下面这个标签来举例：

```html
	<img src="images/1.jpg" class="image-box" title="美女图片" alt="地铁一瞥" id="a1">
```

下面分别介绍。

### 1、获取节点的属性值

**方式1**：

```javascript
	元素节点.属性名;
	元素节点[属性名];
```

举例：（获取节点的属性值）

```html
<body>
<img src="images/1.jpg" class="image-box" title="美女图片" alt="地铁一瞥" id="a1">

<script type="text/javascript">
    var myNode = document.getElementsByTagName("img")[0];

    console.log(myNode.src);
    console.log(myNode.className);    //注意，是className，不是class
    console.log(myNode.title);

    console.log("------------");

    console.log(myNode["src"]);
    console.log(myNode["className"]); //注意，是className，不是class
    console.log(myNode["title"]);
</script>
</body>
```

上方代码中的img标签，有各种属性，我们可以逐一获取，打印结果如下：

![](http://img.smyhvae.com/20180127_1340.png)

**方式2**：

```javascript
	元素节点.getAttribute("属性名称");
```

举例：

```javascript
    console.log(myNode.getAttribute("src"));
    console.log(myNode.getAttribute("class"));   //注意是class，不是className
    console.log(myNode.getAttribute("title"));
```

打印结果：

![](http://img.smyhvae.com/20180127_1345.png)

方式1和方式2的区别在于：前者是直接操作标签，后者是把标签作为DOM节点。推荐方式2。

### 2、设置节点的属性值

方式1举例：（设置节点的属性值）

```javascript
    myNode.src = "images/2.jpg"   //修改src的属性值
    myNode.className = "image2-box";  //修改class的name
```

方式2：

```javascript
	元素节点.setAttribute("属性名", "新的属性值");
```

方式2举例：（设置节点的属性值）

```javascript
    myNode.setAttribute("src","images/3.jpg");
    myNode.setAttribute("class","image3-box");
    myNode.setAttribute("id","你好");
```


### 3、删除节点的属性

格式：

```javascript
	元素节点.removeAttribute(属性名);
```

举例：（删除节点的属性）

```javascript
    myNode.removeAttribute("class");
    myNode.removeAttribute("id");
```


### 总结

获取节点的属性值和设置节点的属性值，都有两种方式。

**如果是节点的“原始属性”**（比如 普通标签的`class/className`属性、普通标签的`style`属性、普通标签的 title属性、img 标签的`src`属性、超链接的`href`属性等），**方式1和方式2是等价的**，可以混用。怎么理解混用呢？比如说：用 `div.title = '我是标题'`设置属性，用 `div.getAttribute('title')`获取属性，就是混用。

但如果是节点的“非原始属性”，比如：

```javascript
div.aaa = 'qianguyihao';

div.setAttribute('bbb', 'qianguyihao');

```

上面的这个“非原始属性”，在使用这两种方式时，是有区别的。区别如下：

- 方式1 的`元素节点.属性`和`元素节点[属性]`：绑定的属性值不会出现在标签上。

- 方式2 的`get/set/removeAttribut`：绑定的属性值会出现在标签上。

- **这两种方式不能交换使用**，get值和set值必须使用同一种方法。

举例：

```html
<body>
<div id="box" title="主体" class="asdfasdfadsfd">我爱你中国</div>
<script>

    var div = document.getElementById("box");

    //采用方式一进行set
    div.aaaa = "1111";
    console.log(div.aaaa);    //打印结果：1111。可以打印出来，但是不会出现在标签上

    //采用方式二进行set
    div.setAttribute("bbbb","2222");    //bbbb作为新增的属性，会出现在标签上

    console.log(div.getAttribute("aaaa"));   //打印结果：null。因为方式一的set，无法采用方式二进行get。
    console.log(div.bbbb);                   //打印结果：undefined。因为方式二的set，无法采用方式一进行get。

</script>
</body>
```


## DOM对象的属性-补充

### innerHTML和innerText的区别

- value：标签的value属性。

- **innerHTML**：双闭合标签里面的内容（包含标签）。

- **innerText**：双闭合标签里面的内容（不包含标签）。（老版本的火狐用textContent）


**获取内容举例：**

如果我们想获取innerHTML和innerText里的内容，看看会如何：（innerHTML会获取到标签本身，而innerText则不会）

![](http://img.smyhvae.com/20180127_1652.png)

**修改内容举例：**（innerHTML会修改标签本身，而innerText则不会）

![](http://img.smyhvae.com/20180127_1657.png)

### nodeType属性

这里讲一下nodeType属性。

- **nodeType == 1  表示的是元素节点**（标签） 。记住：在这里，元素就是标签。

- nodeType == 2  表示是属性节点。

- nodeType == 3  是文本节点。

### nodeType、nodeName、nodeValue

我们那下面这个标签来举例：

```html
<div id="box" value="111">
    生命壹号
</div>
```

上面这个标签就包含了三种节点：

- 元素节点（标签）

- 属性节点

- 文本节点

获取这三个节点的方式如下：

```javascript
    var element = document.getElementById("box1");  //获取元素节点（标签）
    var attribute = element.getAttributeNode("id"); //获取box1的属性节点
    var txt = element.firstChild;                   //获取box1的文本节点

    var value = element.getAttribute("id");         //获取id的属性值

    console.log(element);
    console.log("--------------");
    console.log(attribute);
    console.log("--------------");
    console.log(txt);
    console.log("--------------");
    console.log(value);
```

打印结果如下：

![](http://img.smyhvae.com/20180128_1935.png)

既然这三个都是节点，如果我想获取它们的nodeType、nodeName、nodeValue，代码如下：

```javascript
    var element = document.getElementById("box1");  //获取元素节点（标签）
    var attribute = element.getAttributeNode("id"); //获取box1的属性节点
    var txt = element.firstChild;                   //获取box1的文本节点

    //获取nodeType
    console.log(element.nodeType);       //1
    console.log(attribute.nodeType);     //2
    console.log(txt.nodeType);           //3

    console.log("--------------");

    //获取nodeName
    console.log(element.nodeName);       //DIV
    console.log(attribute.nodeName);     //id
    console.log(txt.nodeName);           //#text

    console.log("--------------");

    //获取nodeValue
    console.log(element.nodeValue);     //null
    console.log(attribute.nodeValue);   //box1
    console.log(txt.nodeValue);         //生命壹号
```

打印结果如下：

![](http://img.smyhvae.com/20180128_1939.png)

## 文档的加载

浏览器在加载一个页面时，是按照自上向下的顺序加载的，读取到一行就运行一行。如果将script标签写到页面的上边，在代码执行时，页面还没有加载，页面没有加载DOM对象也没有加载，会导致无法获取到DOM对象。

**onload 事件**：

onload 事件会在整个页面加载完成之后才触发。为 window 绑定一个onload事件，该事件对应的响应函数将会在页面加载完成之后执行，这样可以确保我们的代码执行时所有的DOM对象已经加载完毕了。

代码举例：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title></title>
    <script type="text/javascript">
      // 【方式一：先加载，后执行】这段 js 代码是写在 <head> 标签里的，所以建议放在 window.onload 里面。
      window.onload = function() {
        // 获取id为btn的按钮
        var btn = document.getElementById("btn");
        // 为按钮绑定点击事件
        btn.onclick = function() {
          alert("hello");
        };
      };
    </script>
  </head>
  <body>
    <button id="btn">点我一下</button>

    <script type="text/javascript">
      // 【方式二：后加载，后执行】这段 js 代码是写在 <body> 标签里的，代码的位置是处在页面的下方。这么做，也可以确保：在页面加载完毕后，再执行 js 代码。

      // 获取id为btn的按钮
      var btn = document.getElementById("btn");
      // 为按钮绑定点击事件
      btn.onclick = function() {
        alert("hello");
      };
    </script>
  </body>
</html>


```

上方代码中，方式一和方式二均可以确保：在页面加载完毕后，再执行 js 代码。

## style属性的获取和修改

在DOM当中，如果想设置样式，有两种形式：

- className（针对内嵌样式）

- style（针对行内样式）

这篇文章，我们就来讲一下style。

需要注意的是：style是一个对象，只能获取**行内样式**，不能获取内嵌的样式和外链的样式。例如：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div {
            border: 6px solid red;
        }
    </style>
</head>
<body>

    <div class="box1" style="width: 200px;height: 100px;background-color: pink;"></div>

    <script>
        var box1 = document.getElementsByTagName("div")[0];

        console.log(box1.style.backgroundColor);
        console.log(box1.style.border);  //没有打印结果，因为这个属性不是行内样式
        console.log(typeof box1.style);  //因为是对象，所以打印结果是Object
        console.log(box1.style);         //打印结果是对象
    </script>
</body>
</html>
```

打印结果：

![](http://img.smyhvae.com/20180129_1407.png)

上图显示，因为border属性不是行内样式，所以无法通过style对象获取。

### 通过 js 读取元素的样式

语法：（方式一）

```javascript
    元素.style.样式名
```

备注：我们通过style属性读取的样式都是**行内样式**。

语法：（方式二）

```javascript
    元素.style["属性"];  //格式

    box.style["width"];  //举例
```

方式二最大的优点是：可以给属性传递参数。

### 通过 js 设置元素的样式

语法：

```javascript
    元素.style.样式名 = 样式值;
```

举例：

```
    box1.style.width = "300px";
    box1.style.backgroundColor = "red"; // 驼峰命名法

```

备注：我们通过style属性设置的样式都是**行内样式**，而行内样式有较高的优先级。但是如果在样式中的其他地方写了`!important`，则此时`!important`会有更高的优先级。

### style属性的注意事项

style属性需要注意以下几点：

（1）样式少的时候使用。

（2）style是对象。我们在上方已经打印出来，typeof的结果是Object。

（3）值是字符串，没有设置值是“”。

（4）命名规则，驼峰命名。

（5）只能获取行内样式，和内嵌和外链无关。

（6）box.style.cssText = “字符串形式的样式”。


`cssText`这个属性，其实就是把行内样式里面的值当做字符串来对待。在上方代码的基础之上，举例：

```html
    <script>
        var box1 = document.getElementsByTagName("div")[0];

        //通过cssText一次性设置行内样式
        box1.style.cssText = "width: 300px;height: 300px;background-color: green;";

        console.log(box1.style.cssText);   //这一行更加可以理解,style是对象

    </script>
```

打印结果：

![](http://img.smyhvae.com/20180129_1410.png)

### style的常用属性

style的常用属性包括：

- backgroundColor

- backgroundImage

- color

- width

- height

- border

- opacity 设置透明度 (IE8以前是filter: alpha(opacity=xx))

注意DOM对象style的属性和标签中style内的值不一样，因为在JS中，`-`不能作为标识符。比如：

- DOM中：backgroundColor

- CSS中：background-color

## style属性的举例

我们针对上面列举的几个style的样式，来举几个例子：

- 举例1、改变div的大小和透明度

- 举例2、当前输入的文本框高亮显示

- 举例3、高级隔行变色、高亮显示

下面来逐一实现。

### 举例1：改变div的大小和透明度

代码举例：

```html
<body>
<div style="width: 100px;height: 100px;background-color: pink;"></div>
<script>

    var div = document.getElementsByTagName("div")[0];
    div.onmouseover = function () {
        div.style.width = "200px";
        div.style.height = "200px";
        div.style.backgroundColor = "black";
        div.style.opacity = "0.2";   //设置背景色的透明度。单位是0.1
        div.style.filter = "alpha(opacity=20)";   //上一行代码的兼容性写法。注意单位是百进制
    }

</script>

</body>
```

### 举例2：当前输入的文本框高亮显示

代码实现：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        input {
            display: block;
        }
    </style>

</head>

<body>
<ul>
    <input type="text"/>
    <input type="text"/>
    <input type="text"/>
    <input type="text"/>
    <input type="text"/>
</ul>
<script>
    //需求：让所有的input标签获取焦点后高亮显示

    //1.获取事件源
    var inpArr = document.getElementsByTagName("input");
    //2.绑定事件
    //3.书写事件驱动程序
    for (var i = 0; i < inpArr.length; i++) {
        //获取焦点后，所有的input标签被绑定onfocus事件
        inpArr[i].onfocus = function () {
            this.style.border = "2px solid red";
            this.style.backgroundColor = "#ccc";
        }
        //绑定onblur事件，取消样式
        inpArr[i].onblur = function () {
            this.style.border = "";
            this.style.backgroundColor = "";
        }
    }
</script>
</body>
</html>
```

### 举例3：高级隔行变色、高亮显示

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            padding: 0;
            margin: 0;
            text-align: center;
        }

        .wrap {
            width: 500px;
            margin: 100px auto 0;
        }

        table {
            border-collapse: collapse;
            border-spacing: 0;
            border: 1px solid #c0c0c0;
            width: 500px;
        }

        th,
        td {
            border: 1px solid #d0d0d0;
            color: #404060;
            padding: 10px;
        }

        th {
            background-color: #09c;
            font: bold 16px "微软雅黑";
            color: #fff;
        }

        td {
            font: 14px "微软雅黑";
        }

        tbody tr {
            background-color: #f0f0f0;
            cursor: pointer;
        }

        .current {
            background-color: red !important;
        }
    </style>
</head>
<body>
<div class="wrap">
    <table>
        <thead>
        <tr>
            <th>序号</th>
            <th>姓名</th>
            <th>课程</th>
            <th>成绩</th>
        </tr>
        </thead>
        <tbody id="target">
        <tr>
            <td>
                1
            </td>
            <td>生命壹号</td>
            <td>语文</td>
            <td>100</td>

        </tr>
        <tr>
            <td>
                2
            </td>
            <td>生命贰号</td>
            <td>日语</td>
            <td>99</td>
        </tr>
        <tr>
            <td>
                3
            </td>
            <td>生命叁号</td>
            <td>营销学</td>
            <td>98</td>
        </tr>
        <tr>
            <td>
                4
            </td>
            <td>生命伍号</td>
            <td>数学</td>
            <td>90</td>
        </tr>
        <tr>
            <td>
                5
            </td>
            <td>许嵩</td>
            <td>英语</td>
            <td>96</td>
        </tr>
        <tr>
            <td>
                6
            </td>
            <td>vae</td>
            <td>体育</td>
            <td>90</td>
        </tr>
        </tbody>
    </table>
</div>

<script>
    //需求：让tr各行变色，鼠标放入tr中，高亮显示。

    //1.隔行变色。
    var tbody = document.getElementById("target");
    var trArr = tbody.children;
    //循环判断并各行赋值属性（背景色）
    for (var i = 0; i < trArr.length; i++) {
        if (i % 2 !== 0) {
            trArr[i].style.backgroundColor = "#a3a3a3";
        } else {
            trArr[i].style.backgroundColor = "#ccc";
        }

        //鼠标进入高亮显示
        //难点：鼠标移开的时候要回复原始颜色。
        //计数器（进入tr之后，立刻记录颜色，然后移开的时候使用记录好的颜色）
        var myColor = "";
        trArr[i].onmouseover = function () {
            //赋值颜色之前，先记录颜色
            myColor = this.style.backgroundColor;
            this.style.backgroundColor = "#fff";
        }
        trArr[i].onmouseout = function () {
            this.style.backgroundColor = myColor;
        }
    }


</script>


</body>
</html>
```

实现的效果如下：

![](http://img.smyhvae.com/20180129_1520.gif)

代码解释：

上方代码中，我们**用到了计数器myColor来记录每一行最原始的颜色**（赋值白色之前）。如果不用计数器，可能很多人以为代码是写的：（错误的代码）

```html
<script>
    //需求：让tr各行变色，鼠标放入tr中，高亮显示。

    //1.隔行变色。
    var tbody = document.getElementById("target");
    var trArr = tbody.children;
    //循环判断并各行赋值属性（背景色）
    for (var i = 0; i < trArr.length; i++) {
        if (i % 2 !== 0) {
            trArr[i].style.backgroundColor = "#a3a3a3";
        } else {
            trArr[i].style.backgroundColor = "#ccc";
        }

        //鼠标进入高亮显示
        //难点：鼠标移开的时候要回复原始颜色。
        //计数器（进入tr之后，立刻记录颜色，然后移开的时候使用记录好的颜色）
        trArr[i].onmouseover = function () {
            this.style.backgroundColor = "#fff";
        }
        trArr[i].onmouseout = function () {
            this.style.backgroundColor = "#a3a3a3";
        }
    }
</script>

```

这种错误的代码，实现的效果却是：（未达到效果）

![](http://img.smyhvae.com/20180129_1525.gif)

## 通过 js 获取元素当前显示的样式

我们在上面的内容中，通过`元素.style.className`的方式只能获取**行内样式**。但是，有些元素，也写了**内嵌样式或外链样式**。

既然样式有这么种，那么，如何获取元素当前显示的样式（包括行内样式、内嵌样式、外链样式）呢？我们接下来看一看。

### 获取元素当前正在显示的样式

（1）w3c的做法：

```javascript
    window.getComputedStyle("要获取样式的元素", "伪元素");
```

两个参数都是必须要有的。参数二中，如果没有伪元素就用 null 代替（一般都传null）。

（2）IE和opera的做法：

```javascript
    obj.currentStyle;
```

注意：

- 如果当前元素没有设置该样式，则获取它的默认值。

- 该方法会返回一个**对象**，对象中封装了当前元素对应的样式，可以通过`对象.样式名`来读取具体的某一个样式。

- 通过currentStyle和getComputedStyle()读取到的样式都是只读的，不能修改，如果要修改必须通过style属性。

综合上面两种写法，就有了一种兼容性的写法，同时将其封装。代码举例如下：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            background-color: pink;
            /*border: 1px solid #000;*/
            padding: 10px;
        }
    </style>
</head>
<body>

<div style="width: 100px;height: 100px;"></div>

<script>

    var div1 = document.getElementsByTagName("div")[0];

    console.log(getStyle(div1, "width"));
    console.log(getStyle(div1, "padding"));
    console.log(getStyle(div1, "background-color"));

    /*
     * 兼容方法，获取元素当前正在显示的样式。
     * 参数：
     *      obj     要获取样式的元素
     *.     name    要获取的样式名
    */
    function getStyle(ele, attr) {
        if (window.getComputedStyle) {
            return window.getComputedStyle(ele, null)[attr];
        }
        return ele.currentStyle[attr];
    }

</script>
</body>
</html>
```

打印结果：

![](http://img.smyhvae.com/20180204_1425.png)

JS动画的主要内容如下：

1、三大家族和一个事件对象：

- 三大家族：offset/scroll/client。也叫三大系列。

- 事件对象/event（事件被触动时，鼠标和键盘的状态）（通过属性控制）。

2、动画(闪现/匀速/缓动)

3、冒泡/兼容/封装

## offset 家族的组成

我们知道，JS动画的三大家族包括：offset/scroll/client。今天来讲一下offset，以及与其相关的匀速动画。

> offset的中文是：偏移，补偿，位移。

js中有一套方便的**获取元素尺寸**的办法就是offset家族。offset家族包括：

- offsetWidth

- offsetHight

- offsetLeft

- offsetTop

- offsetParent

下面分别介绍。

### 1、offsetWidth 和 offsetHight

`offsetWidth` 和 `offsetHight`：获取元素的**宽高 + padding + border**，不包括margin。如下：

- offsetWidth = width + padding + border

- offsetHeight = Height + padding + border

这两个属性，他们绑定在了所有的节点元素上。获取元素之后，只要调用这两个属性，我们就能够获取元素节点的宽和高。

举例如下：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 100px;
            height: 100px;
            padding: 10px;
            border: 10px solid #000;
            margin: 100px;
            background-color: pink;
        }
    </style>
</head>
<body>

<div class="box"></div>
<script>
    var div1 = document.getElementsByTagName("div")[0];

    console.log(div1.offsetHeight);          //打印结果：140（100+20+20）
    console.log(typeof div1.offsetHeight);   //打印结果：number

</script>
</body>
</html>
```

### 2、offsetParent

`offsetParent`：获取当前元素的**定位父元素**。

- 如果当前元素的父元素，**有CSS定位**（position为absolute、relative、fixed），那么 `offsetParent` 获取的是**最近的**那个父元素。

- 如果当前元素的父元素，**没有CSS定位**（position为absolute、relative、fixed），那么`offsetParent` 获取的是**body**。


举例：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
<div class="box1" style="position: absolute;">
    <div class="box2" style="position: fixed;">
        <div class="box3"></div>
    </div>
</div>
<script>

    var box3 = document.getElementsByClassName("box3")[0];

    console.log(box3.offsetParent);
</script>
</body>
</html>
```

打印结果：

![](http://img.smyhvae.com/20180202_1725.png)

### 3、offsetLeft 和 offsetTop

`offsetLeft`：当前元素相对于其**定位父元素**的水平偏移量。

`offsetTop`：当前元素相对于其**定位父元素**的垂直偏移量。

备注：从父亲的 padding 开始算起，父亲的 border 不算在内。

举例：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        .box1 {
            width: 300px;
            height: 300px;
            padding: 100px;
            margin: 100px;
            position: relative;
            border: 100px solid #000;
            background-color: pink;
        }

        .box2 {
            width: 100px;
            height: 100px;
            background-color: red;
            /*position: absolute;*/
            /*left: 10px;*/
            /*top: 10px;*/
        }
    </style>
</head>
<body>
<div class="box1">
    <div class="box2" style="left: 10px"></div>
</div>

<script>

    var box2 = document.getElementsByClassName("box2")[0];

    //offsetTop和offsetLeft
    console.log(box2.offsetLeft);  //100
    console.log(box2.style.left);  //10px


</script>

</body>
</html>
```

在父盒子有定位的情况下，offsetLeft == style.left(去掉px之后)。注意，后者只识别行内样式。但区别不仅仅于此，下面会讲。

### offsetLeft 和 style.left 区别

（1）最大区别在于：

offsetLeft 可以返回无定位父元素的偏移量。如果父元素中都没有定位，则body为准。

style.left 只能获取行内样式，如果父元素中都没有设置定位，则返回""（意思是，返回空字符串）;

（2）offsetTop 返回的是数字，而 style.top 返回的是字符串，而且还带有单位：px。

比如：

```javascript
div.offsetLeft = 100;
div.style.left = "100px";

```

（3）offsetLeft 和 offsetTop **只读**，而 style.left 和 style.top 可读写（只读是获取值，可写是修改值）


总结：我们一般的做法是：**用offsetLeft 和 offsetTop 获取值，用style.left 和 style.top 赋值**（比较方便）。理由如下：

- style.left：只能获取行内式，获取的值可能为空，容易出现NaN。

- offsetLeft：获取值特别方便，而且是现成的number，方便计算。它是只读的，不能赋值。


## 动画的种类

- 闪现（基本不用）

- 匀速（本文重点）

- 缓动（后续重点）

简单举例如下：（每间隔500ms，向右移动盒子100px）

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
            position: absolute;
        }
    </style>
</head>
<body>
<button>动画</button>
<div class="box" style="left: 0px"></div>

<script>
    var btn = document.getElementsByTagName("button")[0];
    var div = document.getElementsByTagName("div")[0];

    //1、闪动
    //    btn.onclick = function () {
    //        div.style.left = "500px";
    //    }

    //2、匀速运动
    btn.onclick = function () {
        //定时器，每隔一定的时间向右走一些
        setInterval(function () {
            console.log(parseInt(div.style.left));
            //动画原理： 盒子未来的位置 = 盒子现在的位置 + 步长；
            //用style.left赋值，用offsetLeft获取值。
            div.style.left = div.offsetLeft + 100 + "px";
            //div.style.left = parseInt(div.style.left)+10+"px";  //NaN不能用

        }, 500);
    }
</script>
</body>
</html>
```

效果如下：

![](http://img.smyhvae.com/20180202_1840.gif)

## 匀速动画的封装：每间隔30ms，移动盒子10px【重要】

代码如下：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        .box1 {
            margin: 0;
            padding: 5px;
            height: 300px;
            background-color: #ddd;
            position: relative;
        }

        button {
            margin: 5px;
        }

        .box2 {
            width: 100px;
            height: 100px;
            background-color: red;
            position: absolute;
            left: 195px;
            top: 40px;
        }

        .box3 {
            width: 100px;
            height: 100px;
            background-color: yellow;
            position: absolute;
            left: 0;
            top: 150px;
        }
    </style>
</head>
<body>
<div class="box1">
    <button>运动到 left = 200px</button>
    <button>运动到 left = 400px</button>
    <div class="box2"></div>
    <div class="box3"></div>
</div>

<script>
    var btnArr = document.getElementsByTagName("button");
    var box2 = document.getElementsByClassName("box2")[0];
    var box3 = document.getElementsByClassName("box3")[0];

    //绑定事件
    btnArr[0].onclick = function () {
        //如果有一天我们要传递另外一个盒子，那么我们的方法就不好用了
        //所以我们要增加第二个参数，被移动的盒子本身。
        animate(box2, 200);
        animate(box3, 200);
    }

    btnArr[1].onclick = function () {
        animate(box2, 400);
        animate(box3, 400);
    }

    //【重要】方法的封装：每间隔30ms，将盒子向右移动10px
    function animate(ele, target) {
        //要用定时器，先清除定时器
        //一个盒子只能有一个定时器，这样的话，不会和其他盒子出现定时器冲突
        //我们可以把定时器本身，当成为盒子的一个属性
        clearInterval(ele.timer);
        //我们要求盒子既能向前又能向后，那么我们的步长就得有正有负
        //目标值如果大于当前值取正，目标值如果小于当前值取负
        var speed = target > ele.offsetLeft ? 10 : -10;  //speed指的是步长
        ele.timer = setInterval(function () {
            //在执行之前就获取当前值和目标值之差
            var val = target - ele.offsetLeft;
            ele.style.left = ele.offsetLeft + speed + "px";
            //移动的过程中，如果目标值和当前值之差如果小于步长，那么就不能在前进了
            //因为步长有正有负，所有转换成绝对值来比较
            if (Math.abs(val) < Math.abs(speed)) {
                ele.style.left = target + "px";
                clearInterval(ele.timer);
            }
        }, 30)
    }
</script>
</body>
</html>
```

实现的效果：

![](http://img.smyhvae.com/20180202_1910.gif)

上方代码中的方法封装，可以作为一个模板步骤，要记住。其实，这个封装的方法，写成下面这样，会更严谨，更容易理解：（将if语句进行了改进）

```javascript
    //【重要】方法的封装：每间隔30ms，将盒子向右移动10px
    function animate(ele, target) {
        //要用定时器，先清除定时器
        //一个盒子只能有一个定时器，这样的话，不会和其他盒子出现定时器冲突
        //我们可以把定时器本身，当成为盒子的一个属性
        clearInterval(ele.timer);
        //我们要求盒子既能向前又能向后，那么我们的步长就得有正有负
        //目标值如果大于当前值取正，目标值如果小于当前值取负
        var speed = target > ele.offsetLeft ? 10 : -10;  //speed指的是步长
        ele.timer = setInterval(function () {
            //在执行之前就获取当前值和目标值之差
            var val = target - ele.offsetLeft;

            //移动的过程中，如果目标值和当前值之差如果小于步长，那么就不能在前进了
            //因为步长有正有负，所有转换成绝对值来比较
            if (Math.abs(val) < Math.abs(speed)) {  //如果val小于步长，则直接到达目的地；否则，每次移动一个步长
                ele.style.left = target + "px";
                clearInterval(ele.timer);
            } else {
                ele.style.left = ele.offsetLeft + speed + "px";
            }
        }, 30)
    }
```

## 代码举例：轮播图的实现

完整版代码如下：（注释已经比较详细）

```html
<!doctype html>
<html lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>无标题文档</title>
    <style type="text/css">
        * {
            padding: 0;
            margin: 0;
            list-style: none;
            border: 0;
        }

        .all {
            width: 500px;
            height: 200px;
            padding: 7px;
            border: 1px solid #ccc;
            margin: 100px auto;
            position: relative;
        }

        .screen {
            width: 500px;
            height: 200px;
            overflow: hidden;
            position: relative;
        }

        .screen li {
            width: 500px;
            height: 200px;
            overflow: hidden;
            float: left;
        }

        .screen ul {
            position: absolute;
            left: 0;
            top: 0px;
            width: 3000px;
        }

        .all ol {
            position: absolute;
            right: 10px;
            bottom: 10px;
            line-height: 20px;
            text-align: center;
        }

        .all ol li {
            float: left;
            width: 20px;
            height: 20px;
            background: #fff;
            border: 1px solid #ccc;
            margin-left: 10px;
            cursor: pointer;
        }

        .all ol li.current {
            background: yellow;
        }

        #arr {
            display: none;
        }

        #arr span {
            width: 40px;
            height: 40px;
            position: absolute;
            left: 5px;
            top: 50%;
            margin-top: -20px;
            background: #000;
            cursor: pointer;
            line-height: 40px;
            text-align: center;
            font-weight: bold;
            font-family: '黑体';
            font-size: 30px;
            color: #fff;
            opacity: 0.3;
            border: 1px solid #fff;
        }

        #arr #right {
            right: 5px;
            left: auto;
        }
    </style>

    <script>
        window.onload = function () {

            //需求：无缝滚动。
            //思路：赋值第一张图片放到ul的最后，然后当图片切换到第五张的时候
            //     直接切换第六章，再次从第一张切换到第二张的时候先瞬间切换到
            //     第一张图片，然后滑动到第二张
            //步骤：
            //1.获取事件源及相关元素。（老三步）
            //2.复制第一张图片所在的li,添加到ul的最后面。
            //3.给ol中添加li，ul中的个数-1个，并点亮第一个按钮。
            //4.鼠标放到ol的li上切换图片
            //5.添加定时器
            //6.左右切换图片（鼠标放上去隐藏，移开显示）


            //1.获取事件源及相关元素。（老三步）
            var all = document.getElementById("all");
            var screen = all.firstElementChild || all.firstChild;
            var imgWidth = screen.offsetWidth;
            var ul = screen.firstElementChild || screen.firstChild;
            var ol = screen.children[1];
            var div = screen.lastElementChild || screen.lastChild;
            var spanArr = div.children;

            //2.复制第一张图片所在的li,添加到ul的最后面。
            var ulNewLi = ul.children[0].cloneNode(true);
            ul.appendChild(ulNewLi);
            //3.给ol中添加li，ul中的个数-1个，并点亮第一个按钮。
            for (var i = 0; i < ul.children.length - 1; i++) {
                var olNewLi = document.createElement("li");
                olNewLi.innerHTML = i + 1;
                ol.appendChild(olNewLi)
            }
            var olLiArr = ol.children;
            olLiArr[0].className = "current";

            //4.鼠标放到ol的li上切换图片
            for (var i = 0; i < olLiArr.length; i++) {
                //自定义属性，把索引值绑定到元素的index属性上
                olLiArr[i].index = i;
                olLiArr[i].onmouseover = function () {
                    //排他思想
                    for (var j = 0; j < olLiArr.length; j++) {
                        olLiArr[j].className = "";
                    }
                    this.className = "current";
                    //鼠标放到小的方块上的时候索引值和key以及square同步
//                    key = this.index;
//                    square = this.index;
                    key = square = this.index;
                    //移动盒子
                    animate(ul, -this.index * imgWidth);
                }
            }

            //5.添加定时器
            var timer = setInterval(autoPlay, 1000);

            //固定向右切换图片
            //两个定时器（一个记录图片，一个记录小方块）
            var key = 0;
            var square = 0;

            function autoPlay() {
                //通过控制key的自增来模拟图片的索引值，然后移动ul
                key++;
                if (key > olLiArr.length) {
                    //图片已经滑动到最后一张，接下来，跳转到第一张，然后在滑动到第二张
                    ul.style.left = 0;
                    key = 1;
                }
                animate(ul, -key * imgWidth);
                //通过控制square的自增来模拟小方块的索引值，然后点亮盒子
                //排他思想做小方块
                square++;
                if (square > olLiArr.length - 1) {//索引值不能大于等于5，如果等于5，立刻变为0；
                    square = 0;
                }
                for (var i = 0; i < olLiArr.length; i++) {
                    olLiArr[i].className = "";
                }
                olLiArr[square].className = "current";
            }

            //鼠标放上去清除定时器，移开后在开启定时器
            all.onmouseover = function () {
                div.style.display = "block";
                clearInterval(timer);
            }
            all.onmouseout = function () {
                div.style.display = "none";
                timer = setInterval(autoPlay, 1000);
            }

            //6.左右切换图片（鼠标放上去显示，移开隐藏）
            spanArr[0].onclick = function () {
                //通过控制key的自增来模拟图片的索引值，然后移动ul
                key--;
                if (key < 0) {
                    //先移动到最后一张，然后key的值取之前一张的索引值，然后在向前移动
                    ul.style.left = -imgWidth * (olLiArr.length) + "px";
                    key = olLiArr.length - 1;
                }
                animate(ul, -key * imgWidth);
                //通过控制square的自增来模拟小方块的索引值，然后点亮盒子
                //排他思想做小方块
                square--;
                if (square < 0) {//索引值不能大于等于5，如果等于5，立刻变为0；
                    square = olLiArr.length - 1;
                }
                for (var i = 0; i < olLiArr.length; i++) {
                    olLiArr[i].className = "";
                }
                olLiArr[square].className = "current";
            }
            spanArr[1].onclick = function () {
                //右侧的和定时器一模一样
                autoPlay();
            }


            function animate(ele, target) {
                clearInterval(ele.timer);
                var speed = target > ele.offsetLeft ? 10 : -10;
                ele.timer = setInterval(function () {
                    var val = target - ele.offsetLeft;
                    ele.style.left = ele.offsetLeft + speed + "px";

                    if (Math.abs(val) < Math.abs(speed)) {
                        ele.style.left = target + "px";
                        clearInterval(ele.timer);
                    }
                }, 10)
            }
        }
    </script>
</head>

<body>
<div class="all" id='all'>
    <div class="screen" id="screen">
        <ul id="ul">
            <li><img src="images/1.jpg" width="500" height="200"/></li>
            <li><img src="images/2.jpg" width="500" height="200"/></li>
            <li><img src="images/3.jpg" width="500" height="200"/></li>
            <li><img src="images/4.jpg" width="500" height="200"/></li>
            <li><img src="images/5.jpg" width="500" height="200"/></li>
        </ul>
        <ol>

        </ol>
        <div id="arr">
            <span id="left"><</span>
            <span id="right">></span>
        </div>
    </div>
</div>
</body>
</html>


```

实现效果：

![](http://img.smyhvae.com/20180202_2020.gif)



## scroll 相关属性

### window.onscroll() 方法

当我们用鼠标滚轮，滚动网页的时候，会触发 window.onscroll() 方法。效果如下：（注意看控制台的打印结果）

![](http://img.smyhvae.com/20180202_2258.gif)

如果你需要做滚动监听，可以使用这个方法。

我们来看看和 scroll 相关的有哪些属性。

### 1、ScrollWidth 和 scrollHeight

`ScrollWidth` 和 `scrollHeight`：获取元素**整个滚动区域**的宽、高。包括 width 和 padding，不包括 border和margin。


**注意**：

`scrollHeight` 的特点是：如果内容超出了盒子，`scrollHeight`为内容的高（包括超出的内容）；如果不超出，`scrollHeight`为盒子本身的高度。`ScrollWidth`同理。


```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 100px;
            height: 100px;
            padding: 10px;
            margin: 3px;
            border: 8px solid red;
        }
    </style>
</head>
<body>

<div class="box">
    静，能寒窗苦守；动，能点石成金。
    静，能寒窗苦守；动，能点石成金。
    静，能寒窗苦守；动，能点石成金。
    静，能寒窗苦守；动，能点石成金。
    静，能寒窗苦守；动，能点石成金。
    静，能寒窗苦守；动，能点石成金。
</div>
<script>

    var div = document.getElementsByTagName("div")[0];

    // `scrollHeight` 的特点是：如果内容超出了盒子，`scrollHeight`为内容的高（包括超出的内容）；如果不超出，`scrollHeight`为盒子本身的高度。
    //IE8以下（不包括IE8），为盒子本身内容的高度。
    console.log(div.scrollWidth);
    console.log(div.scrollHeight);

</script>
</body>
</html>
```

打印结果：

![](http://img.smyhvae.com/20180203_1235.png)

### 2、scrollTop 和 scrollLeft

- `scrollLeft`：获取水平滚动条滚动的距离。

- `scrollTop`：获取垂直滚动条滚动的距离。

**实战经验**：

当某个元素满足`scrollHeight - scrollTop == clientHeight`时，说明垂直滚动条滚动到底了。

当某个元素满足`scrollWidth - scrollLeft == clientWidth`时，说明水平滚动条滚动到底了。

这个实战经验非常有用，可以用来判断用户是否已经将内容滑动到底了。比如说，有些场景下，希望用户能够看完“长长的活动规则”，才允许触发接下来的表单操作。

### scrollTop 的兼容性

如果要获取页面滚动的距离，scrollTop 这个属性的写法要注意兼容性，如下。

（1）如果文档没有 DTD 声明，写法为：

```javascript
    document.body.scrollTop
```

在没有 DTD 声明的情况下，要求是这种写法，chrome浏览器才能认出来。

（2）如果文档有 DTD 声明，写法为：

```javascript
   document.documentElement.scrollTop
```

在有 DTD 声明的情况下，要求是这种写法，IE6、7、8才能认出来。

综合上面这两个，就诞生了一种兼容性的写法：

```javascript
    document.body.scrollTop || document.documentElement.scrollTop //方式一

    document.body.scrollTop + document.documentElement.scrollTop  //方式二
```

另外还有一种兼容性的写法：`window.pageYOffset` 和 `window.pageXOffset`。这种写法无视DTD的声明。这种写法支持的浏览器版本是：火狐/谷歌/ie9+。

综合上面的几种写法，为了兼容，不管有没有DTD，**最终版的兼容性写法：**

```javascript
    window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop;
```

### 判断是否已经 DTD 声明

方法如下：

```javascript
    document.compatMode === "CSS1Compat"   // 已声明
    document.compatMode === "BackCompat"   // 未声明
```

### 将 scrollTop 和 scrollLeft 进行封装

这里，我们将 scrollTop 和 scrollLeft 封装为一个方法，名叫scroll()，返回值为 一个对象。以后就直接调用`scroll().top` 和 `scroll().left`就好。

代码实现：

```html
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        body {
            height: 6000px;
            width: 5000px;
        }
    </style>
</head>
<body>

<script>

    //需求：封装一个兼容的scroll().返回的是对象，用scroll().top获取scrollTop，用scroll().left获取scrollLeft

    window.onscroll = function () {
//        var myScroll = scroll();
//        myScroll.top;
        console.log(scroll().top);
        console.log(scroll().left);
    }

    //函数封装（简单封装，实际工作使用）
    function scroll() {
        return { //此函数的返回值是对象
            left: window.pageYOffset || document.body.scrollTop || document.documentElement.scrollTop,
            right: window.pageXOffset || document.body.scrollLeft || document.documentElement.scrollLeft
        }
    }
</script>
</body>
</html>
```

上方代码中，函数定义的那部分就是要封装的代码。

另外还有一种比较麻烦的封装方式：（仅供参考）

```javascript
function scroll() {  // 开始封装自己的scrollTop
    if(window.pageYOffset !== undefined) {  // ie9+ 高版本浏览器
        // 因为 window.pageYOffset 默认的是  0  所以这里需要判断
        return {
            left: window.pageXOffset,
            top: window.pageYOffset
        }
    }
    else if(document.compatMode === "CSS1Compat") {    // 标准浏览器   来判断有没有声明DTD
        return {
            left: document.documentElement.scrollLeft,
            top: document.documentElement.scrollTop
        }
    }
    return {   // 未声明 DTD
        left: document.body.scrollLeft,
        top: document.body.scrollTop
    }
}
```

## 获取 html 文档的方法

获取title、body、head、html标签的方法如下：

- `document.title` 文档标题；

- `document.head`  文档的头标签

- `document.body`  文档的body标签；

- `document.documentElement`  （这个很重要）。

`document.documentElement`表示文档的html标签。也就是说，基本结构当中的 `html 标签`而是通过`document.documentElement`访问的，并不是通过 document.html 去访问的。

## scrollTop 举例：固定导航栏

完整版代码实现：

（1）index.html：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            margin: 0;
            padding: 0
        }

        img {
            vertical-align: top;
        }

        .main {
            margin: 0 auto;
            width: 1000px;
            margin-top: 10px;

        }

        #Q-nav1 {
            overflow: hidden;
        }

        .fixed {
            position: fixed;
            top: 0;
            left: 0;
        }
    </style>

    <!--引入工具js-->
    <script src="tools.js"></script>
    <script>
        window.onload = function () {
            //需求1：当我们滚动界面的时候，被卷曲的头部如果超过第二个盒子距离顶部的位置，那么直接给第二个盒子加类名.fixed
            //需求2：当我们滚动界面的时候，被卷曲的头部如果小于第二个盒子距离顶部的位置，那么直接给第二个盒子取消类名.fixed

            //1.老三步。
            var topDiv = document.getElementById("top");
            var height = topDiv.offsetHeight;
            var middle = document.getElementById("Q-nav1");
            var main = document.getElementById("main");

            window.onscroll = function () {
                //2.判断 ，被卷曲的头部的大小
                if (scroll().top > height) {
                    //3.满足条件添加类，否则删除类
                    middle.className += " fixed";
                    //第二个盒子也要占位置，为了避免重叠，我们给第三个盒子一个上padding的空间，把这个空间留给第二个盒子
                    main.style.paddingTop = middle.offsetHeight + "px";
                } else {
                    middle.className = "";
                    //清零
                    main.style.paddingTop = 0;
                }
            }

        }
    </script>
</head>
<body>
<div class="top" id="top">
    <img src="images/top.png" alt=""/>
</div>
<div id="Q-nav1">
    <img src="images/nav.png" alt=""/>
</div>
<div class="main" id="main">
    <img src="images/main.png" alt=""/>
</div>
</body>
</html>

```

上方代码中，有一个技巧：

```javascript
main.style.paddingTop = middle.offsetHeight + "px";
```

仔细看注释就好。

（2）tools.js：

```javascript
/**
 * Created by smyhvae on 2018/02/03.
 */
function scroll() {  // 开始封装自己的scrollTop
    if (window.pageYOffset !== undefined) {  // ie9+ 高版本浏览器
        // 因为 window.pageYOffset 默认的是  0  所以这里需要判断
        return {
            left: window.pageXOffset,
            top: window.pageYOffset
        }
    }
    else if (document.compatMode === "CSS1Compat") {    // 标准浏览器   来判断有没有声明DTD
        return {
            left: document.documentElement.scrollLeft,
            top: document.documentElement.scrollTop
        }
    }
    return {   // 未声明 DTD
        left: document.body.scrollLeft,
        top: document.body.scrollTop
    }
}
```


实现效果：

![](http://img.smyhvae.com/20180203_1619.gif)


工程文件：

- 2018-02-03-scrollTop固定导航栏.rar


## 缓动动画

### 三个函数

缓慢动画里，我们要用到三个函数，这里先列出来：

- Math.ceil()         向上取整

- Math.floor()        向下取整

- Math.round();   四舍五入

### 缓动动画的原理

缓动动画的原理就是：在移动的过程中，步长越来越小。

设置步长为：**目标位置和盒子当前位置的十分之一**。用公式表达，即：

```
    盒子位置 = 盒子本身位置 + (目标位置 - 盒子本身位置)/ 10；
```

代码举例：

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
            position: absolute;
        }
    </style>
</head>
<body>
<button>运动到left = 400px</button>
<div></div>

<script>

    var btn = document.getElementsByTagName("button")[0];
    var div = document.getElementsByTagName("div")[0];

    btn.onclick = function () {
        setInterval(function () {
            //动画原理：盒子未来的位置 = 盒子当前的位置+步长
            div.style.left = div.offsetLeft + (400 - div.offsetLeft) / 10 + "px";
        }, 30);
    }

</script>
</body>
</html>
```

效果：

![](http://img.smyhvae.com/20180202_2046.gif)

### 缓慢动画的封装（解决四舍五入的问题）

我们发现一个问题，上图中的盒子最终并没有到达400px的位置，而是只到了396.04px就停住了：

![](http://img.smyhvae.com/20180202_2140.png)

原因是：JS在取整的运算时，进行了四舍五入。

我们把打印396.04px这个left值打印出来看看：

![](http://img.smyhvae.com/20180202_2150.png)

我么发现，通过`div.style.left`获取的值是精确的，通过`div.offsetLeft`获取的left值会进行四舍五入。

此时，我们就要用到取整的函数了。

通过对缓动动画进行封装，完整版的代码实现如下：


```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: pink;
            position: absolute;
            left: 0;
        }
    </style>
</head>
<body>
<button>运动到200</button>
<button>运动到400</button>
<div></div>

<script>

    var btn = document.getElementsByTagName("button");
    var div = document.getElementsByTagName("div")[0];

    btn[0].onclick = function () {
        animate(div, 200);
    }

    btn[1].onclick = function () {
        animate(div, 400);
    }

    //缓动动画封装
    function animate(ele, target) {
        //要用定时器，先清定时器
        //一个萝卜一个坑儿，一个元素对应一个定时器
        clearInterval(ele.timer);
        //定义定时器
        ele.timer = setInterval(function () {
            //获取步长
            //步长应该是越来越小的，缓动的算法。
            var step = (target - ele.offsetLeft) / 10;
            //对步长进行二次加工(大于0向上取整,小于0向下取整)
            //达到的效果是：最后10像素的时候都是1像素1像素的向目标位置移动，就能够到达指定位置。
            step = step > 0 ? Math.ceil(step) : Math.floor(step);
            //动画原理： 目标位置 = 当前位置 + 步长
            ele.style.left = ele.offsetLeft + step + "px";
            console.log(step);
            //检测缓动动画有没有停止
            console.log("smyhvae");
            if (Math.abs(target - ele.offsetLeft) <= Math.abs(step)) {
                //处理小数赋值
                ele.style.left = target + "px";
                clearInterval(ele.timer);
            }
        }, 30);
    }

</script>
</body>
</html>
```

实现效果：

![](http://img.smyhvae.com/20180202_2239.gif)


##  window.scrollTo()方法举例：返回到顶部小火箭

（1）index.html：


```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        img {
            position: fixed;
            bottom: 100px;
            right: 50px;
            cursor: pointer;
            display: none;
            border: 1px solid #000;
        }

        div {
            width: 1210px;
            margin: 100px auto;
            text-align: center;
            font: 500 26px/35px "simsun";
            color: red;
        }
    </style>
    <script src="tools.js"></script>
    <script>
        window.onload = function () {
            //需求：被卷去的头部超过100显示小火箭，然后点击小火箭屏幕缓慢移动到最顶端。
            //难点：我们以前是移动盒子，现在是移动屏幕，我们没有学过如何移动屏幕。
            //      技术点：window.scrollTo(x,y);浏览器显示区域跳转到指定的坐标
            //步骤：
            //1.老三步
            var img = document.getElementsByTagName("img")[0];
            window.onscroll = function () {
                //被卷去的距离大于200显示小火箭，否则隐藏
                //2.显示隐藏小火箭
                if (scroll().top > 1000) {
                    img.style.display = "block";
                } else {
                    img.style.display = "none";
                }
                //每次移动滚动条的时候都给leader赋值，模拟leader获取距离顶部的距离
                leader = scroll().top;
            }
            //3.缓动跳转到页面最顶端（利用我们的缓动动画）
            var timer = null;
            var target = 0; //目标位置
            var leader = 0; //显示区域自身的位置
            img.onclick = function () {
                //技术点：window.scrollTo(0,0);
                //要用定时器，先清定时器
                clearInterval(timer);
                timer = setInterval(function () {
                    //获取步长
                    var step = (target - leader) / 10;
                    //二次处理步长
                    step = step > 0 ? Math.ceil(step) : Math.floor(step);
                    leader = leader + step; //往上移动的过程中，step是负数。当前位置减去步长，就等于下一步的位置。
                    //显示区域移动
                    window.scrollTo(0, leader);
                    //清除定时器
                    if (leader === 0) {
                        clearInterval(timer);
                    }
                }, 25);
            }
        }
    </script>
</head>
<body>
<img src="images/Top.jpg"/>
<div>
    我是最顶端.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>
    生命壹号，永不止步.....<br>

</div>
</body>
</html>
```

（2）tools.js:

```javascript
/**
 * Created by smyhvae on 2015/12/8.
 */

//函数：获取scrollTop和scrollLeft的值
function scroll() {  // 开始封装自己的scrollTop
    if (window.pageYOffset != null) {  // ie9+ 高版本浏览器
        // 因为 window.pageYOffset 默认的是  0  所以这里需要判断
        return {
            left: window.pageXOffset,
            top: window.pageYOffset
        }
    }
    else if (document.compatMode === "CSS1Compat") {    // 标准浏览器   来判断有没有声明DTD
        return {
            left: document.documentElement.scrollLeft,
            top: document.documentElement.scrollTop
        }
    }
    return {   // 未声明 DTD
        left: document.body.scrollLeft,
        top: document.body.scrollTop
    }
}

```

实现效果：

![](http://img.smyhvae.com/20180203_1710.gif)

小火箭的图片资源：

![](http://img.smyhvae.com/20180203-Top.jpg)

## client 家族的组成

### clientWidth 和 clientHeight

元素调用时：

- clientWidth：获取元素的可见宽度（width + padding）。

- clientHeight：获取元素的可见高度（height + padding）。


body/html 调用时：

- clientWidth：获取网页可视区域宽度。

- clientHeight：获取网页可视区域高度。

**声明**：

- `clientWidth` 和 `clientHeight` 属性是只读的，不可修改。

- `clientWidth` 和 `clientHeight` 的值都是不带 px 的，返回的都是一个数字，可以直接进行计算。


### clientX 和 clientY

event调用：

- clientX：鼠标距离可视区域左侧距离。

- clientY：鼠标距离可视区域上侧距离。



### clientTop 和 clientLeft

- clientTop：盒子的上border。

- clientLeft：盒子的左border。


## 三大家族 offset/scroll/client 的区别

### 区别1：宽高

- offsetWidth  = width  + padding + border
- offsetHeight = height + padding + border

- scrollWidth   = 内容宽度（不包含border）
- scrollHeight  = 内容高度（不包含border）

- clientWidth  = width  + padding
- clientHeight = height + padding


### 区别2：上左


offsetTop/offsetLeft：

- 调用者：任意元素。(盒子为主)
- 作用：距离父系盒子中带有定位的距离。


scrollTop/scrollLeft：

- 调用者：document.body.scrollTop（window调用）(盒子也可以调用，但必须有滚动条)
- 作用：浏览器无法显示的部分（被卷去的部分）。


clientY/clientX：

- 调用者：event
- 作用：鼠标距离浏览器可视区域的距离（左、上）。




## 函数封装：获取浏览器的宽高（可视区域）

函数封装如下：

```javascript
//函数封装：获取屏幕可视区域的宽高
function client() {
    if (window.innerHeight !== undefined) {
        //ie9及其以上的版本的写法
        return {
            "width": window.innerWidth,
            "height": window.innerHeight
        }
    } else if (document.compatMode === "CSS1Compat") {
        //标准模式的写法（有DTD时）
        return {
            "width": document.documentElement.clientWidth,
            "height": document.documentElement.clientHeight
        }
    } else {
        //没有DTD时的写法
        return {
            "width": document.body.clientWidth,
            "height": document.body.clientHeight
        }
    }
}

```


**案例：根据浏览器的可视宽度，给定不同的背景的色。**

> PS：这个可以用来做响应式。

代码如下：（需要用到上面的封装好的方法）

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>

<script src="tools.js"></script>
<script>
    //需求：浏览器每次更改大小，判断是否符合某一标准然后给背景上色。
    //  // >960红色，大于640小于960蓝色，小于640绿色。

    window.onresize = fn;  //页面大小发生变化时，执行该函数。
    //页面加载的时候直接执行一次函数，确定浏览器可视区域的宽，给背景上色
    fn();

    //封装成函数，然后指定的时候去调用和绑定函数名
    function fn() {
        if (client().width > 960) {
            document.body.style.backgroundColor = "red";
        } else if (client().width > 640) {
            document.body.style.backgroundColor = "blue";
        } else {
            document.body.style.backgroundColor = "green";
        }
    }
</script>
</body>
</html>
```


上当代码中，`window.onresize`事件指的是：在窗口或框架被调整大小时发生。各个事件的解释如下：

- window.onscroll        屏幕滑动

- window.onresize       浏览器大小变化

- window.onload	        页面加载完毕

- div.onmousemove    鼠标在盒子上移动（注意：不是盒子移动）



## 获取显示器的分辨率

比如，我的电脑的显示器分辨率是：1920*1080。


获取显示器的分辨率：

```javascript
    window.onresize = function () {
        document.title = window.screen.width + "    " + window.screen.height;
    }
```

显示效果：


![](http://img.smyhvae.com/20180203_2155.png)


上图中，不管我如何改变浏览器的窗口大小，title栏显示的值永远都是我的显示器分辨率：1920*1080

## 正则

正则表达式是表达如何匹配文本模式的一种非常简洁的方法。

在编程中经常会提出从文本中解析和提取数据或验证某些文本是否符合特定模式的要求，

可以说是一个很好用工具

## 正则表达式简介

**定义**：正则表达式用于定义一些字符串的规则。

**作用**：计算机可以根据正则表达式，来检查一个字符串是否符合指定的规则；或者将字符串中符合规则的内容提取出来。

如果你想查看正则更多的内容，可以查阅官方文档关于 RegExp 这个内置对象的用法。

## 创建正则表达式的对象

### 方式一：使用构造函数创建正则表达式的对象

语法：

```javascript
	var 变量 = new RegExp("正则表达式"); // 注意，参数是字符串

	var 变量 = new RegExp("正则表达式", "匹配模式"); // 注意，两个参数都是字符串
```

备注：`RegExp`的意思是 **Regular expression**。使用typeof检查正则对象，会返回object。

上面的语法中，既可以传一个参数，也可以传两个参数。

创建了正则表达式的对象后，该怎么使用呢？大致分为两个步骤：

- （1）创建正则表达式的对象 reg。

- （2）使用 reg 的test() 方法，判断指定字符串是否符合规则。

**正则表达式的`test()`方法**：【重要】

```javascript
	myReg.test(str); // 判断字符串 str 是否符合 指定的 myReg 这个正则表达式的规则
```

解释：使用`test()`这个方法可以用来检查一个字符串是否符合正则表达式的规则，**如果符合则返回true，否则返回false**。

我们来看看下面的例子。

**1、传一个参数时**：

构造函数 RegExp 中，可以只传一个参数。

代码举例：

```javascript
	var reg = new RegExp("a"); // 定义一个正则表达式：检查一个字符串中是否含有 a

	var str1 = "qianguyihao";
	var str2 = "smyh";

	// 通过 test()方法，判断字符串是否符合 上面定义的 reg 规则
	console.log(reg.test(str1)); // 打印结果：true
	console.log(reg.test(str2)); // 打印结果：false

```

注意，上面的例子中，我们是先定义了一个正则表达式的规则，然后通过正则表达式的`test()`方法来判断字符串是否符合之前定义的规则。

**2、传两个参数时**：匹配模式 【重要】

构造函数 RegExp 中，也可以传两个参数。我们可以传递一个**匹配模式**作为第二个参数。这个参数可以是：

- `i` 忽略大小写。这里的 i 指的是 ignore。

- `g` 全局匹配模式。这里的 g 指的是 global。

代码举例：

```javascript
    var reg = new RegExp('A', 'i');
    var str = 'qiangu';

    console.log(reg.test(str)); // 打印结果：true
```

### 方式二：使用字面量创建正则表达式

我们可以使用字面量来创建正则表达式。

语法：

```javascript
	var 变量 = /正则表达式/;  // 注意，这个语法里没有引号

	var 变量 = /正则表达式/匹配模式;  // 注意，这个语法里没有引号
```

代码举例：

```javascript
	var reg = /A/i; // 定义正则表达式的规则：检查一个字符串中是否含有 a。忽略大小写。
	var str = "qiangu";

	console.log(typeof reg);  // 打印结果：object
	console.log(reg.test(str)); // 打印结果：true
```

### 以上两种方式的对比

- 方式一：使用构造函数创建时，更加灵活，因为参数中还可以传递变量。

- 方式二：使用字面量的方式创建，更加简单。

代码举例：

```javascript
	var reg = new RegExp("a", "i"); // 方式一

	var reg = /a/i; // 方式二
```

上面这两行代码的作用是等价的。

### 避坑指南：全局匹配 g 慎用test()方法

对于非全局匹配的正则表达式，`test()`只会检测**是否存在某个目标字符串**（只要存在就为 true），多次检测的结果都相同。例如：

```javascript
const reg = /test/;
const str = '_test_test';

reg.test(str) // true
reg.test(str) // true
reg.test(str) // true
```

重点来了。

当设置全局标志 `/g` 时，一旦字符串中还存在匹配，test() 方法都将返回 true，同时匹配成功后将把 `lastIndex` 属性的值**设置为上次匹配成功结果之后的第一个字符所在的位置**，下次匹配将从 `lastIndex` 指示的位置开始；匹配不成功时返回 false，同时将 lastIndex 属性的值重置为 0。

举例：（很重要的例子，看仔细）

```javascript
const reg = /test/g;
const str = '_test_test';

console.log(reg.test(str)); // true
console.log(reg.lastIndex); // 5

console.log(reg.test(str)); // true
console.log(reg.lastIndex); // 10

console.log(reg.test(str)); // false
console.log(reg.lastIndex); // 0
```

**总结**：

全局匹配模式`g`一般用于 `exec()`、`match()`、`replace()`等方法。

全局匹配模式`g`如果用于test()方法会有问题。因为g模式会生成一个`lastindex`参数来存储匹配最后一次的位置。

参考链接：

- [JS正则表达式全局匹配的那些坑](https://juejin.im/post/5de9bd5fe51d45582c27b6f3)

- [javascript正则全局匹配g慎用test方法](https://blog.csdn.net/Leolu007/article/details/8576490)

- [issues](https://github.com/qianguyihao/Web/issues/69)


## 正则表达式的简单语法

### 检查一个字符串中是否包含 a或b

**写法1**：

```javascript
	var reg = /a|b/;
```

解释：使用 `|` 表示`或`的意思。

**写法2**：

```javascript
	var reg = /[ab]/;  // 跟上面的那行语法，是等价的
```

解释：这里的`[]`也是表示`或`的意思。

`[]`这个符号在正则还是比较常用的。我们接下来看几个例子。

### []表示：或

一些规则：

- `/[ab]/` 等价于 `/a|b/`：检查一个字符串中是否包含 **a或b**

- `/[a-z]/`：检查一个字符串那种是否包含**任意小写字母**

- `/[A-Z]/`：任意大写字母

- `/[A-z]/`：任意字母

- `/[0-9]/`：任意数字

- `/a[bde]c/`：检查一个字符串中是否包含 abc 或 adc 或 aec

### [^ ] 表示：除了

举例1：

```javascript
  var reg = /[^ab]/; // 规则：字符串中，除了a、b之外，还有没有其他的字符内容？
  var str = "acb";

  console.log(reg.test(str)); // 打印结果：true
```

举例2：（可以用来验证某字符串是否为 纯数字）

```javascript
	var reg = /[^0-9]/;  // 规则：字符串中，除了数字之外，还有没有其他的内容？
	var str1 = "1991";
	var str2 = "199a1";

	console.log(reg.test(str1)); // 打印结果：false （如果字符串是 纯数字，则返回 false）
	console.log(reg.test(str2)); // 打印结果：true
```

## 支持正则表达式的 String 对象的方法

 String对象的如下方法，是支持正则表达式的：

| 方法      | 描述                                                   | 备注 |
| :-------- | :----------------------------------------------------- | :--- |
| split()   | 将字符串拆分成数组                                     |      |
| search()  | 搜索字符串中是否含有指定内容，返回索引 index           |      |
| match()   | 根据正则表达式，从一个字符串中将符合条件的内容提取出来 |      |
| replace() | 将字符串中的指定内容，替换为新的内容并返回             |      |

下面来分别介绍和举例。

### split()

`split()`：将一个字符串拆分成一个数组。可以接受一个正则表达式作为参数。

备注：关于`split()`更详细的用法，可以看之前的关于《内置对象：String》这篇文章。

**正则相关的举例**：根据任意字母，将字符串拆分成数组。

代码实现：（通过正则）

```javascript
	var str = "1a2b3c4d5e6f7g";

	var result = str.split(/[A-z]/); // 参数是一个正则表达式：表示所有字母
	console.log(result);
```

打印结果：

```json
	["1", "2", "3", "4", "5", "6", "7", ""]
```

### search()

`search()`：搜索字符串中是否含有指定内容。如果搜索到指定内容，则会返回第一次出现的索引；否则返回-1。

`search()`方法可以接受一个正则表达式作为参数，然后会根据正则表达式去检索字符串。`serach()`只会查找第一个，即使设置全局匹配也没用。

**举例**：

```javascript
	var str = "hello abc hello aec afc";
	/*
	* 搜索字符串中是否含有abc 或 aec 或 afc
	*/
	result = str.search(/a[bef]c/);
	console.log(result); // 打印结果：6
```

### match()

`match()`：根据正则表达式，从一个字符串中将符合条件的内容提取出来，封装到一个数组中返回（即使只查询到一个结果）。

**注意**：默认情况下，`match()`方法只会找到**第一个**符合要求的内容，找到以后就停止检索。我们可以设置正则表达式为**全局匹配**模式，这样就会匹配到所有的内容，并以**数组**的形式返回。

另外，我们可以为一个正则表达式设置多个匹配模式，且匹配模式的顺序无所谓。

**代码举例**：

```javascript
	var str = "1a2a3a4a5e6f7A8B9C";

	var result1 = str.match(/[a-z]/);   // 找到符合要求的第一个内容，然后返回
	var result2 = str.match(/[a-z]/g);  // 设置为“全局匹配”模式，匹配字符串中 所有的小写字母
	var result3 = str.match(/[a-z]/gi); // 设置多个匹配模式，匹配字符串中 所有的字母（忽略大小写）

	console.log(result1); // 打印结果：["a"]
	console.log(result2); // 打印结果：["a", "a", "a", "a", "e", "f"]
	console.log(result3); // 打印结果：["a", "a", "a", "a", "e", "f", "A", "B", "C"]
```

**总结**：

match()这个方法还是很实用的，可以在一个很长的字符串中，提取出**有规则**的内容。这不就是爬虫的时候经常会遇到的场景么？

### replace()

`replace()`：将字符串中的指定内容，替换为新的内容并返回。不会修改原字符串。

语法：

```javascript
	新的字符串 = str.replace(被替换的内容，新的内容);
```

参数解释：

- 被替换的内容：可以接受一个正则表达式作为参数。

- 新的内容：默认只会替换第一个。如果需要替换全部符合条件的内容，可以设置正则表达式为**全局匹配**模式。

代码举例：

```javascript
    //replace()方法：替换
    var str2 = "Today is fine day,today is fine day !!!"

    console.log(str2);
    console.log(str2.replace("today","tomorrow"));  //只能替换第一个today
    console.log(str2.replace(/today/gi,"tomorrow")); //这里用到了正则，且为“全局匹配”模式，才能替换所有的today
```

## 常见正则表达式举例

### 检查一个字符串是否是一个合法手机号

手机号的规则：

- 以1开头

- 第二位是3~9之间任意数字

- 三位以后任意9位数字

正则实现：

```javascript
	var phoneStr = "13067890123";

	var phoneReg = /^1[3-9][0-9]{9}$/;

	console.log(phoneReg.test(phoneStr));
```

**备注**：如果在正则表达式中同时使用`^`和`$`符号，则要求字符串必须完全符合正则表达式。

### 去掉字符串开头和结尾的空格

正则实现：

```javascript
	str = str.replace(/^\s*|\s*$/g,"");
```

解释如下：

```javascript
	str = str.replace(/^\s*/, ""); //去除开头的空格

	str = str.replace(/\s*$/, ""); //去除结尾的空格
```

### 判断字符串是否为电子邮件

正则实现：

```javascript
	var emailReg = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]{2,5}){1,2}$/;

	var email = "abchello@163.com";

	console.log(emailReg.test(email));
```


## 

## ES6（重点）

### 变量定义：let和const

### 箭头函数

​	   箭头函数中没有 this 绑定，必须通过查找作用域链来决定其值，如果箭头函数被非箭头函数包含，则 this 绑定的是最近一层非箭头函数的 this，否则，this 为 undefined   

### this指向

​         this 永远指向最后调用它的那个

### 函数传递参数的时候的默认值

// bad **function** **test**(quantity) {  

**const** q = quantity || 1; 

} 

// good **function** **test**(quantity = 1) {

  ... }

### 解构

### 模板字符串

### 展开运算符

### class

### Set

### Map

### 数组去重（重点）

参考 JavaScript专题之数组去重

## DOM高级（运动）

运动函数的封装

轮播图的实现一级无缝滚动



## 面向对象

- 对象:JS中万物皆对象,它是一个泛指,（类似生活中的世界）
- 类:对象的具体的细分,（类似生活中的人类，动物类）
- 实例:某一个类别中具体的一个事物（类似人的个体）

JS中有一个内置的类 Array(数组类),每一个数组都是这个类的一个实例,我们拿出一个数组(拿出一个实例)来进行研究,研究出来的知识,我们可以说所有的数组都具备这些知识

内置类:

Number,String,Boolean,Null,Undefined

Object、Array、RegExp、Date、Function…

HTMLCollection(元素集合类),通过getElementsByTagName等获取的元素集合都是它的一个实例

NodeList(节点集合类),通过getElementsByName等获取的节点集合都是它的一个实例

HTMLDivElement(每一个HTML标签都有一个自己对应的类) HTMLElement Element Node EventTarget …

### 创建对象的方式

创建对象的方式，最基本的有5种模式：**单例模式**、**工厂模式**、**构造函数模式**、**原型模式**、**构造函数+原型模式**

### 方式一：对象字面量

**对象的字面量**就是一个{}。里面的属性和方法均是**键值对**：

- 键：相当于属性名。

- 值：相当于属性值，可以是任意类型的值（数字类型、字符串类型、布尔类型，函数类型等）。

例如：

```javascript
var o = {
            name: "千古壹号",
            age: 26,
            isBoy: true,
            sayHi: function() {
                console.log(this.name);
            }
        };

console.log(o);
```

控制台输出：

![](http://img.smyhvae.com/20180125_1834.png)

### 方式二：工厂模式

通过该方法可以大批量的创建对象。

```javascript
    /*
        * 使用工厂方法创建对象
        *  通过该方法可以大批量的创建对象
        */
    function createPerson(name, age, gender) {
        //创建一个新的对象
        var obj = new Object();
        //向对象中添加属性
        obj.name = name;
        obj.age = age;
        obj.gender = gender;
        obj.sayName = function() {
            alert(this.name);
        };
        //将新的对象返回
        return obj;
    }

    var obj2 = createPerson("猪八戒", 28, "男");
    var obj3 = createPerson("白骨精", 16, "女");
    var obj4 = createPerson("蜘蛛精", 18, "女");
```

第一次看到这种工厂模式时，你可能会觉得陌生。如果简化一下，可以写成下面这种形式，更容易理解：（也就是，利用new Object创建对象）

```javascript
var obj = new Obect();
obj.name = '猪八戒';
obj.age = 28;
obj.gender = '男';
obj.sayHi = function() {
    alert('hello world');
};
```


**弊端：**

使用工厂方法创建的对象，使用的构造函数都是Object。**所以创建的对象都是Object这个类型，就导致我们无法区分出多种不同类型的对象**。

### 方式三：利用构造函数

```javascript
        //利用构造函数自定义对象
        var stu1 = new Student("smyh");
        console.log(stu1);
        stu1.sayHi();

        var stu2 = new Student("vae");
        console.log(stu2);
        stu2.sayHi();


        // 创建一个构造函数
        function Student(name) {
            this.name = name;    //this指的是当前对象实例【重要】
            this.sayHi = function () {
                console.log(this.name + "厉害了");
            }
        }
```

打印结果：

![](http://img.smyhvae.com/20180125_1350.png)

接下来，我们专门来讲一下构造函数。

## 构造函数

### 代码引入


```javascript
      // 创建一个构造函数，专门用来创建Person对象
      function Person(name, age, gender) {
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.sayName = function() {
          alert(this.name);
        };
      }

      var per = new Person("孙悟空", 18, "男");
      var per2 = new Person("玉兔精", 16, "女");
      var per3 = new Person("奔波霸", 38, "男");

      // 创建一个构造函数，专门用来创建 Dog 对象
      function Dog() {}

      var dog = new Dog();
```

### 构造函数的概念

**构造函数**：是一种特殊的函数，主要用来创建和初始化对象，也就是为对象的成员变量赋初始值。它与 `new` 一起使用才有意义。

我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个构造函数里面。

### 构造函数和普通函数的区别

构造函数的创建方式和普通函数没有区别，不同的是构造函数习惯上首字母大写。

构造函数和普通函数的区别就是**调用方式**的不同：普通函数是直接调用，而构造函数需要使用new关键字来调用。

**this的指向也有所不同**：

- 1.以函数的形式调用时，this永远都是window。比如`fun();`相当于`window.fun();`

- 2.以方法的形式调用时，this是调用方法的那个对象

- 3.以构造函数的形式调用时，this是新创建的实例对象

### new 一个构造函数的执行流程

new 在执行时，会做下面这四件事：

（1）开辟内存空间，在内存中创建一个新的空对象。

（2）让 this 指向这个新的对象。

（3）执行构造函数里面的代码，给这个新对象添加属性和方法。

（4）返回这个新对象（所以构造函数里面不需要return）。

因为this指的是new一个Object之后的对象实例。于是，下面这段代码：

```javascript
        // 创建一个函数
        function createStudent(name) {
            var student = new Object();
            student.name = name;      //第一个name指的是student对象定义的变量。第二个name指的是createStudent函数的参数。二者不一样
        }
```

可以改进为：

```javascript
        // 创建一个函数
        function Student(name) {
            this.name = name;       //this指的是构造函数中的对象实例
        }

```

注意上方代码中的注释。

### 类、实例

使用同一个构造函数创建的对象，我们称为一类对象，也将一个构造函数称为一个**类**。

通过一个构造函数创建的对象，称为该类的**实例**。

### instanceof

使用 instanceof 可以检查**一个对象是否为一个类的实例**。

**语法如下**：

```javascript
对象 instanceof 构造函数
```

如果是，则返回true；否则返回false。

**代码举例**：

```javascript
      function Person() {}

      function Dog() {}

      var person1 = new Person();

      var dog1 = new Dog();

      console.log(person1 instanceof Person); // 打印结果： true
      console.log(dog1 instanceof Person); // 打印结果：false

      console.log(dog1 instanceof Object); // 所有的对象都是Object的后代。因此，打印结果为：true
```

根据上方代码中的最后一行，需要补充一点：**所有的对象都是Object的后代，因此 `任何对象 instanceof Object` 的返回结果都是true**。


## others

### json的介绍

> 对象字面量和json比较像，这里我们对json做一个简单介绍。

JSON：JavaScript Object Notation（JavaScript对象表示形式）。

JSON和对象字面量的区别：JSON的属性必须用双引号引号引起来，对象字面量可以省略。

json举例：

```
      {
            "name" : "zs",
            "age" : 18,
            "sex" : true,
            "sayHi" : function() {
                console.log(this.name);
            }
        };
```

注：json里一般放常量、数组、对象等，但很少放function。

另外，对象和json没有长度，json.length的打印结果是undefined。于是乎，自然也就不能用for循环遍历（因为遍历时需要获取长度length）。

**json遍历的方法：**

json 采用 `for...in...`进行遍历，和数组的遍历方式不同。如下：

```html
<script>
    var myJson = {
        "name": "smyhvae",
        "aaa": 111,
        "bbb": 222
    };

    //json遍历的方法：for...in...
    for (var key in myJson) {
        console.log(key);   //获取 键
        console.log(myJson[key]); //获取 值（第二种属性绑定和获取值的方法）
        console.log("------");
    }
</script>
```

打印结果

### 函数也是个对象

定义一个函数(用构造函数的方式定义函数，只是想告诉你函数是个对象，不是让你这样用) fn就是个变量，也是函数名，函数名就是变量名，fn是对象

 var fn = new Function("alert('hi')");   fn();

### prototype原型模式

我们创建的每个函数都有一个 prototype （原型）属性，这个属性是一个指针，指向一个对象，而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法

### 原型的引入

```javascript
        function Person(name, age, gender) {
            this.name = name;
            this.age = age;
            this.gender = gender;
            //向对象中添加一个方法
            this.sayName = function () {
                console.log("我是" + this.name);
            }
        }

        //创建一个Person的实例
        var per = new Person("孙悟空", 18, "男");
        var per2 = new Person("猪八戒", 28, "男");
        per.sayName();
        per2.sayName();

        console.log(per.sayName == per2.sayName);  //打印结果为false
```

**分析如下**：

上方代码中，我们的sayName方法是写在构造函数 Person 内部的，然后在两个实例中进行了调用。造成的结果是，**构造函数每执行一次，就会给每个实例创建一个新的 sayName 方法**。也就是说，每个实例的sayName都是唯一的。因此，最后一行代码的打印结果为false。

按照上面这种写法，假设创建10000个对象实例，就会创建10000个 sayName 方法。这种写法肯定是不合适的。我们为何不让所有的对象共享同一个方法呢？

还有一种方式是，将sayName方法在全局作用域中定义：（不建议。原因看注释）

```javascript
        function Person(name, age, gender) {
            this.name = name;
            this.age = age;
            this.gender = gender;
            //向对象中添加一个方法
            this.sayName = fun;
        }

        //将sayName方法在全局作用域中定义
        /*
         * 将函数定义在全局作用域，污染了全局作用域的命名空间
         *  而且定义在全局作用域中也很不安全
         */
        function fun() {
            alert("Hello大家好，我是:" + this.name);
        };
```

比较好的方式是，在原型中添加sayName方法：

```javascript
    Person.prototype.sayName = function(){
        alert("Hello大家好，我是:"+this.name);
    };
```

这也就引入了我们本文要讲的「原型」。

### 原型prototype的概念

**认识1**：

我们所创建的每一个函数，解析器都会向函数中添加一个属性 prototype。这个属性对应着一个对象，这个对象就是我们所谓的原型对象。

如果函数作为普通函数调用prototype没有任何作用，当函数以构造函数的形式调用时，它所创建的实例对象中都会有一个隐含的属性，指向该构造函数的原型，我们可以通过__proto__来访问该属性。

代码举例：

```javascript
	// 定义构造函数
	function Person() {}

	var per1 = new Person();
	var per2 = new Person();

	console.log(Person.prototype); // 打印结果：[object object]

	console.log(per1.__proto__ == Person.prototype); // 打印结果：true
```

上方代码的最后一行：打印结果表明，`实例.__proto__` 和 `构造函数.prototype`都指的是原型对象。

**认识2**：

原型对象就相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象，我们可以将对象中共有的内容，统一设置到原型对象中。

以后我们创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中，这样就不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法了。

**认识3**：

使用 `in` 检查对象中是否含有某个属性时，如果对象中没有但是**原型中**有，也会返回true。

可以使用对象的`hasOwnProperty()`来检查**对象自身中**是否含有该属性。

### 原型链

原型对象也是对象，所以它也有原型，当我们使用或访问一个对象的属性或方法时：

- 它会先在对象自身中寻找，如果有则直接使用；

- 如果没有则会去原型对象中寻找，如果找到则直接使用；

- 如果没有则去原型的原型中寻找，直到找到Object对象的原型。

- Object对象的原型没有原型，如果在Object原型中依然没有找到，则返回 null

### 总结

第一次接触「原型」和「原型链」的时候，会比较难理解。多接触几次，再回过头来看，就慢慢熟悉了。

## 对象的 toString() 方法

我们先来看下面这段代码：

```javascript
	function Person(name, age, gender) {
	this.name = name;
	this.age = age;
	this.gender = gender;
	}

	var per1 = new Person("vae", 26, "男");

	console.log("per1 = " + per1);
	console.log("per1 = " + per1.toString());
```

打印结果：

```
per1 = [object Object]
per1 = [object Object]
```

上面的代码中，我们尝试打印实例 per1 的内部信息，但是发现，无论是打印 `per1` 还是打印 `per1.toString()`，结果都是`object`，这是为啥呢？分析如下：

- 当我们直接在页面中打印一个对象时，其实是输出了对象的toString()方法的返回值。

- 如果我们希望在打印对象时，不输出[object Object]，可以手动为对象添加一个toString()方法。意思是，重写 toString() 方法。

重写 toString() 方法，具体做法如下：

```javascript
	function Person(name, age, gender) {
	this.name = name;
	this.age = age;
	this.gender = gender;
	}

	//方式一：重写 Person 原型的toString方法。针对 Person 的所有实例生效
	Person.prototype.toString = function() {
		return (
		  "Person[name=" +
		  this.name +
		  ",age=" +
		  this.age +
		  ",gender=" +
		  this.gender +
		  "]"
		);
	};

	// 方式二：仅重写实例 per1 的 toString方法。但是这种写法，只对 per1 生效， 对 per2 无效
	/*
	per1.toString = function() {
		return (
		  "Person[name=" +
		  this.name +
		  ",age=" +
		  this.age +
		  ",gender=" +
		  this.gender +
		  "]"
		);
	};
	*/

	var per1 = new Person("smyh", 26, "男");

	var per2 = new Person("vae", 30, "男");

	console.log("per1 = " + per1);
	console.log("per2 = " + per2.toString());
```

打印结果：

```javascript
per1 = Person[name=smyh,age=26,gender=男]
per2 = Person[name=vae,age=30,gender=男]
```

代码分析：

上面的代码中，仔细看注释。我们重写了 Person 原型的 toString()，这样的话，可以保证对 Person 的所有实例生效。

从这个例子，我们可以看出 `prototype` 的作用。

## JS的垃圾回收（GC）机制

程序运行过程中会产生垃圾，这些垃圾积攒过多以后，会导致程序运行的速度过慢。所以我们需要一个垃圾回收的机制，来处理程序运行过程中产生垃圾。

当一个对象没有任何的变量或属性对它进行引用时，此时我们将永远无法操作该对象，此时这种对象就是一个垃圾，这种对象过多会占用大量的内存空间，导致程序运行变慢，所以这种垃圾必须进行清理。

上面这句话，也可以这样理解：如果堆内存中的对象，没有任何变量指向它时，这个堆内存里的对象就会成为垃圾。

JS拥有自动的垃圾回收机制，会自动将这些垃圾对象从内存中销毁。我们不需要也不能进行垃圾回收的操作。我们仅仅需要做的是：如果你不再使用该对象，那么，将改对象的引用设置为 null 即可。

### constructor

每个对象都有一个constructor属性， 它就是对象的类（ 构造函数）；    
            用constructor可以判断一个对象属于哪个类（ instanceof也可以达到这个效果） 
            用constructor还可以判断两个对象是不是同一个类

### 案例

弹力球：面向过程和面向对象

放大镜：面向过程和面向对象

tab

轮播图：

烟花

购物车

## 了解前后端

```
前端：用户看的见，摸得着的部分，也是评价一个软件好坏，优劣的重要的指标，完成人机交互（界面，动画效果，正则验证 ）

​         HTML,CSS,JS 三者结合起来完成前端功能
```

      后端：用户感知不到的部分，后端完成的功能是：如：注册，登录，对数据增删改查
            
              php，或者jsp，或者aspx，或者python，或者nodejs等等都是可以完成后端的功能的      
```
 全栈： 前端后端合起来
```



## php

php(Personal Home Page) 是一门后端语言，它有自己的服务器，服务器就相当于一台电脑，它的作用是与前端交互(接收和发送请求)，保存文件，执行后端代码等，

- php的扩展名：.php
- php代码必须写在  <?php   ?> 之间
- php代码后面的分号必须加
- 输出语句   echo

#### 前端交互

接收前端的数据

$_GET[键]

$_POST[键]

给前端响应内容

echo 内容

## myspl_php

myspl 是一种开源的数据库软件，用来存储数据的，

用来完成php与数据库之间交互的功能

#### 创建库和表

创建库：create database 库名

创建表：create table 表名（字段列表）

create table person(

  xxxxx,

xxxxx,

)

#### 数据库的增删改查

         增（添加数据）：格式：insert into 表名(字段列表) value(值的列表)
    
         查（查询数据）：格式：select 字段列表 from  表名 where 条件
    
         删（删除数据）：格式： delete from 表名  where 条件
    
         改（修改数据）：格式： update 表名 set 字段名1=值1, 字段名2=值2 where 条件

#### php操作数据库

1、连接数据库

​         mysql_connect（）：完成php与数据库的连接

2、执行sql语句

​         mysql_query()：在php中执行sql语句（执行结果会到mysql里面）

3、关闭数据库

​		mysqli_close(连接对象);

#### 让php返回一个json（数组）数据

​           8.0一下的phpstudy     用MYSQL_ASSOC  
​                 8.0以上的 用 MYSQLI_NUM
​                 把结果集$result进行解析：    
​                 $arr = mysqli_fetch_all($result, MYSQL_ASSOC);

​                3、响应结果    
​                把数组的内容解析成json    
​                echo json_encode($arr);

## AJAX

替代浏览器完成和后端的交互，完成异步请求，局部刷新页面，提高用户的体验

​     核心对象：XMLHTTPRequest（完成和后端的交互）



```js
     发送 Ajax 请求的五个步骤：
        • （1）创建异步对象。即 XMLHttpRequest 对象。
         兼容性写法
            1. var xmlhttp;
            2. if (window.XMLHttpRequest)
            3. {
            4.     //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
            5.     xmlhttp=new XMLHttpRequest();
            6. }
            7. else
            8. {
            9.     // IE6, IE5 浏览器执行代码
            10.     xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
            11. }
        • （2）设置请求的参数。包括：请求的方法、请求的url。
        	xhr.open(请求方式，请求的地址，是否异步);
        • （3）发送请求。设置回调函数，onreadystatechange
                    注意： 事件属性 onreadystatechange 全是小写
              xhr.onreadystatechange = function(){
                      xhr.readyState==4  表示请求响应的过程完毕了
                     xhr.status==200：表示后端执行没有问题。
              if(xhr.readyState==4  && xhr.status==200){
                         5、接收响应
                        xhr.responseText;  
                    }
               }
        • （4）注册事件。 onreadystatechange事件，状态改变时就会调用。• 如果要在数据完整请求回来的时候才调用，我们需要手动写一些判断的逻辑。send 方法：发送请求。
             xhr.send();
        • （5）获取返回的数据。responseText
        	xhr.responseText ; 这句话是写在第三步的事件处理函数里。
```


### 案例

验证用户名的存在性

注册

登录

百度搜索框

加载更多

## HTTP

​    http是无状态的；http的默认端口号是：80；https默认端口号是：443；

### cookie的作用

​	和后端的session配合区分不同的客户端

​	本地保存数据

### cookie的使用

保存cookie

保存cookie：document.cookie=键=值;expires=日期gmt格式;path=;domain

获取cookie

document.cookie

删除cookie

保存cookie时，把失效时间写成过去

### cookie的封装

## webStorage（面试题）

   localStorage和sessionStorage

​    纯粹为了本地（浏览器端）保存数据。



## 跨域请求（面试题）

 从其它域名的服务器上获取数据

### 解决方法

#### jsonp

本质：利用script属性的src可以跨域

1、动态创建script创建

2、给script标签的src属性赋值（回调函数和请求参数）

3、添加document.body

4、删除script标签

### 案例

淘宝关键字

## Promise（重点）

解决回调地狱，把异步的回调函数按照同步的写法，一直用then，重点是让调用函数显得好阅读。

### 回调函数

         把函数A作为函数B的参数，那么A函数就是回调函数。
Function是类，和Array，Date是同类型的事物
定义函数就是定义对象，函数名就是对象名（也就是变量名）。
所以，函数名作为参数传入另外一个函数就是可行的，这就是回调函数。
回调的理解：传入函数（对象）的地址，调用函数时，返回去调用，这就是回调的意思

​         如：
function fnA(){
​    console.log("a");
}

function fnB(fn){
    console.log("b");
    fn();
}

fnB(fnA); // 函数fnA作为函数fnB的参数。那么fnA就是回调函数

### 回调地狱

​          层层的回调函数，代码的可阅读性很差，就形成了回调地狱。
​    
​     一直用回调函数，嵌套层级多了后，阅读性很差，如下：

​      fnA(function(){
​          fnB(function(){
​              fnC(fnD);
​          });
​      });

### Promise定义以及应用

 

```
1、创建Promise对象：
let p = new Promise(参数)

2、构造函数Promise的参数是个回调函数，回调函数的参数有两个：resolve，reject
    resolve：是异步操作成功后，调用函数
    reject：是异步操作失败后，调用的函数
如下示例：
let p = new Promise(function(resolve,reject){
    异步操作
});

3、把原来的异步代码放在 回调函数体里（因为Promise是个异步操作）

4、Promise对象的方法：then
       then() 里面的两个参数；
         1)、第一个参数就是异步操作成功时调用的函数
          2）、第二个参数就是异步操作失败时调用的函数
          

5、Promise（改造）异步代码的步骤（使用场景：对于有异步操作并且有回调函数的情况）

   1)、 new Promise
   2）、把异步操作的代码放在构造函数的参数（回调函数）的函数体里
   3）、异步操作代码里的回调函数：如果是成功时调用 的函数，那么用resolve，如果是失败时调用函数用reject
   4）、把Promise对象return出去；
   5）、调用时，then方法的第一个参数就是resolve；第二个参数就是reject。
```

如下示例：

```js
function fnA(){
    console.log("a开始");
    let p = new Promise(function(resolve,reject){
        // 异步操作的代码
        setTimeout(function(){
            console.log("a函数的异步代码");            
            resolve();
        },3000);        
    });    
    console.log("a结束");
    return p;
}
fnA().then(fnB); //fnB就是resolve。
```

## 案例

红绿灯

## async和await（重点）

​      特点： 

​		代码更加简洁    

​		错误处理  

​		解决回调地狱

 回调地狱的终极解决方案，在实际使用中和Promise结合起来，目的是彻底解决回调地狱，比Promise彻底。即就是：把异步的回调变成了同步的写法，async和await是回调地狱的终极解决方案

```js
// 有异步操作

function testf1() {

  return new Promise(function (resolve, reject) {

​    setTimeout(() => {

​      resolve("testf1：两秒钟到了");        

​    }, 2000);

  })

}



// 有异步操作

function testf2() {

  return new Promise(function (resolve, reject) {

​    setTimeout(() => {

​      resolve("testf2：一秒钟到了");        

​    }, 1000);

  })

}



async function fn(){

  // 1、调用testf1

  let str1 = await testf1();

  console.log(str1);

  // 2、调用testf2

  let str2 = await testf2();

  console.log(str2);

}



fn();



/*

function fn(){

  testf1().then(function(str){

​    console.log(str);

​    testf2().then(function(str){

​      console.log(str);

​    });

  })

}

*/
```

```js
 语法:
    async function 函数名()
    {
          await 异步操作
          await 异步操作
    }
  返回值：Promise对象；
  功能：将异步操作按同步操作的方式书写，即上一步未执行完，会阻塞当前函数的进程，不影响主线程
  知识点：
    1）、async：修饰的函数表示函数里面有异步操作，返回值是Promise对象
    2）、await：
       2.1）、一般await后跟 promise对象，或者返回Promise对象的函数；
       2.2）、await 修饰函数后，那么，返回值变成了Promise对象中resolve的参数；
                如 Let res = await fn(); //res是函数fn返回的Promise对象里的resolve的参数。
      2.3）、如果要拿到reject里参数，就使用try catch。
      如：
             try{
                Let res = await fn();  //res是 fn函数里Promise的resolve的参数
            }catch(err){
                  err 是 fn函数里Promise的reject的参数
            }
```


## 闭包（重点）

​         当在函数内部定义了其它函数时，就创建了闭包；闭包有权访问包含函数内部的所有变量；（其实只要函数运行了，就形成了封闭的作用域，就是闭包了）

​			特点：

​			1、 局部作用域空间不被销毁，也就是说让局部变量一直保持在内存中。

​			2、 可以通过闭包语法，从外部访问函数内部变量

​			3、 保护私有变量：私有变量（局部变量）可以被其它函数（闭包）访问，但是不是被所有函数访问。

​			4、父函数里一般需要把闭包作为返回值进行返回

```js
function fnA（）{
        let n = 10;
        function fnB(){
               n++;
               return n;
        }
        return fnB;
}
```



## 构造函数

任何一个函数都可以被new，new了之后，就成了构造方法。

如下：

```javascript
    function Foo(name, age) {
        this.name = name;
        this.age = age;
        //retrun this;   //默认有这一行。new一个构造函数，返回一个对象

    }

    var fn1 = new Foo('smyhvae', 26);
    var fn2 = new Foo('vae',30);    //new 多个实例对象
```

与普通函数相比，构造函数有以下明显特点：

- 用new关键字调用。

- 不需要用return显式返回值的，默认会返回this，也就是新的实例对象。

- 建议函数名的首字母大写，与普通函数区分开。

参考链接：

- [JavaScript中的普通函数与构造函数](http://www.cnblogs.com/SheilaSun/p/4398881.html)

当new之后，this会先变成一个空对象，然后通过`this.name = name`来赋值。

### 构造函数的扩展

![](http://img.smyhvae.com/20180306_1633.png)

上图中发现，数组、对象、函数也有构造函数，它们的构造函数是Array、Object、funtion。实际开发中，都推荐前面的书写方式。

## 原型规则

原型规则是学习原型链的基础。原型规则有五条，下面来讲解。

### 规则1

所有的引用类型（数组、对象、函数），都具有对象特性，都可以**自由扩展属性**。null除外。

举例：

![](http://img.smyhvae.com/20180306_1651.png)


### 规则2

所有的**引用类型**（数组、对象、函数），都有一个`_proto_`属性，属性值是一个**普通的对象**。`_proto_`的含义是隐式原型。

![](http://img.smyhvae.com/20180306_1656.png)

其实，规则2是规则1的特例，只不过，js语法帮我们自动加了 规则2。

### 规则三

所有的**函数**（不包括数组、对象），都有一个`prototype`属性，属性值是一个**普通的对象**。`prototype`的含义是**显式原型**。（实例没有这个属性）

![](http://img.smyhvae.com/20180306_1659.png)


### 规则四

所有的**引用类型**（数组、对象、函数），`_proto_`属性指向它的**构造函数**的`prototype`值。

![](http://img.smyhvae.com/20180306_1701.png)

总结：以上四条，要先理解清楚，然后再来看下面的第五条。

### 规则五

当试图获取一个对象的某个属性时，如果这个对象本身没有这个属性，那么会去它的`_proto_`中寻找（即它的构造函数的`prototype`）。

`举例代码1`：

```javascript
    //创建方法
    function Foo(name) {
        this.name = name;
    }

    Foo.prototype.alertName = function () {// 既然 Foo.prototype 是普通的对象，那也允许给它添加额外的属性 alertName
        console.log(this.name);
    }


    var fn = new Foo('smyhvae');
    fn.printName = function () {
        console.log(this.name);
    }

    //测试
    fn.printName();   //输出结果：smyhvae
    fn.alertName(); //输出结果：smyhvae
```

上方代码中，虽然 alertName 不是 fn 自身的属性，但是会从它的构造函数的`prototype`里面找。

**扩展：**遍历循环对象自身的属性

我们知道，`for ... in`循环可以遍历对象。针对上面的那个fn对象，它自身有两个属性：`name`、`printName`，另外从原型中找到了第三个属性`alertName`。现在，如果我们对fn进行遍历，能遍历到两个属性还是三个属性呢？

答案：两个。因为，**高级浏览器中已经在 `for ... in`循环中屏蔽了来自原型的属性。但是，为了保证代码的健壮性，我们最好自己加上判断**，手动将第三个属性屏蔽掉：

```javascript
    for (var item in fn) {
        if (fn.hasOwnProperty(item)) {
            console.log(item);
        }
    }

```


## 原型链

还是拿上面的``举例代码1``举例，如果此时在最后面加一行代码：

```
	fn.toString();   //去 fn._proto_._proto_ 中查找 toString()方法
```

上面的代码中，fn直接调用了 toString()方法，这是因为它通过**原型链**，去`_proto_`的`_proto_`里找到了`Object`，而`Object`是由`toString()`方法的。

### instanceof

格式：

```javascript
	对象 instanceof 构造函数
```

`instanceof`的作用：用于判断**引用类型**属于哪个**构造函数**。

例1：判断一个变量是否为数组： `变量 instanceof Array`

例2：

```javascript
    function Person(){
    }

    //p--->Person.prototype--->Object.prototype--->null
    var p = new Person();
    //构造函数的**原型**是否在 p 对象的原型链上！
    console.log(p instanceof Person);
```

例3：

```javascript
	fn instanceof Foo
```

上面这句话，判断逻辑是：**fn 的`_proto_`一层一层往上找，看能否对应到 Foo.prototype**。

原型链如下：（重要）

![](http://img.smyhvae.com/20180306_1853.png)


注意，Object这个构造方法的显式原型是null，这是一个特例。


## 常见题目

- 如何准确判断一个变量时数组类型

- 写一个原型链继承的例子

- 描述 new 一个对象的过程

- zepto(或其他框架)源码中如何使用原型链

下面分别讲解。

### 题目一：如何准确判断一个变量时数组类型

答案：

```javascript
    var arr1 = [];

    console.log(arr1 instanceof Array); //打印结果：true。
    console.log(typeof arr1);           //打印结果：object。提示：typeof 方法无法判断是否为数组
```

上方代码表明，只能通过 instanceof 来判断是否为数组。而 typeof 的打印结果是 object。

### 题目二：写一个原型链继承的例子

来看个基础的代码：

![](http://img.smyhvae.com/20180306_1931.png)

上面这个例子是基础，但是，在回答面试官的问题时，不要写上面的例子。要写成下面这个例子：（更贴近实战）

**举例：**写一个封装DOM查询的例子

> 这个例子有点像 jQuery 操作DOM节点。

表示这个例子，略难。

### 题目三：描述 new 一个对象的过程

（1）创建一个新对象

（2）this 指向这个新对象

（3）执行代码（对this 赋值）

（4）返回this

## 继承(ES6、重点)

​	1、子类**自动拥有**父类**的属性和方法。即父类里的属性和方法，在子类里可以直接使用

​    2、 提高了代码的复用性

### 原型（链）继承

​       原型继承：子类的prototype属性指向父类的实例（对象），就完成了原型继承；

​       原型链继承：B类的prototype属性指向A类的实例（对象），C类的prototype属性指向B类的实例（对象），以此类推，就是原型链



​    **注意点：**

 1）、先完成继承关系，再增加子类的prototype方法（子类特有的方法）

​    因为，完成继承关系时，是给prototype属性赋值（改变prototype的指向），那么前面写的prototype属性的内容就全部被覆盖了

 2）、给子类增加prototype方法时，不要使用json的方式，因为使用json的方式，也会改变prototype的指向，那么，继承就失效了      



​        **缺点：**

​       在new子类时，没法给父类的属性赋值（没法传递父类的属性）；导致，每次new出来的子类对象的父类属性值是一样的。



### call和apply继承

​      call继承：就是在子类的构造函数里用call的方式调用父类的构造函数，并且传递参数：

  function Person(id,name){

​        this.id = id;

​        this.name = name;

}

function Programmer(id,name,computeLanguage){

​     用call继承:是在调用父类的构造函数，那么就会继承构造函数里写的属性和方法

​    **Person.call(this,id,name); 这句话表达的意思是：this.Person(id,name);** 

​    this.computeLanguage = computeLanguage;    

}



### 组合继承（把原型链和call（apply）的继承结合起来）

1）、call完成的是父类构造函数里的属性的继承

2）、prototype完成的是父类原型上的方法的继承



function Person(id,name){

​    if(arguments.length>0){

​        this.id = id;

​        this.name = name;

​    }

}

Person.prototype.eat = function(str){

​    console.log(this.name+"在吃"+str);

}



function Programmer(id,name,computeLanguage){

​     用call继承:是在调用父类的构造函数，那么就会继承构造函数里写的属性和方法

​    Person.call(this,id,name); 这句话表单的意思是：this.Person(id,name); 

​    this.computeLanguage = computeLanguage;    

}

 原型继承：继承的是父类的原型属性上的方法；

Programmer.prototype = new Person();

Programmer.prototype.writeCode = function(){

​    console.log(this.name+"用"+this.computeLanguage+"在敲代码");

}

let p1 = new Programmer("001","张三疯","javascript");

console.log(p1.name);

p1.eat("方便面");

### ES6的继承

 ES6继承的关键字：extends。    extends在英文中就是扩展的意思。即子类是在父类的基础上进行的扩展

 ES6继承时，子类的构造函数里需要用super调用父类的构造函数，而且super必须写在子类构造函数里的第一行。

ES6的写法就是ES5（ES3）写法的语法糖



 父类：

class Person{

​    constructor(id,name){

​        this.id = id;

​        this.name = name;

​    }

​    eat(str){

​        console.log(this.name+"在吃"+str);

​    }

}



 子类

class Programmer extends Person{

​    constructor(id,name,computeLanguage){

​        super(id,name);调用父类的构造函数 ，即先把人造出来。

​        this.computeLanguage = computeLanguage; 给人加一个属性computeLanguage，那么人就成了程序员了。

​    } 

​    writeCode(){

​        console.log(this.name+"用"+this.computeLanguage+"在敲代码");

​    }

}







### call、apply、bind的区别（面试题）

	相同点：apply、call、bind 都是可以改变 this 的指向的，
	不同点： 唯一不同的是，call 调用多个参数时  一个参数是 this对象 之后的参数才是正真要调用的参数  参数可以是多个，是以传统列表的方式，进行排列的 ，    
	 apply 方法与call 方法类似  只是 调用真正的参数时 是以数组的形式调用的 ,数组也可以用arguments,切参数只有两个 
	 bind和call 方法的区别是  bind返回的是一个函数，所以要调用
	 
	 1、改变this指向：
	 	call和apply变大的意思是一样的，只是临时改变一次
	 	bind:永久绑定
	 2、调用bind和调用call和apply的区别
	 	调用call函数，就是在调用原函数本身
	 	调用bind函数，并不是原函数，二十完成了函数和对象的绑定，并且尝试一个新的函数（里面的this就是绑定的对象）


## 面试题：深拷贝和浅拷贝

浅拷贝：浅拷贝的意思就是只复制引用，而未复制真正的值。

深拷贝：深拷贝就是对目标的完全拷贝，不像浅拷贝那样只是复制了一层引用，就连值也都复制了。

只要进行了深拷贝，它们老死不相往来，谁也不会影响谁

目前实现深拷贝的方法不多，主要是两种：

1. 利用 `JSON` 对象中的 `parse` 和 `stringify`
2. 利用递归来实现每一层都重新创建对象并赋值



总结：

1. 赋值运算符 `=` 实现的是浅拷贝，只拷贝对象的引用值；
2. JavaScript 中数组和对象自带的拷贝方法都是“首层浅拷贝”；
3. `JSON.stringify` 实现的是深拷贝，但是对目标对象有要求；
4. 若想真正意义上的深拷贝，请递归



所谓拷贝，就是赋值。把一个变量赋给另外一个变量，就是把变量的内容进行拷贝。把一个对象的值赋给另外一个对象，就是把一个对象拷贝一份

1、基本数据类型赋值时，不存在深拷贝和浅拷贝的问题，因为赋得值使数据。

2、引用类型赋值时，赋的值地址（就是引用类型变量在内存中保存的内容）



## 自运行函数

var f = function(){

return "hi"

}

let str = f();

相当于

let str = (function(){

return "hi";

})();

# 设计模式（重点）

## 设计模式的概念



​            设计模式并没有新的知识点，因为，设计模式是前人**总结的经验**：**针对某种特定场景，类应该如何去写**；总结起来，进行统一编目。那这就是设计模式。

​        

​             常见的有23中设计模式



## 单例模式

​    单例模式的场景：在某些项目里，**某些类只能创建一个实例（对象）**。

​        1、把构造函数放在一个自运行函数里，防止构造函数被随意 调用。

​        2、自运行函数返回一个对象（该对象里 函数控制着构造函数的调用）

​        解释：自运行的目的是，保证函数只被调用一次，那么就能保证局部变量instance被定义一次。



let singleton = (function(){

​    // 把构造函数放在另外一个函数内部，不让外部随便调用

​    function ChairMan(name,sex){

​        this.name = name;

​        this.sex = sex;

​    }

​    let instance; //就是用来保存单例对象的。

​    return {

​        getInstance:function(name,sex){

​            if(instance==undefined){

​                instance = new ChairMan(name,sex);

​            }

​            return instance;

​        }

​    }

})(); 

## 观察者模式

1、观察者模式：又叫发布订阅模式。

2、使用场景：

**发布订阅模式一般使用在广播，有若干个订阅者和一个发布者**

 1）、先添加若干个订阅者

 2）、当有数据发生变化时，会把变化发布（通知）给所有的订阅值

### 案例

数据绑定

## 组合模式

1、组合模式：组合模式是的程序员对于单个对象和组合对象的使用具有一致性。

​         组合模式是一种专门为创建Web上的动态用户界面而量身制定的模式。使用这种模式可以用一条命令(函数)在多个对象上激发复杂的或**递归**的行为。这可以简化粘合性代码，使其更容易维护，而那些复杂行为则被委托给各个对象

2、使用场景：**树形结构（DOM）,即：部分与整体的层次结构**。

​                         如：web开发时的菜单。

### 案例

web页面菜单

## JQuery

### jQuery 的两大特点

（1）**链式编程**：比如`.show()`和`.html()`可以连写成`.show().html()`。

链式编程原理：return this。

通常情况下，只有设置操作才能把链式编程延续下去。因为获取操作的时候，会返回获取到的相应的值，无法返回 this。

（2）**隐式迭代**：隐式 对应的是 显式。隐式迭代的意思是：在方法的内部会为匹配到的所有元素进行循环遍历，执行相应的方法；而不用我们再进行循环，简化我们的操作，方便我们调用。

如果获取的是多元素的值，大部分情况下返回的是第一个元素的值。

### 使用 jQuery 的基本步骤

（1）引包

（2）入口函数

原生 js 的入口函数指的是：`window.onload = function() {};` 如下：

```js
        //原生 js 的入口函数。页面上所有内容加载完毕，才执行。
        //不仅要等文本加载完毕，而且要等图片也要加载完毕，才执行函数。
       window.onload = function () {
           alert(1);
       }
```

而 jQuery的入口函数，有以下几种写法：

写法一：

```js
       //1.文档加载完毕，图片不加载的时候，就可以执行这个函数。
       $(document).ready(function () {
           alert(1);
       })
```

写法二：（写法一的简洁版）

```js
       //2.文档加载完毕，图片不加载的时候，就可以执行这个函数。
       $(function () {
           alert(1);
       });
```

写法三：

```js
       //3.文档加载完毕，图片也加载完毕的时候，在执行这个函数。
       $(window).ready(function () {
           alert(1);
       })
```

（3）功能实现代码（事件处理）

**jQuery入口函数与js入口函数的区别**：

区别一：书写个数不同：

- Js 的入口函数只能出现一次，出现多次会存在事件覆盖的问题。
- jQuery 的入口函数，可以出现任意多次，并不存在事件覆盖问题。

区别二：执行时机不同

- Js的入口函数是在**所有的文件资源加载**完成后，才执行。这些**文件资源**包括：页面文档、外部的js文件、外部的css文件、图片等。
- jQuery的入口函数，是在文档加载完成后，就执行。文档加载完成指的是：DOM树加载完成后，就可以操作DOM了，不用等到所有的**外部资源**都加载完成。

文档加载的顺序：从上往下，边解析边执行。

### js中的DOM对象 和 jQuery对象 比较（重点，难点）

通过 jQuery 获取的元素是一个**数组**，数组中包含着原生JS中的DOM对象。举例：

针对下面这样一个div结构：

```js
<div></div>
<div class="box"></div>
<div id="box"></div>
<div class="box"></div>
<div></div>
```

通过原生 js 获取这些元素节点的方式是：

```js
    var myBox = document.getElementById("box");           //通过 id 获取单个元素
    var boxArr = document.getElementsByClassName("box");  //通过 class 获取的是数组
    var divArr = document.getElementsByTagName("div");    //通过标签获取的是数组
```

通过 jQuery 获取这些元素节点的方式是：（获取的都是数组）

```js
    //获取的是数组，里面包含着原生 JS 中的DOM对象。
    var jqBox1 = $("#box");
    var jqBox2 = $(".box");
    var jqBox3 = $("div");
```

**总结**：jQuery 就是把 DOM 对象重新包装了一下，让其具有了 jQuery 方法。

### 二者的相互转换

**1、 DOM 对象 转为 jQuery对象**：

```
	$(js对象);
```

举例：（拿上一段的代码举例）

```js
	//转换。
	jqBox1 = $(myBox);
	jqBox2 = $(boxArr);
	jqBox3 = $(divArr);
```

DOM 对象转换成了 jquery 对象之后，上面的功能可以直接调用。

**2、jQuery对象 转为 DOM 对象**：

```js
	jquery对象[index];      //方式1（推荐）

	jquery对象.get(index);  //方式2
```

jQuery对象转换成了 DOM 对象之后，可以直接调用 DOM 提供的一些功能。如：

```js
    //jquery对象转换成 DOM 对象之后
    jqBox3[0].style.backgroundColor = "black";
    jqBox3.get(4).style.backgroundColor = "pink";
```

**总结**：如果想要用哪种方式设置属性或方法，必须转换成该类型。

### 案例

#### 隔行变色

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <script src="jquery-1.11.1.js"></script>
    <script>
        //入口函数
        jQuery(function () {
            var jqLi = $("li");
            for (var i = 0; i < jqLi.length; i++) {
                if (i % 2 === 0) {
                    //jquery对象，转换成了js对象
                    jqLi[i].style.backgroundColor = "pink";
                } else {
                    jqLi[i].style.backgroundColor = "yellow";
                }
            }
        });
    </script>
</head>
<body>
<ul>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
</ul>
</body>
</html>
```

### jQuery 选择器

### 案例

#### 鼠标悬停时，弹出下拉菜单【重要】

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }

        ul {
            list-style: none;
        }

        .wrap {
            width: 330px;
            height: 30px;
            margin: 100px auto 0;
            padding-left: 10px;
            background-color: pink;
        }

        .wrap li {
            background-color: yellowgreen;
        }

        .wrap > ul > li {
            float: left;
            margin-right: 10px;
            position: relative;
        }

        .wrap a {
            display: block;
            height: 30px;
            width: 100px;
            text-decoration: none;
            color: #000;
            line-height: 30px;
            text-align: center;
        }

        .wrap li ul {
            position: absolute;
            top: 30px;
            display: none;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        //入口函数
        $(document).ready(function () {
            //需求：鼠标放入一级li中，让他里面的ul显示。移开隐藏。
            var jqli = $(".wrap>ul>li");

            //绑定事件
            jqli.mouseenter(function () {
                //这个位置用到了this.
                // console.log(this);  //打印结果是js中的dom对象。注意：jquery对象绑定的事件中，this指js中的dom对象。【重要】

                //让this中的ul显示出来。
//                原生 js 的做法是：this.children[1].style.display = "block";
                //把js的dom对象包装为jquery对象，然后用jquery方法操作
                $(this).children("ul").show();
            });

            //绑定事件：鼠标移开时，隐藏下拉菜单
            jqli.mouseleave(function () {
                $(this).children("ul").hide();
            });
        });
    </script>

</head>
<body>
<div class="wrap">
    <ul>
        <li>
            <a href="javascript:void(0);">一级菜单1</a>
            <ul>
                <li><a href="javascript:void(0);">二级菜单1</a></li>
                <li><a href="javascript:void(0);">二级菜单2</a></li>
                <li><a href="javascript:void(0);">二级菜单3</a></li>
            </ul>
        </li>
        <li>
            <a href="javascript:void(0);">一级菜单1</a>
            <ul>
                <li><a href="javascript:void(0);">二级菜单1</a></li>
                <li><a href="javascript:void(0);">二级菜单2</a></li>
                <li><a href="javascript:void(0);">二级菜单3</a></li>
            </ul>
        </li>
        <li>
            <a href="javascript:void(0);">一级菜单1</a>
            <ul>
                <li><a href="javascript:void(0);">二级菜单1</a></li>
                <li><a href="javascript:void(0);">二级菜单2</a></li>
                <li><a href="javascript:void(0);">二级菜单3</a></li>
            </ul>
        </li>
    </ul>
</div>
</body>
</html>
```

##### **this的用法：**

上方代码中，核心的一行代码是：

```js
	$(this).children("ul").show();

	$(this).children("ul").hide();
```

如果我把这行代码中的this直接写成 DOM对象：

```js
	jqli.children("ul").show();

	jqli.children("ul").hide();
```

当点击某一个ul时其它的都显示了

两张图的对比，可以看出this的作用：谁正在调用函数，this就指的是谁。

#### 鼠标悬停时变色

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <script src="jquery-1.11.1.js"></script>
    <script>
        $(function () {

            //需求；隔行变色；鼠标悬停时，还要变色。
            var jqli1 = $("li:odd");
            var jqli2 = $("li:even");
            jqli1.css("background", "#cccccc");
            jqli2.css("background", "white");

            //鼠标悬停时变色
            var color = "";
            $("li").mouseenter(function () {
                color = $(this).css("background");  //先把之前的颜色保存下来，鼠标离开时还原
                $(this).css("background", "green");
            });
            //鼠标离开时，恢复为原来的颜色
            $("li").mouseleave(function () {
                $(this).css("background", color);
            });
        });
    </script>
</head>
<body>

<ul>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
    <li>生命壹号，永不止步</li>
</ul>

</body>
</html>
```

#### 突出显示

要求：鼠标悬停时，突出显示这个li，让其他的li都半透明。

用 jQuery的选择起来实现，会发现非常方便。

完整版代码如下：

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }

        ul {
            list-style: none;
        }

        body {
            background: #000;
        }

        .wrap {
            margin: 100px auto 0;
            width: 630px;
            height: 394px;
            padding: 10px 0 0 10px;
            background: #000;
            overflow: hidden;
            border: 1px solid #fff;
        }

        .wrap li {
            float: left;
            margin: 0 10px 10px 0;

        }

        .wrap img {
            display: block;
            border: 0;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        jQuery(window).ready(function () {
            //需求：鼠标放入li中，其他的li半透明，当前盒子的opacity值为1
            $(".wrap").find("li").mouseenter(function () {
                //链式编程
                $(this).css("opacity", 1).siblings("li").css("opacity", 0.4);
            });

            //离开wrap的时候所有的li的全部opacity值为1；
            $(".wrap").mouseleave(function () {
                $(this).children().children("li").css("opacity", 1);
//                $(".wrap li").css("opacity",1);
            });
        });
    </script>
</head>
<body>
<div class="wrap">
    <ul>
        <li><a href="#"><img src="images/01.jpg" alt=""/></a></li>
        <li><a href="#"><img src="images/02.jpg" alt=""/></a></li>
        <li><a href="#"><img src="images/03.jpg" alt=""/></a></li>
        <li><a href="#"><img src="images/04.jpg" alt=""/></a></li>
        <li><a href="#"><img src="images/05.jpg" alt=""/></a></li>
        <li><a href="#"><img src="images/06.jpg" alt=""/></a></li>
    </ul>
</div>
</body>
</html>
```

注意这里的css布局里，每一个图片都用一个li来存放。设置li的父亲的宽度之后，然后将li设置为浮动，即可自适应地排列成两排

#### 手风琴效果

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {padding: 0;margin: 0;}
        ul { list-style-type: none;}

        .parentWrap {
            width: 200px;
            text-align:center;

        }

        .menuGroup {
            border:1px solid #999;
            background-color:#e0ecff;
        }

        .groupTitle {
            display:block;
            height:20px;
            line-height:20px;
            font-size: 16px;
            border-bottom:1px solid #ccc;
            cursor:pointer;
        }

        .menuGroup > div {
            height: 200px;
            background-color:#fff;
            display:none;
        }

    </style>
    <script src="jquery-1.11.1.min.js"></script>
    <script>
        $(function () {
            //需求：鼠标点击span，让他下面的div显示出来。让其他的div隐藏。
            $(".parentWrap span").click(function () {
//                $(this).next().show();
//                //让其他的隐藏
//                //点击的span的父亲li，的所有的兄弟元素li，的孩子元素div全部隐藏。
//                $(this).parent("li").siblings("li").children("div").hide();
                //连式编程
                $(this).next().show().parent("li").siblings("li").find("div").hide();
            });
        })
    </script>
</head>
<body>
<ul class="parentWrap">
    <li class="menuGroup">
        <span class="groupTitle">标题1</span>
        <div>我是弹出来的div1</div>
    </li>
    <li class="menuGroup">
        <span class="groupTitle">标题2</span>
        <div>我是弹出来的div2</div>
    </li>
    <li class="menuGroup">
        <span class="groupTitle">标题3</span>
        <div>我是弹出来的div3</div>
    </li>
    <li class="menuGroup">
        <span class="groupTitle">标题4</span>
        <div>我是弹出来的div4</div>
    </li>
</ul>
</body>
</html>
```

#### 淘宝精品服饰广告

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
            font-size: 12px;
        }

        ul {
            list-style: none;
        }

        a {
            text-decoration: none;
        }

        .wrapper {
            width: 298px;
            height: 248px;
            margin: 100px auto 0;
            border: 1px solid pink;
            overflow: hidden;
        }

        #left, #center, #right {
            float: left;
        }

        #left li, #right li {
            background: url(images/lili.jpg) repeat-x;
        }

        #left li a, #right li a {
            display: block;
            width: 48px;
            height: 27px;
            border-bottom: 1px solid pink;
            line-height: 27px;
            text-align: center;
            color: black;
        }

        #left li a:hover, #right li a:hover {
            background-image: url(images/abg.gif);
        }

        #center {
            border-left: 1px solid pink;
            border-right: 1px solid pink;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        jQuery(function () {
            //需求：鼠标放入两侧的li中，让中间的ul中对应索引值的li显示出来，其他的隐藏。（右侧的li要+9）
            //左侧先绑。获取绑mouseenter
            $("#left li").mouseenter(function () {
                //显示对应索引值的中间的li
                //alert($(this).index());  获取索引值
                $("#center li").eq($(this).index()).show().siblings("li").hide();
            });

            //右侧
            $("#right li").mouseenter(function () {
                //显示对应索引值的中间的li
                //alert($(this).index());  获取索引值
                $("#center li:eq(" + ($(this).index() + 9) + ")").show().siblings("li").hide();
            });
        });
    </script>
</head>
<body>
<div class="wrapper">

    <ul id="left">
        <li><a href="#">女靴</a></li>
        <li><a href="#">雪地靴</a></li>
        <li><a href="#">冬裙</a></li>
        <li><a href="#">呢大衣</a></li>
        <li><a href="#">毛衣</a></li>
        <li><a href="#">棉服</a></li>
        <li><a href="#">女裤</a></li>
        <li><a href="#">羽绒服</a></li>
        <li><a href="#">牛仔裤</a></li>
    </ul>
    <ul id="center">
        <li><a href="#"><img src="images/女靴.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/雪地靴.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/冬裙.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/呢大衣.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/毛衣.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/棉服.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/女裤.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/羽绒服.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/牛仔裤.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/女包.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/男包.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/登山鞋.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/皮带.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/围巾.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/皮衣.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/男毛衣.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/男棉服.jpg" width="200" height="250"/></a></li>
        <li><a href="#"><img src="images/男靴.jpg" width="200" height="250"/></a></li>
    </ul>
    <ul id="right">
        <li><a href="#">女包</a></li>
        <li><a href="#">男包</a></li>
        <li><a href="#">登山鞋</a></li>
        <li><a href="#">皮带</a></li>
        <li><a href="#">围巾</a></li>
        <li><a href="#">皮衣</a></li>
        <li><a href="#">男毛衣</a></li>
        <li><a href="#">男棉服</a></li>
        <li><a href="#">男靴</a></li>
    </ul>
</div>
</body>
</html>
```

### 动画

jQuery提供的一组网页中常见的动画效果，这些动画是标准的、有规律的效果；同时还提供给我们了自定义动画的功能。

#### 举例

解释：通过控制元素的宽高、透明度、display属性，逐渐显示，2秒后显示完毕。

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 300px;
            height: 300px;
            display: none;
            background-color: pink;
        }
    </style>

    <script src="jquery-1.11.1.js"></script>
    <script>
        $(function () {
            //点击按钮后产生动画
            $("button:eq(0)").click(function () {

                //滑入动画： slideDown(毫秒值，回调函数[显示完毕执行什么]);
                $("div").slideDown(2000, function () {
                    alert("动画执行完毕！");
                });
            })

            //滑出动画
            $("button:eq(1)").click(function () {

                //滑出动画：slideUp(毫秒值，回调函数[显示完毕后执行什么]);
                $("div").slideUp(2000, function () {
                    alert("动画执行完毕！");
                });
            })

            $("button:eq(2)").click(function () {
                //滑入滑出切换（同样有四种用法）
                $("div").slideToggle(1000);
            })

        })
    </script>
</head>
<body>
<button>滑入</button>
<button>滑出</button>
<button>切换</button>
<div></div>

</body>
</html>
```

```js
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            width: 300px;
            height: 300px;
            display: none;
            /*opacity: 1;*/
            background-color: pink;
        }
    </style>

    <script src="jquery-1.11.1.js"></script>
    <script>
        $(function () {
            //点击按钮后产生动画
            $("button:eq(0)").click(function () {
//                //淡入动画用法1:   fadeIn();   不加参数
                $("div").fadeIn();

//                //淡入动画用法2:   fadeIn(2000);   毫秒值
//                $("div").fadeIn(2000);
//                //通过控制  透明度和display

                //淡入动画用法3:   fadeIn(字符串);   slow慢：600ms   normal正常:400ms   fast快：200ms
//                $("div").fadeIn("slow");
//                $("div").fadeIn("fast");
//                $("div").fadeIn("normal");

                //淡入动画用法4:   fadeIn(毫秒值，回调函数[显示完毕执行什么]);
//                $("div").fadeIn(5000,function () {
//                    alert("动画执行完毕！");
//                });
            })

            //滑出动画
            $("button:eq(1)").click(function () {
//                //滑出动画用法1:   fadeOut();   不加参数
//                $("div").fadeOut();

//                //滑出动画用法2:   fadeOut(2000);   毫秒值
//                $("div").fadeOut(2000);  //通过这个方法实现的：display: none;
//                //通过控制  透明度和display

                //滑出动画用法3:   fadeOut(字符串);   slow慢：600ms   normal正常:400ms   fast快：200ms
//                $("div").fadeOut("slow");
//                $("div").fadeOut("fast");
//                $("div").fadeOut("normal");

                //滑出动画用法1:   fadeOut(毫秒值，回调函数[显示完毕执行什么]);
//                $("div").fadeOut(2000,function () {
//                    alert("动画执行完毕！");
//                });
            })

            $("button:eq(2)").click(function () {
                //滑入滑出切换
                //同样有四种用法
                $("div").fadeToggle(1000);
            })

            $("button:eq(3)").click(function () {
                //改透明度
                //同样有四种用法
                $("div").fadeTo(1000, 0.5, function () {
                    alert(1);
                });
            })
        })
    </script>
</head>
<body>
<button>淡入</button>
<button>淡出</button>
<button>切换</button>
<button>改透明度为0.5</button>
<div></div>

</body>
</html>
```

### 自定义动画

```
	$(selector).animate({params}, speed, callback);
```

作用：执行一组CSS属性的自定义动画。

- 第一个参数表示：要执行动画的CSS属性（必选）
- 第二个参数表示：执行动画时长（可选）
- 第三个参数表示：动画执行完后，立即执行的回调函数（可选）

代码举例：

```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        div {
            position: absolute;
            left: 20px;
            top: 30px;
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        jQuery(function () {
            $("button").click(function () {
                var json = {"width": 500, "height": 500, "left": 300, "top": 300, "border-radius": 100};
                var json2 = {
                    "width": 100,
                    "height": 100,
                    "left": 100,
                    "top": 100,
                    "border-radius": 100,
                    "background-color": "red"
                };

                //自定义动画
                $("div").animate(json, 1000, function () {
                    $("div").animate(json2, 1000, function () {
                        alert("动画执行完毕！");
                    });
                });

            })
        })
    </script>
</head>
<body>
<button>自定义动画</button>
<div></div>
</body>
</html>
```

### 停止动画

```
	$(selector).stop(true, false);
```

**里面的两个参数，有不同的含义。**

第一个参数：

- true：后续动画不执行。
- false：后续动画会执行。

第二个参数：

- true：立即执行完成当前动画。
- false：立即停止当前动画。

PS：参数如果都不写，默认两个都是false。实际工作中，直接写stop()用的多。

**效果演示：**

当第二个参数为true时，效果如下：

[![img](https://camo.githubusercontent.com/30bf585a037fd70fee894bd5f2b0c8f6c4e73313/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313434352e676966)](https://camo.githubusercontent.com/30bf585a037fd70fee894bd5f2b0c8f6c4e73313/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313434352e676966)

当第二个参数为false时，效果如下：

[![img](https://camo.githubusercontent.com/ccd766d3e780945bb19b8ebc2fb316f348ae97bd/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313435302e676966)](https://camo.githubusercontent.com/ccd766d3e780945bb19b8ebc2fb316f348ae97bd/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313435302e676966)

这个**后续动画**我们要好好理解，来看个例子。

**案例：鼠标悬停时，弹出下拉菜单（下拉时带动画）**

```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        * {
            margin: 0;
            padding: 0;
        }

        ul {
            list-style: none;
        }

        .wrap {
            width: 330px;
            height: 30px;
            margin: 100px auto 0;
            padding-left: 10px;
            background-color: pink;
        }

        .wrap li {
            background-color: green;
        }

        .wrap > ul > li {
            float: left;
            margin-right: 10px;
            position: relative;
        }

        .wrap a {
            display: block;
            height: 30px;
            width: 100px;
            text-decoration: none;
            color: #000;
            line-height: 30px;
            text-align: center;
        }

        .wrap li ul {
            position: absolute;
            top: 30px;
            display: none;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        //入口函数
        $(document).ready(function () {
            //需求：鼠标放入一级li中，让他里面的ul显示。移开隐藏。
            var jqli = $(".wrap>ul>li");

            //绑定事件
            jqli.mouseenter(function () {
                $(this).children("ul").stop().slideDown(1000);
            });

            //绑定事件(移开隐藏)
            jqli.mouseleave(function () {
                $(this).children("ul").stop().slideUp(1000);
            });
        });
    </script>

</head>
<body>
<div class="wrap">
    <ul>
        <li>
            <a href="javascript:void(0);">一级菜单1</a>
            <ul>
                <li><a href="javascript:void(0);">二级菜单1</a></li>
                <li><a href="javascript:void(0);">二级菜单2</a></li>
                <li><a href="javascript:void(0);">二级菜单3</a></li>
            </ul>
        </li>
        <li>
            <a href="javascript:void(0);">一级菜单1</a>
            <ul>
                <li><a href="javascript:void(0);">二级菜单1</a></li>
                <li><a href="javascript:void(0);">二级菜单2</a></li>
                <li><a href="javascript:void(0);">二级菜单3</a></li>
            </ul>
        </li>
        <li>
            <a href="javascript:void(0);">一级菜单1</a>
            <ul>
                <li><a href="javascript:void(0);">二级菜单1</a></li>
                <li><a href="javascript:void(0);">二级菜单2</a></li>
                <li><a href="javascript:void(0);">二级菜单3</a></li>
            </ul>
        </li>
    </ul>
</div>
</body>
</html>
```

效果如下：

[![img](https://camo.githubusercontent.com/8958a8336c176d13ccadd502d9d4421aeee2bac1/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313530302e676966)](https://camo.githubusercontent.com/8958a8336c176d13ccadd502d9d4421aeee2bac1/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313530302e676966)

上方代码中，关键的地方在于，用了stop函数，再执行动画前，先停掉之前的动画。

如果去掉stop()函数，效果如下：（不是我们期望的效果）

[![img](https://camo.githubusercontent.com/9378a917b109311df2a7bc604f40582a3514609b/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313530352e676966)](https://camo.githubusercontent.com/9378a917b109311df2a7bc604f40582a3514609b/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230355f313530352e676966)

### stop方法的总结

当调用stop()方法后，队列里面的下一个动画将会立即开始。 但是，如果参数clearQueue被设置为true，那么队列面剩余的动画就被删除了，并且永远也不会执行。

如果参数jumpToEnd被设置为true，那么当前动画会停止，但是参与动画的每一个CSS属性将被立即设置为它们的目标值。比如：slideUp()方法，那么元素会立即隐藏掉。如果存在回调函数，那么回调函数也会立即执行。

注意：如果元素动画还没有执行完，此时调用stop()方法，那么动画将会停止。并且动画没有执行完成，那么回调函数也不会被执行。

#### 举例：右下角的弹出广告

代码实现：

```js
<!DOCTYPE html>
<html>

<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style type="text/css">
        .ad {
            position: fixed;
            right: 0;
            bottom: 0;
            width: 230px;
            height: 120px;
            background-image: url(images/ad.jpg);
            display: none;
        }

        .ad span {
            position: absolute;
            right: 0;
            top: 0;
            width: 40px;
            height: 18px;
            background-image: url(images/h.jpg);
            cursor: pointer;
        }
    </style>
    <script src="jquery-1.11.1.js"></script>
    <script>
        $(function () {
            //需求：然广告ad部分，先滑入，在滑出，在淡入。然后绑定事件，点击span弹出
            //步骤：
            $(".ad").slideDown(1000).slideUp(1000).fadeIn(1000).children("span").click(function () {
                $(this).parent().fadeOut(1000);
            });


            //第二种写法
//            $(".ad").slideDown(1000, function () {
//                $(".ad").slideUp(1000, function () {
//                    $(".ad").fadeIn(1000, function () {
//                        $(".ad").children("span").click(function () {
//                            $(this).parent().fadeOut(1000, function () {
//                                alert("执行完毕！");
//                            });
//                        });
//                    });
//                });
//            })
        })
    </script>
</head>

<body>

<div class="ani">我是内容</div>
<div class="ad">
    <span></span>
</div>

</body>
</html>
```