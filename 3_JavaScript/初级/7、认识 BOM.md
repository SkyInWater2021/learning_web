# JavaScript 中的 BOM（Browser Object Model 浏览器对象模型）



## 1、认识 DOM

- DOM：浏览器对象模型，浏览器提供的用于处理文档(document)之外的所有内容的其他对象
- DOM 主要包括的对象模型
  - window：包括全局属性、方法，控制浏览器窗口相关的属性、方法
  - location：浏览器连接到的对象的位置(URL)
  - history：操作浏览器的历史
  - navigator：用户代理(浏览器)的状态和标识(很少用到)
  - screen：屏幕窗口信息(很少用到)

![image-20220607135627728](https://tva1.sinaimg.cn/large/e6c9d24ely1h2zn0oxw8wj20oc0mqdh3.jpg)



## 2、window 对象

- window 对象的作用
  - 包含大量的属性：localStorage、console、location、history、screenX、scrollX等等(大概60+个属性)
  - 包含大量的方法：alert、close、scrollTo、open等等(大概40+个方法)
  - 包含大量的事件：focus、blur、load、hashchange等等(大概30+个事件)
  - 包含从EventTarget继承过来的方法，addEventListener、removeEventListener、dispatchEvent方法
  - MDN 文档：https://developer.mozilla.org/zh-CN/docs/Web/API/Window

- window 常见的属性、方法、事件

  ```js
  window.outerHeight
  window.innerHeight
  window.screenX
  window.screenY
  window.scrollX
  window.scrollY
  ...
  
  close()
  scrollTo()
  open('url','_self | _blank')
  ...
  
  onfocus()
  onblur()
  onload()
  onhashchange()
  ...
  ```



## 3、location 对象

- location 对象用于表示 window 上当前链接到的 URL 信息

- location 对象常见的属性

  - href：当前 window 对应的超链接URL，整个 URL
  - protocal：当前的协议
  - host：主机地址
  - hostname：主机地址（不带端口）
  - port：端口
  - pathname：路径
  - search：查询字符串
  - hash：哈希值

  ![image-20220607141020090](https://tva1.sinaimg.cn/large/e6c9d24ely1h2znf2vgp7j21tw08675k.jpg)

- location 对象常见的方法

  - assign：赋值一个新的 URL，并且跳转到该 URL
  - replace：打开一个新的 URL，并跳转到该 URL 中，不会在浏览器中留下之前的记录
  - reload：重新加载页面，可以传入一个 Boolean 类型

## 

## 4、URLSearchParams

- URLSearchParams 常见的方法
  - get：获取搜索参数的值
  - set：设置一个搜索参数的值
  - append：追加一个搜索参数的值
  - has：判断是否有某个搜索参数
  - MDN 文档：https://developer.mozilla.org/zh-CN/docs/Web/API/URLSearchParams
- 中文会使用encodeURLComponents和decodeURLComponent进行编码和解码



## 5、history 对象

- history 对象允许我们访问浏览器曾经的回话历史记录
- history 的两个属性
  - length：会话中的记录条数
  - state：当前保留的状态值
- history 的五个方法
  - back()：返回上一页
  - forwords()：前往下一页
  - go()：加载历史中的某一个
  - pushState()：打开一个指定的地址
  - replaceState()：打开一个新的地址，并且使用 replace
- history 和 hash时目前 vue 和 react等框架底层的实现原理，具体的实现方法后续了解



## 6、navigator 对象

- navigator 对象表示用户代理的状态和标识等信息

  ![image-20220607142915004](https://tva1.sinaimg.cn/large/e6c9d24ely1h2znyruh0aj21240u0gps.jpg)



## 7、screen 对象

- screen 主要记录的是浏览器窗口外面的客户端显示器的信息，比如屏幕的逻辑像素 screen.width、screen.height

  ![image-20220607143057564](https://tva1.sinaimg.cn/large/e6c9d24ely1h2zo0jgm9aj21u00ragpk.jpg)



## 8、JSON 的由来

- JSON 全称 JavaScript Object Notation（JavaScript对象符号）
- SON是由Douglas Crockford构想和设计的一种轻量级资料交换格式，算是JavaScript的一个子集
- JSON 的基本语法

  - 简单值
  - 对象值
  - 数组值
- JSON 序列化
- Stringify 的 replace 参数

  ```js
  JSON.stringify(obj)
  JSON.stringify(obj,['name','age'])
  JOSN.stringify(obj,(key,value) => {
    if(key === 'name') return 'otherName'
  })
  ```
- Stringify 的参数 space

  - 如果对象本身包含 toJSON 方法，那么会直接使用 toJSON 方法返回的结果

- parse 方法

  - JSON.parse 用来解析字符串，构造由字符串描述的 JavaScript 对象或值

  - 提供可选的 reviver 函数用以在返回之前对所得到的对象执行操作

    ```js
    const info = JSON.parse(objString,(key,value) => {
    	....
    })
    ```



## 9、认识 Storage

- localStorage：本地存储，提供的是一种永久性的存储方法，在关闭网页重新打开时，存储的内容依旧保留
- sessionStorage：会话存储，提供本次会话的存储，在会话关闭时，存储内容会被清除
- 两者的区别
  - 关闭网页重新打开时，localStorage 会保留，sessionStorage 不会保留
  - 在页面内跳转时，两只都会保留
  - 在页面外跳转时，localStorage 会保留，sessionStorage 不会保留
- Storage 常见的属性和方法
  - Storage.length：只读属性，表示存储在 Storage 对象中的数据数量
  - Storage.key()：该方法接受一个数值 N 作为参数，返回存储中的第 N 个 key 名称
  - Storage.setItem()：该方法接受一个key和value，并且将会把key和value添加到存储中
  - Storage.getItem()：该方法接受一个key作为参数，并且返回key对应的value
  - Storage.removaItem()：该方法接受一个key作为参数，并把该key从存储中删除
  - Storage.clear()：该方法的作用是清空存储中的所有key
