1.ref
    引用的缩写 固定的
    调用的时候要写 this.refs
        引用如果绑在一个普通标签上，引用的是标签本身
            所以this.refs.xxx.value可以拿到input的值
2.React render的时候可以选择按照严格模式渲染，默认套在React.StrictMode里
    <React.StrictMode>
        <App />
    </React.StrictMode>
3.refs将被弃用
    ref可以重复多个，编译器检查不出来，容易被覆盖
4.refs更新的方案
    React.createRef()
        创建完之后返回的是一个ref对象(这个做通信的时候可能会用得上)
            之后把对象绑在ref上 this.myref
                点击之后拿到的是一个对象
                    对象上有一个current属性
                        属性里才是原生的DOM节点
5.React中尽量减少DOM操作
    只关注数据的改变
        状态改完了，页面自动维护更新
6.为什么写一个状态变量，更新变量之后，视图不显示
    在vue中，data属性是利用Objet.defineProperty处理过的，更改data数据的时候会触发数据的getter和setter，但是React中没有这样的处理，直接更改，React无法得知，所以要使用this.setState改变状态
7.setState 间接修改状态
8.状态是组件内部特有的数据载体