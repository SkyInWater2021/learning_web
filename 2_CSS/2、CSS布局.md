# 标准流（Normal Flow）与脱离标准流



# 定位



## 1、position属性：

- 定位元素：position: static | relative | absolute | fixed | sticky（相对于滚动祖先的滚动视口）

- 定位的规则

- 画布与视口的概念

- 对于绝对定位来说：定位参照对象的宽度 = left + right + margin-left + margin-right + 绝对定位元素实际占用宽度    高度同理



## 2、z-index 属性：



# 浮动



## 1、float属性：

- 指定一个元素应沿其容器的左侧或右侧放置，允许文本和内联元素环绕它

- 浮动的规则

- 浮动出现的问题：高度塌陷，通过clear属性：指定一个元素必须移动到之前浮动元素的下面

  ```css
  .clear_fix {
  	content:'',
    clear:both,
    display:block,
      /* 兼容其他浏览器*/
    visibility:hidden,
    height:0
  }
  .clear_fix {
    *zoom:1 /* 兼容IE6、IE7*/
  }
  ```

  

# 弹性盒子(Flex Box)



## 1、flex概念：

- display: flex | inline-flex

- flex container 与 flex item

- 主轴：main axis  交叉轴：cross axis



## 2、flex属性：

- flex-direction: row(默认) | column | row-reverse | column-reverse

- flex-wrap: wrap | nowrap(默认) | wrap-reverse

- flex-flow:  flex-direction | | flex-wrap 

- 对齐调整：justify-content: flex-start | flex-end | center | space_between | space-around | space-evenly  | start | end 

- 交叉轴上的对齐方式：align-items: normal | stretch | flex-start | flex-end | center | baseline

- 多行情况下交叉轴对齐方式：align-content: stretch |  flex-start | flex-end | center | space-around | space-between | space-evenly

#### item 项相关：

- flex-item属性：

- order: Number 数字越大，排的越靠后

- align-self: auto | stretch | flex-start | flex=end | center| baseline 可以覆盖flex container设置的align-items

- 拉伸：flex-grow:  Number |  默认值 0

- 压缩：flex-shrink:  Number | 默认值1

- 主轴方向上的基础尺寸: flex-basis: auto |  例如一个单词显示不完时，会自动拉伸

- 缩写属性：flex: flex-grow | flex-shrink | flex-basis

- 简写举例：flex: none(o o auto) | auto(1 1 auto) | 1(flex-grow) |  