1.componentWillUpdate与componentWillMount都是DOM没有更新
    willUpdate执行频率高,willMount只会执行一次
        willUpdate只要setState一次就会执行一次
            render也必须重新执行一遍
            之后componentDidUpdate是更新完可以修改DOM
2.render在第一次执行的时候也会执行一次
    执行顺序
        willUpdate
        render
        DidUpdate
    与初始化的三个流程类似
3.document.getElementById("myname").innerHTML
    能拿到div里面的文字内容
4.willUpdate
    将要更新还没更新，里面拿到的值是以前的
        正在进行状态的改变，但是DOM还没有更新
            有人说像vue的beforeUpdate
    不推荐使用
        处在React调用机制 Fiber的第一个阶段 找出需要更新哪个DOM可以被高优先级任务打断
            此函数会再次执行，不够安全
    此处setState会死循环
        setState会再走willUpdate，走render，再走didUpdate，一直setState一直走
            * 不过也并没有懂为什么会死循环 *
5.didUpdate
    已经更新完成，拿到的是更新完的节点
    可以在更新后，获取DOM节点，此时安全靠谱，能够拿到完整的DOM
        不管是不是有异步加载或者同步加载，因为节点已经挂载完毕了
    缺点
        会执行多次
            每次更新都会执行
    此时里面的什么东西都是最新的，如何获取之前的状态
        didUpdate有两个参数
            prevprops prevstate 之前的属性 之前的状态
6.如果axios处于异步，setState会同步更新的到真实的DOM节点
    就可以直接访问到真实DOM 
7.与didMount的区别
    第一次从本地存储中读出东西，所以第一次初始化应该在didMount中
    didUpdate是更新完了，所有都完事了，再做初始化就可以
8.每调用一次setState,render更新一次
    都会走一遍willUpdate,render,didUpdate
        每次setState，值没有改变，但是React会把状态先做成虚拟DOM，与老的虚拟DOM进行对比
        就是只要调用setState，即使值没有改变，也会重新执行一遍
        React中最影响性能的也就是虚拟DOM的对比

        shouldComponmentUpdate() 可以自己判断组件是否应该更新
            设置为true与默认不写一样，调用setState就会更新
            设置为false，阻止更新，调用setState也不会更新

            可以通过判断老的状态 !== 新的状态的时候更新
9.DidUpdate中参数是上一次的参数与上一次的状态
    shouldCUpdate中正好相反
        生命周期刚开始更新，连willUpdate都没有执行
            访问的时候拿到的是老的状态 this.state.xxx
            参数中传的反而是新的状态
                nextProps nextState
        真正做到了手动控制React组件的性能
            React组件因为有虚拟DOM，所有能够提高性能，为了防止无效的虚拟DOM的对比，可以通过shouldCU进一步的提升性能
            只有在更新的时候才会对比，父传子传了新的属性的时候，会自助的执行一次，组件不会再浪费时间做状态diff对比

            如果状态过多，可以直接判断两个对象是否相等 不过直接判断对象无法对比，两个对象永远不相等，可以把对象转换为字符串对比字符串
                if JSON.stringify(this.state) !== JSON.stringify(nextState)
10.面试题 scu是什么意思
    快捷打印方法
