1.由于路由拦截导致的props丢失
    之前的写法component直接传的组件，会把组件当成孩子，Route会提供props属性
    render的写法把Center组件自己给实例化了，实例化的过程中也没有传任何属性
2.Route的源码
    class Route extends Component {
        ...
        render() {
            var MyComponent = this.props.component
            return <div>
                <MyComponent history={} match={} ... />
            </div>
        }
    }
3.render写法也可以传参数
    回调函数里写一个形参即可
        通过{...props}即可传值 **** 传值方式可以借鉴
4.如果父组件里的props没有history，父组件的父组件里也没有history
    可以用withRouter高阶组件
5.withRouter的能力就是把组件包装一层，变成父组件，给子组件传数据
    没有父组件或者父组件没有history属性的时候，可以使用withRouter
        由withRouter提供此属性
        可以跨级传输history这些值
            只要接收原始的组件，把组件能力增强，由路由提供，隔空提供history,match等属性
6.withRouter是一个高阶组件