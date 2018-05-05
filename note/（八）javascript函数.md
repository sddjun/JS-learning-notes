函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。JavaScript 使用关键字 function 来定义函数。

## 函数的作用
函数主要起到封装代码块和复用代码块的作用。

## 函数的完整语法
```
function [函数名]([参数1,参数2,。。。。]){
	// 函数体 代码块
	[return 值]
}
// [] 可选填
```
## 函数定义
#### 函数声明
函数声明后不会立即执行，会在需要的时候调用到。以下是函数声明的语法：
```
function name(parameters) {
	//执行的代码
};
name (); 
```

#### 函数表达式
如果将函数存储在变量中，可以通过变量名来调用，这种定义函数的方式称为函数表达式。
```
var a = function () {};
a();
/* 或 */
documen.getElementById('id').onclick = function(){};
```

## 函数调用
- 直接调用函数，也被成为非事件调用。写法：函数名+()。
```
fn();
```
- 在事件中调用函数，如：el.onclick = 函数名。
```
documen.getElementById('id').onclick = fn;
```
注：函数的每一次调用执行，就相当于新写了一个函数，互不干扰。
```
function fn() {
    var a = 0;
    a++：
    console.log(a);
}
fn();  //输出1
fn();  //输出1
fn();  //输出1
```

## 函数传参
分为形参和实参，他们是一一对应的，以逗号隔开。
- 形参：形参是在函数的内部声明的变量，在定义函数时写在小括号中，默认值为undefined。
- 实参：实际传入函数内部的参数，在调用函数时写在小括号中，把实参赋值。
语法形式如下：
```
function fn(a, b) {
	console.log(a, b)
};
fn(1, 2);  //输出1,2
``` 
###### 什么情况下需要用到传参？
当我们要执行的代码中，有两段（及以上）代码块，功能极其相似，就可以把他们写到一个函数中，然后把不一样的地方抽离出来，使用参数传递进去。

###### arguments 不定参
arguments 叫不定参（可变参），形参个数不固定的情况下使用，它是函数实参的集合、类数组。
```
function fn () {
    console.log(arguments);
}
fn(1, 2, 3, 4);  //输出[1, 2, 3, 4]
```

## 匿名函数
匿名函数即函数没有名称。不需要重复使用的函数，可以不需要函数名称。

#### 匿名函数自执行
在书写中，不建议在全局中定义变量，这样会对全局形成污染。
- 匿名函数自执行写法：
```
(function(){})();   // 下面两种方式兼容性不太好，建议使用这第一种
!function(){}();
~function(){}();
```
- 匿名函数自执行写法的传参
```
// a,b是形参数，1,2是实参
(function(a, b) {
	console.log(a, b);  //输出1,2
})(1 ,2);
```

## 函数返回值
函数的执行结果就是函数的返回值。每个函数被调用之后都会有一个返回值。
- 调用后默认为 undefined；
- 使用 return 函数返回值，给函数定义一个值，在函数执行的时候可以拿到。
- return 只能在函数中使用
- 在函数中 return 之后的代码不再执行
```
function fn () {
    var a = 10;
}
var b = fn();
console.log(b);  //输出undefined

function fn2 () {
    var a = 10;
    return a;
}
var c = fn2();
console.log(c);  //输出10
```

## 预解析
#### var 的预解析
在正常解析之前，会先快速把 script（或function） 中的 var 声明及声明的名字，提升到代码块（作用域）的最前面。

#### function 的预解析
在正常解析之前，会先快速把 script（或function） 中的 function 及内容，提升到代码块（作用域）最前面，跟在 var 声明之后。

预解析之后，js 会再从上往下一行一行去执行。
例题：
```
console.log(a);  //输出函数 function () {var b = 1;}
var a = 10;
console.log(a);  //输出10
function a () {
    var b = 1;
}
console.log(a);  //输出10
var a = function () {
    var b = 2;
}
console.log(a); //输出函数 function () {var b = 2;}
```
预解析之后：
```
var a;
var a;
function a () {
    var b = 1;
}
console.log(a);  //输出函数 function () {var b = 1;}
a = 10;
console.log(a);  //输出10
console.log(a);  //输出10
a = function () {
    var b = 2;
}
console.log(a); //输出函数 function () {var b = 2;}
```

## 函数作用域
作用域，一条数据可以使用的范围。
- 在函数内声明的数据就只能在该函数内部使用，他们的作用域就是这个函数。
- 两个 script 标签之间不会产生作用域，在 js 中唯一会产生作用域的是函数。
```
<script>
var a = 0;
</script>
<script>
console.log(a);  //输出0
</script>
```
### 全局作用域（window）
声明在任何函数之外，那么它可以在全局任何地方被调用和修改，这条数据也叫做全局变量，它的作用范围是全局的，称为全局作用域。
- 声明在任何函数之外，那么它可以在全局任何地方被调用和修改。
- 当一个变量未定义的情况下，js 默认这个变量是属于 window 的，拥有全局作用域。
- window 对象的属性拥有全局作用域，书写的时候可以不写 window.;

### 局部作用据（函数作用域）
声明在函数内部的数据（参数、函数、变量），只能在这个函数内部进行调用和修改，这些数据就叫做这个函数的局部数据（私有数据），对于这些数据他们起作用的范围也只是这个函数内部，这个数据的作用范围是局部的，叫做函数作用域。
```
function fn () {
    a = 10;
    
}
function fn2 () {
    console.log(a);
    
}
fn();
fn2();
```
### [[Scopes]] 函数作用域
函数本身有个内置属性[[Scopes]]。当我们调用这个函数时，就会把声明在这个函数中的所有数据存入这个属性中；当我们在函数中调用数据时，就会去这个属性 [[Scopes]] 查找数据。

## 作用域链
在作用域嵌套的时候，函数中的变量会形成作用域链，即一种查找规则。
- 作用域链的作用：保证执行环境有权访问的所有变量和函数的有序访问。
- 查找标识符：标识符解析是沿着作用域链一级一级搜索的过程，一直搜索到全局作用域。如果找到标识符则能拿到标识符的值；如果找不到标识符就会发生错误。
```
function fn(){
	var a = 0;
	function fn2(){
		console.log(a);
	}
	fn2();
}	
fn();  // 输出0
```

## 闭包
函数嵌套函数时，内层函数可以访问外层函数中的变量，就会形成闭包。
- 当函数嵌套函数时，子函数可以访问父函数作用域链中局部变量，但是 父函数不能访问子函数的局部数据;
- 闭包的应用
```
var btns = document.querySelectorAll('input');
for(var i = 0; i < btns.length; i++){
	toIndex(i);
}
function toIndex(nub){
	btns[nub].onclick = function(){
		console.log(nub);  // 点击按钮输入按钮对应的索引值
	}
}
```

## 函数的一些难懂的写法
- 写法一：
```
function fn () {
    var a = 10;
    return function () {
        return a;
    };
}
var b = fn();
var c = fn()();
console.log(b);  // 输出function () { return a;};
console.log(c);  // 输出10
```
写法二：
```
function fn(){
	var a = 0;  //fn 作用域中的私有数据
	return function (){
		a++;   //本作用域中没有，向父作用(fn)域找
		console.log(a);
	};
}

var b = fn();
b();  //输出1
b();  //输出2
b();  //输出3
```