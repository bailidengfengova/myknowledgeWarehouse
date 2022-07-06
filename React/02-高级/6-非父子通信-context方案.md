1.context状态数传餐
    React提供的跨级通信方案
    应用理念
        生产者-消费者设计模式
2.所有供应商与消费者均由context对象创建
    生产者可以通过这个包裹
         <GlobalContext.Provider>
    不过消费者有所变化
        要在 <GlobalContext.Consumer>里放一个回调函数
            把内容放在回调函数里
            回调函数可以接受形参，接受供应商提供的公共服务
    供应商通过一个固定的属性value传递服务
3.回调函数大括号里记得要写return
4.谁想要通信，在父组件身上包装一个Provider供应商组件
    供应商组件通过React的createContext方法创建
    也叫做跨组件通信方案
5.还有一种组件通信方式
    redux