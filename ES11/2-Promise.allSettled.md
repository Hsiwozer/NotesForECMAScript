# Promise.allSettled

##### 接收一个 Promise 对象数组，返回一个成功的 Promise 对象，返回的结果是一个Promise 对象数组，该结果中的每个 Promise 对象的状态取决于接收到的 Promise 对象的成功与否。

###### 而 Promise.all 与之不同，它需要其中的 Promise 对象数组中的每个 Promise 对象都成功，才返回成功的 Promise 对象。

```js
const p1 = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('商品数据-1');
    }, 1000)
});
const p2 = new Promise((resolve, reject) => {
    setTimeout(() => { // resolve('商品数据-2');
        reject('出错了');
    }, 1000)
});

// 调用 allSettled 方法
// const result = Promise.allSettled([p1, p2]);

// 调用 all 方法
const result = Promise.all([p1, p2]);

console.log(result);
```

