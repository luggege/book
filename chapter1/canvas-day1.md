# canvas day1

## 定义

* 是一个用来展示绘图效果的 标签,行内块元素.同一页面可以拥有多个canvas标签.
* 通过getContext方法打开
* 画布大小默认大小300\*150, 需通过属性改变大小,不加单位,默认px.

### canvas绘图步骤

1. 先移动钢笔到指定位置 ctx.moveTo\(\)
   * 有了 ctx.stroke\(\) 之后,不设当前位置也可以
2. 开始画线条 ctx.lineTo\(\)
3. 描边路径 ctx.stroke\(\)

### 设置描边色

* ctx.strokeStyle = css任意的颜色表示
* 颜色设置,必须放在绘制之前

### 设置线宽

* ctx.lineWidth = 6; \(属性,无单位\)

### 闭合路径

* ctx.closePath\(\); 解决锯齿

 **清除当前路径,开启新路径 ctx.beginPath\(\)** 

### 填充

* ctx.fill\(\);

### 填充色 ctx.fillStyle = 颜色表示;

#### 填充满足非零环绕原则

* 用来判断哪些区域属于路径内
* 顺时针 +1; 逆时针 -1; 非0,即为路径内
* 奇数边的区域一定在路径内

 **canvas绘制线条时,会先向左偏移线宽的一半,线宽为奇数,那么边缘的颜色值会缩减一半** 

### 线帽样式 ctx.lineCap

1. butt 默认
2. square 增长线头\(线头各增加线宽的一半\)
3. round 圆线头

### 线焦点样式 ctx.lineJoin

1. miter 默认 尖角
2. round 圆角
3. bevel 斜面

## 内置画矩形的API

1. ctx.rect\(起始x轴坐标, 起始y轴坐标,宽,高 \);
2. ctx.fillrect\(\);
3. ctx.strokeRect\(\);

#### 清除画布

* ctx.clearRect\(\),清除之后,可以重新绘制图形

#### 设置虚线 ctx.setLineDash\( \[5,3\] \);

1. 传一个代表空白部分和实线部分都是这个值
2. 多个值: 按顺序排\(实线开始\),偶数值是一组

#### 获取线条绘制规则 ctx.getLineDash\(\)

#### 设置偏移量 ctx.lineDashOffset = 3;

