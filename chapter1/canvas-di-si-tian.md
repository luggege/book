# canvas day4

> 小鸟飞翔游戏

## 设计模式的使用

> 出了util外,所有模块都使用了沙箱模式另外这些模块还使用工厂模块bird模块使用了单利模式gameScene使用了观察者模式

## 继承的使用

> 出了util外,其他模块要么使用了原型覆写的继承方式,要么使用了混入式继承.

## 模块之间的依赖

> 几乎所有的模块多依赖util模块,所以它

需要先引入gameScene模块主函数模块依赖:gameScene/overScene

## util模块-extend: 实现混入继承-

loadImage: 图片加载器

## bird模块

-draw: 绘制鸟-updata: 更新小鸟下一帧绘制时需要的数据\#\#\#land模

块-draw: 绘制大地-updata: 更新下一帧绘制时需要的数据

## sky模块

* draw: 绘制天空
* updata: 更新下一帧绘制时需要的数据

  **pipe模块**

* draw: 绘制管道
* updata: 更新下一帧绘制时需要的数据

  **gameScene模块**

* addListener: 添加小鸟死亡事件的听众
* trrigerBirdOver: 通知听众

  **overScene模块**

* 绘制游戏结束场景

