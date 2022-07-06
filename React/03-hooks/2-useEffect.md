1.函数式组件里面没有生命周期的概念
    但useEffect可以配合一些逻辑与依赖模拟类似于类中生命周期的概念
    就是一个函数，不要把类的生命周期概念对号入座
2.useEffect（处理副作用）
3.痛点
    直接在函数内部发送axios请求，然后setState改变状态，控制台会一直发送网络请求
        因为setState更新完之后，整个函数组件会重新运行一遍，结果会更新，之后又axios，又set，又执行。。
    所以完全不被允许直接在函数内放axios请求，会频繁执行n次，所以不应该在这里进行逻辑处理
4.useEffect接受两个参数
    第一个参数为一个函数
    第二个参数为一个数组
        可以传空数组，传空数组的意思是副作用函数不依赖于任何东西，只会执行一次
    setState更新还会导致整个函数重新执行，由于useEffect注册了回调函数，useEffect会重新运行一遍
        但是里面的回调函数只会运行一次，因为第二个参数是个空数组，与cdm生命周期类似，组件已经挂载到节点上，useEffect发送请求，最终更新页面
5.第二个参数为依赖，可以传多个值
6.第二个参数传空数组与不传空数组的区别
    让useEffect中的内容复用
        如果在useEffect里用了状态，但是还传空数组（怎么看用没用，就是看set状态的时候，有没有用到state）
            会出现
                React Hook useEffect has a missing dependency: 'name'. Either include it or remove the dependency array. You can also do 
                a functional update 'setName(n => ...)' if you only need 'name' in the 'setName' call  react-hooks/exhaustive-deps
            造成的后果是
                修改状态后，回调函数也不会执行
    如果在第二个参数中传了state值，将会无警告，更改之后，useEffect也会再次执行，里面的回调函数也会再次执行
        useEffect第一次执行一次，之后state（依赖）更新也会执行一次
7.在函数里用到了这个状态就叫依赖
    依赖这个值的更新
    传空数组表示不依赖任何人