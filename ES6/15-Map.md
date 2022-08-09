## Map

##### ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合。但是 “键” 的范围不限于字符串，各种类型的值（包括对象）都可以当作键。Map 也实现了 iterator 接口，所以可以使用「扩展运算符」和「for...of」进行遍历。

1. #### 基本用法

   ```js
   // 声明一个 Map
   let m = new Map();
   console.log(m, typeof m); //Map(0) 'object'
   ```

   

2. #### 属性和方法

   | 属性和方法 |                     说明                     |
   | :--------: | :------------------------------------------: |
   |    size    |             返回 Map 的元素个数              |
   |    set     |         增加一个新元素，返回当前 Map         |
   |    get     |              返回键名对象的键值              |
   |    has     | 检测 Map 中是否包含某个元素，返回 boolean 值 |
   |   clear    |           清空集合，返回 undefined           |

   ```js
   // 添加元素
   // 键是字符串，值是字符串
   m.set('name', '程序猿');
   // 键是字符串，值是方法
   m.set('change', function() {
       console.log('Hello World!');
   });
   // 键是对象，值是数组
   let key = {
       company: 'tiktok'
   };
   m.set(key, ['北京', '上海', '深圳']);
   
   // size 
   console.log(m.size); //3
   
   // 删除
   m.delete('name');
   
   // 获取
   console.log(m.get('change'));
   console.log(m.get(key));
   
   // 清空
   // m.clear();
   
   // 遍历
   for (let v of m) {
       console.log(v);
   }
   console.log(m);
   ```

   