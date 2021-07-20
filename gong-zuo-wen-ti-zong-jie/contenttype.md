### 原生ajax请求

```js
// 创建异步对象
var xhr = new XMLHttpRequest()

// 调用open方法，配置请求信息
xhr.open("POST", url, async) // async默认：true（执行异步操作）
xhr.open("GET", "/ashx/myzhuye/Detail.ashx?methodName=GetAllComment", async) // get请求参数拼接在URL后边

// post方法需要设置请求头
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')

// 发送请求，post请求传递的参数在这
xhr.send("methodName=GetAllComment&str1=str1&str2=str2")

// 注册回调函数
xhr.onreadystatechange = function(){
  if(xhr.status === 200 && xhr.readyState === 4){
    console.log(this.response)    
  }
}

// readyState： 0：请求未初始化；1：服务器连接已建立；2：请求已接收；3：请求处理中；4：请求已完成，响应已就绪
```

### jquery请求

```js
$.ajax({
  url: 'url',
  type: post,
  contentType: 'application/json',
  dataType: 'json',
  async: true,(默认：true 异步，false：同步)
  cache: true,(默认：true，若为false：不会从浏览器缓存中加载请求信息)
  data: data,
  success: function(){},
  error: function(){}
})
```

* contentType：设置传给服务器的格式

* * application/x-www-form-urlencoded（表单格式）

  > jquery的ajax默认的格式，key1=value1&key2=value2。不能传复杂的json对象

  * application/json

  > 设置contentType：application/json；data需传json格式的字符串。不设置，可以传json对象

  * text/xml

  > xml：面向数据，json：面向对象和结构  
  > data: "&lt;user&gt;&lt;name&gt;"+name+"&lt;/name&gt;&lt;pwd&gt;"+pwd+"&lt;/pwd&gt;&lt;/user&gt;"

  * multipart/form-data

  > 用于文件上传提交文件

* dataType：收到服务器的格式

* * json
  * html
  * xml

### axios请求

```js
// request.js
import axios from 'axios'

const service = axios.create({
  baseURL: process.env.BASE_URL + 'manage/', // api 的 base_url
  // timeout: 5000 // request timeout
})

service.interceptors.request.use(
  config => {
    if (store.getters.token) {
      // 让每个请求携带token
      config.headers['SYJusticeAuthorization'] = getToken()
    }
  }
)

service.interceptors.reponse.use(
  response => {
    if(response.data.status !== 0){
      // 不成功 do something
    }else {
      // 成功
      return response.data
    }
  }
)

export default service

=====================================
// 调用
import request from '@/utils/request'

export function loginByUsername(username, password) {
  const data = {
    username,
    password
  }
  return request({
    url: 'syUser/login',
    method: 'post',
    data: {
      data
    }
  })
}
```

### fetch

> windows内置的（关注分离的设计思想），和xhr同级别，不用下载直接使用，promise风格的。缺点是低版本浏览器不支持

```js
fetch('www.baidu.com').then(
  res => {
    console.log('联系服务器成功', res.json())
    return res.json()  // Promise 实例对象
  }, 
  err => {
    console.log('联系服务器失败', err)
    return new Promise()  // 如果不return，默认非Promise实例，返回undefined，下边还会then还会执行
  }
).then(
  res => console.log('获取数据成功了', res),
  err => console.log('获取数据失败了', err)
)

// 优化
fetch('www.baidu.com').then(
  res => {
    console.log('联系服务器成功', res.json())
    return res.json()  // Promise 实例对象
  }
).then(
  res => console.log('获取数据成功了', res)
).catch(
  // 统一处理错误
  err => console.log('请求出错', err)
)

//继续优化
try {
  const response = await fetch('www.baidu.com')
  const data = await response.json()
} catch(err) {
  console.log('请求出错', err)
}
```



