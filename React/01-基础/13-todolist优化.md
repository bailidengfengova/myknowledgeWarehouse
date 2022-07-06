1.每次点击完后输入框内容清空
    this.myref.current.value = ""
2.条件渲染
    三目运算符也可以用 && 来代替
    {this.state.list.length === 0 ? <div>暂无代办事项</div> : null}
    {this.state.list.length === 0 && <div>暂无代办事项</div>}

    此情况是节点的动态创建与删除

    也可以用类名 动态加hidden来控制显示隐藏
    