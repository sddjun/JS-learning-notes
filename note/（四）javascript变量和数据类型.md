# 变量
变量是js的一种标识符，是一种变化的量，用来储任意类型的数据。
##### （一）变量的声明，变量使用关键字：var 变量名字
```
var name;
```
##### （二）变量的赋值：变量名字 = 变量值
```
var name = "a";
```
##### （三）变量的使用：变量名字
```
var a = 1;
var b = 2;
console.log(a + b);
```
注：使用变量前要先声明，否则程序会报错。

# 数据类型的划分
在js中数据类型的划分有两种方法，一种官方给出的标准划分，还有一种是根据 typeof 运算符来进行划分，并且两种划分还略有不同。
### 标准划分法
标准划分方式可分为两种类型，一种是基础类型，另一种是复合类型。它们的赋值方式有所不同。
- 基础类型数据在赋值过程中，传递的是数值，叫做传值。
```
var a = 0;
var b = a;
a = 3;
console.log(b);  //输出0
```
- 对象在赋值过程中，传递的是内存中的引用地址，叫做传址。
```
var a = [2];
var b = a;
b[0] = 1;
console.log(a);  //输出[1]
```

#### (一)基础类型
- 简单数据类型包括number、string、null、undefined、symbol；
- 简单数据没有自定义属性，也不可以设置自定义属性。
```
var a = "I LOVE YOU";
a.ot = "NO";
console.log(a.ot);  //输出undefined
```
1. 数字类型——Number

在number中包含了我们所有的合法数字，无论小数（浮点数）还是整数。以下是特别要强调的几点：

- js中数字的取值范围，为(-1.7976931348623157e+308, 1.7976931348623157e+308)，当超出取值范围后，用Infinity表示正无穷，-Infinity表示负无穷，它们都属于数字类型。

```
console.log(Number.MAX_VALUE);  //输出1.7976931348623157e+308
console.log(Number.MAX_VALUE*2);  //输出Infinity
console.log(Number.MIN_VALUE);  //输出5e-324
console.log(Number.MIN_VALUE/2);  //输出0
```
- NaN 的数据类型是数字，它是数字中的一个特殊值，表示这不是一个数字，NaN不等于任何值，并且不等于它自己。检测转换后是否是NaN的方法，使用``isNaN()``。

```
console.log(NaN == NaN); //输出false

var a = 1;
var b = 'abc';
console.log(isNaN(a));  //输出true
console.log(isNaN(b));  //输出false
```

2. 字符串类型——String

用一对单引号或者双引号包起来的0个或多个字符组成的串叫做字符串。

- 字符串的长度，使用length属性获取字符串长度、length只能读不能更改；
```
var a = "I LOVE YOU";
console.log(a.length);  //输出10
```
- 取字符串中字符，使用下标或charAt(索引值)方法；
```
var a = "I LOVE YOU";
console.log(a[7]);  //输出Y
console.log(a.charAt(7));  //输出Y
```
- 字符串一旦定义不能更改，想要修改重新开辟空间
- 拼接字符串符号用加号（+）
```
var a = "小明";
var b = "小红";
console.log(a + "和" + b);  //输出"小明和小红"
```
- 查字符串的Unicode编码，使用charCodeAt(索引值)的方法；
```
var str = 'abc';
console.log(str.charCodeAt(0)); // 输出97
console.log(str.charCodeAt(1)); // 输出98
console.log(str.charCodeAt(2)); // 输出99
```
- 根据字符查索引，使用indexOf(要查询的字符串)或lastIndexOf(要查询的字符串)；
- 字符串连接和截取
- 字符串大小写转换
- 去除字符串前后空白，使用trim()；
```
var a = " abc ";
console.log(a.trim());  //输出"abc
```

3. 布尔值——Boolean

表示一个逻辑实体，真=>true，假=>false。

4. 空值——Null

null是一个 JavaScript 字面量，表示空值，获取元素没有获取到的时候，浏览器会返回null。null也被叫做空对象，但是null并不能像对象一样进行属性操作，比如 null.name = "miaov" 这样写的话在浏览器中会报错。
```
console.log(document.getElementById('id')); //找不到，输出null

var a;
console.log(a==null); //输出true
```

5. 未定义——Underfined

undefined 代表未定义，实际上是派生自 null，在比较值的时候是相等的。
- 使用var声明变量未赋值时候，默认值为undefined。
```
var a;
console.log(a); //未赋值，输出underfined
console.log(a==undefined); //输出true
```
- 访问对象的属性不存在时，返回undefined。
```
console.log(window.b); //window的b属性未赋值，输出underfined
```
- 一个函数，如果没有返回值，那么执行之后的结果是undefined。
```
var fn = function(){};
console.log(fn());  //fn函数执行没有返回值，输出underfined
```

6. Symbol

 symbol是ES6新增类型，表示一个匿名且唯一的值。
 - symbol比较值的时候结果为false，因为symbol是唯一的，所以两个不同的实例的比较结果只能是个 false。
```
var a = Symbol();
var b = Symbol();
console.log(a == b); //输出false
```
- symbol的计算结果是匿名的，所以我们在打印的时候，并不能看见它具体的值。
```
console.log(Symbol());  //输出false
```

