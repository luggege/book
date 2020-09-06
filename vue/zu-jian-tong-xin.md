### 父子组件之间传值

1. 父组件通过**属性**往子组件传值，子组件通过**props**接收
2. 子组件通过**$emit\('事件名', ‘参数’\)**往父组件传值，父组件通过**$on\('事件名', '运行fn'\)**

```js
// 父组件
<delete-dialog :visible.sync="deleteDialogVisible" title="我是title···" @commitDelete="commitDelete(arguments)" />

commitDelete(data) {
    console.log("成功删除了·····", data); // 成功删除了····· Arguments(2) [hello, world, callee: (...), Symbol(Symbol.iterator): ƒ]    
    console.log(data[0]);  // hello
    console.log(data[1]);  // world
}
```

```js
// 子组件
<template>
  <div>
    <el-dialog
      :visible="visible"
      custom-class="small_dialog"
      center
      @close="closeDialog">
      <p class="ac font16"></p>
      <span slot="footer">
        <el-button class="button white bg-deepblue" @click="$emit('commitDelete', 'hello', 'world')">
          确定
        </el-button>
        <el-button class="button bg-white border cancel" @click="closeDialog">取消</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    name: 'DeleteDialog',
    props: ['visible', 'title'],
    data() {
      return {

      }
    },
    methods: {
      closeDialog() {
        // 传入新值
        this.$emit('update:visible', false)
      }
    }
  }
</script>
```

### 非父子组件之间通信

引入公共实例文件bus.js，作为公共数控中央总线。通过**eventBus概念，充当第三者父组件**

1.first.vue

```js
import Bus from '../bus.js';
export default {
  name: 'first',
  data () {
    return {
      value: '我来自first.vue组件！'
    }
  },
  methods:{
    add(){// 定义add方法，并将msg通过txt传给second组件
      Bus.$emit('txt',this.value);
    }
  }
}
```

2.second.vue

```js
import Bus from '../bus.js';    
export default {
    name: 'second',
    data () {
        return {
    }
    },
    mounted:function(){
        Bus.$on('txt',function(val){//监听first组件的txt事件
            console.log(val);
        });
    }
}
```

**对于复杂情况，项目中更多的是使用状态管理模式vuex来获取相应参数**

