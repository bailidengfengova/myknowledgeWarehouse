1.shouldComponentUpdate需要开发者自身判断
    状态是否改变，属性是否改变，需要手动处理
2.PureComponent
    React自己提供的优化的组件对象，可以进行自动化的处理
    引入的时候用PureComponent替代Component
3.不适合的场景
    如果state或props永远都在变，那么PureComponent并不会较快，因为shallowEqual也不需要花时间
    也不必要去阻止更新，按理来说scu也不用做优化，加了PureComponent
        对比新旧状态，新旧属性的时候也会浪费时间
        比如 倒计时
4.快捷键rpc就是PureComponent