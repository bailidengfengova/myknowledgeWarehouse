1.React16.8之前函数组件只能做无状态组件被父组件控制
    只能接受父组件的属性
2.React16.8之后引入了hooks
    函数组件可以独立了
3.高阶组件是为了让类组件更有复用性
    弊端
        代码层级复杂
        函数式组件可以减缓这个问题
4.生命周期复杂
    有了hooks之后复杂的类生命周期可以暂时放一下了
5.之前的痛点
    有时候写成无状态组件之后，如果又需要状态，必须再改成类组件
6.hooks
    可以理解为有了hooks之后函数式可以钩住状态了
7.rfc可以创建一个函数式组件
8.useState
    需要从React中通过大括号的方式解构
    {useState} from 'React'
    useState是一个函数，可以传一个初始值

    useState返回的是一个数组，第一个元素是初始值，第二个元素是一个方法
        第一个值是存储状态的状态值
        第二个值是改变状态的唯一方法
            因为没有this
    所以一般都是 数组解构的方法来写，一般写的需要有意义
        const [name,setName] = useState('hanfei')
    useState可以写多次
    通过自己的方法改变自己唯一的状态
    快捷键
        usss
9.setState
    setState方法是通过覆盖来实现改变原来的状态的
        导致函数重新执行
    setState设置状态，需要的时候直接访问状态就行，不需要再访问什么valuse值了
        setState(value)就可以设置状态
    比this.setState简单
10.不要直接改变原状态，只能用setState方法，因为不好用，可能会造成预期的问题
11.如果想要清空
    可以把input变成受控的，就是给加个value
    追加状态可以setList([...list,text])这么追加