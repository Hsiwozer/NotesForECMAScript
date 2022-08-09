# String.prototype.matchAll

##### 得到正则批量匹配的结果。

```js
let str = `<ul>
                <li>
                    <a>肖申克的救赎</a>
                    <p>上映日期: 1994-09-10</p>
                </li>
            </ul>
            <ul>
                <li>
                    <a>阿甘正传</a>
                    <p>上映日期: 1994-07-06</p>
                </li>
            </ul>`;
const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/sg
const result = str.matchAll(reg);
const arr = [...result];
console.log(arr);
```

