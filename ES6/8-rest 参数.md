# rest 参数

##### ES6 引入 rest 参数，用于获取函数的多余的参数，用来代替 arguments

##### 形式：(...变量名)，把一个分离的参数序列整合为一个数组，值是一个数组。

```js
// ES5 获取实参的方式
// function color() {
//     console.log(arguments);
// }
// color('red', 'yellow', 'blue');
// 输出为 arguments 对象

// rest 参数
function color(...args) {
    console.log(args);
}
color('red', 'yellow', 'blue');
// 输出为数组

// rest 参数必须要放到参数最后
function fn(a, b, ...args) {
    console.log(a); // 1
    console.log(b); // 2
    console.log(args); // [3, 4, 5, 6]
}
fn(1, 2, 3, 4, 5, 6);
```

