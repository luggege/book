### CSS3动画效果

```js
ul li:first-child{
    /*使用动画：动画名称 动画完成时间 速度曲线 开始时间 播放次数 是否下次反向播放 是否正在运行或暂停*/
    animation: jump 2s ease  3 alternate;
}
/*创建动画*/
@keyframes jump {
    0%{
        top:-100px;
        height: 80px;
        background-color: #734aff;

    }
    50%{
        top:-60px;
        height: 120px;
        background-color: #8cff31;

    }
    100%{
        top:-20px;
        height: 180px;
        background-color: #ff2513;
    }
}


@keyframes move {
    30%{
        /*!*设置动画*! 平移 旋转 缩放 倾斜*/
        transform: translate(100px,-100px) rotate(60deg) scale(5,5) skew(30deg,30deg);

    }
    60%{
        transform: translate(150px,-100px) rotate(120deg) scale(2,2) skew(60deg,60deg);

    }
    100%{
        transform: translate(200px,-200px) rotate(360deg) scale(4,4) skew(90deg,90deg);


    }
}
```



