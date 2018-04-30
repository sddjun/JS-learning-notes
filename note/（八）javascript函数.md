函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。JavaScript 使用关键字 function 定义函数。

## 函数声明
函数声明后不会立即执行，会在需要的时候调用到。以下是函数声明的语法：
```
function functionName(parameters) {
	//执行的代码
};
```

## 匿名函数
匿名函数，即函数没有名称。不需要重复使用的函数，可以不需要函数名称，如果将函数存储在变量中，可以通过变量名来调用。
```
var a = function () {};
a();
/* 或 */
documen.getElementById('id').onclick = function(){};
```

## 函数调用
- 正常调用
```
functionName();
```
- 在事件中调用函数
```
documen.getElementById('id').onclick = functionName;
```

