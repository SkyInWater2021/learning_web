# CSS 中的单位



## 1、绝对单位（absolute length units）

​	**绝对单位指于其他任何东西都没有关系，总认为是相同的大小，例如 cm、mm、in、pt、px 等**

- in：英寸  1in = 2.54cm = 96px



## 2、相对单位（relative length units）

- 相对长度单位
  - em：相对于自身的 font-size
  - ex：字符 x 的的高度
  - ch：数字 0 的宽度
  - rem：根元素的字体大小
  - lh：元素的 line-height
  - vw：视口宽度的 1%
  - vh 视口高度的 1%



## 3、像素（pixel）

​	**像素是影响显示的基本单位，pix 是 picture 的缩写，加上元素 element，就得到 pixel**

- 像素的不同分类
  - 设备像素（物理像素）：显示器上的真实像素
  - 设备独立像素（逻辑像素）：操作系统为开发者进行抽象，提供了逻辑像素的概念
  - CSS 像素：默认情况下等同于设备独立像素



- DPR：device pixel ratio  在 Retina（视网膜显示屏） 屏幕中，一个逻辑像素对应两个物理像素，这个比例成为设备像素比
- PPI：pixel per inch  每英寸像素，通常用来表示打印图像或者显示器上像素比例



​	

