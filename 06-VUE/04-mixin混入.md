# `Mixin`混入

> 特别注意：Vue3中尽量避免使用mixin，因为可以使用`Composition`API来代替，可维护性更高。

混入（mixin）是一种用于在多个组件之间共享代码的技术。

使用混入，您可以定义一组可重用的逻辑，然后将其混入到需要该逻辑的组件中。这样可以避免代码重复，提高代码的可维护性和可重用性。

## 优先级

1. 数据和方法：组件data ，methods 优先级高于mixin data，methods优先级。
2. 生命周期：生命周期函数，先执行mixin里面的，再执行组件里的。
3. 自定义的属性、组件中的属性、优先级高于mixin属性的优先级。

## 基础使用

```js
export default{
    data(){...some code},
    methods:{...some code}
    mouted(){...somecode}
    ...
}
```

```js
//全局混入
Vue.mixin(xxx)
//局部混入
mixins:['xxx','xxx']
//随后使用即可
```



