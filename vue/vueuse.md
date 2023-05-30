### Vue.use\(plugin, arguments\)

#### plugin\(Function \| Object\)

插件的两种方式：

* 一种是**对象**，但是必须有一个**install**函数
* 一种是直接是**函数**暴露给Vue，当作install直接执行

源码分析：

1. 先看这个组件是否注册过（不允许重复注册），注册过就直接返回this（Vue对象）
2. 然后将arguments伪数组对象转为真正的数组，并且将参数数组的第一个参数即vue去除掉
3. 没注册过就看如果有install方法，就调用plugin.install\(\)方法，通过apply改变this为该plugin组件并传参arguments；
4. 如果没有，就把plugin当作install，直接调用函数，此时plugin内的this为null
5. 最后push到installedPlugins中，告知vue该插件已经被注册过，避免重复注册

```js
function initUse(Vue) {
  Vue.use = function (plugin) {
      var installedPlugins = this._installedPlugins || (this._installedPlugins = []);
      if (installedPlugins.indexOf(plugin) > -1) {
          return this;
      }
      // additional parameters
      var args = toArray(arguments, 1);
      args.unshift(this);
      if (isFunction(plugin.install)) {
          plugin.install.apply(plugin, args);
      }
      else if (isFunction(plugin)) {
          plugin.apply(null, args);
      }
      installedPlugins.push(plugin);
      return this;
  };
}

/**
* Convert an Array-like object to a real Array.
*/
function toArray(list, start) {
  start = start || 0;
  var i = list.length - start;
  var ret = new Array(i);
  while (i--) {
      ret[i] = list[i + start];
  }
  return ret;
}
```



