## contentType

* ### contentType：设置传给服务器的格式
* * application/x-www-form-urlencoded

  > jquery的ajax默认的格式，key1=value1&key2=value2。不能传复杂的json对象

  * application/json

  > 设置contentType：application/json；data需传json格式的字符串。不设置，可以传json对象

  * text/xml

  > xml：面向数据，json：面向对象和结构  
  > data: "&lt;user&gt;&lt;name&gt;"+name+"&lt;/name&gt;&lt;pwd&gt;"+pwd+"&lt;/pwd&gt;&lt;/user&gt;"

  * multipart/form-data

  > 用于文件上传提交数据
* ### dataType：收到服务器的格式

* * json
  * html
  * xml



