# CSS 预处理器



## 1、CSS 编写的痛点

- 代码量大，维护性差
- 没有专门的作用域和嵌套
- 需要定义大量的 class/id 来保证选择器的准确性



## 2、常见的 CSS 预处理器（CSS_Preprocessor)

​	**社区为了解决 CSS 面临的大量问题，出现了一系列的 CSS 预处理器**

- Sass/Scss
- Less
- stylus



## 3、认识 Less（leaner style sheets）

- Less 增加了很多相比于 CSS 更好用的特性
- 比如定义变量、混入、嵌套、计算等
- Less 最终需要编译为 CSS 运行于浏览器，包括部署到服务器中
- Less 代码的编译：...



## 4、Less 常见语法

- Less 兼容 CSS

- 变量（variables）

  ```css
  // 定义变量
  @mainColor：#eee
  @mainFontSize：14px
  
  .box {
    color: @mainColor;
    font-size: @mainFontSize;
  }
  ```

- 嵌套（nesting）

  ```less
  .main {
    .left-container {
      
    }
    .right-container {
      
      &:hover {
        
      }
    }
  }
  // & 表示当前选择器的父级
  ```

- 运算（Operations）

  - 算数运算符在加、减或比较之前会进行单位换算，计算的结果以左侧数的单位为准（特殊情况除外）
  - 如果单位换算无效或者失去意义，则会忽略单位
  - 对颜色也可以进行运算
  - 运算不要乱用，只推荐用在特殊场景

- 混入（mixin）和映射（map）

  ```less
  // 混入：讲编写好的代码插入到对应的位置，注意混入和继承两者的区别
  .single_ellipsis {
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
  }
  // 混入是可以传递参数的
  .box_border(@borderWidth: 2px, @borderColor: #eee) {
    border: @borderWidth solid @borderColor;
  }
  
  .container {
    .single_ellipsis();
    .box_border(10px,orange);
  }
  
  // 混入和映射结合使用：为了弥补 Less 不能自定义函数的缺陷
  .box_size {
    width: 100px;
    height: 100px;
  }
  .box1 {
    width: .box_size()[width];
  }
  
  .pxToRem(@px) {
    result: (@px / @htmlFontSize) * 1rem;
  }
  .box {
    width: .pxToRem(100)[result];
    font-size: .pxToRem(18)[result]
  }
  ```

  

- 继承（extend) 

  ```less
  // 继承：相当于在被继承类处加了一个并集选择器
  .box_border {
    border: 2px solid #eee;
  }
  .container {
    &:extend(.box_border) {
    }
  }
  // 继承相对于混入用的比较少，推荐用混入
  ```

- 内置函数

  ```less
  // Less 不能自定义函数，但是提供了一些内置函数
  
  // color: 将颜色转为 16 进制颜色
  // convert: 可以做一些单位的运算
  // ceil/floor/...（数学上的一些转换函数）: 向上/向下取值
  .box {
    color: color(skyblue);
    width: convert(100px, 'in');
    font-size: (18.5px);
  }
  
  ```

- 作用域（scope）

  ```less
  // 本地查找没有或者混入查找没有，那么优先使用离自己最近的变量
  @mainColor: red;
  .container {
    @mainColor: blue;
    
    .left {
      color: @mainColor;
    }
  }
  ```

- 注释（comment）

  ```
  // 单行注释
  /* 多行注释 */
  ```

- 导入（importing）

  ```
  // 导入的方式和 css 的方式是一样的
  // 导入一个 .less 文件，此文件下的所有变量都可以使用了
  // 如果导入的是 .less 拓展名，那么可以将拓展名去掉
  ```



## 5、认识 Sass 和 Scss

**Sass 和 css 的区别很大, 后来官方推出了全新的语法 Scss, 意思是 Sassy CSS, 它是完全兼容CSS 的**

- SCSS 语法也包括变量、嵌套、混入、函数、操作符、作用域等
- 包括更强大的控制语句、更灵活的函数、差值语法等
- 文档：https://sass-lang.com/guide



