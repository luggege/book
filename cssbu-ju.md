## 两列布局左边定宽右边自适应

```css
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
```



