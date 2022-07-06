1.useContext经常与useReducer一起使用
2.hooks觉得Redux状态管理方案挺好，把理念引入到了React hooks里
    useReudcer
3.在一个组件内可能包含
    数据逻辑
        状态
    视图逻辑
        事件绑定
        遍历
    理念
        把数据逻辑与视图逻辑分离出来，降低耦合度
            把状态管理放在外面做    
                对于单个组件来说，增加复杂度，无意义
                对于多个组合共享状态的时候才有意义
                    之前多个组件，通过中间人模式设计，App做根组件，其余组件访问会或改变根组件状态
                        子传父与父传子的操作会很乱
                        此时把状态提到外面会很好
                            不需要与父组件多次子传父、父传子了
                            外部状态管理可以在通信的时候让代码更加容易维护，降低项目的复杂度与耦合度
                            实现复杂通信需要useReducer+useContext跨级通信
                                能力上模拟Redux
4.useReducer有三个参数
    (顺序千万不要反了)
    第一个参数传的是一个函数 reducer叫减数器
        专门在外面管理状态的
    第二个参数是初始状态值
        就是一个外部的对象
    
    返回值是一个数组结构对象
        第一个参数是状态值，第二个参数是改变状态的唯一方法
5.useState是在内部管理状态，管理处理函数
    useReducer是在外部进行管理
6.dispatch要传一个固定的type值
    并不是直接覆盖掉state的，低耦合度，尽量不碰状态自身
    调用dispatch会把对象传到reducer里面，在reducer里进行处理
        处理函数的第一个参数会得到老的状态（对象），第二个参数会得到传过来的action对象，可以根据对象中的type值控制状态
            const reducer = (prevState,action) => {}
                第一个参数是旧的状态值
7.写法必须不影响原状态
    需要深复制老的状态 let newState = {...prevState}
8.好处在于根组件无状态
    完全通过外部状态控制
9.复杂的父子通信方式更适合
10.每次useReducer总是返回一个全新的对象
    在不同组件内创建的都不一样
    所以只能在根组件内创建一份，让大家共享
    useReducer不能放在函数外，只能在一个函数式组件内调用 
        不过可以配合useContext进行跨级通信
            使用Provider，把state和dispatch作为公共服务放在里面
11.Provider的value里也是双大括号写法
12.dispatch可以传一个type和value
13.只要点击改变方法，会立即发送一个dispatch传过去一个对象
    通过case判断改变哪个，更改之后会导致整个函数重新渲染，state接着往下传递
        孩子会拿到最新的state，得到最新的值
        useReducer真正有意义的点
            配合useContext跨级通信，把状态和处理函数送到孩子那里去
                一个孩子改，一个孩子访问
            整个代码耦合度非常低
                在根组件中没有任何状态的出现，子组件中也不涉及set更新状态的感觉
                    视图逻辑与状态逻辑完全分离
            最大的区别就是把set换成dispatch
14.useReducer缺点
    异步无法处理，只能在自己组件内写异步
    redux支持异步
        支持中间件写法
15.useReducer第三个参数理解1
    https://blog.csdn.net/NinthMonee/article/details/113855035 不太全
    https://www.likecs.com/ask-1129804.html 这个讲的还可以
    https://blog.csdn.net/qq_41890177/article/details/122200146 讲的很懂