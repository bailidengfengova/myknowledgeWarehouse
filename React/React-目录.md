200
一、React介绍（001-002）
    1.React起源与发展    
    2.React与传统MVC的关系
    3.React的特性
    4.虚拟DOM
二、create-react-app（003-003）
三、编写第一个react应用程序（004-004）
四、JSX语法与组件（005-013）
    1. JSX语法 （005）
    2. 2.Class组件 （006）
    3. 函数式组件 （007）
    4. 组件的样式 （009）
    5. 事件处理 （010-012）
       5.1、绑定事件
       5.2、事件handler的写法
       5.3、Event 对象
    6.Ref的应用  （013）
       6.1给标签设置ref="username"
       6.2 给组件设置ref="username"
       6.3  新的写法
五、组件的数据挂载方式（014-030）
    1、状态(state)    （014-025）
       (1) 定义state
       (2) setState
    2、属性(props)   （026-029）
    3、属性vs状态 （030）
六、表单中的受控组件与非受控组件（031-033）
    1、非受控组件 （031）
    默认值
    2、受控组件  （032-033）
七、组件通信的方式（034-042）
    1. 父子组件通信方式 （034-038）
    2. 非父子组件通信方式  （038-042）
       (1) 状态提升(中间人模式)
       (2)  发布订阅模式实现
       (3)  context状态树传参
八、React生命周期（043-057）
    1. 初始化阶段 （043-045）
    2. 运行中阶段  （046-050）
    3. 销毁阶段  （051）
    新生命周期的替代 （052-054）
    react中性能优化的方案 （055）
       1. shouldComponentUpdate 
       2. PureComponent 
九、React Hooks（058-067）
    使用hooks理由
    useState(保存组件状态)
    useEffect(处理副作用)和useLayoutEffect (同步执行副作用)
    useEffect和useLayoutEffect有什么区别？
    useCallback(记忆函数)
    useMemo 记忆组件
    useRef(保存引用值)
    useReducer和useContext(减少组件层级)
    自定义hooks
十、React 路由（068-078）
    1. 什么是路由？
    2. 路由安装
    3. 路由使用
       (1) 路由方法导入
       (2) 定义路由以及重定向
       (3) 嵌套路由
       (4) 路由跳转方式
       (5)  路由传参
       (6)  路由拦截
       (7)  withRouter的应用与原理 
    4.项目注意
       (1) 反向代理
       (2)  css module
十一、Flux与Redux（079-086）
    1. redux介绍及设计和使用的三大原则
    2. redux工作流
    3. 与react绑定后使用redux实现案例
    4. redux原理解析
    5. reducer 扩展
    6. redux中间件
    7. Redux DevTools Extension
十二、 react-redux （087-090）
    1. 介绍
    2. 容器组件与UI组件
    3. Provider与connect 
    4. HOC与context通信在react-redux底层中的应用
    5. 高阶组件构建与应用
    6. Redux 持久化
十三、UI组件库（091-098）
    1. ant-design （PC端）
    2. antd-mobile （移动端）
十四、Immutable（099-102）
    1.Immutable.js介绍
    1. 深拷贝与浅拷贝的关系
    2. Immutable优化性能的方式
    3. Immutable中常用类型（Map，List）
    4. Immutable+Redux的开发方式
    5. 缺点
十五、Mobx（103-107）
    1. Mobx介绍
    2. Mobx与redux的区别
    3. Mobx的使用
    4. mobx-react的使用
    5. 支持装饰器
十六、TS（108-116）
    1-typescript
    2-安装
    3-声明
    4-变量声明
    5-定义普通函数
        接口描述形状
        传参
        类型断言as
    6-定义普通类
    7-定义类组件
    8-定义函数式组件
        useRef
        useContext
        useReducer
    9-父子通信
    10-路由
        编程式导航
        动态路由
    11-redux 
十七、styled-components（117-119）
    基本
    透传props
    基于props做样式判断
    样式化任意组件(一定要写className )
    扩展样式
    加动画
十八、单元测试（120-122）
    挂载组件
    测试组件渲染出来的 HTML
    模拟用户交互
十九、 redux-saga（123-128）
    代码实现
二十、 React补充（129-133）
    1. Portal （129-130）
       1、用法
       2、在protal中的事件冒泡
    2.Lazy 和 Suspense  （131）
       1、React.lazy 定义
       2、如何使用React.lazy
    3. forwordRef  （132）
       未使用forwordRef
       使用forwardRef
    4. Functional Component缓存 （133）
       为啥起memo这个名字？
       作用
       与PureComponent 区别
       用法
二十一、React扩展（134-151）
    1. GraphQL  （134-141）
       （1）介绍与hello
       （2）参数类型与传递
       （3）mutation
       （4）结合数据库
       （5）客户端访问
       （6） 结合React
    2. dva  （142-145）
       dva 应用的最简结构
       数据流图
    3. umi  （146-151）
       安装脚手架
       目录
       路由
       mock功能
       反向代理
       antd
       dva集成