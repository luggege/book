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

### lazy-load

> 组件随用随加载

```js
// index.js中： import Lazy from './components/lazy_load'

import React, { Component, lazy, Suspense } from 'react'
import {NavLink, Route, Switch, Redirect} from 'react-router-dom'
// import Home from './Home'
// import About from './About'

const Home = lazy(() => import('./Home'))
const About = lazy(() => import('./About'))

export default class Lazy extends Component {
    render() {
        return (
            <div>
                <h1>React Router Demo</h1>
                <div>
                    <NavLink to="/about">About</NavLink>  
                    <NavLink to="/home/a/b">Home</NavLink>
                </div>
                // 需要Suspense包裹，并指定fallback未加载回来组件时的处理（该组件不能懒加载）
                <Suspense fallback={<h1>loading...</h1>}>
                    <Switch>
                        <Route path="/about" component={About} />
                        <Route path="/home" component={Home} />
                        {/* <Route path="/home" component={Test} /> */}
                        {/* <Redirect to="/about" /> */}
                    </Switch>
                </Suspense>
            </div>
        )
    }
}
```



