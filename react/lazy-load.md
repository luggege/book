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



