### antv

> 阿里的一种可视化工具，定制化更强

使用：

* 安装、引用`import { chart } from '@antv/g2'`
* 实例化图表，指定容器，宽，高
* ```js
  const chart = new chart({
      container: 'div',
      height: 300,
      autoFit: true
  })
  ```
* 使用API，进行图表绘制
* ```js
  chart.data(data)
  chart.axis('', {})
  chart.scale({})
  chart.tooltip()
  chart.legend()
  ```
* 渲染图表
* ```js
  chart.render()
  ```



