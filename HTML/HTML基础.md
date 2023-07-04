# HTML

## 1. 排版标签

1. `<h1>`~`<h6>`标题

   > `<h1>`最好只写一个

2. `<p>`段落

   > `<p>` 标签很特殊！它里面不能有： `<h1>~<h6>` 、 `<p>` 、 `<div>` 标签

3. `<div>`用于整体布局,无具体含义

## 2. 图片标签`img`

```html
<img src="图片路径" alt="描述图片的文字">
```

> `alt` 属性的作用：
>
> 1. 搜索引擎通过 `alt` 属性，得知图片的内容。**主要作用**
>
> 2. 当图片无法展示时候，有些浏览器会呈现 `alt` 属性的值。
>
> 3. 盲人阅读器会朗读 `alt` 属性的值。

## 3. 超链接`a`

`<a>`超链接:

必要属性:

* `href`:指定跳转具体目标

  > - 跳转到指定页面
  > - 跳转到指定文件（也可触发下载）
  > - 跳转到锚点位置
  > - 唤起指定应用

* `target`:
  * `_self`:本窗口打开
  * `_blank`:新窗口打开

## 4.列表

1. 有序列表(ordered list)

2. 无序列表(unordered list)

   * 需配合`<li>`使用

3. 自定义列表(definition list)

   > 所谓自定义列表<`<dl>`，就是一个包含`术语名称<dt>`(definition title)以及`术语描述<dl>`(definition list)的列表

## 5. 表格`<table>`

![table](C:\Users\zhaom\Desktop\笔记\images\table.png)

## 6. 表单

### `<form>`表单

可选属性:

* `action`:指定表单提交地址
* `target`:指定提交后如何打开网页
  * `_slef`/`_blank`
* `method`:表单的提交方式
  * `get`/`post`等

### input基本格式

```html
<input type="text" name="input-name" value="default-value">
```

#### type属性

可选值:

- `text`: 单行文本
- `password`: 密码
- `email`: 电子邮件地址
- `number`: 数字
- `checkbox`: 复选框
- `radio`: 单选框
- `submit`: 提交按钮
- `button`: 普通按钮

## H5新增标签

`<header>`头部

`<fotter>`脚步

`<aside>`侧栏
