### fs模块(file system)

fs模块是官方提供的用于操作文件的模块

1. `readFile(path,[utf8],(eror,result)=>{})` -> 读取文件

   参数 :

   1. 文件路径
   2. 字符编码[可选]
   3. 回调函数,拿到读取结果
      - error -> 读取失败
      - result -> 读取结果

2. `writeFile(path,content,[utf8],(error)=>{})` -> 写入内容

   参数 :

   1. 文件路径+文件名称
   2. 写入内容
   3. 字符编码[可选]
   4. 回调函数 -> err 写入失败

   > 文件写入时,
   >
   > 1. 没有对应文件,node会创建并写入内容
   >
   > 2. 路径错误,回调函数会报错
   >
   > Node中,相对路径,是以node命令执行时,所处目录,为参照
   >
   > `__dirname`代表当前文件的绝对路径

### Path模块

path文件中,保存了路径片段

1. `join(...path)`,拼接地址
2. `basename(path,[文件拓展名])`,获取文件名
3. `extname(path)`获取文件拓展名