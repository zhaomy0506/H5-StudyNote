## Element-Ui相关

### 关于el-form表单校验规则

el-form校验 需要

1. el-form标签 需要model属性指定数据存储位置(注:不是v-model)
2. el-from标签 需要rules指定校验对应规则
3. el-form-item标签 需要prop指定校验字段

示例(表单元素):

```html
<el-form :model='formData' :rules='rules'>
    <el-form-item prop='name'>
        <el-input v-model='inputData'></el-input>
    </el-form-item>
</el-form>
```

```js
let formData = ref({name:''})
let rules = {
    /*
      1. required: 表示字段是必须的
      2. trigger: 表示触发校验的时机
          blur: 失去焦点 change: 发生变化
      3. validator: 自定义校验规则 -> 指定对应函数
    */
    name:[{required:true,trigger'blur',validator:validatorName}]
}
```

自定义校验规则:

```js
// 自定义校验规则
/*
  1. rule 规则对象
  2. value 当前的值
  3. callback 放行函数
*/
const validatorName = (_: any, value: any, callback: any) => {
      if (value.length >= 2 && value.length <= 10) {
        callback()
      } else {
        callback(new Error('品牌名称长度2-10位'))
      }
}
```



