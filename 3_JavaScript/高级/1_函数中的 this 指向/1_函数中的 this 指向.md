## JavaScript 中的 this 指向相关问题



### 1、关于 this 的指向

- JavaScript 在执行函数时，会给 this 绑定一个值

- this 的绑定和函数定义的位置没有关系，只和调用方式调用位置有关
- this 的绑定的值是在函数执行的时候才被确定的

### 2、关于 this 的绑定规则

- **规则一 默认绑定**

  - 独立函数调用时，在非严格模式下，this 的指向是 window，严格模式下是 undefined

    ```js
    			// 1. 普通函数
          function foo() {
            console.log("foo", this);
          }
          foo(); // window
    
          //  2. 定义在对象中的函数
          const obj = {
            foo: function () {
              console.log("obj", this);
            },
          };
          const bar = obj.foo;
          bar(); //window
    
          // 3. 高阶函数
          function text(fn) {
            fn();
          }
          text(obj.foo); //window
    ```


- **规则二 隐式绑定**

  - 当函数被某个对象调用时，浏览器引擎自动实现的绑定，将 this 指向这个对象

    ```js
    			function foo() {
            console.log("foo", this);
          }
          const obj = {
            name: "obj",
            bar: foo,
            baz: function () {
              console.log("baz", this);
            },
          };
    
          const obj2 = {
            name: "obj2",
            baz: obj.baz,
            obj,
          };
    
          obj.bar(); // obj
          obj.baz(); // obj
    
          obj2.obj.bar(); // obj
          obj2.obj.baz(); // obj
          obj2.baz(); // obj2
    ```

- **规则三 显式绑定**

  - apply、call

    ```js
    			function foo(...args) {
            console.log("foo", this, ...args);
          }
    
          foo(); // window
    
          foo.call(123, 1, 2, 3); // Number(123), 1 2 3
          foo.apply("apply", [1, 2, 3]); // String(apply), 1 2 3
    
          foo.call({ name: "apply", age: 18 }); // {apply:'apply'}
          foo.apply({}); // {}
    ```

  - bind   MDN文档：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind

    ```js
    			// bind 方法创建了一个新的绑定函数(BF, bound function)
          // 绑定函数是一个 exotic function object(怪异函数对象，ECMAScript 2015 中的术语)
          // 在 bind() 被调用时，这个新函数的 this 被指定为 bind() 的第一个参数，而其余参数将作为新函数的参数，供调用时使用
          // MDN 文档解释:
          // https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind
    
          const obj = {
            name: "bind",
          };
          const bar = foo.bind(obj, 1, 2, 3);
          const baz = foo.bind(123, 1, 2, 3);
    
          bar(); // { name: "bind" }, 1, 2, 3
          bar(4, 5, 6); // { name: "bind" }, 1, 2, 3, 4, 5, 6
    
          baz(); // Number(123), 1, 2, 3
    ```

  - 显式绑定中的细节

    ```js
    			// 在非严格模式下，显式指定的 this 如果一个基本类型,且该基本类型有对应的包装类，则会自动转换为该包装类型
          // 如果没有该基本类型没有对应的包装类型,则会指向 window
          // 在严格模式下,则不会进行包装类型的转换, 传入的 this 参数是啥,this 指向就是啥
    
          // 非严格模式
          foo.call(undefined, [1, 2, 3]); // Window, 1 2 3
          foo.apply(null, [1, 2, 3]); // Window, 1 2 3
          foo.call(123); // Number(123)
          // 严格模式
          foo.call(undefined, [1, 2, 3]); // undefined, 1 2 3
          foo.apply(null, [1, 2, 3]); // null, 1 2 3
          foo.call(123); // 123
    
           // 关于包装类
          const num = new Number(1);
          const str = new String("123");
          const flag = new Boolean(true);
          console.log(num, typeof num, "--number"); // Number(1) 'object' '--number'
          console.log(str, typeof str, "--string"); // String('123') 'object' '--string'
          console.log(flag, typeof flag, "--boolean"); // Boolean(true) 'object' '--boolean'
    
          // 对象
          const newObj = new Object();
          console.log(newObj, typeof newObj, "--object"); // {} 'object' '--object'
    ```

- **规则四 new 绑定**

  - JavaScript 中的函数可以当做一个类的构造函数来使用,也就可以使用 new 关键字

    ```js
    			// 使用 new 关键字来调用函数时,会执行四步操作
          // 1. 创建一个新的空对象
          // 2. 这个新对象会被执行prototype连接
          // 3. 这个新对象会绑定到函数调用的this上(this的绑定在这个步骤完成)
          // 4. 如果函数没有返回其他对象，表达式会返回这个新对象
    
          function Persion(name) {
            console.log(this, "开始执行函数体"); // Persion{}
            this.name = name;
          }
          const student = new Persion("小明");
          console.log(student); // Persion{ name: "小明" }
    ```

### 3、关于 this 绑定规则优先级

- 默认绑定优先级最低

- 显式绑定高于隐式绑定

- 显式绑定中 bind 绑定高于 apply 和 call 绑定

- new 绑定高于隐式绑定

