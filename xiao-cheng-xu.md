

### 使用小程序首先需https域名

### 循环

> &lt;view class="navbar"&gt;

> &lt;text wx:for="{{navbar}}" data-idx="{{index}}" class="nav-item {{currentTab==index ? 'active' : ''}}" wx:key="unique" bindtap="navbarTap"&gt;{{item}}&lt;/text&gt;

> &lt;/view&gt;



1. 使用wx.for的循环,如果不加wx.key属性会出现黄色警告,但是不影响代码执行

2. 使用自定义属性\*\*data-idx="{{index}}"\*\*,js端获取相关属性值:  \*\*e.currentTarget.dataset.idx\*\*

    &gt;     navbarTap: function \(e\) {

     &gt;     this.setData\({

      &gt;     // 获取设置的idx的值

      &gt;      currentTab: e.currentTarget.dataset.idx

     &gt;      }\)

    &gt;     }





### 通过接口请求回来的图片地址必须是后台已经拼接好了的\*\*完整地址\*\*,否则会报错,例如\(https://taihehaodeshop.com/uploades/images/1.png\);





# 小程序开发之使用百度地图



## 开发步骤:



### 准备工作及环境配置



    1. 在"百度地图开发平台"官网"API控制台"创建应用,应用类型选为"微信小程序",填上小程序的APPID,即可获取到"ak秘钥",此秘钥是代码中所需.

    2. "微信公众平台"中对该小程序进行"服务器域名"配置,\(api.map.baidu.com\)

    3. 下载地图中所用到的插件,即bmap-wx.js.然后在相关js中按如下方式引入:var bmap = require\('../../libs/bmap-wx.js'\);

      插件位置:\( http://lbsyun.baidu.com/index.php?title=wxjsapi/wxjs-download\)

      

相关代码文档事例中有

