### query 和 params的区别

路由跳转的几种传参方式：

* query

```js
// 传参: 
this.$router.push({
    path:'/xxx',
    query:{
      id:id
    }
})  

// 接收参数:
this.$route.query.id
```

* params

```js
// 传参: 
this.$router.push({
    name:'xxx',
    params:{
      id:id
    }  
})

// 接收参数:
this.$route.params.id

// 如果路由配置里没有添加 /:id，则参数不会体现在url中，如果添加则会在地址栏出现，
// 但是如果params不传参数就会导致页面没有内容或者跳转失败，所以可以设置 /:id? 表示可选
```

**注意：params传参，只能用name来引用路由，否则页面接收到的参数为undefined**

**区别：query传参会带到URL中（?id='001'），相当于get请求。params不会，相当于post请求**

* path 拼接（因为在url中，所以页面刷新参数不会丢失）

```js
// 传参：
this.$router.push({
    path: `/describe/${id}`,
})

// 路由配置
{
 path: '/describe/:id',
 name: 'Describe',
 component: Describe
}

// 接收参数：
this.$route.params.id
```

* 路由props，路由解耦

```js
// 传参：
<router-link :to="{name: 'industryDocument', params: {id: tradeType, key: industryType}}"></router-link>

// 路由配置（将路由的props设置为true，组件内通过props接收params参数，query接收不到）
{
    path: 'industryDocument/:id/:key',
    name: 'industryDocument',
    props: true,
    component: () => import('@/views/industryFocus/industryDocument')
}

// 接收参数：
export default {
    props: ['id', 'key'],
    mounted() {}
}
```

#### params传参页面刷新导致数据丢失问题

解决方案如下：

* 使用query传参，但是遇对象（利用JSON.striginfy先转为字符串）可能会造成地址栏特别丑且信息暴露
* 利用localStorage，在接收页面created周期获取数据放入缓存，beforeDestorye阶段清除缓存



