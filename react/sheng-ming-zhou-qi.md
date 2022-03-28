### 生命周期

* componentWillMount
* componentDidMount
* componentWillReceiveProps\(props\): 从父类接受props，并且在渲染前调用
* shouldComponentUpdate\(nextProps, nextState\): true/false，组件是否更新，默认false
* * 一般不用，容易出现bug，但是为了不多次render（state、prop改变就会render、内存地址变了所以render）可以用来做性能优化
* componentWillUpdate
* componentDidUpdate
* componentWillUnMount
* getDerivedStateFromProps\(nextProps, prevState\): 从父类接受props，并且在渲染前调用
* getSnapshotBeforeUpdate\(prevProps, prevState\): render之后，渲染之前调用



