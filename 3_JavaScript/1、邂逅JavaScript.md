# 邂逅 JavaScript



## 1、编程语言

- 编程语言特点
  - 数据和数据结构
  - 指令及流程控制
  - 引用机制和重用机制
  - 设计哲学
- 常见的编程语言
- 编程语言的发展历史
  - 机器语言
  - 汇编语言
  - 高级语言



## 2、认识 JavaScript 语言

- JavaScript（通常缩写为 JS），是一种高级的，解释型的语言
- JavaScript 是一门基于原型，头等函数的语言，是一门多范式的语言，支持支持面向对象程序设计，指令式编程以及函数式编程

- JavaScript 的起源
  - 作者：Brendan Eich 花费大概十天时间设计出来的
  - ...
- JavaScript 的组成
  - JavaScript 是对 ECMAScript 标准的一种实现
  - 除了基本实现之外，还包括 DOM操作、BOM操作
  - ECMA5: 2009年发布
  - ECMA6: 2015年发布
- JavaScript 的运行：浏览器内核（WebCore => 负责HTML 解析、布局、渲染等工作，JSCore => 解析、执行 JS 脚本）
  - Gecko：早期被 Netscape 和 Mozilla Firefox 使用
  - Trident：微软开发，被 Ie4-Ie11 浏览器使用，但是 Edge 已经转向了 Blink
  - Webkit：苹果基于KHTML开发、开源的，用于 Safair，Chrome之前也在使用
  - Blink：是 Webkit 的一个分支，Google 开发，目前运用于 Chrome、Edge、Opera等
- JavaScript 的运行：JS 引擎
  - SpiderMonkey：第一款 JS 引擎，由 Brendan Eich 开发
  - Chakra：微软开发
  - JavaScriptCore：Webkit 中的 JS 引擎，Apple 公司开发
  - V8：Google 开发的强大的 JS 引擎
  - 等等...
- JavaScript 应用
  - Web 开发
  - 移动端开发
  - 桌面应用开发
  - 后端开发
  - 等等...
- JavaScript 的编写方式
  - HTML 内部
  - Script 标签中
- 浏览器禁止 JavaScript ：`noscript`标签 <noscript>您的浏览器不支持 JavaScript</noscript>



## 3、JavaScript 的交互方式

- 弹窗查看：alert()
- 浏览器控制台查看：console.log()
- 浏览器页面查看：document.write()
- 浏览器接受用户输入：prompt()



## 4、Chrome 调试工具



## 5、JavaScript 语句

- 语句（statements）：向浏览器发出的指令，通常表示一个操作或行为（Action）
- 一条语句通常会在最后添加一个分号（semicolon）表示语句结束
- 当存在换行符（line break）时，大多数情况可以省略分号，JavaScript 将换行符理解为“隐式”的分号



## 6、JavaScript 中的注释	

```js
// 单行注释
/*多行注释*/
/**
* 文档注释
*/
```



## 7、JavaScript 中的变量

- 变量：变化数据的记录，相当于存放数据的容器
- 变量声明：通过关键字 `var`
- 变量命名规范
  - 第一个字符必须是`$`、`_`、字母开头
  - 其他字符可以使字母、数字、下划线、美元符号
  - 不能使用关键字和保留字命名：
  - 关键字和保留字：https://developer.mozilla.org/zh-CN/docs/web/javascript/reference/lexical_grammar

## 

## 8、JavaScript 中的数据类型

- 8 中基本数据类型（7 种原始类型，一种复杂类型）
  - Number
  - String
  - Object
  - Boolea
  - Undefined
  - Null
  - Symbol
  - Bigint
- 操作符：`typeof` 可以获取到变量的类型，typeof() 并不是代表一个函数，而是将小括号里面当成一个整体



## 9、字符串中的转义字符

- `\'`、`\"`、`\\`、`\n`、`\r`、`\t`、`\b` 等等



## 10、JavaScript 中的操作符

- `+` `-` `*` `/` `%` `** `等等...
- `++` `--`
- 运算符优先级：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Operator_Precedence
- 比较运算符

- == 和 === 的区别



## 11、JavaScript 分支语句

- 程序的执行顺序
- 代码块的理解
- 条件判断
  - if 语句
  - switch 语句
  - 三元运算符
  - 逻辑运算符



## 12、JavaScript 循环语句（遍历(traversal)、迭代(iteration)）

- 循环语句：while、do while、for
- 循环控制：break、continue



## 13、认识 JavScript 中的函数

- 程序中 foo、bar、baz 这些名词的由来，目前已经成为了编程术语的一部分
  - 一种说法来自Digtal（迪吉多，数字设备公司，成立于1957 年的美国电脑公司）的说明手册流行起来的
  - 一种说法来自电子学中的反转信号 foo
  - 一种说法是应为 foo 出现在了一个漫画当中，在漫画中代表"好运",于中文“福”发音类似，所以流行起来的
- 函数的声明和调用
  - 函数的命名规范：
  - 函数的参数
  - 函数的返回值
  - 函数中的 arguments（类数组，是对象类型）
  - 函数中的变量
  - 函数的递归使用
- 函数表达式
- 头等函数的特点
  - 可以赋值给变量
  - 让函数在变量中传递
  - 可以作为另一个函数的参数和返回值
  - 等等...
- 回调函数( callback function )
- 匿名函数( anonymous )
- 立即执行函数



## 14、对象



## 15、数组



## 16、堆内存和栈内存



## 17、认识构造函数



## 18、原始类型的包装类

