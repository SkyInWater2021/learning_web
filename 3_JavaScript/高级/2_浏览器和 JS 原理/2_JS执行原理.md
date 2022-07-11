## JavaScript 的执行原理



### 1、V8 引擎的执行原理

- V8 引擎的定义是什么？

- V8 引擎的架构

  - Parse模块
  - Lgnition模块
  - TurboFan编译器

  ![image-20220709170033843](https://tva1.sinaimg.cn/large/e6c9d24ely1h40s64nv00j22460iwdk8.jpg)



### 2、JavaScript 代码的执行原理

- 不同的版本有不同的描述
- ECMA3之前、ECMA5 和 ECMA6、TC39三个版本中用的术语有所区别，但整体思路大体相同



- 初始化全局变量（Global Object）
- 执行上下文（Execution Contexts）