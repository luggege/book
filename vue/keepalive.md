### keepalive组件

> vue在页面切换的时候，会将原来的页面注销掉，然后渲染新的页面，看似一样，实则每次打开的都是新页面。性能不好，所以有了keepalive

* 它拥有两个独有的生命周期钩子函数，分别为 activated 和 deactivated

* keepalive包裹的组件不会销毁，而是会缓存在 deactivated 钩子函数中，根据缓存渲染后执行 activated 函数



