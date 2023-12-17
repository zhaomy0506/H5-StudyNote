# AJAX(异步的JS和XML)

> AJAX是浏览器提供的一些方法,用来与服务器通信的技术

优点:

- 异步的JavaScript和XML

  > XML是一种可拓展标记语言,有更好的替代品(**JSON**)

- 解决了与服务器通信问题,无需刷新即可获取数据

- 允许根据用户事件更新页面内容

缺点:

- 没有历史记录,不能回退
- 存在跨域问题
- seo(搜索)优化不友好

## HTTP网络请求

每次请求需要

- 请求首行,请求方式,请求地址,http协议
- 请求头 键值对
- 空行 用来**分隔**请求头和请求体
- 请求体 GET没有请求体,Post有

响应首行 http协议 http状态码 状态码描述

响应头

响应体

## 发送请求

1. 需要创建出请求实例

   ```js
   let xhr = new XMLHttpRequest();
   ```

2. 设定请求的地址/方式(get/psot...)

   ```js
   xhr.open('请求方式','地址')
   //get请求,请求携带参数,需要拼接到url后
   //通过?分割,key=value形式
   ```

   POST请求,需要设置请求头

   ```js
   xhr.setRequestHeader('Content-type','规则集')
   //Content-type字段用于表明传输的格式(文档中会写)
   //application/json	json格式
   //application/x-www-form-urlencoded	要去数据格式 key=value&key=value格式
   //multipart/form-data 二进制文件格式
   xhr.responseType = 'json'
   ```

3. 发送请求

   ```js
   xhr.send()
   ```

   等待返回

4. 接收服务器返回的数据

   第四步可以写在第二步,可以监听到open状态

   ```js
   //该函数请求实例的状态发生变化,该函数就会触发
   xhr.onreadystatechange = ()=>{
   	//判断请求步骤
   	if(xhr.readyState == 4){
   		//判断请求状态
   		if(xhr.statue == 200){
   			//获取到的数据
   			console.log(xhr.response)//JSON格式
   			let result = JSON.parse(xhr.response);
   			console.log(result)
           }
       }
   }
   ```

   监听请求完成的状态,也可以通过绑定onload事件实现

   ```js
   xhr.onload = ()=>{
   	if(xhr.status == 200){
   		console.log(xhr.response)
       }
   }
   ```

   

常用属性

1. `.readyState` 状态码

   - `0` 请求还未初始化

   - `1` 设定请求

   - `2` 请求已接受

   - `3` 正在处理请求

   - `4` 请求已完成

2. `.status` 响应状态码

   - 200成功

   - 404不存在

3. `.statusText` HTTP状态码的语言描述

4. `.responseType = 'json'` 服务器返回的是json字符串,会被自动转换成json对象

5. `.setRequestHeader()`设置请求头类型

6. `.send()`发送Ajax请求

7. `.abort()`取消请求

## 超时设定

`.timeOut = 时间(ms)` 超时未响应,就取消请求

# fetch

fetch 也是发送异步请求的工具(Promise版的AJAX)

fetch('url')

fetch会直接返回一个promise 结果

