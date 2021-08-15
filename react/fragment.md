### Fragment

```js
import React, { Component, Fragment } from 'react'

export default class index extends Component {
    render() {
        return (
            // Fragment: 代码片段，编译时最终会丢失掉这个标签，只接收一个key属性。
            <Fragment key={2}>
                <input type="text"/>
                <input type="text"/>
            </Fragment>
        )
    }
}
```



