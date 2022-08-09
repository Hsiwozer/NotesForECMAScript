# Set

##### ES6 提供了新的数据结构 Set（集合）。它类似于数组，但成员的值都是唯一的，集合实现了 iterator 接口，所以可以使用「扩展运算符」和「for..of..」进行遍历。

1. #### 基本用法

   ```js
   // 声明一个 Set
   let s = new Set();
   let s2 = new Set(['red', 'yellow', 'blue', 'yellow', 'green']);
   
   console.log(s, typeof s); // Set(0) 'object'
   console.log(s2); //Set(4) {'red', 'yellow', 'blue', 'green'}
   ```

   **注：**集合中不包含重复元素，如果声明时含有重复元素，则会自动<font color="red">去重</font>。

2. #### 属性及方法

   | 属性和方法 |                    说明                     |
   | :--------: | :-----------------------------------------: |
   |    size    |             返回集合的元素个数              |
   |    add     |        增加一个新元素，返回当前集合         |
   |   delete   |          删除元素，返回 boolean 值          |
   |    has     | 检测集合中是否包含某个元素，返回 boolean 值 |
   |   clear    |              清空集合内的元素               |
   |  for...of  |                  遍历元素                   |

   

3. #### 应用

   ```js
   let arr = [1, 2, 3, 4, 5, 4, 3, 2, 1];
   // 1. 数组去重
   // let result = [...new Set(arr)];
   // console.log(result);
   
   // 2. 交集
   let arr2 = [4, 5, 6, 5, 6];
   // let result = [...new Set(arr)].filter(item => new Set(arr2).has(item));
   // console.log(result);
   
   // 3. 并集
   // let union = [...new Set([...arr, ...arr2])];
   // console.log(union);
   
   // 4. 差集
   let diff = [...new Set(arr)].filter(item => !(new Set(arr2).has(item)));
   console.log(diff);
   ```

   

