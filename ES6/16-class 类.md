# class 类

##### ES6 提供了更接近很统语言的写法，引入了 Class（类）这个概念，作为对象的模板。通过 class 关键字，可以定义类。基本上，ES6 的class 可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的class 写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而己。

1. #### 类声明

   ```js
   class Phone {
       // 构造方法 名字不能改
       constructor(brand, price) {
           this.brand = brand;
           this.price = price;
       }
       // 方法必须使用该语法，不能使用 ES5 中的对象完整形式
       call() {
           console.log('call...');
       }
   }
   let apple = new Phone('苹果', 6999);
   
   console.log(apple);
   ```

   

2. #### 静态成员

   ###### 属于类本身，不属于实例对象。

   ```js
   class Phone {
       // 静态属性
       static name = '手机';
       static change() {
           console.log('change...');
       }
   }
   let apple = new Phone();
   console.log(apple.name); // undefinde
   console.log(Phone.name); // 手机
   ```

   

3. #### 对象继承与方法重写

   ###### 类似于 Java

   ```js
   class Phone {
       constructor(brand, price) {
           this.brand = brand;
           this.price = price;
       }
       call() {
           console.log('call...');
       }
   }
   class SmartPhone extends Phone {
       constructor(brand, price, color, size) {
           super(brand, price);
           this.color = color;
           this.size = size;
       }
       photo() {
           console.log('photo...');
       }
       game() {
           console.log('game...');
       }
     
     	// 重写父类 Phone 的 call 方法
       call() {
         console.log('videoCall...');
     	}
   }
   const apple = new SmartPhone('苹果', 6999, '蓝色', '5.5inch');
   console.log(apple);
   apple.call();
   apple.photo();
   apple.game();
   ```

   

4. #### get 和 set

   ```js
   class Phone {
       get price() {
           console.log('getPrice...');
           return 123;
       }
       set price(newVal) {
           console.log('setPrice...');
       }
   }
   let s = new Phone();
   // console.log(s.price);
   s.price = 'free';
   ```