### 创建函数三种方式

> 函数是 js 中的一等公民，**函数**是唯一可以限定变量**作用域**的结构

1. 函数声明：`funtion fn() {}`
2. 函数表达式\(变量声明\)：`var fn = function() {}`（开发中使用居多，详情见（JavaScript预解析））
3. new Function：`var fn = new Function("console.log('1')")`

1. * Function函数所有的参数全都是字符串
   * Function函数的作用就是将所有的参数组合起来，变成一个函数
   * 如果不传参数，表示创建一个空函数
   * ```js
     //传统的方式
     function foo(){}

     //Function 
     var func = new Function();
     ```
2. * 如果只传一个参数，那么这个函数必然是函数体
   * ```js
     //传统的方式
     function foo(){
         console.log("你好");
     }

     //使用Function
     var func = new Function("console.log('你好');");
     ```
3. * 如果传多个参数，那么最后一个参数表示函数体，前面的参数代表将要创建的函数的参数 `new Function(arg1, arg2, arg3, ..., argN, body);`
   * ```js
     //传统的方式
     function foo(num){
         console.log(num);
     }

     //Function
     var func = new Function(){
         "num", "console.log(num);"
     };
     ```

     ```js
     // 两个数字, 打印其和
     var func = new Function(
      'num1','num2','console.log( num1 + num2);
     );
     ```

     ```js
     // 创建一个求三个数中最大数的函数.

     // 传统
     function foo ( a, b, c ){
         var res = a > b ? a : b;
         res = res > c ? res : c;
         return res;
     }

     // Function
     var func = new Function( 
         'a','b','c',
         'var res = a > b ? a : b;
         res = res > c ? res : c;
         return res;'
     )
     ```



