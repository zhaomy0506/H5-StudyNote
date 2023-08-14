# flex布局

主轴:伸缩项目沿着主轴排列,主轴默认水平,从左到右

侧轴: 与主轴垂直,默认从上到下

## 容器属性

### 主轴相关

| 属性              | 值及作用                                                     |
| ----------------- | ------------------------------------------------------------ |
| `flex-direction`  | 控制主轴换行方式<br />`row`:从左到右(默认)<br />`row-reverse`:从右到左<br />`column`:垂直从上到下<br />`column`:垂直从下到上 |
| `flex-wrap`       | `nowrap`:不换行(默认)<br />`wrap`:换行<br />`wrap-reverse`:反向换行 |
| `flex-flow`       | 前两个的复合属性(不建议使用)                                 |
| `justify-content` | 主轴对齐方式<br />`flex-start`:延主轴对齐<br />`flex-end`:延主轴末尾对齐<br />`center`:居中<br />`space-between`:两端对齐,中间均匀分布<br />`space-around`:每个项目两侧的间隔相等<br />`space-evenly`:项目均匀分布 |

### 侧轴相关

| 属性                  | 值及属性                                                     |
| --------------------- | ------------------------------------------------------------ |
| `align-items`(单行)   | 单行侧轴对齐方式<br />`flex-start`:侧轴起始位置对齐<br />`flex-end`:结束位置对齐<br />`center`:中间位置对齐<br />`baseline`:基线对齐<br />`stretch`:拉伸(当没有设置高度时,充满容器,默认) |
| `align-content`(多行) | 多行侧轴对齐方式<br />`flex-start`:起始位置对齐<br />`flex-end`:结束位置对齐<br />`center`:中间位置对齐<br />`space-between`:两端对齐,中间均匀分布<br />`space-around`:每个项目两侧的间隔相等<br />`space-evenly`:项目均匀分布<br />`stretch`:拉伸(默认) |

## 项目属性

| 属性                 | 值及作用                                                     |
| -------------------- | ------------------------------------------------------------ |
| `flex-basic`         | 设置伸缩项目在主轴上的基准长度<br />值：非负数，通常为正整数,默认`auto` |
| `flex-grow`          | 定义项目放大比例,有多余的空间,项目按比例增长<br />值:正整数  |
| `flex-shrink`        | 定义项目缩小比例,当空间不足时，项目按比例缩小<br />值:正整数<br />计算:(元素宽*收缩比)/容器宽 |
| `flex`               | 是 `flex-grow`、`flex-shrink` 和 `flex-basis` 的缩写         |
| `order`              | 项目排序,越小排在前面                                        |
| `align-self`(不常用) | 单独对齐,覆盖容器的`align-items`                             |
