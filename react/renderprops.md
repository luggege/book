### renderProps

* children props
* render props

```js
import React, { Component, PureComponent } from 'react'
import './index.css'

export default class index extends PureComponent {
    render() {
        return (
            <div className="parent">
                <h3>我是parent组件</h3>
                {/* 1、children props */}
                {/* <A>
                    Hello A
                    <B>Hello B</B>
                </A> */}
                {/* 2、render props：通过组件标签传入结构，而且可以携带数据，一般用render函数属性 */}
                <A render={name => <B name={name}/>} />
            </div>
        )
    }
}

class A extends PureComponent {
    state = {
        name: 'tom'
    }
    render() {
        console.log('A--render', this.props)
        const {name} = this.state
        return (
            <div className="child">
                <h3>我是A组件</h3>
                {/* <B /> */}
                {/* 1、children props： this.props.children: 标签体内容 */}
                {/* <div>{this.props.children}</div> */}
                {this.props.render(name)}
            </div>
        )
    }
}

class B extends PureComponent {
    render() {
        console.log('B-render', this.props)
        return (
            <div className="child1">
                <h3>B组件: {this.props.name}</h3>
                {/* 1、children props：问题：B组件无法拿到A组件的数据 */}
                <div>{this.props.children}</div>
            </div>
        )
    }
}
```



