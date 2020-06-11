# lifecycle

```javascript
new Vue({
  router,
  render: h => h(App),
  data: {
    message: 'Vue的生命周期'
  },
  beforeCreate: function() {
    console.group('------beforeCreate创建前状态------');
    console.log("%c%s", "color:red" , "el     : " + this.$el); //undefined
    console.log("%c%s", "color:red","data   : " + this.$data); //undefined 
    console.log("%c%s", "color:red","message: " + this.message) //undefined
  },
  created: function() {
    console.group('------created创建完毕状态------');
    console.log("%c%s", "color:red","el     : " + this.$el); //undefined
    console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化 
    console.log("%c%s", "color:red","message: " + this.message); //已被初始化
  },
  beforeMount: function() {
    console.group('------beforeMount挂载前状态------');
    console.log("%c%s", "color:red","el     : " + this.$el); //undefined
    console.log(this.$el);
    console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化  
    console.log("%c%s", "color:red","message: " + this.message); //已被初始化  
  },
  mounted: function() {
    console.group('------mounted 挂载结束状态------');
    console.log("%c%s", "color:red","el     : " + this.$el); //已被初始化
    console.log(this.$el);    
    console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化
    console.log("%c%s", "color:red","message: " + this.message); //已被初始化 
  },
  beforeUpdate: function () {
    console.group('beforeUpdate 更新前状态===============》');
    console.log("%c%s", "color:red","el     : " + this.$el);
    console.log(this.$el);   
    console.log("%c%s", "color:red","data   : " + this.$data); 
    console.log("%c%s", "color:red","message: " + this.message); 
  },
  updated: function () {
    console.group('updated 更新完成状态===============》');
    console.log("%c%s", "color:red","el     : " + this.$el);
    console.log(this.$el); 
    console.log("%c%s", "color:red","data   : " + this.$data); 
    console.log("%c%s", "color:red","message: " + this.message); 
  },
  beforeDestroy: function () {
    console.group('beforeDestroy 销毁前状态===============》');
    console.log("%c%s", "color:red","el     : " + this.$el);
    console.log(this.$el);    
    console.log("%c%s", "color:red","data   : " + this.$data); 
    console.log("%c%s", "color:red","message: " + this.message); 
  },
  destroyed: function () {
    console.group('destroyed 销毁完成状态===============》');
    console.log("%c%s", "color:red","el     : " + this.$el);
    console.log(this.$el);  
    console.log("%c%s", "color:red","data   : " + this.$data); 
    console.log("%c%s", "color:red","message: " + this.message)
  }
}).$mount('#app')

// render函数选项 > template选项 > outer HTML.
```

![](/assets/屏幕快照 2020-02-27 下午3.54.13.png)参考博客：[https://segmentfault.com/a/1190000011381906](https://segmentfault.com/a/1190000011381906)

### 什么是钩子函数

> 钩子函数是Windows处理消息机制的一部分，通过设置钩子，应用程序可以在**系统级对所有消息、事件进行过滤**，可以访问在正常情况下无法访问到的消息，钩子的**本质是一段用以处理系统消息的程序 **

![](/assets/vue lifecycle.png)

