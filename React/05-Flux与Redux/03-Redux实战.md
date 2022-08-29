1.Redux原理其实就是订阅发布模式
2.按照redux
    npm i redux
3.store处理不了状态的，需要交给reducer进行处理
    reducer是专门处理状态的函数
4.action必须有type属性
5.顺序
    先dispatch，然后触发action，然后触发订阅者
   *** 它说的是订阅者会首先进行订阅，但是第一个执行并没有打印出执行信息？**
    ***这点应该说的是触发**
6.状态不会在订阅的时候，传递给订阅的参数，而是需要订阅者自己获取
    store.getState()
7.正常dispatch发出的action对象是通过Action Creator创建出来的
    可以写一个函数生成这个对象
8.export default只能导出一个，想要导出多个可以导出一个对象
9.redux中的状态只是一个普通的对象而已
    需要把对象转化为组件内部的状态