# javascript基础复习

### instanceof

* 语法: 对象 instanceof 构造函数
* 判断构造函数的原型是否在该对象的原型链上

  **Function**

* 可当做构造函数,其原型是空函数,其原型的原型是Object.prototype\(空对象\).

   **在当前对象中,调用当前对象的其他方法,需要使用this** 

## 数组和字符串相关API

### 数组方法

1. slice**\(索引, 索引\)** 截取:    **原数组不会改变　一个参数索引包左不包右**

```javascript
var arr = [1, 2, 3, 4, 5];
arr.slice();      //[1, 2, 3, 4, 5] ==> arr=[1, 2, 3, 4, 5]
arr.slice(0);     //[1, 2, 3, 4, 5] ==> arr=[1, 2, 3, 4, 5]
arr.slice(-1);    //[5] ==> arr=[1, 2, 3, 4, 5]
arr.slice(2);     //[3, 4, 5] ==> arr=[1, 2, 3, 4, 5]
arr.slice(0, 2);  //[1,2] ==> arr=[1, 2, 3, 4, 5]
```

2. splice**\(索引, 个数, 替换内容\)** 删除/替换:   **原数组会改变** 返回删除截取出来的数组,原数组为**剩下的内容组成的数组**

```javascript
var arr = [1, 2, 3, 4, 5];
arr.splice();                      // [] ==> arr=[1, 2, 3, 4, 5];
arr.splice(0);                     // [1, 2, 3, 4, 5] ==> arr=[];所以可用来清空数组
arr.splice(-1);                    // [5] ==> arr=[1, 2, 3, 4];
arr.splice(2);                     // [3, 4, 5] ==> arr=[1, 2];
arr.splice(0, 3);                  // [1, 2, 3] ==> arr=[4, 5];
arr.splice(0, 2, '9', '8', '7');   // [1, 2] ==> arr=["9", "8", "7", 3, 4, 5];
```

3.push：数组尾部添加, 返回个数

4.pop：数组尾部删除,返回取出的那个值

5.unshift：数组头部添加, 返回个数

6.shift：数组头部删除,返回取出的那个值（都是对原数组进行操作）

7.indexOf：查索引, 未找到返回 -1

8.lastIndexOf：从后往前查索引，索引值不会变

9.valueOf：返回原数组

10.toLocaleString：转为字符串

11.toString: 同Array.join\(\)方法

```javascript
var aaa = [1, 2, 3, 4, 5]
aaa.toString()
"1,2,3,4,5"
```

12.isArray 判断是否是数组,是的话返回true

13.join 转换成字符串

```javascript
var arr = [1, 2, 3, 4, 5];

arr.join()              // 1,2,3,4,5
arr.join('')            // 12345
arr.join(' ')           // 1 2 3 4 5
arr.join(',')           // 1,2,3,4,5
arr.join('|')           // 1|2|3|4|5
arr.join('&')           // 1&2&3&4&5
```

14.sort 排序

15.reverse 数组反转

16.concat / Array.prototype.push.apply\(arr1,arr2\) 数组合并

> concat: arr1.concat\(b\) ：
>
> 1. 将后一个数组合并到前一个数组, 作为新数组返回, **原数组不会改变**; 
>
> 2. 合并时的长度无限制
>
> Array.prototype.push.apply\(arr1,arr2\)：
>
> 1. 数组合并后返回新数组的个数, **arr1改变, arr2不变;**
>
> 2. 合并时长度一般不超过十万

```javascript
var a = [1,2,3];
var b = [4,5];

b.concat(a)                       // [4, 5, 1, 2, 3, 4, 5]
console.log(b);                   // [4, 5]
console.log(a);                   // [1, 2, 3, 4, 5]

Array.prototype.push.apply(a,b)   // 5 
console.log(a);                   // [1, 2, 3, 4, 5]
console.log(b);                   // [4, 5]
```

![](../../.gitbook/assets/console%20%282%29.png)

### 字符串方法

1.split 劈成数组

```javascript
var str = "I Love You";
str.split()            // ["I Love You"]
str.split('')          // ["I", " ", "L", "o", "v", "e", " ", "Y", "o", "u"]
str.split(' ')         // ["I", "Love", "You"]

var str1 = "I|Love|You";
str1.split()           // ["I|Love|You"]
str1.split('')         // ["I", "|", "L", "o", "v", "e", "|", "Y", "o", "u"]
str1.split(' ')        // ["I|Love|You"]
str1.split('|')        // ["I", "Love", "You"]
```

2.slice**\(索引, 索引\)** ： 截取 **原字符串不会改变**

```javascript
var str = "abcdefg"
str.slice();        // abcdefg ==> str='abcdefg';
str.slice('');      // abcdefg ==> str='abcdefg';
str.slice(0);       // abcdefg ==> str='abcdefg';
str.slice(-2);      // fg ==> str='abcdefg';         负数从后往前截
str.slice(1);       // bcdefg ==> str='abcdefg';
str.slice(2,5);     // cde ==> str='abcdefg';
```

3.substring**\(索引, 索引\)**：  截取

```javascript
 var str = "abcdefg"
 str.substring(0);   // abcdefg ==> str='abcdefg';
 str.substring(-1);  // abcdefg ==> str='abcdefg';  负数的话全部截取
 str.substring(1,3); // bc ==> str='abcdefg';
 str.substring(4,2); // (智能调换索引值) cd ==> str='abcdefg';
```

4.**substr\(索引, 长度\)**：  ****截取

```javascript
var str = "abcdefg"
str.substr(0);      // abcdefg ==> str='abcdefg';
str.substr(-2);     // fg ==> str='abcdefg';        负数从后往前截
str.substr(1,3);    // bcd ==> str='abcdefg';
str.substr(4,2);    // ef ==> str='abcdefg';
```

5.trim 去除前后空白

```javascript
" aa bb cc ".trim()
"aa bb cc"
```

6.replace\(a,b\) 后边的替换前边的

7.concat 字符串连接

8.toUpperCase 字符串转大写

9.toLowerCase 字符串转小写

10.charAt：返回指定索引的字符

11.charCodeAt：返回指定位置字符的Unicode编码

```javascript
'abcdef'.charAt()           // "a"
'abcdef'.charAt(2)          // "c"

'abcdef'.charCodeAt()       // 97
'abcdef'.charCodeAt(2)      // 99

```

### 数字转换成字符串的三种方法

1. String\(n1\);
2. n1.toString\(\);
3. n1 + 'abc'

### 去除字符串前后空白字符的兼容写法

```javascript
var str = "  hello world ";
if(!String.prototype.trim){
    String.prototype.trim = funcion(){
        return this.replace(/^\s+/,'').replace(/\s+$/,'');
    }
}
```

