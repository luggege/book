### setState

> setState是同步的，但是引起的后续的状态更新是异步的

```js
import React, { Component } from 'react'

export default class SetState extends Component {
    state = {
        count: 0
    }
    add = () => {
        const {count} = this.state
        // 1. 对象式的setState
        // this.setState({
        //     count: count + 1
        // }, () => {
        //     console.log('异步。。。', this.state.count)
        // })
        // console.log('同步。。。', this.state.count)
        // 提示：this.state.count = count + 1 // 错误写法，无法更新状态

        // 2. 函数式的setState
        this.setState((state, prop) => {
            // 可以接收到当前状态，及传过来的props
            console.log(state, prop)
            return {count: count + prop.num}
        })
    }
    render() {
        return (
            <div>
                <h1>当前求和为： {this.state.count}</h1>
                <button onClick={this.add}>点我—+1</button>
            </div>
        )
    }
}


<SetState num={100} />
```



