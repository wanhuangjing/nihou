#### 定义表格
* tr:定义表格的行
* td:定义表格的列
* th:定义表格的表头内容

#### table属性
* width：表格宽度
* height：表格高度
* border：表格边框宽度，以px为单位的数值，px可以省略
* cellspacing：单元格外边距 单元格间的间距
* cellpadding：单元格内边距 单元格的内容与其边框的距离
* align：表格的对齐方式，通常是left,center,right**不赞成使用。请使用样式代替**
* bgcolor：表格的背景颜色 **不赞成使用，用`background-color`代替**

#### tr属性
* align：该行的内容水平对齐方式
* valign：该行的内容垂直对齐方式，取值：top，middle，bottom
* bgcolor：该行的背景颜色 **不赞成使用，用`background-color`代替**
#### td属性
* colspan：设置单元格跨列
* rowspan：设置单元格跨行
#### 表格特有样式属性
* border-collapse:
    * separate:默认值，分离边框模式
    * collapse：边框合并
* border-spacing：边框边距
    * 1个值：表示水平距离和垂直距离相等
    * 2个值：第一个值表示水平距离，第二个值代表垂直距离，两个值中间用空格隔开
    * border-collapse必须是separate时才生效
* table-layout：
    * auto：默认值，自动，列宽由内容决定
    * fixed：固定表格布局，列宽由设定的值决定
    * 自动表格布局：







