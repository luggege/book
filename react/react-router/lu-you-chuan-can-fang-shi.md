### 路由传参方式

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

* state参数：刷新参数不会丢失（前提是用的BrowserRouter）

```js
// Message.jsx
{/* 向路由组件传递state参数 */}
<Link to={{pathname: '/home/message/detail', state: {id: message.id, title: message.title}}}>{message.title}</Link>
{/* state参数无需声明接收，正常注册路由即可 */}
<Route path="/home/message/detail" component={Detail}></Route>

// Detail：接收state参数
const {id, title} = this.props.location.state
```