#### （二️）复合类型(复杂类型)
js中的复合类型只有一种，就是Object (对象)。对象是属性组成的无序集合，属性由”名/值”对构成，对象数据结构的 key 可以是任意的字符串，属性值可以是任意类型。在js中，除了基本数据类型，剩下的都是对象。比如说我们经常使用的 function 函数、Array 数组、{}、window等。

- 对象的分类：
    - 有序集合——数组
```
var arr = [1, 2, 3];
```
    - 可调用对象——函数
```
var arr = ｛
    name: "小明",
    age: "10",
｝;
console.log(arr.name);  //输出小明
```
    - DOM元素
```
var body = document.querySelector('body');
```

- 对象的处理方法
    - valueOf()
    - toString()

### typeof 划分
typeof 是一种一元运算符（操作符），用于检测一个数据的类型，并返回一个表示数据类型的字符串。在 typeof 划分中 js 一共被划分成了 7 种数据类型：number、string、boolean、undefined、symbol、object、function。

typeof划分和标准中定义的区别:
- typeof 中把 null 归为了 object 类型；
- typeof object 检测返回是一个bug
- typeof 函数 为 "function"。函数也是对象，但是它是一个可以被调用的对象，所以很有必要和普通的对象做一个区分。

```
var a = 2;
var b = "bbb"
var c = true
var d;
var e = functon(){};
var f = null;
var g = Symbol();
console.log(typeof a); //输出numbr
console.log(typeof b); //输出string
console.log(typeof c); //输出boolean
console.log(typeof d); //输出underfined
console.log(typeof e); //输出function
console.log(typeof f); //输出object
console.log(typeof g); //输出symbol
```

# 数据转换
把一种数据类型转换成另一种数据类型。在js中，支持转成三种类型，分别是：转数字类型、转字符串类型、转布尔值类型。
## 强制类型转换（显示类型转换）
通过函数或方法调用，明确的将某种类型转换成另一种类型。如：parseInt、parseFloat、Number、Boolean，String……
1. 转成数字

- 调用内置方法Number(val)进行转换，对各个数据类型转换的结果
    - number，原样返回，不转换;
    - string，如果符合数字的规范就转换，否则转换结果为NaN;
    - boolean，参数 true 结果为 1，false 结果为 0；
    - null，返回结果为0；
    - undefined，返回结果为NaN；
    - symbol，直接报错；
    - object，会先调用对象的 valueOf 方法，然后调用的对象的 toString() 方法，然后再次依照前面字符串的转换规则进行转换。

- 调用内置方法 parseInt(string, radix) 进行转换，第一个参数接收的是个字符串，第二个参数接收的是基数，也可以理解为标注出要转换的这个字符串是几进制的数字。
    - 从第一个字符开始，碰到不是数字的字符为止，把是数字的字符转成数字并返回得到的值为整数；
    - 开头和结尾的空格是允许的；
    - 如果字符串的第一个字符不能被转换为数字，那么会返回 NaN。
```
var a = '12px';
var b = 'a12px';
var c = '';
console.log(parseInt(a));  //输出12
console.log(parseInt(b));  //输出NaN
console.log(parseInt(c));  //输出NaN
```
关于基数的注意事项：

在使用 parseInt 的时候，最好设置一下基数，虽然大部分情况下 parseInt 会按照十进制识别我们传入的数据，但是一些特殊的情况下，还是会出问题，示例如下:
```
var a = '0xf';
console.log(parseInt(a));  // 15 这里因 0x是16进制的前缀所以这里识别成了 16 进制的数据，转换结果为 15
var b = "070";
console.log(parseInt(b));  // 新版本为 70，老版本部分浏览器 会识别成 56 因为 0是 八进制的标示，这里按照了八进制进行了处理	
```

- 调用内置方法 parseFloat(string, radix) 进行转换，参数接收的是个字符串，这个方法也叫取浮点数。
    - 规则同 parseInt;
    - 会保留小数部分，如果小数部分为0，则忽略。
```
var a = '12.6cm';
console.log(parseInt(a));  //输出12.6
```

2. 转成字符串
- 调用内置方法 String(val) 进行转换。
    - number，原样返回，不转换;
    - string，原样返回，不转换;
    - boolean，参数 true 结果为 'true'，false 结果为 'false'；
    - null，返回结果为 'null'；
    - undefined，返回结果为 'undefined'；
    - symbol，返回结果为 'Symbol()'；
    - object，直接调用对象的 toString() 方法。

3. 转成布尔值
- 调用内置方法 Boolean(val) 进行转换。
    - number，0 、-0 、 NaN 返回结果为 false，否则返回结果为 true；
    - string，空字符串（其长度为零）返回结果 false ，非空字符串返回结果 true ；
    - null，返回结果为 false；
    - undefined，返回结果为 false；
    - object，返回结果为 true。

## （二）隐式类型转换
为了能够进行必要运算，解析器会自动把要操作的数据进行对应的类型转换，具体转换规则查看javascript的运算符。
```
var a = 0;
var b = '1';
console.log(a - b);  // 输出-1
```

