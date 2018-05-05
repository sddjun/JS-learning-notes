## JavaScript的可以出现的位置
### （一）行间——不建议使用
```
<button onclick="alert(1)">按钮</button>
```
在 a 标签的``href``中也可以写js，href 是 js 内置的 onclick 事件。
```
<a href="javascript:console.log(1);"></a>
```
优点：直接，简单明了。
缺点：可读性差，不易维护，不易扩展。
### （二）内嵌
```
<script type="text/javascript">
	alert("1");	
</script>
```
优点： js和html分离，可以复用代码。
缺点：代码不能多文件使用。
### （三）外链js文件

```
<script type="text/javascript" src="script/index.js"></script>
```
优点：多文件共用

## 注释
#### （一）单行注释

```
// 这是一个单行注释
```
#### （二）多行注释

```
/* 
	这是一个多行注释
*/
```

## 调试检测的方法
##### （一）console方式——全局对象，向控台输出内容
```
console.log(1);
```

##### （二）调试工具——浏览器自带的调试工具，可以方便的调试HTML、js、网络、性能……按快捷键F12可以快速打开。

## 书写案例流程
1. 使用HTML + CSS 布局
2. 对案例进行功能分析，如找到需要修改的样式，排除布局问题，形成基本的思路
3. 开始使用js操作元素编写逻辑

## 标识符
标识符是变量名、常量名、函数名、函数参数名、对象属性名的统称。
##### （一）标识符的命名规则
1. 由数字、字母、下划线和美元符($)组成
2. 首字符不能使数字
3. 不能使用JS的关键字和保留字
##### （二）关键字&保留字
1. 关键字：js语法中正在使用的单词

以下就是ECMAScript的全部关键字（带*号上标的是第5 版新增的关键字）：

关键字 | 关键字 | 关键字 | 关键字
---|---|---|---
break | do | instanceof	 | typeof
case | else | new |	var
catch |	finally | return | void
continue |	for | switch |	while
debugger* | function | this | with
default | if | throw | delete
in | try | |

2. 保留字：将来可能在语法中使用的单词

以下是ECMA-262 第3 版定义的全部保留字：
保留字 | 保留字 | 保留字 | 保留字
---|---|---|---
abstract | enum | int | short
boolean | export | interface | static
byte | extends | long | super
char | final | native | synchronized
class | float | package | throws
const | goto | private | transient
debugger | implements | protected | volatile
double | import | public |

第5 版把在非严格模式下运行时的保留字缩减为下列这些：
保留字 | 保留字 | 保留字 | 保留字
---|---|---|---
class | enum | extends | super
const | export | import	| 

在严格模式下，第5 版还对以下保留字施加了限制：
保留字 | 保留字 | 保留字 | 保留字
---|---|---|---
implements | package | public | interface
private | static | let | protected
yield | | |


##### （三）命名风格
在js中是强制大小写的，命名的大小写不同所表达的东西是不一样的。
1. 驼峰命名法

大驼峰 --- 多个单词组合，从第一单词开始首字母大写（面向对象类的命名）

小驼峰 --- 多个单词组合，从第二单词开始首字母大写（日常使用）

2. 全大写（常量的命名）