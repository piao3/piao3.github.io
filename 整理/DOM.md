# DOM知识点  
***
## 1.定义  
> DOM(文档对象模型(Document Object Model))   
是W3C组织推荐的处理可扩展标志语言的标准编程接口。  
 DOM 定义了所有 HTML 元素的对象和属性，以及访问它们的方法。

## 2.分类  
> 按层级分  

	父节点  
	子节点  
	兄弟节点  
> 按节点类型分  

	1.元素节点
	2.属性节点
	3.文本节点
	8.注释节点
	9.document节点  
	
	注：节点类型与前面的数字是意义对应的

## 3.获取  
> children/childNodes 获取指定元素的第一层子节点  

	区别：
		1.children 在标准浏览器和IE9下，不会造成空白文本解析，获取到的是真实的子节点。（不支持IE6/7/8）
		2.childNodes 会解析空白文本节点  
> firstChild/firstElementChild 获取指定元素的第一个子节点  

	区别：
		1.firstChild 在标准浏览器和IE9下会获取到空白文本节点
		2.firstElementChild 标准下获取第一个子元素节点，IE6/7/8不支持
> lastChild/lastElementChild 获取指定元素的最后一个子节点  

	区别：
		1. lastChild 在标准浏览器和IE9下会获取到空白文本节点  
		2.lastElementChild 标准下获取最后一个子元素节点，IE6/7/8不支持  
> previousSibling/previousElementSibling 获取指定元素的上一个兄弟节点  
> nextSibling/nextElementSibling 获取指定元素的下一个兄弟节点  

	区别同上
> parentNode 获取指定元素的父节点  
> offsetParent 获取离指定元素最近的具有定位属性的祖先节点  

	以上两个属性都是把获取到的元素结构整体返回，不仅仅只是返回一个标签  
> 获取元素属性的方式  

	1.元素.属性名
		注意：如果获取的是元素的class的话，在写的时候必须是className，获取不到非标准属性
	2.["属性名"]
	3.getAttribute("属性名")
		注意：可以获取到元素的自定义属性
	4.setAttribute("属性名"，"属性值")  设置元素属性
	5.removeAttribute("属性名")  移除元素属性
	注意:attributes属性能访问到元素上所有的属性,返回的是一个类数组,我们可以通过下标的形式拿到每一个属性。  

## 4.增删改查
> 创建节点

	document.createElement(' ');
> 给指定元素追加子节点  

	appendChild()
> 插入元素  

	insertBefore(插入的元素，参照元素)
> 移除子节点  

	removeChild()
> 替换子节点  

	replaceChild(替换元素，被替换元素)
> 克隆节点  

	cloneNode()  接受一个布尔值作为参数  
	当参数为true时，会克隆元素的innerHTML  
	false不会，默认是false  
> 判断指定元素是否拥有子节点  

	hasChildNodes()  
	返回布尔值true或false  
	
## 5.获取窗口可视区域宽高/页面滚动高度  
> 调整窗口大小时触发的事件  

	window.onresize = function  () {
		
	}
> 获取浏览器窗口可视区域宽度/高度  

	document.documentElement.clientWidth/clientHeight
> 获取页面滚动高度

	document.documentElement.scrollTop

	
## 6.image对象
> 实例化图片对象  

	var img = new Image(width,height);
	接受两个参数 分别代表图片的宽高 直接传数值，不需要加单位
	如果只传一个参数，这个参数表示宽度
	hspace  图片左右的空间(留白)
	vspace  图片上下的空间(留白)
	complete  返回浏览器是否已经完成对图像的加载
> 图片对象事件

	1.onload  图片加载成功时触发的事件
	2.onerror  图片加载失败时触发的事件
	3.onabort  当用户放弃加载时触发的事件
	
###### 强调：因为图片是在给定src之后就开始加载，为了避免图片已经加载出来，但是事件还没来得及执行的极端情况，所以我们一般要把图片src赋值放到最后 

## 7.弹出框
> 1.alert() 如果需要换行的话，用\n  
> 2.confirm() 适用于疑问或者判断 会返回布尔值true或者false  
> 3.prompt() 带输入框的弹出框

## 8.网页重定向
> 1.location.href()

	网页的完整路径 可读可写  是属性
	如：location.href = "https://www.baidu.com";
> 2.location.assign() 

	是方法
	如：location.assign("https://www.baidu.com");
> 3.location.replace()

	是方法
	如：location.replace("https://www.baidu.com")
> 4.location.reload()

	重新加载页面
	可以传递一个参数true,表示绕过缓存，从服务器重新加载 如果不写参数true的话，有可能会从缓存中加载

###### 区别：
	1.location.href()和location.assign()都会产生历史记录，可会退到前一个页面
	2.location.replace()不会产生历史记录，不能后退到前一个页面







	