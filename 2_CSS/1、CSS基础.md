# 邂逅CSS



## 1、css 历史：



## 2、将  CSS 样式应用到元素上的方式：

- ##### 内联样式
- ##### 内部样式表
- ##### 外部样式表
- ##### @import 导入



## 3、CSS 注释 : 

- ##### /*    我是CSS注释    */



## 4、CSS 样式规则顺序

- ##### 定位（ position ） |  布局 ( Layout )
- ##### 展示 （ Display ）|  可见（Visibility）
- ##### 盒子模型（ Box Model ）
- ##### 背景设置（ Background ）
- ##### 字体（ Font ） | 文本（ Text）
- ##### 其他属性（ Other Property ）



## 5、CSS 文档查询

- ##### 官方文档： https://www.w3.org/TR/?tag=css

- ##### MDN：https://www.w3.org/TR/?tag=css

- ##### 检查浏览器支持情况：https://caniuse.com/



## 6、CSS文本属性：

- ##### text-decoration：none、underline、overline、line-through

- ##### text-align：left、center、right、justify

- ##### text-transform：capitalize、uppercsase、lowercase、none

- ##### text-indent、letter-spacing、word-spacing



## 7、CSS字体属性：

- ##### fon-size：数值、百分比

- ##### font-family：...

- ##### font-weight：...

- ##### line-height：...

- ##### font-style：normal、italic、oblique

- ##### font-varient：normal、small-caps

##### ~ 关于line-height：

- ##### 行高：两行文字基线之间的距离

- ##### 顶线、中线、基线、底线

- ##### 设置line-height使文字垂直居中的原理

##### ~关于font简写属性：

- ##### font-style font-variant font-weight font-size/line-height font-family

- #####  font-style、font-variant、font-weight可以随意调换顺序，也可以省略

- ##### /line-height可以省略，如果不省略，必须跟在font-size后面

- ##### font-size、font-family不可以调换顺序，不可以省略



## 8、CSS选择器（selector）：

- ##### 通用选择器（universal selector）: *{ }           尽量不要使用，效率较低

- ##### 元素选择器（type selectors）: 

- ##### 类选择器（class selectors）: 

- ##### id选择器（id selectors）：id是唯一的，可以使用中划线（连字符hyphen）、下划线、驼峰标识连接

- ##### 属性选择器（attribute selectors）：[attr = val]、[attr *= val]、[attr ^= val]、[arrt $= val]、[attr |= val]、[ attr ~= val]

- ##### 组合（combinators）：后代选择器、直接子代选择器、兄弟选择器（+ 、~）、交集选择器、并集选择器

- ##### 伪类（pseudo-classes）：https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-classes

- ##### 伪元素（pseudo-elements）：https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-elements
  




## 9、CSS 的属性继承与层叠：

- ##### 常见可继承属性有 font-size、font-family、font-weight、line-height、color、text-align

- ##### 关于样式层叠的规则：先后顺序, 权重相同时, 后面设置的生效

- ##### 关于权重的计算：!important、内联样式、id选择器、类选择器、元素现择器、通配符—继承



## 10、CSS元素类型：

- ##### 块元素（block)：

- ##### 行内替换元素：

- ##### 行内非替换元素：

- ##### 可以通过 display：block、inline、inline-block、none 改变元素类型



# 11、CSS中的display属性：

- ##### display值的特性：

- ##### 编写HTML时的注意事项：一般情况，block、inline-block可以包含任意元素，inline只能包含行内级元素



## 12、元素隐藏的方法：

- ##### display：none

- ##### visibility：hidden

- ##### rgba：将a设置为0

- ##### opacity：设置为0



## 13、CSS中的overflow属性：

- ##### overflow：visible、hidden、scroll、auto

- ##### 隐藏滚动条：

  ```css
  .com-hide-scrollbar {
    overflow-x: hidden;
    overflow-y: auto;
    scrollbar-width: none; /* firefox */
    -ms-overflow-style: none; /* IE 10+ */
  }
  .com-hide-scrollbar::-webkit-scrollbar {
    display: none;
  }
  ```



## 14、CSS盒子模型（Box Model）：

- ##### 内容（content）：

- ##### 内边距（padding）：

- ##### 边框（border）：

- ##### 外边距（margin）：

##### ~关于border：

- ##### 设置border边框：border-with（简写属性）、border-top-width、border-right-width、border-bottom-width、border-left-width

- #####  边框颜色：border-color（简写属性）、border-top-color、border-right-color、border-bottom-color、border-left-color

- ##### 边框样式： border-style（简写属性）、 border-top-style、border-right-style、border-bottom-style、border-left-style

- ##### border简写：1px solid #eee、border-top 、border-right、border-bottom、border-left

