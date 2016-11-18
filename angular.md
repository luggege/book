###内置指令
* ng-include 引入模板(不会使全局变量增多,js中iframe标签会使全局变量window增多)

disabled 是一个无值属性,通过ng-变成angular形式,就可以设置其状态

###url
截取的是锚点后面的内容

###$http
本质是对XMLHttpRequest对象的封装

###接口
url地址

###接口方式
SOAP  RESTFUL(angularjs优先支持这种方式,默认就会将对象形式的{age: 10}===>字符串形式:age=10(key=value&key=value的形式))