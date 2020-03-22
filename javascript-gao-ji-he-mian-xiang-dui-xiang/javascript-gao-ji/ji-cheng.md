# 继承

## 继承

* 定义：自己没有的属性和方法,拿过别人有的来用,就叫继承
* 实现：利用原型中的成员可以被和其相关的对象共享这一属性

### 混入式继承

* for in  

### 原型继承

> ### 通过修改原型的结构，实现的继承是原型继承

１．继承原型的成员

２．直接替换原型对象\(手动添加constructor属性\)

３．利用混入的方式给原型对象添加成员

注意：使用替换原型的方式实现继承，现有原型中的成员就会丢失

### 经典继承

Object.create\(obj\)

#### 解决兼容性问题:

1. 检测浏览器是否支持 Object.create 方法,如果支持,直接返回 Object.create\(obj\) .如果不支持,手动添加给
2. 自定义函数,在函数内部判断是否 支持 Object.create 方法,如果不支持,手动添加


