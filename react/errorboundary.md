### errorBoundary

> 错误边界：捕获**后代**组件的**生命周期**产生的错误

```js
import React, { Component, PureComponent } from 'react'
import Child from './Child'

/**
 * 错误边界：找出错的父组件进行处理，只能捕获后代组件的生命周期产生的错误，只在打包后的项目才不会将错误扩散
 */
export default class index extends PureComponent {
    state = {
        hasError: '' // 用于标识子组件是否产生错误
    }
    // 子组件出错时都会调用该组件，并携带错误信息
    static getDerivedStateFromError(error) {
        console.log('@', error)
        return {hasError: error}
    }
    componentDidCatch() {
        console.log('组件出错了（此处统计错误，反馈给服务器，通知编码人员）')
    }
    render() {
        return (
            <div className="parent">
                <h3>我是parent组件</h3>
                {this.state.hasError ? <h2>当前网络不稳定，请稍后重试</h2> : <Child />}
            </div>
        )
    }
}
```



