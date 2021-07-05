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
  render() {
    return (
      <div></div>
    )
  }
}

ReactDOM.render(<App />, document.getElementById('root'));
```



