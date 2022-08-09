# async 和 await

##### async 和 await 两种语法结合可以让异步代码像同步代码一样。

- #### async 函数

  - async 函数的返回值为 promise 对象
  - promise 对象的结果由 async 函数执行的返回值决定
  - 只要返回的不是 Promise 类型的对象，那么返回的结果就是成功的 Promise
  - 返回的如果是 Promise 类型的对象，那么返回的结果就根据该 Promise 返回的失败与否
  - 如果返回的是抛出错误，那么返回的结果是失败的 Promise

- #### await 表达式

  - await 必须写在 async 函数中
  - await 右侧的表达式一般为 promise 对象
  - await 返回的是 promise 成功的值
  - await 的 promise 失败了，就会拋出异常，需要通过 try...catch 捕获处理

- #### async 与 await 结合

  ```js
  const fs = require('fs');
  
  function readWeiXue() {
      return new Promise((resolve, reject) => {
          fs.readFile('./resources/为学.md', (err, data) => {
              if (err) {
                  reject(err);
              }
              resolve(data);
          })
      })
  }
  
  function readJinYeSi() {
      return new Promise((resolve, reject) => {
          fs.readFile('./resources/静夜思.md', (err, data) => {
              if (err) {
                  reject(err);
              }
              resolve(data);
          })
      })
  }
  
  function readCao() {
      return new Promise((resolve, reject) => {
          fs.readFile('./resources/草.md', (err, data) => {
              if (err) {
                  reject(err);
              }
              resolve(data);
          })
      })
  }
  
  async function main() {
      let weixue = await readWeiXue();
      let jinyesi = await readJinYeSi();
      let cao = await readCao();
  
      console.log(weixue.toString());
      console.log(jinyesi.toString());
      console.log(cao.toString());
  }
  
  main();
  ```

  

- 