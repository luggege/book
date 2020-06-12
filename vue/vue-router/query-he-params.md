### query 和 params的区别

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
```

**注意：params传参，只能用name来引用路由，否则页面接收到的参数为undefined**

**区别：query传参会带到URL中，相当于get请求。params不会，相当于post请求**

* path 拼接

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

// 接受参数：
this.$route.params.id
```

* 路由props

```js
// 传参：
<router-link :to="{name:'industryDocument', params:{id: tradeType,key: industryType}}"></router-link>

// 路由配置（将路由的props设置为true，组件内通过props接收params参数，query接收不到）
{
    path: 'industryDocument/:id/:key',
    name: 'industryDocument',
    props: true,
    component: () => import('@/views/industryFocus/industryDocument')
}

// 接受参数：
props: ['id', 'key'],
```



