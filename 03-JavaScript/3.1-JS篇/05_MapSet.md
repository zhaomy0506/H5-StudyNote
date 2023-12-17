# Map和Set(映射与集合)

## 1).Map

Map(映射),类似于对象的一种数据结构,

与对象不同之处,可以使用任意数据类型作为key值

### WeakMap(弱映射)

WeakMap是Map的一种变种,与Map不同的是,它只能使用引用值作为Key值

## 2).Set

Set(集合),类似于数组的一种数据结构,

与数组不同之处,在于其内部不能储存相同的数据

### WeakSet(弱集合)

WeakSet是Set的一种变体

与Set不同之处在于,他也只能存储引用值

Map与Set方法：

1. has() 判断是否拥有某个属性
2. set() 设置添加某个属性
3. get() 获取指定key的value值
4. entries() 遍历 结果为数组 [key,value]的数组

# xxx.keys,values,entries方法..

它们支持：

- `Map`
- `Set`
- `Array`

普通对象也支持类似的方法，但是语法上有一些不同。

## Object.keys，values，entries

对于普通对象，下列这些方法是可用的：

- Object.keys(obj)—— 返回一个包含该对象所有的键的数组。
- Object.values(obj) —— 返回一个包含该对象所有的值的数组。
- Object.entries(obj —— 返回一个包含该对象所有 [key, value] 键值对的数组。
