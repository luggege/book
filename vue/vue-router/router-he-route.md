### $router 和 $route 的区别

* 传参用 this.$router，接收用 this.$route
* this.$router 是VueRouter实例，通过 this.$router.push 导航到不同URL
* this.$route 是当前路由对象，包含当前路由的name、path、query、params

![](/assets/router.png)

