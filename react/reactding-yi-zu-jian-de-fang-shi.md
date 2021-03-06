### 定义组件的两种方式

* 函数式组件

```js
// 首字母大写的标签
function App() {
  return (
    <div></div>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

* 类式组件

```js
import React, { Component } from 'react'

export default class App extends Component {
  // 给实例直接添加一个属性
  state = {}

  // 调用几次：1次
  constructor() {}

  // 调用几次：1（初始化）+ n（状态更新）次
  render() {
    return (
      <div onClick={this.handle}></div>
    )
  }

  // 调用几次：点几次调几次
  // this指向问题
  // 作为onclick的回调，所以不是通过实例调用的，而是直接调用，类中的方法默认开启局部的严格模式，所以this为undefined
  // handle() {
  //    // 该方法放在原型对象上，供实例使用
  // }
  // 自定义方法：赋值语句+箭头函数
  handle = () => {
    // 该方法放在实例上
    // 箭头函数：this取决于上下文（实例）
  }
}

ReactDOM.render(<App />, document.getElementById('root'));
```

#### ReactDOM.render\(\)做了什么

* React解析组件标签，找到了App组件
* 发现该组件是类式组件，随后new出来该类的实例，并通过该实例调用原型链上的render方法
* 将render返回的虚拟dom转为真实dom，随后呈现在页面上



