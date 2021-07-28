### 编程式路由导航

```js
handleReplace = (id, title) => {
    // this.props.history.replace(`/home/message/detail/${id}/${title}`)
    // this.props.history.replace(`/home/message/detail/?id=${id}&title=${title}`)
    this.props.history.replace(`/home/message/detail`, {id, title})
}
handlePush = (id, title) => {
    // this.props.history.push(`/home/message/detail/${id}/${title}`)
    // this.props.history.replace(`/home/message/detail/?id=${id}&title=${title}`)
    this.props.history.replace(`/home/message/detail`, {id, title})
}
forward = () => {
    this.props.history.goForward()
}
back = () => {
    this.props.history.goBack()
}
go = () => {
    this.props.history.go(2)
}
render() {
    const { messageArr } = this.state
    return (
        <div>
            <ul className="todo-list">
                {
                    messageArr.map(message => {
                        return (
                            <li>
                                {/* 向路由组件传递params参数 */}
                                {/* <Link to={`/home/message/detail/${message.id}/${message.title}`}>{message.title}</Link> */}
                                {/* 向路由组件传递search参数 */}
                                {/* <Link to={`/home/message/detail/?id=${message.id}&title=${message.title}`}>{message.title}</Link> */}
                                {/* 向路由组件传递state参数 */}
                                <Link replace to={{pathname: '/home/message/detail', state: {id: message.id, title: message.title}}}>{message.title}</Link>
                                <button onClick={() => this.handlePush(message.id, message.title)}>push查看</button>
                                <button onClick={() => this.handleReplace(message.id, message.title)}>replace查看</button>
                            </li>
                        )
                    })
                }
            </ul>
            {/* 声明接收params参数 */}
            {/* <Route path="/home/message/detail/:id/:title" component={Detail}></Route> */}
            {/* search参数无需声明接收，正常注册路由即可 */}
            {/* <Route path="/home/message/detail" component={Detail}></Route> */}
            {/* state参数无需声明接收，正常注册路由即可 */}
            <Route path="/home/message/detail" component={Detail}></Route>

            <button onClick={this.forward}>前进</button>
            <button onClick={this.back}>回退</button>
            <button onClick={this.go}>go</button>
        </div>
    )
}
```



