### Vue3新特性

* ES5：defineProperty：劫持----&gt; ES6：Proxy：拦截\(解决之前监听数组的漏洞\)
* 包体积更小（按需打包）
* 虚拟dom
* TypeScript
* 生命周期
* Fragment、Teleport、Suspense

#### vue3的生命周期

|   vue2.x | vue3.x |
| :--- | :--- |
|   beforeCreated | Not needed\* |
| `created` | Not needed\* |
| `beforeMount` | `onBeforeMount` |
| `mounted` | `onMounted` |
| `beforeUpdate` | `onBeforeUpdate` |
| `updated` | `onUpdated` |
| `beforeUnmount` | `onBeforeUnmount` |
| `unmounted` | `onUnmounted` |
| `errorCaptured` | `onErrorCaptured` |
| `renderTracked` | `onRenderTracked` |
| `renderTriggered` | `onRenderTriggered` |
| `activated` | `onActivated` |
| `deactivated` | `onDeactivated` |





