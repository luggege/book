### JS的6种加载方式

1. 正常模式：JS阻塞dom渲染

   ```js
   <script src="index.js"></script>
   ```

2. async模式：异步加载JS，但**加载完立即执行js，**再继续解析文档

   ```js
   <script async src="index.js"></script>
   ```

3. defer模式：异步加载JS，但是**文档加载完顺序执行JS**

   ```js
   <script defer src="index.js"></script>
   ```

4. module模式：在主流的现代浏览器中，对import引用发起HTTP请求，获取模块内容，同defer模式一样。vite就是利用浏览器支持原生的es module模块，开发时跳过打包的过程，提升编译效率

   ```js
   <script type="module">import { a } from './a.js'</script>
   ```

5. preload：link标签的preload属性：用于提前加载一些需要的依赖，这些资源会优先加载。vue2项目打包的index.html文件，会自动给首页所需要的资源，全部添加preload，实现关键资源的提前加载

   ```js
   <link rel="preload" as="script" href="index.js">
   ```

   preload特点：

   1. preload加载的资源是在浏览器渲染机制之前进行处理的，并且不会阻塞onload事件
   2. preload 加载的JS脚本其加载和执行的过程是分离的，即preload 会预加载相应的脚本代码，待到需要时自行调用

6. prefetch：利用浏览器的空闲时间，加载页面将来可能用到的资源的一种机制。通常可以用于加载其他页面（非首页）所需要的资源，以便加快后续页面的打开速度

   ```js
   <link rel="prefetch" as="script" href="index.js">
   ```

   prefetch 特点：

   1. prefetch 加载的资源可以获取非当前页面所需要的资源，并且将其放入缓存至少5分钟（无论资源是否可以缓存）

   2. 当页面跳转时，未完成的prefetch请求不会中断



