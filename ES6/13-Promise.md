# Promise

##### Prormise 是 ES6 引入的异步编程的新解决方案。语法 上 Promise 是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果。

1. promise 构造函数：Promise (excutor) {}

2) Promise.prototype.then 方法
3) Promise.prototype.catch 方法

- #### 基本语法

  Promise 异步操作有三种状态：pending（进行中）、fulfilled（已成功）和 rejected（已失败）。

  then 方法接收两个函数作为参数，第一个参数是 <font color="red">Promise 执行成功时的回调</font>，第二个参数是 <font color="red">Promise 执行失败时的回调</font>，**两个函数只会有一个被调用**。

  ```js
  // 实例化 Promise 对象
  const p = new Promise(function(resolve, reject) {
      setTimeout(function() {
          // let data = '数据库中的用户数据';
          // resolve 表示成功，会调用 Promise 执行成功时的回调
          // resolve(data);
        
        	let err = '数据读取失败';
          // reject 表示失败，会调用 Promise 执行失败时的回调
          reject(err);
      }, 1000)
  });
  // 调用 Promise 对象中的 then 方法
  p.then(function(value) {
      // Promise 执行成功时的回调
      console.log(value);
      // 输出 数据库中的用户数据
  }, function(reason) {
      // Promise 执行失败时的回调
      console.error(reason);
      // 输出 数据读取失败
  })
  ```

  

- #### Promise.prototype.then

  ###### then 方法的返回结果是 Promise 对象，对象状态由回调函数的执行结果决定

  1. 如果回调函数中返回的结果是 非Promise 类型的属性，状态为成功，返回值为对象的成功的值

  2. 如果回调函数中返回的结果是 Promise 类型的属性，状态取决于该 Promise 的返回的状态，即 resolve 为成功、reject 为失败。

  3. 如果回调函数中返回的结果抛出错误（throw），状态为失败，返回值为抛出的值。

     

  注意：<font color="red">**then 方法可以链式调用**</font>，可以有效解决<u>回调地狱</u>问题。

  ```js
  // 引入 fs 模块
  const fs = require('fs');
  const { resolve } = require('path/posix');
  
  // fs.readFile('./resources/为学.md', (err, data1) => {
  //     fs.readFile('./resources/静夜思.md', (err, data2) => {
  //         fs.readFile('./resources/草.md', (err, data3) => {
  //             let result = data1 + '\r\n' + data2 + '\r\n' + data3;
  //             console.log(result);
  //         });
  //     });
  // });
  
  // 使用 Promise 实现
  const p = new Promise((resolve, reject) => {
      fs.readFile('./resources/为学.md', (err, data) => {
          resolve(data);
      })
  });
  
  p.then((value) => {
      return new Promise((resolve, reject) => {
          fs.readFile('./resources/静夜思.md', (err, data) => {
              resolve([value, data]);
          });
      })
  }).then(value => {
      return new Promise((resolve, reject) => {
          fs.readFile('./resources/草.md', (err, data) => {
              // 压入
              value.push(data);
              resolve(value);
          });
      })
  }).then(value => {
      console.log(value.join('\r\n'));
  });
  ```

  

- #### catch 方法

  效果与 then 方法相似，用于失败的回调。

  ```js
  const p = new Promise((resolve, reject) => {
      setTimeout(() => {
          // 设置 p 对象的状态失败，并设置失败的值
          reject('出错啦');
      }, 1000)
  });
  
  // p.then((value) => {}, (reason) => {
  //     console.error(reason);
  // })
  
  p.catch(function(reason) {
      console.warn(reason);
  })
  ```

  