# new Vue(options)配置项

## 1.`template`

功能: 指定需要渲染的HTML结构 

注意: `template`中的内容会替换el指定的容器中的所有内容

### 代码示例

```js
new Vue({
    template:`
    	<h1>你好</h1>
    `
})
```

## 2.`el`

功能: 指定页面中已存在的DOM元素作为Vue实例的挂载目标 

使用: 可以使用【**CSS选择器**】或【**DOM对象**】

两种使用方式:

1. 创建Vue实例的时候配置el属性
2. 先创建Vue实例,随后通过`vm.$mount('#root')`指定el值

### 代码示例

```js
//方式一
new Vue({el:'.app'})
//方式二
new Vue({...some code}).$mount('.app')
```

## 3.`data`

功能: 存储组件中用到的数据 

注意: `data`中的所有属性都会被代理到【vm】或【组件实例对象】上,可以直接通过`this.xxx`访问

使用: 可以是对象或函数(组件中必须是函数) 

```js
//对象式写法,仅可以使用在创建vm时
new Vue({ data:{ ...data code } })
```

```js
//函数式写法,可以作用在vm或组件实对象上
new Vue({
    data(){
		return { ...data code }
    }
})
```

## 4.`methods`

功能: 存储组件中用到的方法,通常是事件回调函数 

使用: 通过this.yyy调用方法 

注意: methods中的方法不要与data中的属性重名



## 5.`computed`

计算属性: `computed`配置项,该配置项为一个对象

1. 定义: 要用的属性不存在,是根据已有的<span style="color:red">**属性**</span>计算得来的
2. 原理: 底层借助了`Object.definedProperty`方法提供的`getter`和`setter`实现
3. `getter`什么时候执行?
   1. 属性被初次读取时
   2. 当依赖的数据发生变化时

> *与methods相比,内部拥有缓存机制(方便复用),效率更高,调试方便*

**备注:**

1. 计算属性会出现在vm上,直接读取使用即可,**不是函数!**
2. 计算属性被修改,必须写setter去响应修改,且setter中要引起依赖的数据发生变化

计算属性的两种写法:

```js
//正常写法
computed: {
    fullName: {
        get() {
            return this.firstName + '-' + this.lastName
        },
        set(value) {
            console.log(value);
        }
    }
}
//简写形式
//只考虑读取,不考虑修改,可以把属性直接写成一个函数,无需配置单独配置getter
computed: {
	fullName() {
		return this.firstName + '-' + this.lastName
	}
}
```



## 6.`watch`

[Vue监视数据原理](./面试题.md#2.Vue中监视数据的原理)

1. 当被监视的属性发生变化时,回调函数自动调用
2. 监视的属性必须存在,才能进行监视!
3. 监视的两种写法:
   - `new Vue`时传入`watch`配置项
   - 通过`vm.$watch(attr,{option})`监视

监视一个属性时,可以传入一些配置项:

| 配置项      | 类型   | 说明                                                         | 默认值 |
| ----------- | ------ | ------------------------------------------------------------ | ------ |
| `handler`   | 函数   | 监视回调函数，接收新值和旧值作为参数                         | 无     |
| `immediate` | 布尔值 | 表示是否在初始化时就触发handler函数                          | false  |
| `deep`      | 布尔值 | 表示是否深度监视属性，即如果属性是一个对象或数组，是否监视其内部的变化 | false  |

### 深度监视

1. vue中的watch默认不监测对象内部数据(一层)
2. 配置`deep:true`可以监测到对象内部的数据变化(多层)

> *vue自身可以监测对象内部值的改变,但是vue提供的watch配置项默认不可以*
>
> *使用watch根据数据的具体结构,来决定是否开启深度检测*

### 正常与简写形式

```js
//正常写法
watch:{
    fullName:{
        immediate:true,//初始化时触发
        deep:true,//深度监视
        handler(newValue,oldValue){ //监视到数据改变时触发该函数}
    }
}
//在不需要immediate和deep配置项时,可以简写
watch: {
    fullName(){}
}
```

### 6.1 `computed` 和 `watch` 区别

`computed`可以完成的,`watch`都可以完成

`watch`能完成的功能,`computed`不一定可以完成,例如:`watch`可以进行异步操作

两个重要的原则:

1. 所有被Vue所管理的函数,最好写成普通函数,这样this的指向是vm或组件对象实例
2. 所有不被vue所管理的函数(定时器,ajax...),最好写成箭头函数,这样this才能指向【vm】或【组件实例对象】



## 7.`filters`

> 定义:对于要显示的数据进行特定格式化后在显示***(适用于一些简单逻辑的处理)***

功能: 对要显示的数据进行特定格式化后再显示 

语法:

1. 注册过滤器:`Vue.filter(name,callback)`或者`new Vue({fileters:{}})`
2. 使用过滤器:`{{xxx | 过滤器名}}`或者`v-bind:属性="xxx | 过滤器名"`

注意:

1. 过滤器也可以接收额外的参数,多个过滤器也可串联使用
2. 并没有改变原值,是产生新的对应数据



## 8.`props`

功能: 让组件***接收***外部传入的数据

1. 传递数据

```html
<Demo name="xxx"/>
```

2. 接收数据

简单接收:

```js
props:['name',...]
```

限制类型接收:

```js
props:{
    name:String
}
```

限制类型,限制是否必须,指定默认值

```js
props:{
    name:{
		type:String,//限制类型
        required:true,//限制必要性
        default:'老王'//默认值
    }
}
```

>***props是只读的,如需修改,请复制一份在data上使用***
>
>***该配置项会优先于data配置项放置VueComponent实例对象上***