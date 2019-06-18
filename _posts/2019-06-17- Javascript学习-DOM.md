---
layout:     post
title:      DOM
subtitle:   Javascript学习
date:       2019-06-17
author:     丁帅
header-img: img/post-bg-js-version.jpg
catalog: true
tags:
    - Javascript
---

# DOM

文档对象模型（Document Object Model），通过DOM可以来任意来修改网页中各个内容。

### 文档

文档指的是网页，一个网页就是一个文档。

### 对象

对象指将网页中的每一个节点都转换为对象
转换完对象以后，就可以以一种纯面向对象的形式来操作网页了
	

### 模型

模型用来表示节点和节点之间的关系，方便操作页面。

### 节点（Node）

节点是构成网页的最基本的单元，网页中的每一个部分都可以称为是一个节点。
虽然都是节点，但是节点的类型却是不同的

#### 常用的节点

1. 文档节点 （Document），代表整个网页
2. 元素节点（Element），代表网页中的标签
3. 属性节点（Attribute），代表标签中的属性
4. 文本节点（Text），代表网页中的文本内容
   	
### DOM操作

#### DOM查询

   在网页中浏览器已经为我们提供了document对象，
   它代表的是整个网页，它是window对象的属性，可以在页面中直接使用。



## innerHTML和innerText

这两个属性并没有在DOM标准定义，但是大部分浏览器都支持这两个属性
两个属性作用类似，都可以获取到标签内部的内容
不同是innerHTML会获取到html标签，而innerText会自动去除标签
如果使用这两个属性来设置标签内部的内容时，没有任何区别的	



#### document查询方法：

#### 通过具体的 元素节点 来查询

1. **根据标签名来查询一组元素节点对象： `document.getElementsByTagName("标签名");`**

   通过标签名查询当前元素的指定后代元素       `元素.getElementsByTagName()`
   


2. **根据元素的class属性值查询一组元素节点对象**

   `getElementsByClassName()`可以根据class属性值获取一组元素节点对象，但是该方法不支持IE8及以下的浏览器
   
   ```
   	var box1 = document.getElementsByClassName("box1");
       console.log(box1.length);
   ```
   
   

​		获取页面中的所有的div

​		

```
var divs = document.getElementsByTagName("div");
```



3. ##### 根据元素的id属性查询一个元素节点对象：`document.getElementById("id属性值");`

4. ##### 根据元素的name属性值查询一组元素节点对象: `document.getElementsByName("name属性值");`

5. **其它的两个方法,　ie 根本就不支持, 所以不建议使用**  

   ```
   			document.getElementsByClassName();
   			document.getElementsByTagNameNS();
   ```

   

3. ##### document.querySelector()

   需要一个选择器的字符串作为参数，可以根据一个CSS选择器来查询一个元素节点对象

   虽然IE8中没有`getElementsByClassName()`但是可以使用`querySelector()`代替

   使用该方法总会返回唯一的一个元素，如果满足条件的元素有多个，那么它只会返回第一个

           var div = document.querySelector(".box1 div");
           var box1 = document.querySelector(".box1");
           console.log(div.innerHTML);
           console.log(box1.innerHTML);

4. ##### document.querySelectorAll()

   该方法和`querySelector()`用法类似，不同的是它会将符合条件的元素封装到一个数组中返回

   即使符合条件的元素只有一个，它也会返回数组

           box1 = document.querySelectorAll(".box1");
           box1 = document.querySelectorAll("#box2");
           console.log(box1);

8. **在document中有一个属性body，它保存的是body的引用**

   ```
   	var body = document.body;
       document.documentElement保存的是html根标签
       var html = document.documentElement;
       console.log(html);
   ```

   

9. **document.all代表页面中所有的元素**

   ```
   	var all = document.all;
       console.log(all.length);
       for(var i=0 ; i<all.length ; i++) {console.log(all[i]);}
   
       all = document.getElementsByTagName("*");
       console.log(all.length);
   ```

   



`元素.childNodes`    			获取当前元素的所有子节点，会获取到空白的文本子节点

`元素.children`        			获取当前元素的所有子元素

`元素.firstChild`    			获取当前元素的第一个子节点

`元素.lastChild`      			获取当前元素的最后一个子节点

`元素.parentNode`    			获取当前元素的父元素

`元素.previousSibling` 	 获取当前元素的前一个兄弟节点

`元素.nextSibling` 			 获取当前元素的后一个兄弟节点



### DOM修改

1. **`document.createElement()`    			可以根据标签名创建一个元素节点对象**

   按照给定的标签名创建一个新的元素节点. 方法只有一个**参数**：被创建的元素节点的名字, 是一个字符串.

   **方法的返回值**：是一个指向新建节点的引用指针. 返回值是一个元素节点, 所以它的 nodeType 属性值等于 1.

   新元素节点不会自动添加到文档里, 它只是一个存在于 JavaScript 上下文的对象.

   

2. **`document.createTextNode() `  			可以根据文本内容创建一个文本节点对象**

   创建一个包含着给定文本的新文本节点. 这个方法的返回值是一个指向新建文本节点引用指针。
   方法只有一个参数：新建文本节点所包含的文本字符串. 新元素节点不会自动添加到文档里



