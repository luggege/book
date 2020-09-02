# MVC和MVVM的区别

### **MVC的定义：**即model-view-controller（模型-视图-控制器）

1. Model（模型）：是应用程序中用于处理应用程序数据逻辑的部分。通常模型对象负责在数据库中存取数据。 
2. View（视图）：是应用程序中处理数据显示的部分。通常视图是依据模型数据创建的。（就是看到界面一切东西） 
3. Controller（控制器）：是应用程序中处理用户交互的部分。通常控制器负责从视图读取数据，控制用户输入，并向模型发送数据。（Controller是MVC中的数据和视图的协调者，也就是在Controller里面把Model的数据赋值给View来显示） 总之就是view操作会触发controller去改变model，然后model再去改变视图，这么以来，三个部分代码都分开来写，逻辑就会清晰很多。

### 脏检查

Angular内部的$watch会实时检查\(观察者模式,深度优先遍历\)$scope的值,当$scope的值发生变化时,就会触动$scope.$digest来将变化的值更新到视图中.手动设置.....也可将变化的值更新到视图中

### **MVVM定义：**即Model-View-ViewModel

1. Model 代表数据**模型**，也可以在Model中定义数据修改和操作的业务逻辑
2. View 代表UI**视图**，负责数据的展示 
3. ViewModel 负责监听 Model 中数据的改变并且控制视图的更新，**处理用户交互**操作
4. Model 和 View 并无直接关联，而是通过 ViewModel 来进行联系的，Model 和 ViewModel 之间有着**双向数据绑定**的联系。 

mvvm的设计原理是基于mvc的，所以说mvvm不算是一种创新，是一种改造，这其中的ViewModel便是一个小小的创新

最后它们之间的最大**区别**：mvvm它实现了View和Model的自动同步，也就是当Model的属性改变时，我们**不用再自己手动操作Dom元素**，来改变View的显示，而是改变属性后该属性对应View层显示会自动改变,因此开发者只需要专注对数据的维护操作即可。

举个例，vue.js就是如此：Vue实例中的data相当于Model层，而ViewModel层的核心是Vue中的双向数据绑定，即Model变化时VIew可以实时更新，View变化也能让Model发生变化。

整体看来，MVVM比MVC精简很多，不仅简化了业务与界面的依赖，还解决了数据频繁更新的问题，不用再用选择器操作DOM元素。因为在MVVM中，View不知道Model的存在，Model和ViewModel也观察不到View，这种低耦合模式提高代码的可重用性。

### 双向数据绑定的原理

首先利用defineProperty的get、set来定义获取属性，然后调用Ovserve方法，启用观察者模式，当数据发生变化时，会通知watcher重新计算，通过compile模版指令更新视图

