1.盒子模型

布局页面的三大核心:盒子模型,浮动和定位

**1.1看透网页布局的本质**

1.先准备好相关的网页元素,网页元素基本都是盒子

2.利用CSS设置好盒子样式，然后摆到对应位置

3.往盒子里面装内容

网页布局的核心本质:利用CSS摆盒子

**1.2盒子(Box Model)模型组成**

盒子模型:就是把HTML页面中的布局元素看作是一个矩形的盒子,也就是一个盛装内容的容器

CSS盒子模型本质上是一个盒子,封装周围的HTML元素,它包括:边框,外边距,内边距和实际内容

   border(边框)           content(内容)          padding(内边距)         margin(外边距)  

**1.3边框(border)**

border:边框粗细,边框样式,边框颜色

语法:

border:border-width || border-style || border-color

属性                        作用

border-width        定义边框粗细,单位是px

border-style          边框的样式   solid实线边框    dashed虚线边框     dotted(点线边框)

border-color          边框颜色

边框简写:

border:1px solid red;(没有顺序)

边框分开写法:

border-top(bottom  left   right):2px solid red;

**1.4表格的细线边框**

border-collapse属性控制浏览器绘制表格边框的方式。它控制相邻单元格的边框

语法:

border-collapse:collapse;

#collapse是合并的意思,border-collapse:collapse;表示相邻边框合并在一起

**1.5边框会影响盒子的实际大小**

边框会增加盒子的实际大小,一般有两种解决方案

(1)测量盒子大小的时候,不量边框

(2)如果测量的时候包含了边框,则需要width/height减去边框宽度

**1.6内边距(padding)**

padding属性用于设置内边距,即边框与内容之间的距离

属性                                   作用

padding-top                    左内边距

padding-bottom             右内边距

padding-left                     上内边距

padding-right                   下内边距

**padding属性(简写属性)可以有一到四个值

值的个数                                                                表达意思

padding:5px                                                    1个值,代表上下左右倒是5像素内边距

padding:5px  10px;                                         2个值,代表上下内边距是5像素,左右内边距是10像素  

padding:5px 10px 20px                                  3个值,代表上边距5像素, 左右内边距10像素,下内边距20像素

padding:5px 10px 20px 30px                         4个值,代表上是5像素,右是10像素,下20像素,左30像素

当我们给盒子指定padding之后,发生了两件事:

(1)内容和边框有了距离,添加了内边距

(2)padding影响了盒子实际大小

解决方案:

让width/height减去多出来的内边距即可

###特殊情况:

如果盒子本身没有指定width/height属性,则此时padding不会撑开盒子大小

**1.7外边距(margin)**

属性                                 作用

margin-left                     左外边距1

margin-right                   右外边距

margin-top                     上外边距

margin-bottom              内外边距

简写与padding完全相同

##外边距典型应用

外边距可以让盒子水平居中，但必须满足两个条件:

(1)盒子必须指定了宽度(width)

(2)盒子左右的外边距都设置为auto

.header(width:960;margin:0 auto;)

常见的写法,以下三种都可以:

(1)margin-left:auto;  margin-right:auto;

(2)margin:auto;

(3)margin:0 auto;(最常用)

注意:以上方法是让块级元素水平居中,行内元素或者行内块元素水平居中给其父元素添加text-align:center;即可

**1.8外边距合并**

(1)当上下两个相邻的块元素相遇时,他们的垂直距离不是上元素的下边距与下元素的上边距之和，而是取两值中的较大者,这种现象被称为相邻块元素垂直外边距的合并

解决方案:尽量只给一个盒子添加margin属性

(2)嵌套块元素垂直外边距的塌陷

对于两个嵌套关系的块元素,父元素有上边距同时子元素也有上边距,此时父元素会塌陷较大的外边距值

解决方式:

1.可以为父元素定义上边框                border: 1px solid transparent(透明的);

2.可以为父元素定义上内边距            padding:1px;

3.可以为父元素添加overflow:hidden

**1.9清除内外边距**

*{

padding:0;             清除内边距

margin:0;               清楚外边距

}

注意:行内元素为了照顾兼容性,尽量值设置左右内外边距,不要设置上下内外边距，但是转换为块级和行内块元素就可以了。

注意:去掉li前面的项目符号(小圆点)

list-style:none;