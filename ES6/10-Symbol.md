# Symbol

##### ES6 引入了一种新的原始数据类型 Symbol ，表示独一无二的值，最大的用法是用来定义对象的唯一属性名。

##### ES6 数据类型除了 Number 、 String 、 Boolean 、 Object、 null 和 undefined ，还新增了 Symbol 。

1. #### 基本用法

   ```js
   // 创建 Symbol
   let s = Symbol();
   console.log(s, typeof s); // Symbol() 'symbol'
   
   let s2 = Symbol('Hello');
   let s3 = Symbol('Hello');
   console.log(s2 === s3); // false
   
   // Symbol.for() 创建
   let s4 = Symbol.for('Hello');
   console.log(s4, typeof s4); // Symbol(Hello) 'symbol'
   
   let s5 = Symbol.for('Hello');
   console.log(s4 === s5); // true
   ```

   ##### 注意事项: 不能与其他数据进行运算

2. #### Symbol 创建对象属性

   ```js
   // 向对象中添加方法 up down
   let game = {
       name: '俄罗斯方块',
       up() {
           console.log('...up');
       },
       down() {
           console.log('...down');
       }
   }
   // 声明一个对象
   let methods = {
       up: Symbol(),
       down: Symbol()
   };
   game[methods.up] = function() {
       console.log('up...');
   }
   game[methods.down] = function() {
       console.log('down...');
   }
   console.log(game);
   ```

   ```js
   let youxi = {
       name: '狼人杀',
       [Symbol('say')]: function() {
           console.log('say...');
       },
       [Symbol('zibao')]: function() {
           console.log('zibao...');
       }
   }
   console.log(youxi);
   ```

   

3. #### 内置值

   |           方法            |                             说明                             |
   | :-----------------------: | :----------------------------------------------------------: |
   |    Symbol.hasInstance     | 当其他对象使用 instanceof 运算符，判断是否为该对象的实例时，会调用这个方法 |
   | Symbol.isConcatSpreadable | 对象的 Symbol.isConcatSpreadable 属性等于的是一个布尔值，表示该对象用于 Array.prototype.concat() 时，是否可以展开 |
   |    Symbol.unscopables     |  该对象指定了使用 with 关键字时，哪些属性会被 with 环境排除  |
   |       Symbol.match        | 当执行了 str.match(myObject) 时，如果该属性存在，会调用它，返回该方法的返回值 |
   |      Symbol.replace       | 当该对象被 str.replace(myObject) 方法调用时，会返回该方法的返回值 |
   |       Symbol.search       | 当该对象被 str.search(Object) 方法调用时，会返回该方法的返回值 |
   |       Symbol.split        | 当该对象被 str.split(Object) 方法调用时，会返回该方法的返回值 |
   |      Symbol.iterator      | 对象进行 for...of 循环时，会调用 Symbol.iterator 方法，返回该对象的默认遍历器 |
   |    Symbol.toPrimitive     | 该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值 |
   |    Symbol.toStringTag     |     在该对象上面调用 toString 方法时，返回该方法的返回值     |
   |      Symbol.species       |                 创建衍生对象时，会使用该属性                 |