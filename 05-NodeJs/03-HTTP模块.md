### HTTP模块

```js
//引入模块
const http = require('http') 
//创建服务器实例
const server = http.creatServer()
// 监听request事件,即可监听客户端发送来的请求
server.on('request',(req,res)={
    //req请求对象,包含跟请求有关的信息
    req.url 请求路径
    //res代表响应体,包含响应有关的信息
    res.end(响应体)//返回的响应体
})
//监听端口
server.listen(端口号,()=>{

})
```

1. `const server = http.creatServer()`

   使用http模块,需要引入后,创建服务器实例

2. `server.on('request',(req,res)=>{})`

   参数 :

   1. req 请求对象,携带请求有关的信息
      - req.url 请求路径
      - req.method 请求方式
   2. res 响应对象,携带服务器响应信息
      - res.end(str) 返回信息

   > 出现中文乱码问题,可以通过设置响应头来解决

# Express框架

1. `app = Express();`

2. `Express`中同样使用`listen()`来监听端口

3. 使用`get('路径',function(req,res){})`/`post()`...来监听不同的请求方式

   回调函数参数 :

   req,请求对象

   - req.query 请求体携带参数对象
   - req.params 动态请求参数

express.static(路径),静态资源服务器

app.use(express.static(路径))