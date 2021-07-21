### react-router-dom

> react插件react-router有三种方式web、native、anywhere，前端网页一般采用web，即react-router-dom

#### 一般组件&路由组件区别

* 一般组件直接标签引用，路由组件需要Route标签注册
* 一般组件传递什么接收什么，路由组件（this.props）接收到三个固定的属性：history\location\match

#### NavLink与封装NavLink

* NavLink可以实现路由链接的跳转，通过activeClassName指定当前高亮类名
* 标签体内容是一个特殊的标签属性
* 通过this.props.children可以获取标签体内容

```js
// App.js
import {NavLink, BrowserRouter, Route, HashRouter, Redirect} from 'react-router-dom'

render() {
    return (
        <HashRouter>
          <Header />
          <div>
              {/* Link标签换为 NavLink会追加 active类，添加 activeClassName会将选中的类变为指定的类名 */}
              <NavLink activeClassName="gray" to="/about">About</NavLink>
              // 可简写：<NavLink activeClassName="gray" to="/home" children="Home">
              <NavLink activeClassName="gray" to="/home">Home</NavLink>
          </div>

          <h3>
            {/* 注册路由 */}
              <Route path="/about" component={About} />
              <Route path="/home" component={Home} />
              {/* Redirect */}
              <Redirect to="/home" />
          </h3>
        </HashRouter>
    )
}
```

```js
<MyNavLink to="/about" title="About"/>
<MyNavLink to="/home" title="Home" />   
// index.jsx:7 MyNavLink {to: "/home", title: "Home"}
```

```js
// App.js 标签体内容
<MyNavLink to="/about">About</MyNavLink>
<MyNavLink to="/home">Home</MyNavLink>
// index.jsx:7 MyNavLink {to: "/home", children: "Home"}

// MyNavLink.jsx
<NavLink activeClassName="gray" {...this.props}>{this.props.children}</NavLink> 
// 或者
<NavLink activeClassName="gray" {...this.props} />
```

#### Switch

* 通常情况下，path和component是一一对应的关系
* Switch可以提高路由匹配效率（单一匹配，匹配到一个就不往下继续匹配）

```js
import {NavLink, BrowserRouter, Route, HashRouter, Switch} from 'react-router-dom'

{/* 注册路由 */}
<Switch>
  <Route path="/about" component={About} />
  <Route path="/home" component={Home} />
  <Route path="/home" component={Test} />
</Switch>
```

#### 解决多级路径刷新页面样式丢失的问题

* public/index.html 中引入样式时不写 ./ 写 / （常用）
* public/index.html 中引入样式时不写 ./ 写 %PUBLIC\_URL%（常用，只存在于react脚手架中）
* 使用HashRouter

#### 路由的模糊匹配与精准匹配

* 默认使用模糊匹配（输入的路径开头必须包含要匹配的路径）
* 开启严格模式
* 严格模式不要随便开启，需要再开，有些时候开启会导致无法继续匹配二级路由

#### 嵌套路由

* 注册子路由时要写上**父路由的path**值
* 路由的**匹配**是按照注册路由的**顺序**进行的

#### 路由传参方式

* params

```js
// Message.jsx
{/* 向路由组件传递params参数 */}
<Link to={`/home/message/detail/${message.id}/${message.title}`}>{message.title}</Link>
{/* 声明接收params参数 */}
<Route path="/home/message/detail/:id/:title" component={Detail}></Route>

// Detail：接收params参数
const {id, title} = this.props.match.params
```

* search

```js
// Message.jsx
{/* 向路由组件传递search参数 */}
<Link to={`/home/message/detail/?id=${message.id}&title=${message.title}`}>{message.title}</Link>
{/* search参数无需声明接收，正常注册路由即可 */}
<Route path="/home/message/detail" component={Detail}></Route>

// Detail：接收search参数
import qs from 'querystring'
const {id, title} = qs.parse(this.props.location.search.slice(1))
```

* state参数：刷新参数不会丢失

```js
// Message.jsx
{/* 向路由组件传递state参数 */}
<Link to={{pathname: '/home/message/detail', state: {id: message.id, title: message.title}}}>{message.title}</Link>
{/* state参数无需声明接收，正常注册路由即可 */}
<Route path="/home/message/detail" component={Detail}></Route>

// Detail：接收state参数
const {id, title} = this.props.location.state
```



