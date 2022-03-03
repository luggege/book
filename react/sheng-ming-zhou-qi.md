### 生命周期

* componentWillMount
* componentDidMount
* componentWillReceiveProps\(props\): 从父类接受props，并且在渲染前调用
* shouldComponentUpdate\(\): true/false，组件是否更新，默认false
* componentWillUpdate
* componentDidUpdate
* componentWillUnMount
* getDerivedStateFromProps\(nextProps, prevState\): 从父类接受props，并且在渲染前调用
* getSnapshotBeforeUpdate\(prevProps, prevState\): render之后，渲染之前调用



