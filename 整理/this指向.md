# <center> this指向</center>  
> this是Javascript语言的一个关键字它代表函数运行时，自动生成的一个内部对象，只能在函数内部使用,随着函数使用场合的不同，this的值会发生变化。但是有一个总的原则，那就是this指的是，调用函数的那个对象。下面分四种情况：  


### 情况一：存粹的函数调用

> #### 这是函数的最通常用法，属于全局性调用，因此this就代表全局对象Global。 
> ##### 请看下面这段代码，它的运行结果是1：
    function test(){ 
        this.x = 1; 
		alert(this.x); 
	} 
	test(); // 结果1 
> ##### 为了证明this就是全局对象，对代码做一些改变： 
	var  x = 1;
    function test(){ 
        this.x = 0; 
		alert(this.x); 
	} 
	test(); // 结果0
	
### 情况二：作为对象方法调用

> #### 函数还可以作为某个对象的方法调用，这时this就指这个上级对象 
> ##### 请看下面这段代码：
    function test(){ 
    	alert(this.x); 
    } 
    var b = {}; 
    b.x = 1; 
    b.m = test; 
    b.m(); // 结果1 
    
### 情况三 作为构造函数调用 
> #### 所谓构造函数，就是通过这个函数生成一个新对象（object）。这时，this就指这个新对象。 
> ##### 请看下面这段代码：
	function test(){ 
		this.x = 1; 
	} 
	var b = new test(); 
	alert(b.x); // 结果1 
> ##### 为了表明这时this不是全局对象，我对代码做一些改变： 
	var x = 2;
	function test(){ 
		this.x = 1; 
	} 
	var b = new test(); 
	alert(x); // 结果2 	
	
### 情况四 作为构造函数调用 
> #### apply()是函数对象的一个方法，它的作用是改变函数的调用对象，它的第一个参数就表示改变后的调用这个函数的对象。因此，this指的就是这第一个参数。call()方法与apply()类似，在这里不举例了；
> ##### 请看下面这段代码：
	var x = 0;
	function test(){ 
		 alert(this.x); 
	} 
	var b = {};
	b.x = 1;
	b.m = test;
	b.m.apply();// 结果0
##### apply()de 参数为空时，默认调用全局对象。因此，这是的运行结果为0，证明this指向的是全局对象。	
> ##### 如果把最后一行代码修改为如下： 
	b.m.apply(b); // 结果1
##### 运行结果就变成了1，证明了这是的this指向变成了对象b。


## 刚才介绍的只是一些普通情况下的this指向，下面介绍一下特殊的，不按常理出牌的this指向
***  

### 通常情况下，this都是指向函数的拥有者。(重要)
	var number = 1;
	var obj = {
		number: 2,
		showNumber: function(){
			this.number = 3;
			(function(){
		　		console.log(this.number);
			})();
    　　		console.log(this.number);
    　　}
    };
    obj.showNumber();
    
##### 这是一道常见面试题。由于showNumber是属于obj对象下的函数，所以this.number = 3，修改的是obj对象下的number属性。第一个console.log（this.number），在函数自执行里面，按理说结果应该是3，因为它是在obj对象下的，但是特殊就特殊在它是函数自执行，在函数自执行里，this指向window，所以结果是1。第二个console.log（this.number）,就是刚刚修改过的number属性，结果为3。
##### ** 注：在定时器里的this也是默认指向window**

#### [this指向问题](http://www.cnblogs.com/lisha-better/p/5684844.html)  
[__proto__和prototype的关系](https://github.com/dreamapplehappy/hacking-with-javascript/blob/master/points/understand-prototype-__proto__.md)  
这两个链接都不错。下次看完继续更新...
    
			
