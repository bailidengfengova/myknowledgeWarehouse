1.useReducer与useContext解决了非父子通信的问题
    将状态分离出来，一个组件能够改变状态，一个组件能够分离状态
        如果状态越来越多，功能做的就显得比较复杂，状态多不好维护与管理
    推出了一种写法，hooks的写法相同，就是把状态放在组件外面进行管理（需要共享的状态）
        想找一种状态管理的模式，React提供了一种方案，与React搭配使用非常方便
            可以让组件变成受控组件，无状态组件，把共享状态放在公共的外部进行管理，来实现组件状态的可维护，可迁移的特性
2.flux是一种架构思想，专门解决软件的结构问题，它跟MVC架构是同一类东西，但是更简单清晰
    facebook flex希望利用单向数据流的方式来组合React中的视图组件

    I.  用户访问View
    II. View发出用户的Action
    III.Dispatcher收到Action，要求Store进行相应的更新（分发到Store中）
    IV. Store更新后，发出一个"change"事件
    V.  View收到"change"事件后，更新页面

                    --------    Action  ------
                    \/                       |
    Action  ->  Dispatcher  ->  Store   ->  View

    Store提前会在View中进行订阅，Dispatcher发出Action里的某个事件之后，会更新页面
        即低耦合度更新视图，不在视图内部写更新逻辑，而是放在外部的Store中进行管理，View只不过是发起了一个Action动作，可能是点击了一下按钮，或者外部ajax异步请求回来

    View里并不需要管理逻辑，只需要管理视图，监听个事件，所有的行为放在外面管理，让View能够更加专心

    flux更像一个模式而不是一个正式的框架
        所以要用的话，需要手动设置Action，View，再写Store
3.flux存在多种实现（至少15种）
    https://github.com/voronianski/flux-comparison

    flux是用来构建客户端web应用的应用架构，利用单向数据流的方式组合React钟的视图组件
4.flux是架构思想，Redux是实现
    Redux是纯js实现的，并不依赖于React，所以可以与其他框架同用
5.Redux实现方法
    用一个单独的常量状态树（state对象）保存整个应用的状态，此对象不能直接被改变，可以使用actions和reducers进行管理

    目的是在整个组件外部设置一个"全局"状态树，像全局，但是比全局多很多限制