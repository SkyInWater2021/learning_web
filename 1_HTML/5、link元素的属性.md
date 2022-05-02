# link元素



## 一、link 图标

- 文档：https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link

- favicon 是 favorites icon 的缩写，亦被称为 website icon（站点图标） 、page icon（页面图标）



## 二、CSS 样式的字符编码

- 在样式表中有很多方法去声明字符编码，浏览器会按照已下的顺序尝试（一旦找到就停止并得出结果）
  1. 文件的开头的 Unicode byte-order（字节顺序标记）字符值 [维基百科解释](https://en.wikipedia.org/wiki/Byte_order_mark)
  2. 由 Content-Type：HTTP header 中的 charset 属性给出的值或用于提供样式表的协议中的等效值
  3. CSS @规则 @charset
  4. 使用参考文档定义的字符编码：  元素的 charset 属性(已被废除)
  5. 假设文档是 UTF-8
- 开发中推荐在CSS的开头编写@charset指定编码 `@chartset "UTF-8"`

