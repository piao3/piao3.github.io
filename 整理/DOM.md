# DOM知识点  
***
## 定义  
> DOM(文档对象模型(Document Object Model))   

## 分类方式  
> 按层级分  

	父级节点  子级节点  兄弟级节点  
> 按节点类型分  

	1.元素节点
	2.属性节点
	3.文本节点
	8.注释节点
	9.document节点  
	
	注：节点类型与前面的数字是相关联的，不可更改

## 获取元素节点
> children/childNodes 获取指定元素的第一层的所有子节点  

	注：
		1.children 在标准浏览器和IE9下，不会造成空白文本解析，获取到的是真实的子节点。（不支持IE6/7/8）
		2.childNodes 会解析空白文本节点  
> firstChild/firstElementChild 获取指定元素的第一个子节点  

	注：
		1.firstChild 在标准浏览器和IE9下会获取到空白文本节点
		2.firstElementChild 标准下获取第一个子元素节点，IE6/7/8不支持
> lastChild/lastElementChild 获取指定元素的最后一个子节点  

	注：
		1. lastChild 在标准浏览器和IE9下会获取到空白文本节点  
		2.lastElementChild 标准下获取最后一个子元素节点，IE6/7/8不支持  
> previousSibling/previousElementSibling 获取指定元素的上一个兄弟节点  
> nextSibling/nextElementSibling 获取指定元素的下一个兄弟节点  

	注：
		1. previousElementSibling/nextElementSibling 在标准浏览器和IE9下不会获取到空白文本节点  
		2.previousSibling/nextSibling 在标准浏览器和IE9下会获取到空白文本节点  


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

## 操作元素节点
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
	

	