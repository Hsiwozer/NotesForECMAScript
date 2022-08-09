# 扩展运算符与 rest 参数

##### Rest 参数与 spread 扩展运算符在 ES6 中已经引入，不过 ES6 中只针对于数组，在 ES9 中为对象提供了像数组一样的 rest 参数和扩展运算符。

- #### 扩展运算符

  ```js
  const colorOne = {
      r: 'red'
  }
  const colorTwo = {
      g: 'green'
  }
  const colorThree = {
      b: 'blue'
  }
  const color = {...colorOne,
      ...colorTwo,
      ...colorThree
  };
  console.log(color); //{r: 'red', g: 'green', b: 'blue'}
  ```

  

- #### rest 参数

  ```js
  function connect({
      host,
      port,
      ...user
  }) {
      console.log(host);
      console.log(port);
      console.log(user);
  }
  connect({
      host: '127.0.0.1',
      port: 3306,
      username: 'root',
      password: 'root',
      type: 'master'
  });
  ```

  

