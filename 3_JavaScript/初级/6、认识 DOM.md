# JavaScript 中的 DOM（Document Object Model 文档对象模型）



## 1、DOM 元素之间的关系

- DOM 的继承关系图

![image-20220529124226165](https://tva1.sinaimg.cn/large/e6c9d24ely1h2p6aw6ln4j21rc0r2439.jpg)

```js
// DOM 元素节点(Node)之间的导航
	父节点:parentNode
 前兄弟节点:previousSibling  后兄弟节点:nextSibling
 子节点:childNodes
 第一个子节点:firstChild
 最后一个节点:lastChild

```

```js
// DOM 元素(Element) 之间的导航
	父元素:parentElement
 前兄弟节点:previousElementSibling  后兄弟节点:nextElementSibling
 子节点:children
 第一个子节点:firstElementChild
 第二个子节点:lastElementChild

```

```js
// 表格(table)元素的导航
	table.rows -> <tr>元素的集合
	table.caption/tHead/tFoot -> 引用元素 <caption>、<tHead>、<tFoot>\
  table.tBodies -> <tbody>元素

	tbody(thead/tfoot).rows -> 表格内部的<tr>元素集合

	tr.cell -> 指定 <tr> 中的 <td>、<th> 单元格集合
	tr.sectionRowIndex -> 给定的<tr>在封闭的<thead> | <tboyd> | <tfoot> 中的索引
	tr.rowIndex -> 指定<tr>在整个表格中的索引

	td.cellIndex -> 在封闭的 <tr> 中单元格的编号

```

```js
// 表单(form)元素的导航
	const formEl = document.forms
  const elements = fromEl[0].elements
  可以通过表单子元素的 name 来获取他们
  
```



## 2、获取 DOM 元素的方法

```js
  querySelector  可在元素上调用：true   实时：true
  querySelectorAll  可在元素上调用：true   实时：true
  getElementById  可在元素上调用：false   实时：false
  getElementByName  可在元素上调用：false   实时：true
  getElementByTagName  可在元素上调用：true   实时：true
  getElementByClassName  可在元素上调用：true   实时：true
  
```



## 3、DOM 节点的 type、tag、content

- 节点的类型

  ```js
  	Node.ELEMENT_NODE  1  一个元素节点
    Node.TEXT_NODE  3  element 或者 Attr 中实际的文字
    Node.COMMENT_NODE  8  一个 comment 节点
    Node.DOCUMENT_NODE  9  一个Document 节点
    Node.DOCUMENT_TYPE_NODE  10   描述文档类型的节点
  ```
  
  其他类型可以查看MDN文档: https://developer.mozilla.org/zh-CN/docs/Web/API/Node/nodeType

  

- 节点的属性

  ```js
  	Node 节点有一个属性 nodeName，可以获取到节点类型的字符串
    Element 节点有一个 tagName 属性，可以获取到节点名称字符串
    
    innerHTML属性
    outerHTML属性
    textContent属性
    
    nodeValue | data 获取非元素节点的文本内容
    
  // 节点的其他属性
     hidden
     value
     href
     id
     ...等等
  ```

  

## 4、DOM 节点的 attributes、properies

- 元素的属性和特性

- attribute 的操作

  ```js
  // 属性的分类
  	标准的 attribute
    非标准的 attribute （自定义属性）
    
  // 对于所有的 attribute 都支持的操作
    ele.hasAttribute(name) 
  	ele.getAttribute(name)
  	ele.setAttribute(name)
  	ele.remoteAttribute(name)
  	ele.attributes: attr对象的集合，具有name、value属性
    
  // attribute 特征
    大小写不敏感
    它们的值总是字符串类型
    
  // 通过 property 获取标准的 attribute 的值，可以获取到对应的类型
    大多数情况下，property 和 attribute 是相互影响的
    特殊情况: ...
    
  // HTML 中的 data-* 自定义属性
  
  // 动态修改样式
    ele.style.color = 'red'
  	ele.style.color = '' // 空字符串则使用浏览器默认样式
  	ele.style.cssText = 'font-size: 30px; color: red' // 设置多个值
  	特殊全局方法：getComputedStyle 拿到 style 中的属性
    getComputedStype(ele).fontSize // 获取 style 中编写样式中的font-size
    
    
  	ele.className = 'new-class' // 会覆盖之前的 class,不推荐
  	特殊的对象：classList
    ele.classList.add(class): 添加一个类
    ele.classList.remove(class):移除一个类
    ele.classList.toggle(class):如果存在就移除，不存在就添加
    ele.classList.contains(class):检查给定类，返回true | false
  
  ```

  

## 5、DOM 节点的创建、插入、克隆、删除

```js
// 创建元素
	document.createElement(tagName)

// 插入元素
	node.append(...nodes or strings)  在 node 末尾追加
	node.prepend(...nodes or strings)  在 node 开头追加
	node.before(...nodes or strings)  在 node 前面追加
  node.after(...nodes or strings) 在 node 后面追加
  node.replaceWidth(...nodes or strings)  将 node 替换为指定的节点或字符串
  
// 移除和克隆元素
  node.remove()  // 移除自身
	node.cloneNode(boolean)  // 克隆元素，参数：true or false 是否深度克隆

// 旧的元素操作方法
	parentElement.appendChild(node)  在parentElem的父元素最后位置添加一个子元素
	parentElement.insertBefore(node,nextsibing)  在parentElem的nextSibling前面插入一个子元素
  parentElement.replaceChild(node,oldChild)  在parentElem中，新元素替换之前的oldChild元素
  parentElement.removeChild(node)  在parentElem中，移除某一个元素
```



## 6、DOM 节点的样式、类



## 7、DOM 元素的大小、滚动、坐标

- 元素的大小、滚动

  ```js
  	clientWidth: contentWidth + padding(不包含滚动条)
  	clientHeight: contentHeight + padiing
  	clientTop: border-top 的高度
    clientLeft: border-left 的宽度
    
    offsetWidth: 元素完整的宽度
    offsetHeight: 元素完整的高度
    offsetTop: 距离父元素的 y
    offsetLeft：距离父元素的 x
    
    scrollHeight: 整个可滚动区域的高度
    scrollTop：滚动部分的高度
  	
  ```

- window 的大小、滚动

  ```js
  	innerWidth | innerHeight: 获取 window 窗口的宽度和高度（包含滚动条）
    outerWidth | outerHeight: 获取 window 窗口的整个宽度和高度（包含调试工具、工具栏）
    documentElement.clientHeight | documentElement.clientWdith 获取 html 元素的宽度和高度(不包含滚动条)
  
  // window 的滚动位置
  	scrollX： X轴滚动的位置（别名 pageXOffset）
    scrollY: Y轴滚动的位置（别名 pageYOffset）
    
    scrollBy(x,y) 将页面滚动至相对于当前位置的(x,y)
  	scrollTo(x,y) 将页面滚动至(pageX,pageY),绝对坐标
  ```



## 8、DOM 中的事件处理

- 事件监听方式

  - 在 `script` 中直接监听

  - DOM 属性，通过元素的 on 来监听事件

  - 通过 EventTarget 中的 addEventListener 来监听

- 常见的事件列表

  - 鼠标事件：click、mouseover、mouseout、mousemove、mousedown、mouseout
  - 键盘事件：keydown、keyup
  - 表单(form)元素事件：submit、focus
  - Docuement 事件：DOMContentLoaded => 当HTML 的加载和处理均完成，DOM 被完全构建完成时

  - CSS 事件：transitionend =>当一个CSS 动画完成时

- 认识事件流

  - 事件处理中的 this = event.target  这是因为在浏览器内部，调用event handler是绑定到当前的target上的
  - EventTarget类中常见的方法
    - addEventListener
    - removeEventListener
    - dispatchEvent  派发某个事件到EventTarget上
      - 例如：window.dispatchEvent(new Event('heyuan'))  向 window对象派发了一个 heyuan 事件

- 事件冒泡和时间捕获

  - el.addEventListener("click", fn, true) // 第三个参数为 true 时监听捕获的过程

- 事件对象中常见的属性

  - type：事件类型
  - target：当前事件发生的元素
  - currentTarget：当前处理事件的元素
  - eventPhase：事件所处的阶段  捕获：1  当前事件：2   冒泡 3
  - offsetX、offsetY：事件发生在元素内的位置
  - clientX、clientY：事件发生在客户端的位置
  - pageX、pageY：事件发生在客户端相对于 document 的位置
  - screenX、screenY：事件发生相对于屏幕的位置

- 阻止默认行为

  - event.eventDefault() 阻止事件默认行为
  - event.stopPropagation 阻止事件传递（冒泡和捕获）

- 事件委托

- 常见的鼠标事件

  ![image-20220601200953826](https://tva1.sinaimg.cn/large/e6c9d24ely1h2t03g67yqj21n00t611g.jpg)

  - mouseenter | mouseleave 和 mouseover | mouseout 的区别

- 常见的键盘事件

  - onkeydown  发生在键盘按键按下的时候

  - onkeypress  发生在文本输入的时候

  - onkeyup  发生在文本输入完成的时候

  - 可以通过 event 对的 code | key 来区分输入的某个键

- 常见的表单事件

  ![image-20220601222414040](https://tva1.sinaimg.cn/large/e6c9d24ely1h2t3z54zzlj21n00lun1f.jpg)


- 文档加载事件
  - DOMContentLoaded：浏览器已经完全加载了HTML，并构建了DOM 树，但外部资源可能没有完全加载
  - load：包括外部资源在内全部加载完毕
- 事件类型：https://developer.mozilla.org/zh-CN/docs/Web/Events



## 9、认识定时器

- setTimeout 语法如下

  ```js
  let timeId = setTimeout(fn,[delay],[arg1],[arg2],...)
  fn: 想要执行的函数
  delay：想要延迟的毫秒数
  arg1、arg2: 传入函数的参数列表
  
  // 清除定时器
  clearTimeout(timeId)
  ```

- setInterval 同 setTimeout 语法相同，不同的是 setInterval 是周期性的重复执行函数

  

  
