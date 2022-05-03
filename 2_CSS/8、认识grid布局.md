# grid 布局



## 1、认识 Grid 布局

​	**CSS Grid Layout 是一种基于二维的布局系统，相比于 Flex 布局，更加强大，同时也更加复杂**

- 目前兼容性相比于 Flex 较差

- Grid 布局中几个重要的概念

  - Grid Container：设置 display为 grid 的盒子

  - Grid Item：grid container 的直接子项，必须是直接子类

  - Grid Line：构成网格结构的分割线，可以使垂直的或水平的

  - Grid Track：两条网格线之间的距离

  - Grid Area：由四条网格线包围的总空间，一个网格区域可以由任意数量的单元格组成

    ```css
    .box {
    	display: grid;
      grid-template-columns: 100px 1fr 100px; // 列
      grid-template-rows: repeat(2,100px); // 行
    }
    ```

- Grid Container 常见的属性

  - display
  - grid-template-columns、grid-template-rows、grid-template-areas
  - ...

- Grid Item 常见的属性

  - grid-column-star、grid-column-end
  - grid-row-star、grid-row-end
  - grid-row、grid-column、grid-area
  - justify-self、align-self、place-self
  - ...

- Grid 布局文档：https://css-tricks.com/snippets/css/complete-guide-grid/

