# JQ中的AJAX

`$.ajax({setting})`,setting为一个对象,

可以设置如下属性:

1. type 请求类型

2. url 请求地址

3. data 请求携带数据

4. contentType post请求时,设置请求类型

5. success,值为一个函数,可以传参代表请求体,

   请求体为JSON字符串时,会自动转换成JSON对象

6. error:值为一个函数,传参

```js
$.ajax({
    type: 'get',//设置类型get/post...
    url: 'https://v1.hitokoto.cn/',//请求地址

    /* post请求,请求类型
    contentType:'application/x-www-form-urlencoded', */
    
    //请求携带的参数
    data: {
        c: "j",
    },
    //成功后触发,可以传一个形参,res,代表响应体
    success: (res) => {
        $('body').append(`<h1>${res.hitokoto}</h1>`)
        //如果是JSON字符串,会自动转换成JSON对象
    },
    //失败触发
    error: (err) => {
        console.log(err)
    }
})
```

原生==>  [12-原生AJAX](../JavaScript/12-原生AJAX)