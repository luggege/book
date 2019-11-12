#### mpvue的生命周期

```js
  beforeCreate(){
    console.log('``````````````beforeCreate数据观测data和事件event配置之前```````````');
    console.log(this.$el);    //undefined
    console.log(this.$data);  //undefined 
    console.log(this.message);//undefined
    console.log('``````````````beforeCreate数据观测data和事件event配置之前```````````');
  },
  created(){
    console.log('``````````````created数据观测data和事件event配置完成```````````');
    console.log(this.$el);   //undefined
    console.log(this.$data);
    console.log(this.message);
    console.log('``````````````created数据观测data和事件event配置完成```````````');
  },
  onLaunch(){
    console.log('``````````````onLaunch```````````'); 
    console.log(this.$el);
    console.log(this.$data);
    console.log(this.message);
    console.log('``````````````onLaunch```````````');
    checkNormalLogin("pages/message/main")
  },
  onLoad: function(){
    console.log('``````````````onLoad 一个页面只会调用一次```````````'); 
  },
  onShow: function(){
    console.log('``````````````onShow 监听页面显示```````````'); 
  },
  onReady: function(){
    console.log('``````````````onReady 监听页面初次渲染完成 可以和视图层进行交互```````````'); 
  },
  beforeMount(){
    console.log('``````````````beforeMount挂载```````````'); 
    console.log(this.$el);
    console.log(this.$data);
    console.log(this.message);
    console.log('``````````````beforeMount挂载```````````');
  },
  mounted(){
    console.log('``````````````mounted挂载完成```````````'); 
    console.log(this.$el);
    console.log(this.$data);
    console.log(this.message);
    console.log('``````````````mounted挂载完成```````````');
  },
  beforeUpdate(){
    console.log('``````````````beforeUpdate 数据更新时，虚拟DOM打补丁之前```````````'); 
  },
  updated(){
    console.log('``````````````updated 数据更改导致的虚拟DOM重新渲染和打补丁```````````'); 
  },
  beforeDestroy(){
    console.log('``````````````beforeDestroy 实例销毁之前调用 此时实例仍可用```````````'); 
  },
  destroyed(){
    console.log('``````````````destroyed 实例销毁之后调用 所有东西和事件解绑移除 子实例跟随一起销毁```````````'); 
  }
```

![](/assets/lifecycle.jpg)