- ##### 关于边框样式：https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-style

##### ~关于圆角：

- ##### border-radius：数值、百分比   border-top-left-radius、border-top-right-radius、border-bottom-right-radius，和 border-bottomleft-radius

##### ~关于margin：

- ##### margin-top的传递：如果块级元素的顶部线和父元素的顶部线重叠，那么这个块级元素的margin-top值会传递给父元素

- ##### margin-bottom传递:如果块级元素的底部线和父元素的底部线重写，并且父元素的高度是auto，那么这个块级元素的margin-bottom值会传递给父元素

- ##### 建议：margin一般是用来设置兄弟元素之间的间距，padding一般是用来设置父子元素之间的间距

- ##### 上下margin的折叠：垂直方向上相邻的2个margin（margin-top、margin-bottom）有可能会合并为1个margin，这种现象叫做collapse（折叠）

- ##### 两个兄弟块级元素之间上下margin的折叠：

- #####  父子块级元素之间margin的折叠：

##### ~关于外轮廓outline：

- ##### 不占用空间、显示在border外

- ##### 相关属性：outline：outline-width、outline-style、outline-color

##### ~关于盒子阴影box-shadow：

- ##### box-shadow：offest-x、offect-y、blur-radius、spread-radius

- ##### 盒子阴影在线查看：https://html-css-js.com/css/generator/box-shadow/

##### ~关于文字阴影text-shadow：

- ##### text-shadow：offest-x、offect-y、blur-radius

- ##### 文字阴影在线查看：https://html-css-js.com/css/generator/box-shadow/



## 15、CSS中的box-sizing属性：

- ##### content-box：padding、border都布置在width、height外边

- ##### border-box： padding、border都布置在width、height里边





## 16、行内非替换元素的注意事项

- ##### 效果不起作用属性：width、height、margin-top、margin-bottom

- ##### 效果比较特殊属性： padding-top、padding-bottom、上下方向的border



## 17、元素水平居中的方案：



## 18、CSS设置背景图片：

- ##### background-image：会盖在background-color上面，如果设置了多张背景图片，设置的第一张会显示在最上面，其他图片按顺序层叠在下面

- ##### background-repect：repect、no-repect、repect-x、repect-y

- ##### background-size：auto、cover、contain、contain、<percentage>、length

- ##### background-position：具体值、水平方向上 left、center、right 、垂直方向上 top center bottom，如果值设置一个方向，另一个方向默认center

- ##### background-attachment：scroll（相对于元素本身固定）、local（相对于内容固定）、fixed（相对于视口固定）

##### ~background简写属性：

- ##### background：color、image、position、repeat、attachement

##### ~background-image和img的对比：

- ##### img作为网页的组成部分

- ##### background-image：可有可无，让页面更美观



## 19、CSS结构伪类：

- ##### :nth-child(n) ：父元素中的第n个子元素，先找到第n元素，再判断是否是要指定的元素，如果不是则样式不会生效

- ##### :nth-of-type(n)：父元素的第n个子元素，先排除干扰项，在找到第n个

- #####  :nth-last-child(n) | :nth-of-last-type ：父元素中的倒数第n个子元素

- ##### :first-child、:last-child、:first-of-type、:last-of-type

- ##### :only-child、:only-of-type：是父元素唯一的子元素，注意两者的区别

- ##### :root：根元素，就是HTML

- ##### :empty：完全空白的元素

- ##### :not(简单选择器)：否定选择器



## 20、CSS中利用border绘制图形

- ##### 利用border绘制三角形

- ##### 一些CSS画出来的图形：https://css-tricks.com/the-shapes-of-css/



## 21、认识web字体（Web Fonts）

- ##### 工作原理：当浏览器在操作系统中找不到指定字体时，通过@font-face{font-family:'取个字体名字',src:url(XXX)}

- ##### 关于网络字体的兼容性：.ttf、 .oft、.eot、.svg、.svgz、.woff等,

- ##### 兼容性写法与字体类型产出：https://font.qqe2.com/



## 22、认识字体图标

- ##### 阿里图标库：https://www.iconfont.cn/

- ##### 字体图标的使用



## 23、精灵图 | 雪碧图（CSS Sprite）

- ##### 一种CSS图像合成技术，将各个小图片合成到一个图片上面，利用背景定位实现显示

- ##### 好处：减少HTTP请求次数、加快网页响应速度、减少服务器压力、减少图片总大小、较少图片命名的困扰

- ##### 制作：https://www.toptal.com/ 

- ##### 精灵图位置：http://www.spritecow.com/



## 24、光标样式属性（cursor）

- ##### cursor:auto | default | pointer | text | none



## 25、CSS属性vertical-align：

- 

