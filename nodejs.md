强类型  弱类型

#SeaJs


###define
定义模块   同( Angular.moudule() )

##module.exports和exports的区别
### 1. module.exports
本身就是一个空对象,是用来打破封装性, 直接用等于的方式写,返回 字符串 数字 函数 对象 等方法, ** 连续写会发生覆盖 **

### 2. exports
只是module.exports的缩写形式.当需要暴露多个内容的时候,需要通过.的方式来给module.exports添加属性,方法,对象.

** 二者最终暴露出去的都是module.exports这个对象.前者是对module.exports的改写,暴露之后直接用;后者是对其添加了内容,暴露之后需通过.的方式取出 **

##seajs与requirejs
前者懒加载,后者有限加载

