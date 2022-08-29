1.redux设计使用的三大原则
    I.  state以单一对象存储在store对象中
        就是修改的与访问的是同一个对象
    II. state只读（每次都返回一个新的对象）
    III.使用纯函数reducer执行state更新
2.纯函数
    I.  不会有其他的影响，也就是对外界没有副作用
    II. 同样的输入得到同样的输出
3.如果reducer中的状态管理的多了会怎么样
4.action的type是固定的
    payload这个不固定
5.路由退回上一个页面的方法
    props.history.goBack()
6.数据存在了浏览器的内存中
    不过刷新页面之后就没了
        可以参考redux持久化存储
7.缺点
    如果状态过多的话，reducer里的case分支会越来越多
    
    解决
        可以把reducer拆分成几个小的reducer，每个reducer管理里面的一个子状态，最终再合并成一个大的单一对象状态
8.redux提供了一个reducer拆分与合并的扩展
    如果不同的action所处理的属性之间没有联系，可以把Reducer函数拆分，不同的函数负责处理不同属性，最终把它们合并成一个大的Reducer即可
9.合并函数combineReducers
    合并了之后，getState拿到的state也不一样了
    combineReducers接收的是一个对象
10.思考
    如果在不同的dispatch的时候对号入座不同的reducer呢
        其实redux并不知道是给谁发的reducer，会把所有子reducer进行遍历
        dispatch之后，所有的reducer都会被执行一遍，所有的订阅者都会被执行一遍
11.如何提高效率
    如果多个页面用同样的数据，只需要请求一次就行，请求到把数据缓存到redux store中，放到了内存中
        如果想永久缓存，可以用localStorage