# CSS3 新增属性



## 1、CSS 属性 white-space

- normal：合并所有的空白，允许单词超屏时自动换行
- nowrap：合并所有连续空白，不允许自动换行
- pre：阻止合并所有连续的空白，不允许自动换行
- pre-wrap：阻止合并所有的连续空白，允许自动换行
- pre-line：合并所有连续的空白，但是保留换行，允许自动换行



## 2、CSS 属性 text-overflow

**text-overflow 生效的前提是 overflow 不为 visible**

- clip：溢出的内容直接裁掉

- ellipsis：溢出那行的结尾处用省略号表示

- 常见的是将 white-space、text-overflow、overflow 一起使用

  ```css
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  ```

  

## 3、CSS 中的函数

- rgb、rgba、translate、rotate、scale、...

- var：使用 CSS 定义的变量

  ```css
  /* 自定义属性名 需要用两个减号(--)开头*/
  div {
    --he-color: red;
  }
  /* 可以通过 var 函数来使用自定义的 css 变量 */
  span {
    color: var(--he-color)
  }
  
  /* 推荐将自定义属性定义在 html 中，也可以使用 :root 选择器 */
  ```

- calc：计算 CSS 值，通常用于计算元素的大小或位置

- blur：毛玻璃效果

  - blur(radius)：radius 表示模糊半径，用于定义高斯函数的偏差值，偏差值越大，图片越模糊
  - 通常会将两个属性一起使用 filter、backdrop-filter

  ```css
  filter: blur();
  backdrop-filter();
  ```

  

- gradient：颜色渐变函数

  - linear-gradient()：创建一个或多个颜色线性渐变的图片
  - radial-gradient()：创建一个图像，该图像由原点出发，，由一种或多种颜色之间逐步过渡组成
  - repeating-linear-gradient()：创建一个重复线性渐变组成的<image>
  - repeating-linear-gradient()：创建一个重复原点出发渐变组成的<image>

  ```css
  div {
    background-image: linear-gradient(blue,red);
    background-image: linear-gradient(to right, blue, red);
    background-image: linear-gradient(to right bottom, blue, red);
    
    background-image: radial-gradient(at 0% 50%, red, yellow);
  }
  ```

  

## 4、浏览器前缀

- 官方术语：vendor-specific extensions（供应商特定扩展）
- 为什么需要前缀：CSS 属性刚开始并没有成为标准时，浏览器为了防止变更，给新的属性添加浏览器前缀，是w3c，浏览器开发商，开发者们三者之间的一种平衡手段
- 浏览器私有前缀：
  - -0-、-xv-：Opera 等
  - -ms-、mso-：IE 等
  - -moz-：Firefox 等
  - -webkit-：Safari、Chrome 等



## 5、CSS 中的 FC

- 文档：https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flow_Layout/Intro_to_formatting_contexts

- FC (formatting context)，元素在标准流里都是属于一个 FC

- 块级元素的布局属于 BFC （block formatting context）

- 行内级元素的布局属于 LFC （inline formatting context）

- MDN 上整理的哪些具体情况会创建 BFC

  - 根元素：<html>
  - 浮动元素：元素的 float 不是 none
  - 绝对定位元素：position 为absolute、fixed
  - 行内块儿元素：display：inline-block
  - 表格单元格：display：table-cell
  - 表格标题：display：table-caption
  - 匿名表格单元格元素
  - overflow 计算值不为visible的块元素
  - 弹性布局
  - 网格布局
  - display 值为 flow-root 的元素

  

- BFC 有什么特点以及作用？

  - 在 BFC 中box 会在垂直方向上一个接一个的排布
  - 垂直方向上的间距由 margin 决定
  - 在同一个 BFC 中，相邻两个 box 之间的 margin 会折叠（collapse）
  - 在 BFC 中，每个元素的左边缘是紧挨着包含块的左边缘的

  

  - 了解了 BFC 所做的事情，则可以理解为什么 BFC 可以解决折叠问题和浮动高度塌陷问题
  - BFC 解决高度塌陷的两个条件：浮动元素的父容器出发 BFC，父元素的高度是 auto
  - BFC 的高度为 auto 时，是如下计算高度的
    - 如果只有 inline-level，是行高顶部和底部的距离
    - 如果由 block-level，是由块最底层的上边缘和最低增块盒子下边缘之间的距离
    - 如果有绝对定位，高度将会被忽略
    - 如果有浮动元素，那么会增加高度以包括这些浮动元素的下边缘



## 6、媒体查询

​	**媒体查询是一种提供给开发者针对不同设备需求进行定制化的一个接口**

- 媒体查询 - 引入的方式

  - 通过 `@media` 和 `@import`

    ```css
    <style>
    	@import url(xxx) (max-width: 600px);
    </style>
    ```

  - 使用 media 属性为 <style>、<link>、<source> 和其他 HTML 元素指定特定的媒体类型

    ```html
    <link rel="stylesheet" media="(max-width: 600px)" href="./css/miniScreen.css">
    ```

  - 使用 Window.matchMedia() 和 MediaQueryList.addListener() 方法来测试和监控媒体状态

  

- 媒体查询 - 媒体类型（Media types）

  - 使用媒体查询时，必须指定使用的类型。媒体类型时可选的，并且会隐式应用 all 类型
  - 常见的媒体类型
    - all：适用于所有设备
    - print：适用于在打印预览模式下，在屏幕上查看分页材料和文档
    - screen：只要用于屏幕
    - speech：只要用于语音合成器

  

- 媒体查询 - 媒体特性（Media features)
  - 媒体查询描述了浏览器、输出设备、预览环境等的具体特征
  - 通常会将媒体查询描述为一个表达式
  - 每条媒体特性表达式都必须用括号括起来
    - width、height、color
    - 设备比例：device-aspect-ratio
    - 设备宽高度：device-width、device-height
    - 方向：orientation(不支持最大值最小值)
    - 分辨率：resolution



- 媒体查询 - 逻辑操作符
  - 媒体查询的表达式终将获得一个 Boolean 值，如果是多个条件，我们可以通过逻辑操作符联合复杂的媒体查询
    - and：规则组合
    - not：规则否定
    - only：仅在整个媒体匹配时才应用样式
    - ,(逗号)：规则合并



## 7、常见的移动设备