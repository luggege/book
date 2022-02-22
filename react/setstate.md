### setState

> setState是同步的，但是引起的后续的状态更新（DOM更新）是异步的

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

#### setState默认行为

* 如果状态是对象式，重复的两条状态，后面的覆盖前面的，相当于Object.assign\(\)的操作
* 如果状态是函数式，重复的两条状态，两条都会执行



