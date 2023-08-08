> Vue模版语法分为两种:
>
> 1. 插值语法
> 2. 指令语法

# 一、插值语法

功能:用于解析标签体内容

写法:`{{xxx}}`,内部`xxx`要写成js表达式,可以读取到data中所有的属性

# 二、指令语法

## 数据绑定

以下`xxx`为js表达式,可以动态指定任意一个属性的属性值

1. 单项绑定:`v-bind`

   > 数据只能从Data中流向页面

   `v-bind:属性名='xxx'`,简写:`:属性名='xxx'`

2. 双向绑定:`v-model`

   > 数据从Data流向页面,也可以从页面流向Data

   `v-model:value='xxx'`,简写:`v-model='xxx'`

   `v-model`只能作用与表单类的元素上(input,select..)

v-model有三个修饰符

1. `.lazy` 失去焦点后再收集数据
2. `.number` 输入字符串转换为有效的数字
3. `.trim` 去除首位空格

### `v-model`收集表单类数据

`v-model`默认就是收集表单类的`value`值,对于一些特殊的表单,需要使用其他属性配合使用

1. 单选框: `type='radio'`

   需要给每个单选框,设置一个`value`属性,同一组单选框绑定同一个变量,`v-model`会收集选中单选框的`value`值到变量中

2. 复选框: `type='checkbox'`

   - 没有配置value属性,`v-model`会收集`checked`属性(`Boolean类型`)
   - 配置了value属性:
     1. 初始值为非数组,收集checked属性(`Boolean类型`)
     2. 初始值为数组,收集value值(`Array类型`)

## 事件绑定`v-on`

事件绑定使用`v-on:事件='xxx'`,简写`@事件='xxx'`,

其中`xxx`为:

1. 绑定事件触发的函数
2. 需要执行的代码

> 需注意: `@click='demo'`与`@click='demo($event)'`,效果一致,后者可以传参

### 事件修饰符

***修饰符可以链式调用***

事件修饰符总共有七个

1. `.prevent` 阻止默认事件(*)
2. `.stop` 阻止事件冒泡(*)
3. `.once` 只能被触发一次(*)
4. `.capture` 捕获阶段触发事件
5. `.self` 当`event.target=操作的Dom`,触发
6. `.passive` 事件的默认行为立即执行,无需等待事件回调执行完毕直接执行,(滚动条)
7. `.native` 监听原生的事件，而不是Vue封装的事件

#### 键盘事件修饰符

Vue中给常用的按键起了别名,例如:`enter`、`delete`、`esc`、`space`、`tab`、`up`/`down`/`left`/`right`

Vue中未提供别名的按键,可以使用按键的key值绑定,需注意使用`kebab-case(短横线命名法)`

#### 系统修饰键

`ctrl`,`alt`,`shift`,`win`

1. 配合keyup使用,按下修饰键的同时,需要配合其它按键使用
2. 配合keydown使用,正常触发

> 需要自定义别名,可以添加配置,`Vue.config.keyCodes.xxx`

## 条件渲染

1. `v-if`,可配合`<template>`标签使用

   适用于:切换频率低的场景

   特点:不展示的DOM节点直接移除

> `v-if`可以和`v-else-if`和`v-else`配合使用,但要求结构不能被打断

2. `v-show`

   适用于:切换频率高的场景

   特点:不展示的DOM元素,被隐藏:`display:none`

## 列表渲染指令

`v-for`:用于展示列表数据

语法:

- `v-for='item in xxx' :key:'yyy'`

- `v-for='(item,index) of xxx' :key:'yyy'`

可以遍历数据: `Array数组`,`Object对象`,`String字符串`,`Number指定次数`

## 补充

### 1.`v-html`

`v-html`,类似于`Dom.innerHTML`

> ***严重注意:v-html有安全性问题!!!***
>
> 1. 在网站上动态渲染任意HTML是非常危险的行为,容易导致XSS共攻击
> 2. 一定要在可信的内容中使用v-html,永远不要用在用户提交的内容上

### 2.`v-cloak`

v-cloak指令(没有值),配合css使用

本质是一个特殊属性,Vue实例创建完毕并接管后,会删掉v-cloak属性

使用css配合v-cloak可以解决网速慢时页面展示出{{xxx}}的问题

### 3.`v-once`

v-once 所在节点在初次动态渲染后,就视为静态内容了

以后数据的变化不会引起v-once所在的结构的更新,可以用于性能优化

### 4.`v-pre`

该指令跳过其所在节点的编译过程

可利用它跳过:没有使用指令语法,没有使用插值语法的节点,会加快编译

# 三、自定义指令

>1. 指令定义时不需要加 `v-` 前缀,但使用时必须加上 `v-` 前缀
>2. 如果指令名是多个单词，要使用 `kebab-case` 命名方式，不要使用 `camelCase` 命名方式

## 1.局部自定义指令

在局部自定义指令中，vm配置对象的 `directives` 配置中

```js
new Vue({
    directives:{
        指令名:配置对象/回调函数
    }
})
```

## 2.全局自定义指令

在全局自定义指令中，你可以使用 `Vue.directive` 方法来定义指令

```js
Vue.directive(指令名,配置对象/回调函数)
```

### 配置对象常用的三个回调函数

1. `bind`:指令与元素成功绑定时调用
2. `inserted`:指令所在元素被插入页面时调用
3. `update`:指令所在模版结构被重新解析时调用

### 回调函数参数

1. `element`：所添加的真实 DOM 元素
2. `binding`：一个对象，
   1. `banding.value` 传入的指令的值
   2. `banding.oldvalue` 旧值