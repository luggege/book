# 解决代码太长的问题

1.字符串拼接 换行;  
2. 使用模板;  
3. 使用反引号实现换行

1. 利用`+`连接字符串

```js
var func = new Function( 'a', 'b', 'c',
    'var res = a > b ? a : b;' +
    'res = res > c ? res : c;' +
    'return res;'
);
```

1. 利用字符串特性

```js
function foo( a, b, c ) {
    var res = a > b ? a : b;
    res = res > c ? res : c;
    return res;
}
var func = new Function( 'a', 'b', 'c', 'return foo( a, b, c );');
```

2. ES6 语法（很少有浏览器实现） 使用键盘左上角的\`\`\`\`\`表示可换行字符串的界定符，之前我们用的是单引号或者双引号来表示一个字符串字面量，在ES6中可以用反引号来表示该字符串可换行。

3. \(最终\)利用 DOM 的特性完成该方法

```js
<div id= "code" style="display:none">
    var res = a > b ? a : b;
    res = res > c ? res : c;
    return res;
</div>

<script>
    var txt = document.getElementbyId("code").innerHtml + ' ';
    var func = new Function('a', 'b', 'c', txt);
</script>
```



