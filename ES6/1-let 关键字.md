# let 关键字

#### let 变量声明以及声明特性

- ##### 声明变量

  ```js
  let a;
  let b, c, d;
  let e = 100;
  let f = 200, g = 'hello', h = [];
  ```

  **注意：**<font color="red">let 只能声明一次</font>，var 可以声明多次。

  ```js
  // let name = 'xiaoming';
  // let name = 'lihua';
  // 不可行
  ```

  

- ##### 块级作用域

  ###### let 是在代码块内有效，var 是在全局范围内有效

  ```js
  {
    let a = 0;
    var b = 1;
  }
  a  // ReferenceError: a is not defined
  b  // 1
  ```

  **补充：**<font color="red">for 循环计数器很适合用 let</font>，此时 let 只在 for 循环内有效。

  ```js
  for (var i = 0; i < 10; i++) {
    setTimeout(function(){
      console.log(i);
    })
  }
  // 输出十个 10
  
  for (let j = 0; j < 10; j++) {
    setTimeout(function(){
      console.log(j);
    })
  }
  // 输出 0123456789
  ```

  

- ##### 不存在变量提升

  ###### let 不存在变量提升，var 会变量提升

  ```js
  console.log(a);  //ReferenceError: a is not defined
  let a = "apple";
   
  console.log(b);  //undefined
  var b = "banana";
  ```

  变量 b 用 var 声明存在变量提升，所以当脚本开始运行的时候，b 已经存在了，但是还没有赋值，所以会输出 undefined。

  变量 a 用 let 声明不存在变量提升，在声明变量 a 之前，a 不存在，所以会报错。

- ##### 不影响作用域链

  ```js
  {
      let city = 'ShangHai';
      function fn() {
          console.log(city);
      }
      fn();
      // 输出 ShangHai
  }
  ```