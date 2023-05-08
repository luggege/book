### translate、transform、transition、animation的区别和联系

* translate：移动，transform 的一个方法
* transform：变形
* * `transform：translate(10px, 20px) // 平移-量`
  * `transform：scale(2, 4)  // 缩放-倍数`
  * `transform：rotate(90deg)  // 旋转-角度`
  * `transform：skew(30deg, 20deg)  // 翻转-角度`
  * `transform：matrix(scale.x ,, , scale.y , translate.x, translate.y)  // 所有的2D转换方法组合在一起`
* transition：属性过渡：`transition: width/all 2s ease 0s(delay)`
* animation：关键帧动画，搭配@keyframes 使用
* `animation: animation-name animation-duration animatino-timing-function animation-delay animation-iteration-count animation-direction animtion-play-state animation-fill-mode`
* * animatino-timing-function：属性变换速率
  * animation-delay：整个animation执行之前的等待时间
  * animation-iteration-count：定义动画的播放次数，其通常为整数，默认是1,；取值为infinite，动画将无限次的播
  * animation-direction：主要用来设置动画播放方向
  * * normal 默认值，动画每次循环都是向前（即按顺序）播放
    * alternate（轮流），动画播放在第偶数次向前播放，第奇数次向反方向播放（animation-iteration-count取值大于1时设置有效
  * animtion-play-state：属性是用来控制元素动画的播放状态
  * * running，可以通过该值将暂停的动画重新播放，这里的重新播放不是从元素动画的开始播放，而是从暂停的那个位置开始播放 
    * paused，暂停播放
  * **注意**：使用animtion-play-state属性，当元素动画结束后，元素的样式将回到最原始设置状态（这也是为什么要引入animation-fill-mode属性的原因）
  * animation-fill-mod：默认情况下，动画结束后，元素的样式将回到起始状态，animation-fill-mode属性可以控制动画结束后元素的样式。主要具有四个属性值：
  * * none（默认，回到动画没开始时的状态）
    * forwards（动画结束后动画停留在结束状态）
    * backwords（动画回到第一帧的状态） 
    * both（根据animation-direction轮流应用forwards和backwards规则）



