# 第3节：vuex的使用

如果是小型项目或者是很独立的项目，一般不需要使用vuex，但如何涉及到需要相互关联的数据比较多的时候，使用vuex会省去很多麻烦，因为使用vuex来保存我们需要管理的状态值，值一旦被修改，所有引用该值的地方就会自动更新。

- 大多数经常调用的基础数据,可在所有页面公用,这是适用于技术场合的;
- 对于组件,常用的有两种属性,一是data,一是prop.就我的理解而言,data负责组件内部的逻辑,prop负责与内外部数据之间的数据关联,如最常见的value.但对于路由页面组成的框架而言(如iview),如果切换路由页面,会导致原路由页面data清空,此时使用vuex.store来存储数据就可避免这种情况,这是适用于vue组件页面场合的;



首先使用npm 安装Vuex

```
npm install vuex -save
```



然后在main.js中引入

```
import Vuex from 'vuex'
Vue.use(Vuex)
```



vuex有5大方法：state、getters、mutations、actions、module

 

state(仓库)：

vuex的所有数据都放在 state 里，vuex其它方法操作的数据都来源于这里

 

getters(过滤)：

getters 跟 state 同样能获取数据，区别是 state 只能拿数据，getters可以对数据进行加工(过滤)

getters 跟 computed 同样具有缓存能力只有数据再次改变才会重新改变，否则就会直接拿取缓存中的数据。

 

mutations(修改)：

改变 state 的数据必须用 mutation ，异步操作不能用 mutation 要用 action

举个例子：当调用了两个包含异步回调的 mutation 来改变 state，如何知道什么时候回调和哪个先回调呢？

 

action(异步)：

action 补充 mutation 不能异步的方法

action 不能直接操作 state 而通过 mutation 来操作 state

 

module(模块)：

每个模块都有自己的的 state、mutation、action、getter、甚至是嵌套子模块

从上至下进行同样方式的分割(这句话炒官网的已经说得足够明白)

实际开发中都是以模块来开发，团队共同开发一个项目，各程序员负责各自模块文件就行了



> 注意：**官方并不介意我们这样直接去修改store里面的值，而是让我们去提交一个actions，在actions中提交mutation再去修改状态值**



深入使用后还有**mapState、mapGetters、mapActions**需要了解，这里暂不多说。

