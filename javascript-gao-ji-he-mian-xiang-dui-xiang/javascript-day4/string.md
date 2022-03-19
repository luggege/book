### String

#### String 对象属性

| 属性 | 描述 |
| :--- | :--- |
| length | 字符串的长度 |

#### String对象方法

| 方法 | 描述 |
| :--- | :--- |
| split\(\) | 把字符串劈成数组 |
| slice\(索引, 索引\) | 截取，**原字符串不变** |
| substring\(索引, 索引\) | 截取，**原字符串不变，**智能调换 |
| substr\(索引, 长度\) | 截取，**原字符串不变** |
| trim\(\) | 去除前后空白 |
| replace\(\) | 替换与正则表达式匹配的子串 |
| concat\(\) | 连接字符串 |
| includes\(\) | 是否包含某个子串 |
| toUpperCase\(\)/toLocaleUpperCase\(\) | 字符串转大写 |
| toLowerCase\(\)/toLocaleLowerCase\(\) | 字符串转小写 |
| charAt\(\) | 返回指定索引的字符 |
| charCodeAt\(\) | 返回指定索引的字符的Unicode编码 |
| indexOf\(\) | 检索字符串。 |
| lastIndexOf\(\) | 从后向前搜索字符串。 |
| match\(\) | 找到一个或多个正则表达式的匹配。 |
| search\(\) | 检索与正则表达式相匹配的值。 |
| toString\(\) | 返回字符串。 |
| valueOf\(\) | 返回某个字符串对象的原始值。 |
| anchor\(\) | 创建 HTML 锚。 |
| big\(\) | 用大号字体显示字符串。 |
| blink\(\) | 显示闪动字符串。 |
| bold\(\) | 使用粗体显示字符串。 |
| fontcolor\(\) | 使用指定的颜色来显示字符串。 |
| fontsize\(\) | 使用指定的尺寸来显示字符串。 |
| italics\(\) | 使用斜体显示字符串。 |
| link\(\) | 将字符串显示为链接。 |
| small\(\) | 使用小字号来显示字符串。 |
| strike\(\) | 使用删除线来显示字符串。 |
| sub\(\) | 把字符串显示为下标。 |
| sup\(\) | 把字符串显示为上标。 |
| fixed\(\) | 以打字机文本显示字符串。 |
| fromCharCode\(\) | 从字符编码创建一个字符串。 |

**例子：**

1.split：劈成数组

```javascript
var str = "I Love You";
str.split()            // ["I Love You"]
str.split('')          // ["I", " ", "L", "o", "v", "e", " ", "Y", "o", "u"]
str.split(' ')         // ["I", "Love", "You"]

var str1 = "I|Love|You";
str1.split()           // ["I|Love|You"]
str1.split('')         // ["I", "|", "L", "o", "v", "e", "|", "Y", "o", "u"]
str1.split(' ')        // ["I|Love|You"]
str1.split('|')        // ["I", "Love", "You"]
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

3.substring**\(索引, 索引\)**：  截取 **原字符串不会改变**

```javascript
 var str = "abcdefg"
 str.substring(0);   // abcdefg ==> str='abcdefg';
 str.substring(-1);  // abcdefg ==> str='abcdefg';  负数的话全部截取
 str.substring(1,3); // bc ==> str='abcdefg';
 str.substring(4,2); // (智能调换索引值) cd ==> str='abcdefg';
```

4.substr**\(索引, 长度\)**：  截取 **原字符串不会改变**

```javascript
var str = "abcdefg"
str.substr(0);      // abcdefg ==> str='abcdefg';
str.substr(-2);     // fg ==> str='abcdefg';        负数从后往前截
str.substr(1,3);    // bcd ==> str='abcdefg';
str.substr(4,2);    // ef ==> str='abcdefg';
```

5.trim：去除前后空白

```javascript
" aa bb cc ".trim()
"aa bb cc"
```

6.charAt：返回指定索引的字符

7.charCodeAt：返回指定索引的字符的Unicode编码

```javascript
'abcdef'.charAt()           // "a"
'abcdef'.charAt(2)          // "c"

'abcdef'.charCodeAt()       // 97
'abcdef'.charCodeAt(2)      // 99
```

#### 数字转换成字符串的三种方法

1. String\(n1\);
2. n1.toString\(\);
3. n1 + 'abc'

#### 去除字符串前后空白字符的兼容写法

```javascript
var str = "  hello world ";
if(!String.prototype.trim){
    String.prototype.trim = funcion(){
        return this.replace(/^\s+/,'').replace(/\s+$/,'');
    }
}
```



