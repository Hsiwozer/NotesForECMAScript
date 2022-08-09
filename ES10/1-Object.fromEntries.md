# Object.fromEntries

##### 与 ES8 中的 Object.entries 互为逆操作。

##### Object.fromEntries：将二维数组或 Map 转换成对象。

##### Object.entries：将对象转换成二维数组。

```js
// 二维数组
// const result = Object.fromEntries([
//     ['name', '尚硅谷'],
//     ['subject', 'Java, 大数据, 前端, 云计算']
// ]);

// Map
const m = new Map();
m.set('name', 'ATGUIGU');
const result = Object.fromEntries(m);
        
console.log(result);
```

