### query和params的区别

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

**区别：query传参会带到URL中，params不会**

### 第三种传参方式

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



