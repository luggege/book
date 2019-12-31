# 指令的使用

使用ng-options指令生成的option元素填充select元素

可以使用array或者object类型的数据，用法如下：

* for array data sources:
* * lable for value in array        
  * > 基本用法：（显示 array 对象的某一个属性值作为下拉名称）
  * > 显示更多：同一对象显示更多下拉名称（比如需要显示 o 对象的两个或更多个属性值作为一个下拉列表项）:
    >
    > ng-options = ”**\(o.attr1 + ‘-’ + o.attr2\)** for o in dataArr “
  * select as lable for value in array
  * > select: **是 ng-model 绑定的值**
    >
    > lable: **是下拉列表显示的值。**
  * label group by group for value in array
  * > 选项分组（将下拉选项按照 o 对象某一属性分组显示）：
    >
    > ng-options = ” \(o.attr1 + ‘-’ + o.attr2\) **group by o.attr3** for o in dataArr “
  * label disable when disable for value in array
  * label group by group for value in array track by trackexpr
  * label disable when disable for value in array track by trackexpr
  * label for value in array \| orderBy: orderexpr track by trackexpr \(for including a filter with track by\)
* for object data sources:
* * label for \(key, value\) in object
  * select as lable for \(key, value\) in object
  * label group by group for \(key, value\) in object
  * label disable when disable for \(key, value\) in object
  * select as lable group by group for \(key, value\) in object
  * select as lable disable when disable for \(key, value\) in object

**如何解决ng-options遍历渲染的option第一个为空的情况:** &lt;**option value="" selected hidden&gt;&lt;/option&gt;，给ng-model赋初始值即可**

