# Vuex

><span style="color:red">vue2中需要使用Vuex@3版本</span>
>
><span style="color:red">vue3中需要使用Vuex@4版本</span>

专门在Vue中实现集中式状态(数据)管理的【Vue插件】

## 何时使用？

1. 多个组件依赖同一状态
2. 来自不同组件的行为需要便跟同一状态

> 多个组件需要共享数据

## VueX工作原理:

VueComponent (人)

actions 行为、动作 (服务员)

mutations 加工、维护 (厨师)

state 状态对象 (菜品)

<img src="D:/WEB study/H5-StudyNote/img/vuex.png" style="zoom: 33%;" />

## 搭建Vuex环境

```js
//创建文件 ./src/store/index.js
//引入Vue核心库与Vuex
import Vue from 'vue'
import Vuex form 'vuex'
//安装Vuex插件
Vue.use(vuex)
//创建并导出store
export defalut new Vuex.store({
    actions:{},//用于响应组件中用户的动作
    mutations:{},//用于修改state中的数据
    state:{}//用于存储数据
})
```

> 准备好相关文件后,需要在main.js文件中引入并在常见vue实例(vm)的时候,传入store配置项

1. 组件中读取vuex中的数据:`$store.state.xxx`
2. 组件中修改vuex中的数据:`$store.dispatch('方法名',数据)`或者`$store.commit('方法名',数据)`

> 若没有网络请求或其他业务逻辑,组件中可以跳过dispatch,直接进行commit

## 关键属性

| 属性       | 描述                   |
| ---------- | ---------------------- |
| state      | 全局的数据中           |
| getters    | 全局的计算属性         |
| actions    | 处理数据并提交         |
| mutations  | 修改全局数据的方法集合 |
| modules    | 将全局数据分模块       |
| namespaced | 将模块内容独立         |

## getter配置项

用于加工state中的数据,类似于`computed`

组件中获取改配置项中的数据,使用`$store.getters.xxx`

## Vuex中的`mapxxx` API

> `mapXXX`可以方便在组件中使用vuex中的数据,一遍一遍的写`$store.xxx.xxx`

 `mapState`:用于映射state中的数据为计算属性

`mapGetter`:用于映射getter中的数据为计算属性

`mapMutations`/`mapActions`,生成对应的方法,需要在使用时传参

1. 使用mapxxx需要先进行引入

```js
import {mapxxx} from 'vuex'
```

2. 有两种书写方法

```js
computed(或者methods):{
    ...mapxxx({使用名:vuex中数据名})//普通写法
}
...
computed(或者methods):{
    ...mapxxx(['使用名/vuex中数据名'])//简写形式,当使用名和vuex中的数据名相同时,可以使用数组形式
}
```

## Vuex模块化编码+命名空间

> 让代码更好维护,多种数据分类更加明确

```js
const a = {
    namespaced:true,//开启命名空间
    state:{},
    mutations:{},
    actions:{}
}
const store = new Vuex({
    modules:{
        a//使用vuex模块化,新配置项modules
    }
})
```

1. 读取state

```js
//方式一:直接读取
this.$store.state.a.xxx
//方式二:借助mapState
...mapState('a',[xxx,xxx...])
```

2. 读取getter

```js
//方式一:直接读取
this.$store.getter['a/xxx']
//方式二:借助mapGetters
...mapGetters('a',[xxx,xxx...])
```

3. 调用dispatch(action)

```js
//方式一:自己调用
this.$store.dispatch('a/xxx',数据)
//方式二:借助mapActions
...mapActions('a',[xxx,xxx...])
```

4. 调用commit(Mutations)

```js
//方式一:自己调用
this.$store.commit('a/xxx',数据)
//方式二:借助mapMutations
...mapMutations('a',[xxx,xxx...])
```

