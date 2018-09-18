### flex布局

网页布局（layout）是 CSS 的一个重点应用。

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071001.gif)

传统的布局解决方案，基于盒子模型，依赖display属性+position属性+float属性。他对于那些特殊的布局就非常不方便，比如**垂直居中**就不容易实现。

![ccs flex](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071002.png)

- 2009年，w3c提出一种新的解决方案----flex布局，可以简便，完整、响应式的实现各种页面布局。目前，它已经得到所有浏览器的支持，这意味着，现在就很安全的使用这项功能

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071003.jpg)


## 一、flex布局是什么

	Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。
	
任何一个容器都可以指定flex布局

		.box {
			display: flex;
		}
		
行内元素也可以使用flex布局

		.box {
			display: inline-flex
		}
		
Webkit 内核的浏览器，必须加上-webkit前缀。

		.box{
		  display: -webkit-flex; /* Safari */
		  display: flex;
		}
		
**注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。**

## 二、基本概念

采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

## 三、容器的属性

- flex-direction

- flex-wrap

- flex-flow

- justfy-content

- align-items

- align-content

#### flex-direction

flex-direction属性决定主轴的方向（即是项目的排列方向）

		.box {
			display: flex;
			flex-direction: row | row-reverse | column | column-reverse;
		}
		
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071005.png)

flex-direction有四个值：
	
	- row（默认值）: 主轴为水平方向，起点在左端
	- row-reverse： 主轴为水平方向，起点在右端
	- column: 主轴为垂直方向，起点在上沿
	- column-reverse：主轴为垂直方向，起点在下沿。
	
#### flex-wrap

默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071006.png)

		.box {
			flex-wrap: nowrap | wrap | wrap-reverse
		}

它可能取3个值。

- （1）nowrap(默认)： 不换行
	
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071007.png)
		
- （2）wrap: 换行，第一行在上方

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071008.jpg)

- （3）wrap-reverse: 换行，第一行在下方

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071009.jpg)

#### flex-flow
	
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

		.box {
		  flex-flow: <flex-direction> || <flex-wrap>;
		}
		
#### justify-content属性

justify-content属性定义了项目在主轴上的对齐方式

		.box {
			justify-content: flex-start | flex-end | center | space-between | space-around;
		}
		
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png)

它可能取5个值，具体对齐方式与轴相关。下面假设主轴为从左到右。

	- flex-start（默认值）： 左对齐
	- flex-end: 右对齐
	- center: 居中
	- space-between: 两端对齐，项目之间的间隔相等
	- space-around: 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍

#### align-items属性

该属性定义项目在交叉轴上如何对齐

		.box {
			align-items: flex-start | flex-end | center | baseline | stretch;
		}

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png)

它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。

	- flex-start：交叉轴的起点对齐。
	- flex-end：交叉轴的终点对齐。
	- center：交叉轴的中点对齐。
	- baseline: 项目的第一行文字的基线对齐。
	- stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

#### align-content属性

align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。


		.box {
		  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
		}
		
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071012.png)

该属性可能取6个值。

		flex-start：与交叉轴的起点对齐。
		flex-end：与交叉轴的终点对齐。
		center：与交叉轴的中点对齐。
		space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
		space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
		stretch（默认值）：轴线占满整个交叉轴。
		
## 四、项目的属性

以下6个属性设置在项目上。

		order
		flex-grow
		flex-shrink
		flex-basis
		flex
		align-self

#### order属性

定义项目的排列顺序。数值越小，排列越靠前，默认为0。

		.item {
			order: <integer>
		}
		
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071013.png)

#### flex-grow属性

flex-grow属性定义项目的放大比例，默认为0，即使如果存在剩余空间，也不放大。

		.item {
			flex-grow: <number>
		}
		
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071014.png)

如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

#### flex-shrink属性

flex-shrink属性定义了项目的缩小比例，默认为1，即使空间不足
，该项目将缩小

		.item {
			flex-shrink: <number>
		}

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071015.jpg)

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
