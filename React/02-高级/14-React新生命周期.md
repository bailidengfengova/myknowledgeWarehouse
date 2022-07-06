1.getDerivedStateFromProps
    获取衍生的状态从属性身上
        给人的感觉好像可以把属性转换成状态进行二次使用
            就是把属性转换成状态
    第一次的初始化组件以及后续的更新过程中（包括自身状态更新以及父传子），返回一个对象作为新的state
        返回null则说明不需要再这里更新state
    特殊
        初始化的时候会调用，后续更新中也会嗲用
            除了销毁，都不执行
2.直接写gdsfp 会报错
    Lifecycle method should be static
    此方法是类的方法，不是对象的方法，所以需要静态，不能通过new对象之后点调用
    还有是必须得有state状态，然后return也不能为空，最起码要返回一个空对象
3.willMount可以在render之前最后一次修改状态的机会
    初始化要用的
4.gdsfp return的结果会把原来的state对象合并
    初始化执行一次，后续自身的更新也会执行一次，只不过更新的时候会被return里的值覆盖掉
    解决这个问题
        可以不写成固定的
            有两个参数 nextProps nextState
            最新的状态与属性
5.字符串首字母大写的方式
     str.substring(0, 1).toUpperCase() + str.substring(1)
6.此方法特别适合在初始化和更新的时候重复执行一段逻辑
    最早的获取到属性
7.如果要在此方法内读state会报错
    cannot read properties of undefined(reading 'state')
    static 是静态属性，里面没有this，所以只能通过形参获取状态
8.不能让新老生命周期同时存在 会报错
9.在gdsfp中不能发起异步请求
    因为return会立即执行，不会等异步的返回，永远没有可能把list重新覆盖成请求之后的结果

    只有在一定场景下才可以取代willReceibedProps

    官方建议在这个生命周期内把属性值转换成状态之后return
        取数据在didUpdate中获取
            为了解决willReceiveProps更新的隐患
                没有每次更新都重复请求的问题
                    多次父传子都可以
                        return完之后，在同一个事件循环中，多次setState会合并
                        虽说此函数会传进来多次，但return会合并到老状态中
                            在一个事件循环中连续多次会合并成一次进行处理
                                等最终合并完成在didUpdate中做一次请求数据即可
            能够解决频繁异步请求的问题
                不用担心多次异步请求带来的频繁更新或频繁异步操作
10.如果把axios放在didUpdate中请求
    会发现页面会一直加载gdsfp
        发现在didUpdate中还是更新state了
            之后willUpdate render didUpdate 之后又会判断 又会请求 一直循环
        所以didUpdate中也不能直接进行状态的更新 也会死循环
            所以需要在didUpdate中判断一些新旧状态是否相等
        didUpdate与willUpdate正好相反，它拿到的是老的状态值
            这么写只有在改变的时候才会执行一次ajax请求，不会重复执行