4. **`父节点.appendChild(子节点)`    			向父节点中添加指定的子节点**

   var reference = element.appendChild(newChild): 给定子节点 newChild 将成为给定元素节点 element 的最后一个子节点.
   方法的返回值是一个指向新增子节点的引用指针.	

   

5. **`父节点.insertBefore(新节点,旧节点)`  将一个新的节点插入到旧节点的前边**
   	

   `var reference =  element.insertBefore(newNode,targetNode);`
   节点 newNode 将被插入到元素节点 element 中并出现在节点 targetNode 的前面. 节点 targetNode 必须是 element 元素的一个子节点。
   
```
   自定义 insertAfter() 方法     
   	   /**
   		 * 将 newChild 插入到 refChild 的后边
   		 * @param {Object} newChild
   		 * @param {Object} refChild
   		 */
   		function insertAfter(newChild, refChild){
   			var refParentNode = refChild.parentNode;
   			
   			//判断 refChild 是否存在父节点
   			if(refParentNode){
   				//判断 refChild 节点是否为其父节点的最后一个子节点
   				if(refChild == refParentNode.lastChild){
   					refParentNode.appendChild(newChild);
   				}else{
   					refParentNode.insertBefore(newChild, refChild.nextSibling);
   				}	
   			}
   		}
   ```
   
      	
   
6. **`父节点.replaceChild(新节点,旧节点)`  使用一个新的节点去替换旧节点**
    	
    replaceChild(): 把一个给定父元素里的一个子节点替换为另外一个子节点
    `var reference = element.replaceChild(newChild,oldChild);`
    返回值是一个指向已被替换的那个子节点的引用指针
    该节点除了替换功能以外还有移动的功能.  

	该方法只能完成单向替换, 若需要使用双向替换, 需要自定义函数:
	
	```
		   	/*
			 * 互换 aNode 和 bNode
			 * @param {Object} aNode
			 * @param {Object} bNode
			 */
			 
			function replaceEach(aNode, bNode){	
				if(aNode == bNode){
					return;
				}
				
				var aParentNode = aNode.parentNode;
				//若 aNode 有父节点
				if(aParentNode){
					var bParentNode = bNode.parentNode;
					
					//若 bNode 有父节点	
					if(bParentNode){
						var tempNode = aNode.cloneNode(true);
						bParentNode.replaceChild(tempNode, bNode);
						aParentNode.replaceChild(bNode, aNode);	
					}
				}
		
			}
	```
	
	




7. **`父节点.removeChild(子节点)`    			 删除指定的子节点**

   `var reference = element.removeChild(node);`
   返回值是一个指向已被删除的子节点的引用指针. 某个节点被 removeChild() 方法删除时, 这个节点所包含的所有子节点将同时被删除. 
   如果想删除某个节点, 但不知道它的父节点是哪一个, parentNode 属性可以帮忙。

   推荐方式：子节点.parentNode.removeChild(子节点)



### 元素的属性：

可以直接通过 cityNode.id 这样的方式来获取和设置属性节点的值
		

可以直接通过getAttribute/setAttribute/removeAttribute，这样的方式来获取和设置属性节点的值
	
通过元素节点的 getAttributeNode 方法来获取属性节点,然后在通过 nodeValue 来读写属性值 
###### 读取元素的属性：

语法：元素.属性名
例子：
	`ele.name`  

​	`ele.id` 

​	`ele.value` 

​	`ele.className`



###### 修改元素的属性：

语法：元素.属性名 = 属性值



### 事件（Event）

事件指的是用户和浏览器之间的交互行为。比如：点击按钮、关闭窗口、鼠标移动。。。

我们可以为事件来绑定回调函数来响应事件。

###### 绑定事件的方式：

1. 可以在标签的事件属性中设置相应的JS代码
   例子：

```
<button onclick="js代码。。。">按钮</button>
```

​		缺点: 
​			①. js 和 html 强耦合, 不利用代码的维护
​			②. 若 click 相应函数是比较复杂的, 则需要先定义一个函数, 然后再在 onclick 属性中完成对函数的引用, 比较麻烦。



2. 可以通过为对象的指定事件属性设置回调函数的形式来处理事件
   例子：

```
    <button id="btn">按钮</button>

    <script>
        var btn = document.getElementById("btn");
        btn.onclick = function(){

            };
    </script>
```





### 文档的加载

浏览器在加载一个页面时，是按照自上向下的顺序加载的，加载一行执行一行。

**如果将js代码编写到页面的上边，当代码执行时，页面中的DOM对象还没有加载，**
**此时将会无法正常获取到DOM对象，导致DOM操作失败。**

###### 解决方式一：

 可以将`js`代码编写到body的下边

###### 解决方式二：

将`js`代码编写到`window.onload = function(){}`中
window.onload 对应的回调函数会在整个页面加载完毕以后才执行，
所以可以确保代码执行时，DOM对象已经加载完毕了



## DOM IDL  (DOM的接口定义语言)

（待总结）

## DOM规范

（待总结）