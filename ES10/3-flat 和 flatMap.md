# flat 和 flatMap

##### flat(n) 用于将多维数组转换为低维数组，默认一次下降一个维度，n可以指定下降几个维度，不写则默认1个。

```js
// const arr = [1, 2, 3, 4, [5, 6]];
// console.log(arr.flat()); //[1,2,3,4,5,6]

// const arr = [1, 2, 3, 4, [5, 6, [7, 8, 9]]];
// console.log(arr.flat()); //[1, 2, 3, 4, 5, 6, [7, 8, 9]]

const arr = [1, 2, 3, 4, [5, 6, [7, 8, 9]]];
console.log(arr.flat(2)); //[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```js
const arr = [1, 2, 3, 4];

// const result = arr.map(item => [item * 10]);
// console.log(result); //[[10],[20],[30],[40]]

const result = arr.flatMap(item => [item * 10]);
console.log(result); //[10, 20, 30, 40]
```

