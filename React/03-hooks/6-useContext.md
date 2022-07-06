1.useContext减少组件层级
    跨级通信的方案
2.useContext会大大降低代码复杂度
    可以让消费者变得简单
        当时必须套上Consumer，还需要在里面包含一个回调函数
        现在的useContext只需要把用React.createContext定义好的GlobalContext当成参数传进来
            useContext返回的值是供应商提供的对象
                可以大大降低编码复杂度
            