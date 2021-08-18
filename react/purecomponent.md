### PureComponent

```js
import React, { Component, PureComponent } from 'react'
import './index.css'

/**
 * Component的两个问题：
 * 1. 只要执行了this.setState({})，即使不改变数据，组件也会重新render
 * 2. 当前组件render，纵使子组件没有用到父组件的任何数据，都会自动重新render子组件----效率低
 */
/**
 * 效率高的做法：
 * 只有当组件的state、props数据发生变化时才重新render()
 */
/**
 * 优化：
 * PureComponent代替Component，不用手动开关阀门
 */
export default class index extends PureComponent {
    state = {
        carName: '奔驰'
    }
    changeCar = () => {
        this.setState({
            carName: '宝马'
        })
        // 使用了PureComponent，底层做了浅对比，如果obj和之前的state是一个对象，则阀门关闭（false）
        // const obj= this.state
        // obj.carName = '迈巴赫'
        // console.log(obj === this.state) // true
        // this.setState(obj)
    }
    // shouldComponentUpdate(nextState, nextProps) {
    //     // 目前的
    //     console.log('Parent--->', this.props, this.state)
    //     // 要变的
    //     console.log('Parent--->', nextState, nextProps)
    //     return !this.state.carName === nextState.carName
    // }
    render() {
        console.log('parent---render')
        const {carName} = this.state
        return (
            <div className="parent">
                <h3>我是parent组件</h3>
                <div>车： {carName}</div>
                <button onClick={this.changeCar}>点我换车</button>
                <Child carName={carName} />
            </div>
        )
    }
}

class Child extends PureComponent {
    // shouldComponentUpdate(nextState, nextProps) {
    //     // 目前的
    //     console.log('Child--->', this.props, this.state)
    //     // 要变的
    //     console.log('Child--->', nextState, nextProps)
    //     return !this.state.carName === nextState.carName
    // }
    render() {
        console.log('child---render')
        return (
            <div className="child">
                <h3>我是child组件</h3>
                <div>接到的车是： {this.props.carName}</div>
            </div>
        )
    }
}
```



