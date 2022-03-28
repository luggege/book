### TypeScript

> Javascript是弱类型语言，有了TS可以写强类型语言，更面向对象的思想

* 基本数据类型：number、string、boolean、undefined、null、any
* * 参数后面跟冒号指定类型
* 数组

* * ```js
    // 1. 类型后面跟[]
    const list1: number[] = [1, 2, 3];
    // 2. 数组泛型 Array<元素类型>
    const list2: Array<number|string> = [1, '2', 3];
    ```

* 元组：存放多类型的值，
* ```js
  const list1: [number, string, boolean] = [1, '2', true]
  ```

* 枚举
* ```js
  enum Status {
  	ordered=0,
  	bePaid=1,
  	paid=2,
  	complete=3,
  }

  console.log(Status.paid); // 2
  ```

* 函数类型申明
* * **可选参数使用 “?” 符号声明**，**可选参数**、**函数参数的默认值**需要声明在必选参数之后。

  * 还可以在函数后指定冒号来声明函数的返回值类型
* ```js
  // 定义函数返回值为空
  // 给传入的参数定义类型
  // 给传入的参数赋予默认值
  const speak = function(nickname?: string, content: string='Hello'): void {
    console.log('speak', nickname, content);
  }
  speak();

  // 指定函数的返回值为 string
  function test(): string {
  	return 'str';
  }
  ```

* class、接口声明自定义类型

* ```js
  class Person {
    nickname: string;
    age: number;
  }

  const mayJun: Person = new Person();
  mayJun.age = 19;
  ```

* ```js
  interface Person {
    nickname: string;
    age: number;
  }

  function study(obj: Person) {
  	console.log(obj.nickname, obj.age);
  }

  study({ nickname: 'may', age: 20 });
  ```



