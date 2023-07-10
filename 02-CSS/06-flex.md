# flex布局

## 主轴对齐方式

### 主轴方向

属性名:`flex-direction`

1. `row` ==> 主轴方向水平从左到右
2. `row-reverse` ==> 主轴方向水平从左到右
3. `column` ==> 主轴方向垂直从上往下
4. `column-reverse` ==> 主轴方向垂直从下往上

### 主轴换行方式

属性名:`flex-wrap`

常用值:

 	1. `nowrap`:默认值,不换行
 	2. `wrap`:自动换行
 	3. `wrap-reverse`:反向换行

### 主轴对齐方式

属性名:`justify-content`

常用值如下:

1. `flex-start`:主轴起点对齐(默认)

2. `flex-end`:主轴终点对齐

3. `center`:居中对齐

4. `space-between`:均匀分布,两端对齐

5. `space-around` :均匀分布,两端距离是中间距离的一半

6. `space-evenly`:均匀分布,两端距离与中间距离一致

## 侧轴对齐方式

### 一行情况

所需属性:`align-items`

常用值:

1. `flex-start` ：侧轴的起点对齐。 
2. `flex-end` ：侧轴的终点对齐。 
3. `center` ：侧轴的中点对齐。 
4. `baseline` : 伸缩项目的第一行文字的基线对齐。
5. `stretch` ：如果伸缩项目未设置高度，将占满整个容器的高度。—— （默认值)

### 多行情况

所需属性： `align-content` 

常用值： 

1. `flex-start` ：与侧轴的起点对齐。 

2. `flex-end` ：与侧轴的终点对齐。

3. `center` ：与侧轴的中点对齐。 

4. `space-between` ：与侧轴两端对齐，中间平均分布。

5. `space-around` ：伸缩项目间的距离相等，比距边缘大一倍。

6. `space-evenly` : 在侧轴上完全平分。

7. `stretch` ：占满整个侧轴。—— (默认)