- new 绑定高于bind 绑定（new 绑定不能和 apply 和 call 一起使用）

  ```js
  			"use strict";
        function foo() {
          console.log("foo", this);
        }
  
        // 1. 显式绑定高于隐式绑定
        const obj_0 = {
          name: "obj1",
          foo: foo,
        };
        obj_0.foo.call("callThis"); // callThis
  
        // 2.bind 绑定高于隐式绑定
        const bar = foo.bind("BindThis");
        const obj_1 = {
          name: "obj_1",
          bar,
        };
        obj_1.bar(); // BindThis
  
        // 3. bind 绑定高于 call 和 apply 绑定
        bar.call("callThis"); // bindThis
        bar.apply("callThis"); // bindThis
  
        // 4. new 绑定高于隐式绑定
        const obj_2 = {
          name: "obj_2",
          obj_2_foo: function () {
            console.log("obj_2_foo", this, this === obj_2);
          },
        };
        new obj_2.obj_2_foo(); // obj_2_foo obj_2_foo{} false
  
        // 4. new 绑定高于显式绑定(new 绑定不能和 call 和 apply 绑定一起使用)
        new bar(); // foo foo{}
  ```

### 4、关于 this 绑定规则之外的情况

- 忽略显式绑定

- 间接函数引用

- 箭头函数

  ```js
  			// 1. 显式绑定中指定 this 为 null 或者 undefinde 时,使用默认绑定规则
        function foo() {
          console.log(this);
        }
  
        foo.call(null); // 严格模式: null 非严格模式: Window
        foo.call(undefined); // 严格模式: undefined 非严格模式: Window
  
        // 2. 创建一个函数的间接引用, 这种情况使用默认绑定规则
        const obj_1 = {
          name: "obj_1",
          foo,
        };
        const obj_2 = {
          name: "obj_2",
        };
        obj_1.foo(); // {name: 'obj_1', foo:f}
        // TIP: 以小括号中括号等开始的代码一定要注意分号的使用,在上一行代码结束加上分号,或者在代码开始前加上分号
        (obj_2.foo = obj_1.foo)(); // 严格模式下: undefined 非严格模式下: Window
  
        // TIP: 关于箭头函数(Arrow Function)
        // 1 普通函数中都会有 this 标识符, 但是在箭头函数中压根没有 this
        // 2 箭头函数不会绑定 this、arguments 属性
        // 3 箭头函数不能作为构造函数来使用(不能和 new 一起使用, 会抛出错误)
        // 4 箭头函数的编写优化:
        //  4.1 只有一个参数时,小括号可以省略
        //  4.2 如果函数执行体只有一行代码,那么大括号可以省略,且这行代码的返回值作为整个函数的返回值
        //  4.3 如果函数执行体只有返回一个对象, 那么需要给这个对象加上()
  
        // 3. 箭头函数是根据外层作用域来决定 this 的绑定值的
        // TIP: let 和 const 声明的变量不在顶层对象中,而在 script 块儿级作用域中
        var flag = "varGlobal";
        const const_flag = "constGlobal";
        window.windowFlag = "windowFlag";
        console.log(window.flag); // varGlobal
        console.log(window.const_flag); // undefined
        console.log(window.windowFlag); // windowFlag
  
        const bar = () => {
          console.log(this.flag);
        };
  
        const obj_3 = {
          flag: "obj_2",
          bar,
          baz: function () {
            const flag = "bazFlag";
            const foo = () => {
              console.log(this.flag);
            };
            return foo;
          },
        };
  
        bar(); // varGlobal
        bar.call({ flag: "callFlag" }); // varGlobal
        obj_3.bar(); //varGlobal
  
        const fn1 = obj_3.baz();
        fn1(); // obj_3  foo -> baz
        fn1.call({ flag: "callFlag" }); // obj_3
  
  			// 思考：箭头函数中 this 的应用
  			// 1. 嵌套函数时，内部函数需要访问外部函数变量时
  			// 等等...
  ```



### 5、关于 this 在内置函数中的指向

- setTimeout，forEach，onclick 等类似的内置函数，其调用方式如何确定呢？
- 通过经验，总结，猜测判断
- forEach 可以传入第二个参数，显示绑定 this

  ```js
  			// "use strict";
        var flag = "varGlobal";
        // 1. onclick 中this 绑定规则的推测  => 推测为 默认绑定
        const box = document.getElementById("divId");
        box.onclick = () => {
          const flag = "boxGlobal";
          console.log(this, this.flag); // Window varGlobal
        };
        // box.onclick = function () {
        //   const flag = "boxGlobal";
        //   console.log(this, this.flag); // box元素  undefined
        // };
  
        box.onclick.call({ flag: "callThis" }); // { flag: "callThis"} callThis
  
        // 2.setTimeout 中 this 绑定规则的推测  => 推测是通过 apply 或 call 显式绑定的 Window
        const obj = {
          flag: "objFlag",
          foo: function () {
            console.log(this, this.flag);
          },
        };
        const baz = obj.foo.bind({ flag: "bindFlag" });
        const fn = new baz();
        setTimeout(obj.foo); // Window  严格模式下也为 Window
        setTimeout(baz); // bindFlag
  
        // 3. forEach 中 this 绑定规则的推测  => 推测是通过 apply 或 call 显式绑定的全局 this
        // 且第二个参数是通过call 或者 apply 来显示绑定的
        const obj_2 = {
          flag: "obj2Flag",
          foo: function (item) {
            console.log(item, this);
          },
          baz: (item) => {
            console.log(item, this);
          },
        };
        const fn1 = obj_2.foo.bind("bindThis");
        [1].forEach(obj_2.foo); // Window  严格模式下为 undefined
        [1].forEach(obj_2.baz); // Window  严格模式下为 Window
        [1].forEach(fn1); // String(BindThis)
        [1].forEach(obj_2.foo, "customThis"); // String(customThis)
        [1].forEach(obj_2.baz, "customThis"); // Window  严格模式下为 Window
        [1].forEach(fn1, "customThis"); // String(BindThis)
  ```





