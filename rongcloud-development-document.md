\#\# Web IM Widget 开发文档（Angular版）

\[在线示例\]\(http://web.hitalk.im/widget/web/\)   



1. 引入 SDK

从官方下载插件包\(项目源码 dist 目录\)放在自己项目目录中，在页面中引入以下资源：  

  \`\`\`javascript

  &lt;!-- 依赖资源 --&gt;

  &lt;script src="/vendor/jquery-2.2.2.js"&gt;&lt;/script&gt;

  &lt;script src="/vendor/angular-1.4.8.js"&gt;&lt;/script&gt;



  &lt;script src="/vendor/plupload.full.min-2.1.1.js"&gt;&lt;/script&gt;

  &lt;script src="/vendor/qiniu-1.0.17.js"&gt;&lt;/script&gt;

  &lt;link rel="stylesheet" type="text/css" href="/vendor/jqueryrebox/jquery-rebox-0.1.0.css"/&gt;

  &lt;script src="/vendor/jqueryrebox/jquery-rebox-0.1.0.js"&gt;&lt;/script&gt;

  

  &lt;script src="//cdn.ronghub.com/RongIMLib-2.2.5.min.js"&gt;&lt;/script&gt;

  &lt;script src="//cdn.ronghub.com/RongEmoji-2.2.5.min.js"&gt;&lt;/script&gt;

  &lt;script src="//cdn.ronghub.com/Libamr-2.2.5.min.js"&gt;&lt;/script&gt;

  &lt;script src="//cdn.ronghub.com/RongIMVoice-2.2.5.min.js"&gt;&lt;/script&gt;

  &lt;!-- 依赖资源 end --&gt;



  &lt;!-- widget --&gt;

  &lt;link rel="stylesheet" type="text/css" href="{资源目录}/css/RongIMWidget.css"/&gt;

  &lt;scrip type="text/javascript" src="{资源目录}/RongIMWidget.js"&gt;&lt;/script&gt;

  \`\`\` 

&gt; 在页面 body 中加入 \`&lt;rong-widget&gt;&lt;/rong-widget&gt;\` 标签  

&gt; 注意要按照 angular 的规范加在 angular 作用域内。  



2. 初始化

在自己 js 文件中 angular module 中引入 SDK \`var demo = angular.module\("demo", \["RongWebIMWidget"\]\);\`

在整个应用程序全局，只需要调用一次 init 方法。

	\`\`\`javascript

  /\*

   \*@param config {Object} 初始化配置参数

   \*/  

  WebIMWidget.init\(config\);  

  \`\`\`

&gt; 注：如果你的模块是异步加载，可以使用angular主动加载模块  

&gt; \`\`\`javascript

&gt; angular.bootstrap\(document,\["demo"\]\)

&gt; 需要兼容IE9的发送图在初始化时请添加配置 config.uploadFlashUrl。 flash 文件 在vendor/FlashUpload.swf

&gt; \`\`\`  



  最简配置需要 appkey，token，这两个参数是必须的。例:

	\`\`\`javascript

  demo.controller\("main", \["$scope", "WebIMWidget", function\($scope,WebIMWidget\) {

      WebIMWidget.init\({

        appkey:"bmdehs6pdw0ss",

        token:"\*\*\*\*"

      }\);

  }\]\);

	\`\`\`

&gt; 注：请从融云开发者平台注册得到 App Key ，和 Token



 初始化回调函数，onSuccess 初始化成功回调、onError 初始化错误回调。例：

	\`\`\`javascript

  WebIMWidget.init\({

    appkey:"bmdehs6pdw0ss",

    token:"\*\*\*\*",

    onSuccess:function\(\){

      //初始化完成

    },

    onError:function\(\){

      //初始化错误

    }

  }\);

	\`\`\`



3. 初始化配置参数介绍  

  \* style 显示样式  

  style 可以配置显示位置 top、left、bottom、right，positionFixed 是否固定在页面显示。默认 false，对话框显示大小 width、height,。示例：  

  \`\`\`javascript

    WebIMWidget.init\({

      appkey:"bmdehs6pdw0ss",

      token:"\*\*\*\*",

      style:{

        width:500,

        height:600,

        bottom:0,

        left:0

      }

    }\);

  \`\`\`

  \* displayConversationList \[ boolean \] 是否要显示会话列表。默认为 false

  \`\`\`javascript

    WebIMWidget.init\({

      appkey:"bmdehs6pdw0ss",

      token:"\*\*\*\*",

      displayConversationList:true

    }\);

  \`\`\`

  \* conversationListPosition \[ left \| right \] 会话列表位置，会话列表在对话框左边或右边。\(注： displayConversationList 为 true 时才有效\)

  \`\`\`javascript

    WebIMWidget.init\({

      appkey:"bmdehs6pdw0ss",

      token:"\*\*\*\*",

      displayConversationList:true,

      conversationListPosition:WebIMWidget.EnumConversationListPosition.left

    }\);

  \`\`\`

  \* displayMinButton \[ boolean \] 最小化时是否显示最小化按钮。默认为 true

  \`\`\`javascript

    WebIMWidget.init\({

      appkey:"bmdehs6pdw0ss",

      token:"\*\*\*\*",

      displayConversationList:true,

      displayMinButton:false

    }\);

  \`\`\`

  \* desktopNotification \[ boolean \] web 桌面通知，是否开启 WebNotifications。默认为开启 true  



  \* voiceUrl \[ boolean \] 接收消息时的声音提示。声音源格式必须是 audio 标签支持的格式  

4. setConversation 设置当前会话  

  \`\`\`javascript

    /\*\*

     \*@param conversationType 会话类型 {EnumConversationType} \[PRIVATE\|GROUP……\]

     \*@param targetId 会话目标id {string}

     \*@param title 会话显示标题 {string}

     \*/

    WebIMWidget.setConversation\(conversationType,targetId,title\);

  \`\`\`

  &gt;\*\*特别提醒：\*\* setConversation 只有在初始化成功后才可以使用，否则可能引发一些错误。



  \`\`\`javascript

    WebIMWidget.setConversation\(WebIMWidget.EnumConversationType.PRIVATE,"x001","张三"\);

  \`\`\`  

5. 隐藏、显示控件  

  \`\`\`javascript  



  	//呈现会话面板

  	WebIMWidget.show\(\);

  	//隐藏会话面板

  	WebIMWidget.hide\(\);

  \`\`\`

6. 事件  

  \`\`\`javascript  



    //会话面板被关闭时

    WebIMWidget.onClose = function\(\) {

      //do something

    }

    //控件显示时

    WebIMWidget.onShow = function\) {

      //do something

    }

    //接收到消息时

    WebIMWidget.onReceivedMessage = function\(message\) {

      //message 收到的消息

    }

  \`\`\`

7. 用户信息,开发者通过此接口来提供插件中的用户信息设置   

\`\`\`javascript  



  WebIMWidget.setUserInfoProvider\(function\(targetId,obj\){

      $http\({

        method:'GET',

        url:'自己服务器获取用户信息接口',

        params:{

          'userId':targetId

        }

      }\).then\(function\(data\){

          obj.onSuccess\({name:data.name,userId:data.userId,portraitUri:data.portraitUri}\);

      }\);

  }\);

\`\`\`





