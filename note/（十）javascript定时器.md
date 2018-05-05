## 定时器的作用
每隔一段时间或者延迟一段时间执行一段指定的代码

## 定时器的类型
#### 重复执行定时器
setTimeout(fn,delay) 每隔指定间隔时间就会执行指定的函数。
- 参数：fn 是要执行的内容；delay 延迟时间，单位毫秒(ms)。
- 返回值：定时器编号。
```
setTimeout(function(){
	console.log(1);  // 代码执行2s后输出1
},2000);
```

#### 间隔型定时器
setInterval(fn,delay) 延迟一段时间执行指定的函数，仅且仅触发一次。
- 参数：fn 是要执行的内容；delay 延迟时间，单位毫秒(ms)。
- 返回值：定时器编号。

```
setInterval(function(){
	console.log(1);  // 每间隔2s输出1
},2000);
```

## 定时器中this指向
在定时器中，setTimeout、setInterval都属于window的内置属性，所以这里的 this 指向window。

## 清除定时器
- 当调用定时器函数后都会返回一个编号，可以使用这个编号停止定时器。
- 清除定时器方法：
    - 清除重复执行定时器：clearInterval(定时器编号)
    - 清除延迟执行定时器：clearTimeout(定时器编号)
- 通过变量存储定时器编号，这样当清除定时器的时候只要知道是清除哪个变量就可以了。
```
var timer = 0;
var num = 0;
timer = setInterval(function(){
    num++;
	console.log(num);  // 输出0,1,2
	if(num == 2){
	    clearInterval(timer);
	}
},2000);
```