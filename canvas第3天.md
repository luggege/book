#绘制图片
##(需要配合加载完毕事件使用img.onload)
1.ctx.drawImage(img,x坐标,y坐标) 三参数

2.ctx.drawImage(img,x坐标,y坐标,指定位置x坐标,指定y坐标) 五参数

3.ctx.drawImage(img,指定图像位置x坐标,指定y坐标,要裁剪x方向大小,裁剪y大小,x坐标,y坐标,指定x坐标,指定y坐标) 九参数
#帧动画
绘制新的图画时,要先清除画布
##状态保存
ctx.save();把当前的状态(绘制环境的所有属性)copy一份进行保存.
##
ctx.restore();状态回滚
