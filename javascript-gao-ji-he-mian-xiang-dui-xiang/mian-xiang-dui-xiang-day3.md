# jQuery API

## jQuery--DOM操作

#### 1.empty

> 清空所有元素的内容\(dom元素还在\)

#### 2.remove

> 删除所有的元素

#### 3.html

> 不传参,获取第一个元素的内容
>
> 传参,统一设置所有相同元素的内容为这个参数\(可传标签\)

#### 4.text

> 不传参,获取所有元素的内容
>
> 传参,统一设置所有相同元素的内容为这个参数\(不能解析标签\).

#### 5.appendTo

> 1.将DOM元素 jq对象 字符串包装成jq对象,统一处理
>
> 2.外循环控制this实例,内循环控制目标元素\(参数\)
>
> 3.内循环中,如果是第一次添加则将本体添加进去,之后添加克隆版本
>
> 4.**返回包装成jq对象的被添加的元素**\(链式编程\)

#### 6.prependTo

> this.prependTo\(目标元素\),通过insertBefore\(要添加的元素,div.firstChild\),在目标元素之前添加,用法同appendTo方法

#### 7.append

> 1.字符串:累加给所有元素\(isString判断\)
>
> 2.DOM或jq对象: 包装成jq对象统一处理之后仿appendTo添加给this实例
>
> 3.**返回this实例**

#### 8.prepend

> 在之前添加,同append方法
>
> **返回this实例**

## 属性

#### 属性节点和属性\(变量\)的区别

> 属性可以属于任意的对象,而属性节点只属于DOM对象\(nodeType/nodeName\)

\*所有的DOM都有一个attributes属性,这个属性按下标的方式存储了该DOM所有的属性节点

#### 获取属性节点值

> 1.通过DOM的attributes属性得到所有的属性节点对象,按下标取出每一个属性节点对象,再通过nodeValue属性得到这个属性节点值
>
> 2.通过DOM的getAttribute\(属性节点名\)方法

#### 获取属性值

\*直接点或者\[\]

### DOM属性的操作

#### 1.attr

#### 2.prop

#### 3.css

#### 4.val

> getAttribute获取的是默认的value值
>
> .value获取的是**最新**的value值,必须通过点或者\[\]的方式获取

