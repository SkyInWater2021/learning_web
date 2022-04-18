# 认识HTML



## 1、什么是HTML？

- ##### 超文本标记语言（HyperText Markup Language）：是一种创建网页的标准标记语言

- ##### 标记语言（markup language）：由无数个标记（标签、tag）组成，对某些内容进行特殊标记、供其他解释器识别处理

- ##### 超文本（Hyper Text）：不仅可以插入普通文本，还可以插入图片、音频、视频等



## 2、HTML 特点、结构：

- ##### 标签大小写不敏感，但是推荐小写




## 3、开发工具的选择：

- ##### Webstorm：集成开发工具、包罗万象、重、收费

- ##### VSCode：轻、免费、需要安装插件辅助开发



## 4、认识元素 ( Element )：

- ##### 推荐网站 MDN   https://developer.mozilla.org/zh-CN/docs/Web/HTML

- ##### 常用元素：

- ##### 不常用元素：



## 5、元素的组成：

- ##### 开始标签（Opening tag）：

- ##### 结束标签（Close tag)：

- ##### 内容（content）：

- ##### 元素（element）：



## 6、元素的属性 ( Attribute )：

- ##### 文档：https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes

- ##### 公共的：

- ##### 特有的：



## 7、元素属性的分类：

- ##### 块级元素

- ##### 行内元素

- ##### 行内替换元素、行内非替换元素



## 8、HTML 注释 ：

- ##### 快捷键：ctrl + /      <!-- 注释内容 -->



## 9、HTML 中常见的元素：

- ##### 文档声明  <!DOCTYPE html>：必须放在文档最前面，不能省略告诉浏览器当前页面是HTML5页面

  ```html
   <!DOCTYPE html> 
  <html lang="zh-CN | en ">
    <head> // head中编写文档配置信息，元数据（ meta data ）
      <meta charset="utf-8"> // 
      <title>文档标题</title> // head中唯一必须的元素
    </head>
    <body>
    </body>
  </html>
  
  ```
  
- ##### HTML元素：文档的根，顶级元素、根元素 ，W3C标准建议添加一个lang属性，有助于语音和成工具和翻译工具使用相应规则，常见的 en、zh-CN

- ##### head元素：配置信息（元数据），包括文档标题，引入的文档样式，脚本等

- ##### body元素：网页的具体内容和结构，也就是在浏览器窗口看见的东西

##### ~

- ##### 常见的HTML中的元素：https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element

- ##### p元素：浏览器如何识别p元素、关于SEO优化、...

- ##### image元素（可替换元素）：图片格式、必须属性src、...

- ##### a元素：herf、target、锚点链接、图片链接、其他URL地址、...、

- ##### iframe元素：frameborder：0（不显示）、1（显示）、关于a元素的target属性：_parent、_top

- ##### div、span：出现历史、两者区别、



## 10、字符实体：

- ##### 格式：以连字号开头（&）、以分号（;）结尾的文本

- ##### 常见的字符实体：https://www.w3school.com.cn/html/html_entities.asp



## 11、认识URL：

- ##### URL：统一资源定位符（Uniform Resource Locator）

- ##### 理论上讲，每一个有效的URL都指定一个唯一的资源

- ##### 格式：[ 协议类型 ] : // [ 服务器地址 ] : [ 端口号 ] / [ 文件路径 ] [ 文件名 ] ? [ 查询 ] # [ 片段ID ]

- ##### 和URL的区别：URI用于标识Web技术使用的逻辑或物理资源，是URL的一个子集



## 12、元素语义化：

- ##### 好处：方便代码维护、减少沟通成本、有利于SEO，能让语音合成工具正确识别网页用途，做出正确反应、...



## 13、什么是SEO？

- ##### SEO：search engine optimization 通过了解搜索引擎的运作规则来调整网站、提高网站在有关搜索引擎内排名的方式

- ##### SPA、SSR：



## 14、认识字符编码：

- ##### coderwhy文章：https://www.jianshu.com/p/899e749be47c



## 15、关于link元素：

- ##### 作用：外部资源链接元素，规范了文档与外部资源的关系

- ##### 常见的 rel 类型：https://developer.mozilla.org/zh-CN/docs/Web/HTML/Link_types

- ##### rel -> dns-prefetch 提前dns解析



## 16、认识进制：

- ##### 二进制（binary）：0b开头（零b）

- ##### 八进制（Octonary）：0o开头（零o）

- ##### 十进制（decimal）：

- ##### 十六进制（Hexademical）：0x开头

- ##### 进制之间的转换：



## 17、Chrome浏览器调试工具

- ##### 技巧：



## 18、浏览器渲染过程：

- ##### 面试题：

