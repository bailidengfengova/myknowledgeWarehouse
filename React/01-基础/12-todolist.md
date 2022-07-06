1.不操作DOM
    操作的是状态，让状态与节点进行映射
2.官方文档深拷贝写法
    var a = [1,2,3]
    var b = a.slice()
        slice不传参的时候，直接复制了一份a，把a重新复制给了b
        但是a和b是完全两个不同的数组
            并不是截取的理念，其实是深度的复制了一遍新的数组给b
3.深拷贝也可以用...
    b = [...a]
4.bind除了能修正this指向，第二个参数还可以传参
5.猜测 ****
    React里箭头函数传参
        <button onClick={this.handleClickCls(index)}>cls</button>
        直接这么写会直接执行，在render里进行了setState操作，会被认为不是纯函数，会一直循环执行下去
            可以写成
            <button onClick={() => this.handleClickCls(index)}>cls</button>
                然后函数为普通函数就好
6.通过箭头函数的方式，事件对象必须显式的进行传递，但是通过 bind 的方式，事件对象以及更多的参数将会被隐式的进行传递。
    就是传在第一个位置和最后一个位置的区别
        值得注意的是，通过 bind 方式向监听函数传参，在类组件中定义的监听函数，事件对象 e 要排在所传递参数的后面 
7.React事件处理讲的比较透彻
    https://blog.csdn.net/Han_Zhou_Z/article/details/123338807
8.很好的解决了我的困惑
    https://blog.csdn.net/weixin_48255917/article/details/120458535