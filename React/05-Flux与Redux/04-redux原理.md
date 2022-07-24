1.本质上是发布订阅
2.subscribe核心原理为订阅
3.发布订阅模式的写法
    let list = [];
    function subscribe(callback) {
        list.push(callback)
    }

    function dispatch() {
        for (let cb in list) {
            list[cb] && list[cb]()
        }
    }
4.reducer的作用是在dispatch的时候通知reducer执行