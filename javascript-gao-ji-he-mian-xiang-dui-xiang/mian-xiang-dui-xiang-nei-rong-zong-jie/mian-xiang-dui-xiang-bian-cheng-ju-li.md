# 面向对象编程举例 {#面向对象编程举例}

> 设置页面中的`div`和`p`的边框为`1px solid red`

## 传统的处理办法 {#传统的处理办法}

```js
// 任务需求:
// 1> 获取div标签
var divs = document.getElementsByTagName( 'div' );

// 2> 遍历获取到的div标签
for (var i = 0; i < divs.length; i++) {

    //3> 获取到每一个div元素，设置div的样式

    divs[i].style.border = "1px dotted black";
}

// 4> 获取p标签
var ps = document.getElementsByTagName("p");

// 5> 遍历获取到的p标签
for (var j = 0; j < ps.length; j++) {

    // 获取到每一个div元素 设置p标签的样式
    ps[j].style.border = "1px dotted black";
}
```

## 使用函数进行封装优化 {#使用函数进行封装优化}

```js
// 通过标签名字来获取页面中的元素 
function tag(tagName) {

    // var dvs = document.getElementsByTagName(tagName); 
    // return dvs; 
    return document.getElementsByTagName(tagName);
}

// 封装一个设置样式的函数 
function setStyle(arr) {

    for (var i = 0; i < arr.length; i++) {

        // 获取到每一个div元素 
        arr[i].style.border = "1px solid #abc";
    }
}

var dvs = tag("div");

var ps = tag("p");
setStyle(dvs);
setStyle(ps);
```

## 使用面向对象的方式 {#使用面向对象的方式}

```js
// 更好的做法：是将功能相近的代码放到一起 
var itcast = {
    getEle: {
        tag: function(tagName) {

            return document.getElementsByTagName(tagName);
        },
        id: function(idName) {

            return document.getElementById(idName);
        }
    },
    setCss: {
        setStyle: function(arr) {

            for (var i = 0; i < arr.length; i++) {
                arr[i].style.border = "1px solid #abc";
            }
        },
        css: function() {},
        addClass: function() {},
        removeClass: function() {}
```



