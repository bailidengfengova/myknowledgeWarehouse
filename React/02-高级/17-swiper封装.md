1.npm i swiper
2.swiper的坑
    要引入css
        import 'swiper/css'
        中文文档有问题的话，可以看看英文文档
        如果css有问题的话，也可以引入swiper-bundle.min.css
3.引入css/bundle可以全部引入
    不需要use注册一下
    import 'swiper/css/bundle';
        这么写可以解决没有分页器的问题
4.didMount执行的时候
    异步不阻塞
        所以异步下边的new会先执行
        所以应该把new放在dom创建完的地方
            也可以把new放在setTimeout里面
                setTimeout是异步更新的
                    但是里面是同步更新的，所以是DOM更新完了，可以进行new操作
                        异步里面是同步更新DOM的
5.组件封装
    <h1>为了不至于写死，或者是类别特别多的情况下</h1>，为了复用，可以用插槽的方式
    插槽的方式就是给一个this.props.children就可以了
6.图片显示不完整怎么办
    宽度给100%
    让其不超过div的宽度，高度自适应