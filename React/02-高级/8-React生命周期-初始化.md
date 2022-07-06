1.React生命周期 也叫钩子函数
    => 初始化阶段
        componentWillMount: render之前最后一次修改状态的机会
            只会执行一次
            组件将要挂载到真实的DOM中
                可以在此周期内访问状态，进行状态的修改
                    但是获取不到挂载的DOM节点，因为还没有创建DOM结构
                    可以进行一些状态的复杂的逻辑计算
                初始化数据的作用
            16之前
        render: 只能访问this.props和this.state，不允许修改状态和DOM输出
            render函数自动被执行
            render更新状态的时候也会重新渲染，不会只加载一次
                不要在render内执行setState，不然会栈溢出
            作用是渲染页面
        componentDidMount: 成功render并渲染完成真实DOM之后触发，可以修改DOM
            组件已经挂载到DOM节点中，可以拿到真实的DOM节点
            只会执行一次
                可以访问到已经创建完的DOM节点
            推荐在DidMount中进行数据请求，订阅也放在这里，setInterval定时器也可以放这里
                与constructor类似
            * 可以基于创建完的DOM进行初始化 * 无可替代
                BetterScroll就是必须等待DOM创建完了之后才能进行new
                一些第三方的库使用纯js写的，需要基于DOM操作，不知道什么时候DOM创建完，就会无法工作
                    (同步读取的，异步的没啥事)
            因为只有这个周期才知道DOM节点什么时候创建完成
                才可以在这个函数里面进行JS的DOM操作和初始化对象的访问
    => 运行中阶段
        componentWillReceiveProps: 父组件修改属性触发
        shouldComponentUpdate: 返回false会阻止render调用
        componentWillUpdate: 不能修改属性和状态
        render: 只能访问this.props和this.state，不允许修改状态和DOM输出
        componentDidUpdate: 可以修改DOM 
    => 销毁阶段
        componentWillUnmount: 在删除组件之前进行清理操作，比如计时器和事件监听器
2.类才会有生命周期
    函数组件只有属性概念，没有状态，也不会有生命周期
        hooks和副作用函数可以实现类似的功能
3.初始化执行顺序
    WillMount
    render
    DidMount
4.componmentWillMount被弃用
    不被推荐使用
        可能会有副作用函数，可以把代码移入到didmount中去或者在constructor中设置初始状态
    或者使用UNSAFE_componentWillMount避免警告
    16.2更新diff算法，优化性能，提出了fiber技术
        传统的React创建状态之后会创建新的虚拟DOM树，会与老的虚拟DOM树进行对比
            此过程是同步的
                数据量非常多的情况下，更新操作会造成浏览器假死，卡顿，影响体验
        React Fiber优化了虚拟DOM diff算法
            把创建DOM与组件渲染的过程拆分成无数个小的分片任务执行
                可以认为任务无比的碎片化
                    此时如果有优先级较高的任务，就先执行优先级较高的任务，会直接打断低优先级任务
                        先执行高优先级的
                        低优先级任务就是willMount中找哪些节点将要挂载到页面中
                        高优先级任务就是render渲染，didMount
                            找出哪些需要更新DOM的过程是可以打断的
                            更新DOM的过程不能被打断
                            过程
                                willMount找在render之前哪些状态需要更新，willMount是低优先级，碎片化任务，render正在更新，就会打断willMount，不会被保存，只能下次继续找哪些节点需要更新
                                此生命周期可能触发多次，有隐患，所以不推荐
5.时间节点
    16.2
        推出了新的生命周期
    16.8
    17
    18