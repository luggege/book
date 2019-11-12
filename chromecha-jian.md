### 思路: {#思路}

```
1.
 chrome.runtime.sendMessage ===
>
页面向插件发起指定消息{key: 
123321
, 
type
: "personalCenter"}

2.
 chrome.extension.onMessage.addListener ===
>
 插件接收消息,循环遍历每一个标签页(chrome.tabs.query)
3.
 当发现发过来的消息类型(自定义)符合条件时( 
"personalCenter"
 == request.
type
 ),创建新的达人平台标签页,并向其发送
(chrome.tabs.sendRequest)
接收到的消息
(key/type)
和自己的id,中断此次循环

4.
  chrome.extension.onRequest.addListener ===
>
 当页面(dgj.js)接收到本插件的页面(新创建的达人平台页面)时,发起那三次ajax请求,发布数据到达人平台

5.
 当插件接收到页面发过来的信息( {msg: 
"OK"
, 
type
: "tbfrom2", tabid: 162} )后,往复1步骤, 重新开始遍历每一个标签;

6.
 发现
"tbfrom2"
 == request.
type
,并且达人平台这个页面存在了
(刚刚创建的那个)
就删除,并向当前页面发送消息
```



