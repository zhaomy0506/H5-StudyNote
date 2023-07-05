## BOM对象

BOM对象是(Browser)浏览器对象模型

BOM为我们提供了一组对象,通过该对象可以完成对浏览器的各种操作

`window`：浏览器窗口（全局对象）

`navigator`：浏览器对象（识别浏览器）位置、设备、剪贴板...

`location`：地址栏信息

`history`：历史记录（控制浏览器前进后退）

`screen`：屏幕信息

> BOM对象都是作为window对象的属性保存的，可以直接访问

## navigator

userAgent（用户代理） 返回一个用来描述浏览器的字符串

## location

保存了当前网页地址信息的对象 ==> 表示的地址栏(url)

网址:统一资源定位符

.search 返回url查询字符串,`?`开头

.hash url `#` 后的内容

方法:

`location.assign("地址")`调换对应网址

`location.replace = "地址"` 无历史记录(无法回退)

`location.reload()`刷新页面，参数true、false，是否强制清空缓存刷新

`location.href`  获取当前地址

`location = "地址"` 跳转网址

## history对象

`history.back()`回退

`history.forward()`前进

`history.go()`去往哪一页，0刷新

`.length` 历史记录的数量

## window.open()方法

window.open(网址,strWindowName,[StrWindowFeatures])

打开一个小窗口弹窗(某些网站登录效果)

参数:

1. 打开新标签页,加载网页
2. 名字
   - `_self` /`_blank`
   - 任意字符串==>新标签页打开
3. 参数三,需要配合参数二进行使用,并且为新标签页打开
   - 可设置新窗口的宽高,位置

返回值为新标签页的窗口对象

此对象中的opener为原始窗口对象

如果新标签页不同源,只能使用该对象的close()方法

控制台再打印引用值是,弱国点击箭头展开时,看到的是对象的最新情况,(并不是当时的情况)

# web存储

`localStorage`

​	除非用户人为清楚,否则存储数据被长期保存

​	同源使用的是同一个localStorage对象

`.setItem('键名','键值')`存储数据

`.getItem('键名')`获取对应数据

`.removeItem('键名')`删除对用数据

sessionStorage

​	每一个网页都有一个独立的sessionStorage

相同点:都能存储数据

不同点:生命周期不同


