# CSS布局

```css
前两种方法一定不能设置width:100%;只能自适应左边定宽浮动的盒子剩下的宽度,否则是继承整个父盒子的宽度,然后会有超出的部分
//方法一: 左盒子定宽设浮动
left: {
    width: 100px;
    height: 100px;
    float: left;
}
right: {
    margin-left: 100px;
}

//方法二: 右边盒子设浮动,负边距
left: {
    width: 100px;
    height: 100px;
}
right: {
    float: left;
    margin-left: 100px;
    margin-top: -100px;
}

//方法三: 父盒子利用padding占位子
box: {
    padding-left: 100px;
    position: relative;
}
left: {
    width: 100px;
    height: 100px;
    position: absolute;
    left: 0;
    top: 0;
}
right: {
    width: 100%;  //可设可不设
}

//方法四: 利用弹性盒子
box: {
   display: flex;
}
left: {
    width: 100px;
    height: 100px;
}
right: {
    width: 100%;  //可设可不设
    flex: 1;
}
```

## 水平垂直居中一个盒子

```css
//方法一:
father {
    position: relative;
}
son {
    width: 200px;
    height: 200px;
    position: absolute;
    left: 50%;
    top: 50%;
    margin-left: -100px;
    margin-top: -100px;
}

//方法二:  好处: 不需要知道子元素宽高,但是存在兼容性问题
father {
    position: relative;
}
son {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
}

//方法三:  利用弹性盒子
father {
    display: flex;
    jusitify-content: center;
    align-items: center;
}
son {

}
```

## 多行文字垂直居中

1. 单行文字: 使用 line-height 与 height 同高即可解决
2. 多行文字: 给父盒子设置: display: table-cell; \(verticle-align: middle;\)作为表格单元格显示即可垂直居中

### 清除select标签浏览器默认样式

```css
/*去除下拉箭头*/
select {
    /*Chrome和Firefox里面的边框是不一样的，所以复写了一下*/
    border: solid 1px #000;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
}
/*隐藏ie的下拉箭头*/
select::-ms-expand {
    display: none;
}
```
