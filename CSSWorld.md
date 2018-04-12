# CSSWorld  
  
  
### 作者：冰红茶  
### 参考书籍：《CSS世界》
------  

  刚买了一本书《CSS世界》，作者张鑫旭，据说技术很厉害，从个人网站上也是一个蛮有趣的一个人。想从他那里学点实际一点的操作，谢谢代码，练练手^_ ^
  
## 目录

## [一、块级元素](#1)
### [1.1 清除浮动](#1.1)
### [1.2 为什么list-item会出现项目符号](#1.2) 
### [1.3 width/height作用的具体细节](#1.3)
### [1.4 height: auto](#1.4) 
### [1.5 超越!importance，超越最大](#1.5)
### [1.6 内联盒模型](#1.6)
## [二、盒尺寸的四大家族](#2)
### [2.1 替换元素及其特性](#2.1)
### [2.2 替换元素与非替换元素的区别](#2.2) 
### [2.3 content的特性](#2.3)
### [2.4 一些技术](#2.4)
### [2.5 温和的padding](#2.5)
### [2.6 激进的margin](#2.6)
### [2.7 功勋卓越的border](#2.7)
## [三、内联元素与流](#3)
### [3.1 从字母x说起](#3.1)
### [3.2 基线与text-top和text-bottom](#3.2)
### [3.3 line-height](#3.3)
### [3.4 vertical-align](#3.4)
### [3.5 幽灵空白节点](#3.5)
## [四、流的破坏与保护](#4)
### [4.1 魔鬼属性float](#4.1)
### [4.2 float的天然克星clear](#4.2)
### [4.3 CSS世界的结界——BFC](#4.3)
### [4.4 最佳结界——overflow](#4.4)
### [4.5 absolute](#4.5)
### [4.6 relative和fix](#4.6)
------    
    
    
<h2 id='1'> 一、块级元素 </h2>
<h3 id='1.1'> 1.1 清除浮动</h3>     

#### 1) 问题的引出
> - *清除浮动* 到底是什么，以及为什么要清除浮动呢？
> - 如果在一个div盒子里面放一个正常流子元素的话，父元素的高度会自动跟子元素匹配。但是，当子元素变成一个浮动元素而脱离文档流的时候，父元素由于之前没有给他设置高度，此时他的高度就会“崩塌”，子元素露出包含块之外。为了避免这种尴尬的情况，需要想办法维持父元素的高度。
#### 2) 法一：设置高度height
> - 你没有高度是吧，那么最简单的做法就是预先给你设置一个高度喽。
> - 但是这里又会有一个问题，高度是动态变化的，而不是固定的，所以这种做法实际操作起来并不好用；
#### 3) [法二：overflow:hidden](https://zhidao.baidu.com/question/490358034.html?qbl=relate_question_2&word=overflow%BB%E1%BC%EC%B2%E9%CB%F9%D3%D0%D4%AA%CB%D8%B5%C4%B8%DF%B6%C8)
> - 对于overflow:hidden的功能就是说超出部分不显示，达到一个效果“让子元素只在父元素内显示” （1、是剪掉外面的 2、撑开显示）对应下面两种情况。
> - 1、父元素有宽度高度值（是剪掉外面的 ）：这样会剪切掉父元素外的子元素，达到“让子元素只在父元素内显示”的效果。（这才是overflow:hidden的正确用法）
> - 2、父元素无宽度高度值（撑开显示），这样就没有固定边界让它无法识别那是为那是内，但是还是要达到“让子元素只在父元素内显示”的效果，这样寻找边界以达到这种效果，我们不难发现在最大显示子元素（也就是子元素的边上时）刚好能达到“让子元素只在父元素内显示”的效果。即使有了 ”float：left；“ 浮动分离了父子元素，分离是分离但是还是父子啊（就像断绝父子关系，但是血浓于水，生理上有遗传），只要是父子也能满足这句话达到“让子元素只在父元素内显示”的效果。（这个是技巧）
> - hight因为固定了高度撑不开 用min-hight就没问题了，而且ie6中无法识别min-hight，且把hight当成min-hight所以说ie6的高度只能设定最小高度，所以ie6不用overflow：hidden就能撑开。
#### 4) [法三：浮动的父容器](https://blog.csdn.net/nnnaix/article/details/54849680)
> - 另一种思路是，索性将父容器也改成浮动定位，这样它就可以带着子元素一起浮动了。    
    
    <div style="float:left;">   
      <div style="float:left;width:45%;">   
      </div>    
      <div style="float:right;width:45%;">    
      </div>    
    </div>    
    
> - 这种方法不用修改HTML代码，但是缺点在于父容器变成浮动以后，会影响到后面元素的定位，而且有时候，父容器是定位死的，无法变成浮动。
#### 4) [法三：添加新元素，使用clear:both](https://jingyan.baidu.com/article/a24b33cd2eb0e519fe002bbe.html)
> - [原理是父容器现在必须考虑非浮动子元素的位置，而后者肯定出现在浮动元素下方，所以显示出来，父容器就把所有子元素都包括进去了。这种方法比较简单，但是要在页面中增加冗余标签，违背了语义网的原则](https://blog.csdn.net/nnnaix/article/details/54849680)。这种方式优点就是代码少，容易理解，浏览器几乎都支持，出现的问题比较少，但缺点就是如果页面浮动浮动布局多的话，就要添加很多空div去清除浮动，不便优化。虽然这是常用的清除浮动方式，但不建议使用
>>>>>> ![图1-1 法三：添加新元素，使用clear:both](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE1-1%20clear_both.png?raw=true)   

#### 5) [法三：使用伪类:after添加新元素](https://blog.csdn.net/nnnaix/article/details/54849680)	 
> - "clearfix"是父容器的class名称，"content:"020";"是在父容器的结尾处放一个空白字符，"height: 0;"是让这个这个空白字符不显示出来，"display: block; clear: both;"是确保这个空白字符是非浮动的独立区块。
> - 但是，:after选择符IE 6不支持，也就是说上面的这段代码在IE 6中无效，这怎么办？
> - 我们添加一条IE 6的独有命令"zoom:1;"就行了，这条命令的作用是激活父元素的"hasLayout"属性，让父元素拥有自己的布局。IE 6会读取这条命令，其他浏览器则会直接忽略它。     
    
    .clearfix:after {
      content: "\0020";   
      display: block;   
      //其实这里也可以使用table，但是不能使用list-item，原因在于IE不支持在伪元素中生成项目符号的盒子；
      height: 0;    
      clear: both;
    }   
    
    .clearfix {   
      zoom: 1;    
     }    
     
> - 附录 什么是hasLayout
> - IE使用Layout概念来控制元素的尺寸和位置。如果一个元素有Layout，它就有自身的尺寸和位置；如果没有，它的尺寸和位置由最近的拥有布局的祖先元素控制。
在默认情况下，拥有Layout的元素包括：\<html\>, \<body\>，\<table\>, \<tr\>, \<th\>, \<td\>，\<img\>，\<hr\>，\<input\>, \<button\>, \<select\>, \<textarea\>,\<fieldset\>, \<legend\>，\<iframe\>, \<embed\>, \<object\>, \<applet\>，\<marquee\>（注意，\<p\>和\<div\>默认不拥有Layout。）凡是具有以下CSS属性的元素，也会拥有布局：   
>> - position: absolute
>> - float: left|right
>> - display: inline-block
>> - width: any value other than 'auto'
>> - height: any value other than 'auto'
>> - zoom: any value other than 'normal' （IE专用属性）
>> - writing-mode: tb-rl（IE专用属性）
>> - overflow: hidden|scroll|auto（只对IE 7及以上版本有效）
>> - overflow-x|-y: hidden|scroll|auto（只对IE 7及以上版本有效）
> - hasLayout是IE特有的属性，不是CSS属性。可以用JavaScript函数hasLayout查看一个元素是否拥有Layout。如果有，这个函数就返回true；否则返回false。hasLayout是一个只读属性，所以无法使用Javascript进行设置。
  
<h3 id='1.2'> 1.2 为什么list-item会出现项目符号</h3>     

#### 1) 解答
> - 首先li和ul都是可以生成项目符号的，但是实际上项目符号和内容是属于两个的盒子，项目符号的盒子学名叫“标记盒子（marker box）”，专门用来放圆点等符号；
> - IE不支持在伪元素中生成项目符号的盒子；
> - 其实display定义的盒子是分为两层的，height和width作用在内在盒子上，内在盒子就是“flow”，也就是本书的核心——流：
>> - block 外边是“块级盒子”，内边是“块级容器盒子”；
>> - inline 外边是“内联盒子”，内边是“内联容器盒子”；
>> - inline-block 外边是“内联盒子”，内边是“块级盒子”，所以可以在行内跟非替换元素一起放置，也可以定义高度和宽度；
>> - inline-table 外边是“内联盒子”，内边是“表盒子”，如：   
    
    .inline-table {
      display: inline-table;
      width: 128px;
      margin-left: 10px;
      border: 1px solid #cad5eb;
    }
    .inline-table > p {
        display: table-cell;
    }   
    
    HTML：
    和文字平起平坐的表格：<div class="inline-table">
        <p>第1列</p>
        <p>第2列</p>
    </div>
    
>>>>>> ![图1-2 inline-table](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE1-2%20inline-table.png?raw=true)		


<h3 id='1.3'> 1.3 width/height作用的具体细节</h3>     

#### 1) width：auto
> - 100%父元素宽度：\<div\>和\<p\>，这里block使用的是外部尺寸；
> - 收缩与包裹shrink-to-fit 浮动，绝对定位，fixed，inline-block元素和table元素，CSS3的fit-content指的就是这种宽度表现，这里使用的是内部尺寸；
> - 收缩到最小min-content 最容易出现在table-layout为auto的表格中，俗称“一柱擎天”
> - 超出内容限制max-content 子元素既保持inline-block元素的收缩特性，有同时使得内容宽度最大
>>>>>> ![图1-3 一柱擎天](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE1-3%20%E4%B8%80%E6%9F%B1%E6%93%8E%E5%A4%A9.png?raw=true)

#### 2) 外部尺寸与流体特性
> - "鑫三无"准则：无宽度，无图片，无浮动
> - 这条准则是“流存在”的条件，所谓“流”，是一种margin/border/padding/content内容区域可以自动分配水平空间的机制。这就是利用浏览器原生流特性的好处。如果设置了宽度，那么这种特性就会被打破；
#### 3) 内部尺寸与流体特性
> - 内部尺寸指的是元素的尺寸由内部元素决定的，而非由外部的容器决定的，一般替换元素都是内部尺寸的，因为他的大小是由内部内容决定的，如\<img\>,\<textarea\>
> - 那怎么快速判断呢？假如这个元素里面没有内容，宽度就是0，那就是内部尺寸；
> - “格式化宽度”仅出现在绝对定位模型中，宽度表现为“包裹性”，宽度由内部尺寸决定；
> - 宽度的包裹性利用的就是内部尺寸原理；
> - 实际按钮元素中，如果内部的文字过多的话，它是会自动换行的，但是input元素的button类型不行，因为它默认white-space: pre是不会换行的，需要置为normal才可以；
> - 如何实现文字少的时候居中显示，文字多的时候居左显示呢？亲测可以，原理应该是content的块在内容没有满一行的时候，宽度比包含块的宽度要小，而此时由于子元素的宽度是由内部尺寸决定的，所以刚好等于内部文字的尺寸，而子元素又是居中显示的，所以文字看上去是居中显示的。而当文字满一行的时候需要换行了，子元素里面的文字终于可以“暴露”left的特性，而此时子元素的宽度等于包含块的宽度，所以文字整体效果像是居左显示，这一招实在是妙。但是如果你把里面子元素的宽度设定死了，那就没办法显示出流的优越性，也就没有了以上的效果；		
		
		.box{		
			text-align:center;		
		}		
		
		.content{		
			display:inline-block;		
			text-align:left;		
		}		
		
> - 最大宽度：连续内联盒子的宽度，“连续内联盒子”指的是全部都是内联级别的一个或者是一堆元素，中间没有任何的换行标签</br>或者其他内联盒子；
#### 2) width实现的细节
> - 元素的盒子分为四个，分别是content box, padding box, border box, margin box四个盒子； 
> - 一旦元素的宽度设定了，就会丢失流动性
#### 3) CSS流体布局下的宽度分离原则
> - 把宽度width和padding/margin/border分离；
> - 父元素用于定宽，子元素因为width使用的是默认值auto，所以会流水般自动填满容器；		
		
		.father{		
			width: 120px;		
		}		
		
		.son{		
			margin: 10px;		
			border: 1px dotted pink;
			padding: 20px;
		}		
		
> - 采用这种比较有“弹性”的布局有利于自适应不同尺寸的内容，而且方便修改，不会由于在总长限定的情况下修改padding/margin/border而被迫修改width，而且可以避免进行一些不必要的计算；
> - 但是采用这种做法容易造成html的成本，因为你的标签增多了；
#### 4) 更高效的做法——box-sizing
> - 更改width的作用盒子，一般默认是作用于最内层的内容盒子，但是可以修改		
		
		.box1 { box-sizing: content-box; } /* 默认值 */
		.box2 { box-sizing: padding-box; } /* Firefox 曾经支持 */
		.box3 { box-sizing: border-box; } /* 全线支持 */
		.box4 { box-sizing: margin-box; } /* 从未支持过 */		
		
> - 有人会问了，为什么不支持 margin-box，有人觉得可能会破坏他的垂直合并性，从而使规则变得复杂；但是实际上会有很多属性可以灭掉这种合并性（虽然我本人并不知道这是什么属性辣么厉害），张老师认为支持margin-box没有价值；
> - 对于有同行进行全局配置：		
		
		*{		
			box-sizing: border-box;		
		}		
		
> - 张老师认为这样的全局配置没有必要，而且违背了当初设计 *box-sizing: border-box;* 的初衷， *box-sizing: border-box;* 当初的设计应该是为了解决替代元素宽度自适应的问题：		
		
		input, textarea, img, video, object {
			box-sizing: border-box;
		}		
		

<h3 id='1.4'> 1.4 height: auto</h3>     

#### 1) height：auto
> - 背景background-image的大小不能影响父元素的高度height，可以说一点作用都没有；
> - 父元素如果设置了height：auto，即没有具体有效的值的时候，其子元素的百分比高度完全不起任何的作用；
> - 浏览器渲染的原理，先下载文档内容，加载头部样式资源，然后按照由上而下，由外而内的顺序渲染DOM内容；
> - 绝对定位元素的高度百分比计算是以父元素的padding-box的高度为基准的；而正常流元素则是以父元素的content-box的高度为基准的；
> - 要想使用height：100%的效果，有两种方案：
>> - 1，父元素设定显示高度；
>> - 2，子元素设置绝对定位布局；		


<h3 id='1.5'> 1.5 超越!importance，超越最大</h3>     

#### 1) 默认值
> - min-height和min-width的默认值不是0，而是auto；
> - max-height和max-width的默认值不是0，而是none；
#### 2) 优先级
> - min-height/min-width > max-height/max-width > !improtance > js脚本 
#### 3) 展开收起动画效果
> - 动画中的子元素的height还可以影响父元素的高度变化；
> - max-height可以适应不同的元素的高度变化；		
		
		CSS：
		.element {
		  max-height: 0;
		  overflow: hidden;
		  transition: max-height .25s;
		}
		:checked ~ .element {
		  max-height: 666px;
		}		
		
> - 但是这里需要注意的是， max-height:不能设置得太大，否则收起的时候会有延迟。最好在一个安全的最小高度；
		
<h3 id='1.6'> 1.6 内联盒模型</h3>     

#### 1) 定义
> - 内联元素特指“外在盒子”是内联的元素，比如\<img\>,\<button\>,\<input\>,下拉框等原始表单原件都是内联元素，inline，inline-block，inline-table等都是内联元素；
> - 内联盒子(inline box)  
> - 行框盒子(line box) 
> - 包含盒子(containing box) 一般是块级元素
#### 2) 幽灵空白节点
> - 结果，此<div>的高度并不是0，这着实很奇怪，内部的<span>元素的宽高明明都是0，标签之间也没有换行符之类的嫌疑，怎么<div>的高度会是18像素呢？		
		
		div {
			background-color: #cd0000;
		}
		span {
			display: inline-block;
		}		
		
		<div>		
			<span>		
			</span>		
		</div>		
		
>>>>>> ![图1-4 幽灵空白节点.png](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE1-4%20%E5%B9%BD%E7%81%B5%E7%A9%BA%E7%99%BD%E8%8A%82%E7%82%B9.png?raw=true)

> - 规范中的定义是 
>>> Each line box starts with a zero-width inline box with the element’s font and line height properties. We call that imaginary box a “strut”.			
		
------    
    
    
<h2 id='2'> 二、盒尺寸的四大家族 </h2>
<h3 id='2.1'> 2.1 替换元素及其特性</h3>     

#### 1) 什么是替换元素
> - 顾名思义，就是内容可替换的元素；
> - 还拥有一下特性：
>> - 内容的外观不受页面的CSS影响，也就是说，样式表现在CSS的作用于之外；
>> - 有自己的默认尺寸，\<video\>,\<iframe\>,\<canvas\>默认尺寸（没有加载资源之前）都是300px * 150px，而\<img\>则比较特别，各个浏览器下都不一样；
>> - 在很多CSS属性上有自己的一套表现规则，比较明显的就是vertical-align属性，由于不像文字有基线，替换元素的基线被硬生生的定义为元素下边缘  
> - 替换元素的 display值 
>>>>>> ![图2-1 各个替换属性的默认display属性值](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE2-1%20%E5%90%84%E4%B8%AA%E6%9B%BF%E6%8D%A2%E5%B1%9E%E6%80%A7%E7%9A%84%E9%BB%98%E8%AE%A4display%E5%B1%9E%E6%80%A7%E5%80%BC.png?raw=true)		
> - [inline和block和inline-block的区别：](https://zhidao.baidu.com/question/527108547.html)
>> - 内联元素是不可以控制宽和高、margin等；并且在同一行显示，不换行。
>> - 块级元素时可以控制宽和高、margin等，并且会换行。
>> - inline：使用此属性后，元素会被显示为内联元素，元素则不会换行。
>> - block：使用此属性后，元素会被现实为块级元素，元素会进行换行。
>> - inline-block：是使元素以块级元素的形式呈现在行内。意思就是说，让这个元素显示在同一行不换行，但是又可以控制高度和宽度，这相当于内敛元素的增强。
要注意的是IE6 不支持inline-block
> - 替换元素的尺寸由内至外可分为三层：固有尺寸，HTML尺寸和CSS尺寸，优先级：CSS尺寸 > HTML尺寸 > 固有尺寸
>>>>>> ![图2-2 替换元素的三层尺寸](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE2-2%20%E6%9B%BF%E6%8D%A2%E5%85%83%E7%B4%A0%E7%9A%84%E4%B8%89%E5%B1%82%E5%B0%BA%E5%AF%B8.png?raw=true)		

> - 在实际应用开发过程中，图片是需要通过滚屏加载的方式异步加载的，为了布局稳健，体验良好，往往会使用一张透明的图片用于占位，但是透明的用于占位的图片也是多余的资源啊，只要设置了scr="",哪怕里面什么都没有，很多浏览器依然会有请求，所以最直接的方法是什么都不写，就直接上来就是\<img\>。但是这里卖弄又有一个问题，就是\<img\>默认的尺寸各家的浏览器都不一样，有的默认高度还是0。所以那就麻烦了，这很影响初次加载时候的体验和布局。那应该怎么做呢？		
		
		img { 		
			display: inline-block; /*此处是为了避免Firefox设置宽高不起效的问题*/ 		
			width: 200px; 		
			height: 150px; 		
			visibility: hidden;}
		
		<img>		
		
		img[src] { 		
			visibility: visible; 		
		}		
		
		
<h3 id='2.2'> 2.2 替换元素与非替换元素的区别</h3>     

#### 1) “我们是无法改变这个替换元素内容的固有尺寸”
> - 那应该如何证明呢？首先我们需要联系替换元素内容的固有尺寸，那如何联系呢？答案是使用content属性。
> - 比如我们可以使用伪元素::before和::after		
		
		div:before {
			content: url(1.jpg);
			display: block;
			width: 200px; height: 200px;
		}		
		
> - 最终呈现的内容框跟图片固有尺寸不相等
> - 伪元素::before和::after默认放的是行内元素格式；
#### 2) 替换元素与非替换元素的区别
> - 替换元素与非替换元素之间之隔了一个src属性，比如\<img\>去掉或者不加src属性，它的表现就如同非替换元素一般；证明如下，结果是100%占自适应父元素的尺寸：
		
		img {
			display: block;
			outline: 1px solid;
		}
		
		<img>		
		
>> - Chrome 浏览器其实也有类似的表现，只是需要特定的条件触发而已，这个触发条件就是需要有不为空的alt 属性值。例如：此时，Chrome 这个<img>宽度也是100%容器。
		
		<img alt="任意值">		
		
>> - 唯一例外的是IE 浏览器中有个默认的占位替换内容，当src 属性缺失的时候，会使用这个默认的占位内容，这也是IE 浏览器下默认<img>尺寸是28×30 而不像Chrome 浏览器那样为0×0 的原因所在。在高版本的IE 浏览器下，这个占位的替换内容似乎做了透明处理，但是，在原生的IE8浏览器下，这个占位内容却全然暴露了。
> - 另外一个区别就是隔了一个content属性
>> - content属性应用与content-box，从理论层面讲，content属性决定这是替换元素还是非替换元素；
		
<h3 id='2.3'> 2.3 content的特性</h3>     

#### 1) content的特性
> - img元素可以使用content属性进行图片的替换，跟src的效果一模一样，就是有一点区别就是content属性只是视觉的效果（视觉层，其实从本质上将并没有实质性的内容，可以被：empty伪类选择器找到），如果使用右键另存为或者网络搜索得到的对象依然是src。		
		
		<div>有内容</div>
		<div>		
		</div>		
		
		div {		
			padding: 10px;		
			border: 10px solid #cd0000;		
		}		
		
		div:empty {		
			border-style: dashed;		
		}		
		div::after{		
			content: "伪元素生成内容";		
		}
		
> - 最后只有"伪元素生成内容"被红线框住了；
> - 而且还有一个缺点就是使用content属性我们无法改变图片的固有尺寸，所以我们在实际开发过程中直接使用content来加载图片，因为如果没有尺寸限制，都是尺寸为0，然后忽然图片尺寸一下子出现，所导致的问题就是页面加载的时候会晃动，影响体验。为了避免这个问题，我们只能限制容器尺寸，那么，既然限制了容器尺寸，为何不使用background-image 呢？显然更好控制啊？所以，只有不需要控制尺寸的图片才有使用优势。
		
		CSS：
		a {
		  text-decoration: underline;
		  color: #cd0000;
		}
		a[target="_blank"]:after {
		  content: url(data:image/gif;base64,R0lGODlhBQAFAIABAM0AAAAAACH5BAEAAAEALAAAAAAFAAUAAAIHRIB2eKuOCgA7);		
		  /* 所谓"data"类型的Url格式，是在RFC2397中 提出的，目的对于一些“小”的数据，可以在网页中直接嵌入，而不是从外部文件载入。例如对于img这个Tag，哪怕这个图片非常非常的小，小到只有一个 点，也是要从另外一个外部的图片文件例如gif文件中读入的，如果浏览器实现了data类型的Url格式，这个文件就可以直接从页面文件内部读入了。*/ 
		}		
		
		HTML：
		<p>下面这段话所有链接地址都是本实例。</p>
		<p>点击<a href="">这个链接</a>当前页刷新，看看有没有标记；点击<a href="" target="_blank">这个链接</a>，新标签页新打开一次本页面，看看有没有标记。</p>		
		
> - 关于data:解析的链接：[data:](http://www.jb51.net/css/41981.html);
> - 这里有人可能会反驳：content 内容无法复制也可能是伪元素的原因，而不是替换元素的原因。要回答这个问题，我们可以将其与同样是替换元素的::first-letter 对比一下。在IE 和Firefox 浏览器下，::first-letter 伪元素内容都是可以被选中的，但是::before/::after内容却无法选中。由此可见，文字无法选中多半是content 的原因，而非伪元素。
> - 在Chrome浏览器下，所有的元素都支持content 属性，而其他浏览器仅在::before/::after 伪元素中才有支持。在实际项目中，content 属性几乎都是用在::before/::after 这两个伪元素中，因此，“content 内容生成技术”有时候也称为“::before/::after 伪元素技术”。提前说明一下，因为本书目标浏览器是IE8 及以上版本浏览器，而IE8 浏览器仅支持单冒号的伪元素，所以下面内容代码示意部分全部使用单冒号。
> - content辅助元素的生成，将属性值设置为“”即可，不需要加点号“.”
> - attr属性，可以显示任意元素属性的生成，包括自定义属性data-；
> - 混合特性		
		
		a:after {
			content: "(" attr(href) ")";
		}
		q:before {
			content: open-quote url(1.jpg);
		}
		.counter:before {
			content: counters(wangxiaoer, '-') '. ';
		}		
		
		
<h3 id='2.4'> 2.4 一些技术</h3>     

#### 1) 基于伪元素的图片生成技术
> - 定义：我们可以对<img>元素使用::before 和::after 伪元素进行内容生成以及样式构建，但是这种方法支持是有限制的。首先是兼容性问题。
> - 为什么需要这种技术：使用缺省src 的<img>元素实现滚屏加载效果，但是，就有可能存在这样一个体验问题：如果我们的JavaScript 加载比较慢，我们的页面就很有可能出现一块一块白色的图片区域，纯白色的，没有任何信息，用户完全不知道这里的内容是什么。虽然alt 属性可以提供描述信息，但由于视觉效果不好，被隐藏掉了。此时，要是在图片还没加载时就把alt 信息呈现出来该多好啊。
> - 需要达到的目的：在图片还没有加载之前可以有提示信息
> - 条件
>> - （1）不能有src属性（证明观点的关键所在）；
>> - （2）不能使用content 属性生成图片（针对Chrome）；
>> - （3）需要有alt 属性并有值（针对Chrome）；
>> - （4）Firefox 下::before 伪元素的content 值会被无视，::after 无此问题，应该与Firefox 自己占用了::before 伪元素的content 属性有关。	
> - 代码：		
		
		img::after {
		/* 生成alt 信息，attr用来把元素的属性值显示出来 */
		content: attr(alt);
		/* 尺寸和定位 */
		position: absolute; bottom: 0;
		width: 100%;
		background-color: rgba(0,0,0,.5);
		transform: translateY(100%);
		/* 来点过渡动画效果 */
		transition: transform .2s;
		}
		img:hover::after {
		/* alt 信息显示 */
		transform: translateY(0);
		}		
		
#### 2) 正在加载中...动态效果
> - 代码：正在加载中...动态效果		
		
		CSS:
		dot{
			display:inline-block;
			height:1em;
			line-height:1;
			vertical-align:-0.25em;
			text-align:left;
			overflow:hidden;
			/* 如果不加的话，整个行框会被顶起来 */
			background-color:pink;
		}
		dot::before{
			display:block;		
			/* 将原来的三个点推到下面*/
			content:'...\A..\A.';		
			/* 三个点放在第一行，目的是兼容IE9，因为IE9认识：before和dot，但是不认识animation*/
			white-space: pre-wrap;
			/* 张老师说用pre也可以，这是指心情使然，无语ing~*/
			animation:dot 3s infinite step-start both;
		}
		@keyframes dot{		
			/* 初始在。。。开始 */
			33%{
				transform: translateY(-2em);		
				/* 从。开始 */
			}
			66%{
				transform: translateY(-1em);		
				/* 再到。。。 */
			}
		}		
		
		HTML:
		图片加载中<dot>....</dot>		
#### 3) 计数器代码		
> - 计数器代码：
		
		CSS:
		.reset{
			padding-left:1em;
			counter-reset:num;		
			/* 默认值为0 */
		}
		.mylist::before{
			content: counters(num, '-') '. '; 
			counter-increment: num;
			/* 第一次出现的时候就+1，0+1=1 */
		}
		.mylistnext{
			padding-left:1em;
			/* 为什么要加上这个呢？是因为经过插入下一级后返回原级的时候，如果不加，缩进就取消了，*/
		}
		.mylist:hover{
			padding:0 6em;
			border-right: 2px dashed;
			transition:border-right,padding 2s ease-in-out 0.5s ;
			-webkit-transition:border-right,padding 2s ease-in-out 0.5s ; /*Safari and Chrome*/
		}		
		
		HTML:
		<div class="reset" >
			<div class="mylist">冰红茶1</div>
			<div class="reset">
				<div class="mylist">冰红茶11</div>
				<div class="mylist">冰红茶12</div>
				<div class="mylist">冰红茶13</div>
			</div>
		</div>
		<div class="mylist mylistnext">冰红茶2</div>
		<div class="mylist mylistnext">冰红茶3</div>
		<div class="mylist mylistnext">冰红茶4</div>
		<div class="mylist mylistnext">冰红茶5</div>
		</div>		
		
		
<h3 id='2.5'> 2.5 温和的padding</h3>     

#### 1) 定义与作用
> - padding也称元素的“内部间”；
> - inline元素的padding既会影响视觉层叠，也会影响外部尺寸，如左右的em串的间距，上下行的层叠(如果给他加个背景颜色的话是可以看到的，或者给它弄个overflow: scroll,你有机会会看到滚动条;)
> - padding的百分比无论是水平方向还是垂直方向，都是依赖父元素的宽度，我估计这最初的设计是用来避免高度的死循环吧
> - 可以用来增加按钮或者链接的点击区域，因为有时候在手机等小屏幕的上，1em的高度人的手指点起来不方便，可以给他加一个大的padding，
> - 代码实例：三道杠		
		
		CSS:
		.sandaogang{
			display:inline-block;
			width: 140px;
			height:2px;
			padding:10px 0;
			background-color:black;
			border-top:2px solid;
			border-bottom:2px solid;
			background-clip:content-box;
			/*这个background-clip的意思是把背景颜色作用在哪个盒子上，一共有三个选项*/		
			/*一共有三个选项：content-box，padding-box，border-box*/
		}		
					
		
> - 代码实例：双点圆		
		
		CSS:
		我是三道杠<div class="sandaogang"></div>
			.doublecircle{
				display:inline-block;
				width:100px;
				height:100px;
				border-radius:50%;
				padding:10px;
				border:10px solid;
				background-color:black;
				background-clip:content-box;
		}		
		
		HTML：
		我是双点圆<div class="doublecircle"></div>		
		
		
<h3 id='2.6'> 2.6 激进的margin</h3>     

#### 1) margin的百分比值
> - 跟padding一样，都是以父元素的宽度为参考；
#### 2) margin的合并的三种场景
> - 块级元素，但不包括浮动和绝对定位元素，尽管浮动和绝对定位可以让元素块状化。
> - 只发生在垂直方向，需要注意的是，这种说法在不考虑writing-mode 的情况下才是正确的，严格来讲，应该是只发生在和当前文档流方向的相垂直的方向上。由于默认文档流是水平流，因此发生margin 合并的就是垂直方向。
> - 相邻兄弟margin合并
> - 父级和第一个或者最后一个子元素margin合并
>> - 父子margin合并产生的头图掉落问题：父元素没有出一点力，子元素出了全部的力，然后最终的margin 全部合到了父元素上。也就是虽然是在子元素上设置的margin-top，但实际上就等同于在父元素上设置了margin-top，。但是有一点需要注意，“等同于”并不是“就是”的意思。
>>  - 对于 margin-top 合并，可以进行如下操作（满足一个条件即可）：
>>>> - 父元素设置为块状格式化上下文元素,其实就是；
		
		CSS:
		.container {
			overflow: hidden;
		}		
		
>>>> - 父元素设置border-top 值；
>>>> - 父元素设置padding-top 值；
>>>> - 父元素和第一个子元素之间添加内联元素进行分隔。
>> - 对于margin-bottom 合并，可以进行如下操作（满足一个条件即可）：
>>>> - 父元素设置为块状格式化上下文元素；
>>>> - 父元素设置border-bottom 值；
>>>> - 父元素设置padding-bottom 值；
>>>> - 父元素和最后一个子元素之间添加内联元素进行分隔；
>>>> - 父元素设置height、min-height 或max-height。
> - 空块级元素的合并
>> - 其实就是子元素的top和bottom margin合并 
		
		CSS:
		.father { overflow: hidden; }
		.son { margin: 1em 0; }		
		
		HTML：
		<div class="father">
		<div class="son"></div>
		</div>		
		
>>>> - 设置垂直方向的border；
>>>> - 设置垂直方向的padding；
>>>> - 里面添加内联元素（直接Space 键空格是没用的）；
>>>> - 设置height 或者min-height。	
> - margin合并的三规则：“正正取大值”“正负值相加”“负负最负值”0
> - 合并性的好处：增加容错性；
#### 3) 深入理解margin auto
> - 绝对定位元素水平垂直居中
		
		CSS:
		.box{		
			position:relative;		
			width:20em; 		
			height:10em; 		
			border:dashed 2px black;		
		}		
		
		.son{		
			position:absolute; 		
			/* 绝对定位必须要有*/
			top:0; 		
			bottom:0;		
			left:0;		
			right:0;
			/*四个定位的方向必须要有，而且左右相等，上下相等*/
			width:10em;
			height:5em;			
			/*必须要有宽度和高度*/
			margin:auto;	
			/* 外边距auto必须要有*/
			background-color:pink;		
			}		
			
#### 4) margin 无效情形解析		
> - display 计算值inline 的非替换元素的垂直margin 是无效的，虽然规范提到有渲染，但浏览器表现却未寻得一点踪迹，这和padding 是有明显区别的。
> - 对于内联替换元素，垂直margin 有效，并且没有margin 合并的问题，所以图片永远不会发生margin 合并。	
> - 绝对定位元素非定位方位的margin 值“无效”。也就是说，定位方向和margin的方向必须要共存，如；
		
		CSS:
		img { 		
			top: 10%; 	
			left: 30%;		
		}		
		
		img {		
			top: 10%; 		
			left: 30%;		
			margin-right: 30px;		
		}		
		
> - 定高容器的子元素的margin-bottom 或者宽度定死的子元素的margin-right 的定位“失效”。，原因在于margin要生效必要要有依靠，按照普通正常流的定位，是从左到右，从上到下，所以左和上是他的依靠，所以定义margin-left和margin-top才有用，margin-right和margin-bottom只能影响下一个兄弟元素，或者跟父元素的margin合并并影响下一个元素。绝对定位元素也是，他默认没有任何的依靠，只有你声明了上下左右偏移之后才有依靠，浮动元素也同理，设置了浮动方向之后该方向就称为了依靠，此时margin的方向才有用。如：
		
		HTML：
		<div class="box">		
		<div class="child"></div>		
		</div>
		
		CSS:
		.box {		
			height: 100px;		
		}		
		
		.child {		
		height: 80px;		
		margin-bottom: 100px;		
		}		
		
#### 5) 多列两端对齐		
> - 示例代码		
		
		CSS:
		ul{		
			marign-right:-20px;
			/*用来消灭最后一列的右侧空白*/
			/*当然了，你可以使用nth-of-type(),但是IE8不兼容*/		
			/*IE8实在太弱*/
		}		
		
		li{		
			position:float;
			width:100px;
			height:200px;
			margin-right:20px;
		}

#### 6) 为滚动条底部留白
> - Chrome中子元素超过父元素的content box就触发滚动条显示，而IE和Firefox中子元素超过父元素的padding box才触发滚动条显示。所以不能通过修改padding-box来为滚动条底部留白；
> - 比较简单而且兼容性比较好的做法是给子元素使用margin；
> - 分栏等高布局：		
		
		CSS:
		.column-box{
			width:800px;
			margin:auto;
			overflow:hidden;
		}
		.column-left,
		.column-right {
			float:left;
			width:400px;
			text-align:center;
			padding-top:10px;
			margin-bottom: -9999px;
			padding-bottom: 9999px;
			/*为什么要这样一正一负呢？主要是用与增加背景高度*/
			/*同时使用overflow:hidden去消灭多余的高度，实现等高*/
			/*不知道你还记得overflow:hidden减掉溢出的内容的原理？*/
		}
		.column-left {
			background-color: #34538b;
		}
		.column-right {
			background-color: #cd0000;
		}		
		
		HTML：	
		<div class="column-box">
			<div class="column-left">正方<br>正方</div>
			<div class="column-right">反方</div>
		</div>		
		
		
<h3 id='2.7'> 2.7 功勋卓越的border</h3>     

#### 1) 为什么border不支持百分比
> - 等比例缩放不符合边框的语义；
> - 没有应用的场景；
#### 2) 应用实例
> - 三道杠实现的第二个方法——双横线
		
		
		<div style="width:9em; height:2em;
					border-top:double 6em;
					/*此处双横线的上线和下线和中间区域自动平分，各占2em*/
					border-bottom:solid 2em; 
					background-color:pink;">
			我是一个三道杠少年
		</div>		
				
>>>>>> ![图2-4 三道杠少年](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE2-4%20%E4%B8%89%E9%81%93%E6%9D%A0%E5%B0%91%E5%B9%B4.png?raw=true)		

> - 上传图片框：
		
		.add{
			position: relative;
			/*主要是一横和一竖需要重叠，所以设置为相对位置*/
			width:8em;
			height:8em;
			color:grey;
			/*所有的后代及其边框都会跟据这个前景色的变化而变化*/
			transition: color .25s;
			border:dotted;
		}
		.add::before, .add::after {
			content:'';
			position: absolute;
			top: 50%;
			left: 50%;
			border:solid;
		}
		.add:before{
			height:1em;
			width:0;
			margin-top:-0.5em;
			/*一竖也是有宽度的，放中间，*/
		}
		.add:after{
			width:1em;
			height:0;
			margin-left:-0.5em;
			/*一横也是有宽度的，放中间，*/
		}
		.add:hover {
			color:red;
			/*变色*/
		}		
		
>>>>>> ![图2-5 上传图片框](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE2-5%20%E4%B8%8A%E4%BC%A0%E5%9B%BE%E7%89%87%E6%A1%86.png?raw=true)			
> - 正圆 利用dotted边框画正圆；

		CSS:		
		.box{
			width:150px;		
			height:150px; 		
			overflow:hidden;
		}		
		
		.circle{
			/*overflow:hidden;是为了把多余的三个圆点消灭掉*/
			width:100%;		
			height:100%;		
			border:150px dotted #cd0000;
			/*border:150px要与宽度和高度相等*/
		}		
		
> - 圆角矩形 利用dotted边框画圆角矩形；		
				
		CSS:	
		.box{		
		position:relative;		
		/*position:relative 这是为了后面便于文字居中的需要。width/height的比例要大于0.5小于2，避免出现6个或以上圆点*/
		width:120px; 		
		height:80px; 		
		border:150px dotted #cd0000;		
		}
		
		.highRect{
			position:absolute;		
			top:-150px;		
			bottom:0;		
			left:-75px;		
			right:-75px; 		
			height:380px;
			/* top:-150px(border的宽度或者叫圆角的直径); bottom:0;*/
			/* height:380px(2倍border的宽度 + 父元素高度); 把content-box的矩形拉高*/
			background-color:#cd0000; 		
		}		
		
		.longRect{		
			position:absolute; 		
			top:-75px; 		
			bottom:-75px; 		
			left:-150px;		
			right:0px;		
			width:420px; 
			/* left:-150px(border的宽度或者叫圆角的直径);right:0px；*/
			/* width:420px(2倍border的宽度 + 父元素宽度); 把content-box的矩形拉长*/
			background-color:#cd0000;		
		}
		
		.text{
			position:absolute; 		
			top:0; bottom:0;left:0;right:0; 		
			width:10em; 		
			height:1em; 		
			margin:auto">
			/*margin:auto文字居中*/
		}		
				
>>>>>> ![图2-3 正圆与圆角矩形](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE2-3%20%E6%AD%A3%E5%9C%86%E4%B8%8E%E5%9C%86%E8%A7%92%E7%9F%A9%E5%BD%A2.png?raw=true)		
> - 背景图以右下角为参考的技巧——border transparent的属性
		
		CSS：		
		.box{		
			width:540px; 	
			height:640px; 	
			border-right:50px solid transparent;
			/*设置靠右的距离是50px*/
			background:url(123.jpg) bottom right;
			/*设置从右下角开始px*/		
			
			
> - 可以使用透明border或者增加padding来增加点击的区域
> - 可以实现可控的上等腰或者不等腰三角或者下等腰或者不等要三角绘制
		
		CSS：		
		.Triangle{		
			width:0;
			/*有宽度的时候还可以实现梯形*/
			height:40px; 		
			border:solid 10px; 		
			border-left:solid 5px;		
			border-right:solid 5px;	
			/*通过控制边界的尺寸可以控制三角形的角度*/
			border-color:red transparent transparent;		
			/*通过控制透明的边界可以控制三角形的摆放位置，边界的大小和颜色需要分开*/
		}		
		
> - 可以实现可控的四色转角连接
		
		CSS：		
		.Triangle{		
			width:0; 		
			height:40px; 		
			border:solid 30px; 		
			/*通过控制边界的尺寸可以控制三角形的角度*/
			border-color:red blue green black;		
			/*通过控制透明的边界可以控制三角形的摆放位置，边界的大小和颜色需要分开*/
		}	


> - 等高布局，利用border实现2，3，4，5列的布局
		
		CSS：
		/* 导航背景区border创建 */
		.box { 
		  border-left: 150px solid #333;
		  background-color: #f0f3f9;
		}
		/* 清除浮动影响，不能使用overflow:hidden */
		/* 因为overflow的作用域只在padding-box*/
		.box:after {
		  content: "";
		  display: block;
		  clear: both;
		}
		/* 布局主结构 */
		.box > nav {
		  width: 150px;
		  margin-left: -150px;
		  float: left;
		}
		.box > section {
		    overflow: hidden;
		}
		/* 导航列表和模块列表 */
		.nav {
		    line-height: 40px;
		    color: #fff;
		}
		.module {
		    line-height: 40px;
		}		


------    
    
    
<h2 id='3'> 三、内联元素与流 </h2>
<h3 id='3.1'> 3.1 从字母x说起</h3>     

#### 1) 基线
> - 什么是基线？字母x 的下边缘（线）就是我们的基线。
>>>>>> ![图3-1 基线的位置](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE3-1%20%E5%9F%BA%E7%BA%BF%E7%9A%84%E4%BD%8D%E7%BD%AE.png?raw=true)		
		
#### 2) 不严格的垂直对齐的替换——line-height=1em
> - 理论上x的高度是0.5em，x头顶着的就是中线，所以设置inline-block的高度为1em就可以实现垂直对齐。其实就是相当于vertical-align: middle；		
		
		.icon-arrow {
			display: inline-block;
			width: 20px;
			height: 1ex;
			background: url(arrow.png) no-repeat center;
		}	
		
		
#### 3)  多行文本的内联元素近似垂直对齐
> - 本质上是把line-height当成是盒子的高度，然后把多行文本当成是一个inline-block，然后设置vertical-align:middle;
> - inline-block的出现为盒子.content 元素带来了“行框盒子”，而每个“行框盒子”都会附带的一个产物—“幽灵空白节点”，即一个宽度为0、表现如同普通字符的看不见的“节点”。有了这个“幽灵空白节点”，line-height就有了作用的对象，从而相当于在.content元素前面撑起了一个高度为line-height的宽度为0的内联元素，以及提供了基线的基准。
		
		.box {
			line-height: 120px;
			background-color: #f0f3f9;
		}
		.content {
			display: inline-block;
			line-height: 20px;
			margin: 0 20px;
			vertical-align: middle;
		}
		<div class="box">
		<div class="content">基于行高实现的...</div>
		</div>	
		
> - 为什么说近似呢？因为真正的中间对齐的位置应该在x的交叉点再上去一点点，说明x在大部分的字体中其实是下沉的，而且这种不对齐现象在字号越大的情况下越明显
		
		
#### 4) 内容区(content area)
> - 大多数场景下，内容区域(content area) 和em-box 是不一样的，内容区域高度受font-family 和 font-size 双重影响，而em-box 仅受font-size 影响，通常内容区域高度要更高一些。除了下面这种情况，也就是“当我们的字体是宋体的时候，内容区域和em-box 是等同的”，因为宋体是一种正统的印刷字体，方方正正，所以千万不要小看宋体。

#### 5) 行间距
> - border以及line-height 等传统CSS属性并没有小数像素的概念（从CSS3 动画的细腻程度可以看出），因此，这里的3.5px 需要取整处理，如果标注的是文字上边距，则向下取整；如果是文字下边距，则向上取整，因为绝大多数的字体在内容区域中都是偏下的。

<h3 id='3.2'> 3.2 基线与text-top和text-bottom</h3>     

#### 1) 定义
> - vertical-align 属性的默认值baseline 在文本之类的内联元素那里就是字符x的下边缘
> - 对于替换元素则是替换元素的下边缘
> - 对于inline-block元素，如果里面没有内联元素，或者overflow 不是visible，则该元素的基线就是其margin底边缘；否则其基线就是元素里面最后一行内联元素的基线。

#### 2) text-top和text-bottom
> - 其实就是内联元素的上下边缘与父元素的字体的内容区域的上下边缘对齐。
>>>>>> ![图3-2 text-top和text-bottom.png](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE3-2%20text-top%E5%92%8Ctext-bottom.png?raw=true)			



<h3 id='3.3'> 3.3 line-height</h3> 

#### 1) 作用区域
> - 对于纯文本元素，line-height直接决定最终的高度。但是，如果同时有替换元素，则line-height只能决定最小高度，而由vertical-align和height决定上行边界，下行边界由下边距决定。
#### 2) line-height=0的后果
> - 行间距消失;
> - 多行合一;
> - 行框线挂在文字中间；
> -如果有background或者border的话显示区域下降0.5em。这是因为line-height=0使得行框变成一条直线并与有形元素框的上边缘重叠，此时文字的中心线与行框线与上边缘重合，使得background或者border的话显示区域相比较下下降0.5em。

#### 3) font-size=0的后果——文字从中间消失，基线上下分别就是上下半行距
> - 相对来讲，font-size=0的后果比line-height轻得多，跟据公式：
		
		对于有文字的inline-block，文字不见了		
		
		但是行间距不变，上下间距的大小取决于line-height的大小		
		
		基线在上下间距的内边界上重合，基线位于行框的中心线上，其实就相当于文字从中间消失，基线上下分别就是上下半行距		
	

<h3 id='3.4'> 3.4 vertical-align</h3>		

#### 1) 作用前提
> - 只能应用于内联元素以及display 值为table-cell 的元素。换句话说，vertical-align 属性只能作用在display 计算值为inline、inlineblock，inline-table 或table-cell 的元素上。因此，默认情况下，、\<span\>、\<strong\>、\<em\>等内联元素，\<img\>、\<button\>、\<input\>等替换元素，非HTML 规范的自定义标签元素，以及\<td\>单元格，都是支持vertical-align 属性的，其他块级元素则不支持。
#### 2) vertical-align:baseline
> - vertical-align:baseline 或者默认情况下，作用元素外面的内联元素的受作用元素内部的内联元素影响，作用元素外面的内联元素的基线与作用元素内部的内联元素的基线对齐。
#### 3) vertical-align:middle
> - vertical-align:middle作用在content内联元素上，使得content元素垂直中线（不是里面的子元素，就是该元素本身垂直中线）匿名内联元素的中线（基线往上0.5ex）同在行框的中心线上，基线由于匿名内联元素的移动而变化。如果作用元素的高度比原有行框的高度要高，则会撑大行框（即双边作用）。作用元素外面的内联元素的不受作用元素内部的内联元素影响，两者独立开来；其他内联元素inline-block则按照默认baseline的对齐方式；
#### 4) vertical-align:top bottom top,bottom,text-top和text-bottom
> - vertical-align:top bottom top,bottom,text-top和text-bottom 作用在content内联元素上，使得content元素上下边框边缘或者文本框上下边缘（不是里面的子元素，就是该元素本身上下边框边缘或者文本框上下边缘）在行框的上下边框边缘或者文本框上下边缘，但这种影响只能是单边作用，无法起到撑大行框的作用，只会撑大盒子元素的高度。作用元素外面的内联元素的不受作用元素内部的内联元素影响，也不受作用元素影响，该干嘛还是干嘛，两者独立开来。此时由于纯内联元素的上边缘或者下边缘发生移动，使得基线发生了移动，也就是或基线是跟着纯内联元素运动的，纯内联元素基线发生了运动，那么对准机制就发生了变化		
#### 5) 案例
> - 基于vertical-align 属性的水平垂直居中弹框		
> - 关于父元素和子元素都不定高的垂直问题
		
		HTML：
		<div class="container">
			<div class="dialog"></dialog>
		</div>		
		
		CSS：
		.container {		
			position: fixed;		
			top: 0; right: 0; bottom: 0; left: 0;
			background-color: rgba(0,0,0,.5);
			text-align: center;
			font-size: 0;
			/* 使得基线和中线重合*/
			/* 其实用line-height：0替代也可以，只是line-height：0会继承给子元素，那么子元素里面的文字就会被挂在上边缘，你又得去弄子元素的line-height值，然而你又不好确定line-height到底去多少比较好，这就尴尬了*/
			/* 保证伪元素的字不可见*/
			white-space: nowrap;		
			/* 使得整个父元素只有一行*/
			overflow: auto;
		}		
		
		.container:after {
			content: '';
			display: inline-block;
			height: 100%;
			/* 撑起行框，使得整个父元素只有一行*/
			vertical-align: middle;		
			/* 影响周围的纯内联元素，使其一起居中，但是基线也会跟着一起移动*/
		}		
		
		.dialog {
			display: inline-block;
			vertical-align: middle;
			text-align: left;
			font-size: 14px;
			white-space: normal;
		}		
		
		

<h3 id='3.5'> 3.5 幽灵空白节点</h3>  

> - 在HTML5 文档模式下，每一个“行框盒子”的前面都有一个宽度为0的“幽灵空白节点”，其内联特性表现和普通字符一模一样；
> - 他的基线是作为参考用的。所以vertical-align对它没有任何用处；
> - 如果要消灭他的行间距，只有使用line-height=0的方法;
> - 如果要消灭他的存在，只有使用fon-size=0的方法，但是会保留行间距；	
	

------    
    
    
<h2 id='4'> 四、流的破坏与保护 </h2>
<h3 id='4.1'> 4.1 魔鬼属性float</h3>     

#### 1) 浮动的本质
> - 呈现文字环绕的效果
#### 2) 浮动的特点
> - “鑫三无”准则：无宽度，无图片，无浮动，无浮动这是因为纯浮动的布局容差性比较差，容易出现严重的布局问题，还有很多兼容性的问题；
>> - 包裹性
>> - 块状化并格式化上下文
>> - 破坏文档流
>> - 没有任何margin的合并
> - 不要指望使用text-align属性控制浮动元素的左右对齐，因为text-align对块级元素是无效的。
#### 3) 文字环绕的作用原理
> - 行框盒子与浮动元素的不可重叠性（块状盒子却可以重叠）；
> - 父元素的高度坍塌（高度坍塌的时候对父元素以外大的元素也会有浮动的作用）；
#### 4) 更深入的作用机制
> - 浮动锚点 浮动锚点是float 元素所在的“流”中的一个点，这个点本身并不浮动，就表现而言更像一个没有margin、border 和padding 的空的内联元素；
> - 浮动参考 浮动参考指的是浮动元素对齐参考的实体；
> - 在CSS 世界中，float 元素的“浮动参考”是“行框盒子”，也就是float 元素在当前“行框盒子”内定位。再强调一遍，是“行框盒子”，不是外面的包含块盒子之类的东西。
> - 然而，上面的解释有一个很大的漏洞就是，如果float 元素前后全是块元素，那根本没有“行框盒子”，何来对齐的说法？此时，就需要上面提到的“浮动锚点”出马了。“浮动锚点”这个术语名称本身很具有欺骗性，看上去应该与float 的定位位置有关，实际上关系浅薄，在我看来，其作用就是产生“行框盒子”，因为“浮动锚点”表现如同一个空的内联元素，有内联元素自然就有“行框盒子”，于是，float 元素对齐的参考实体“行框盒子”对于块状元素也同样适用了，只不过这个“行框盒子”由于没有任何内容，所以无尺寸，看不见也摸不着罢了。		

<h3 id='4.2'> 4.2 float的天然克星clear</h3>     

#### 1) 官方解释
>> - “元素盒子的边不能和前面的浮动元素相邻。”
#### 2) 需要注意的地方
>> - 凡是clear:left 或者clear:right 起作用的地方，一定可以使用clear:both 替换！
>> - clear 属性对“后面的”浮动元素不闻不问，因此，当clear:left 有效的时候，clear:right必定无效，也就是此时clear:left 等同于设置clear:both；同样地，clear:right 如果有效也是等同于设置clear:both。由此可见，clear:left 和clear:right 这两个声明就没有任何使用的价值，至少在CSS 世界中是如此，直接使用clear:both 吧。
>> - 如下第三个item设置了clear:both，结果只有left有用，right却没有用
>>>>>> ![图4-1 列表2行显示](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE4-1%20%E5%88%97%E8%A1%A82%E8%A1%8C%E6%98%BE%E7%A4%BA.png?raw=true)		

#### 3) 不足之处
>> - clear作用的元素必须是块级元素，所以伪元素的计算值必须改为inline-block
>> - 使用清除浮动有时候也会有一些错位的发生，即使采用margin=-9999px也不济于事
>>>>>> ![图4-2 清除浮动导致的错位](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE4-2%20%E6%B8%85%E9%99%A4%E6%B5%AE%E5%8A%A8%E5%AF%BC%E8%87%B4%E7%9A%84%E9%94%99%E4%BD%8D.png?raw=true)		

		
<h3 id='4.3'> 4.3 CSS世界的结界——BFC</h3>     

#### 1) 定义
>> - BFC 全称为block formatting context，中文为“块级格式化上下文”。
#### 2) 触发条件（任一即可）
>> - <html>根元素；
>> - float 的值不为none；
>> - overflow 的值为auto、scroll 或hidden；
>> - display 的值为table-cell、table-caption 和inline-block 中的任何一个；
>> - position 的值不为relative 和static。
>>>>>> ![图4-3 BFC的作用对比](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE4-3%20BFC%E7%9A%84%E4%BD%9C%E7%94%A8%E5%AF%B9%E6%AF%94.png?raw=true)		
			
			
<h3 id='4.4'> 4.4 overflow与锚点</h3>     

#### 1) 最佳结界——overflow
>> - overflow 剪裁界线border box
#### 2) 经典的不兼容问题
>> - 在Chrome 浏览器下，如果容器可滚动（假设是垂直滚动），则padding-bottom 也算在滚动尺寸之内，IE 和Firefox 浏览器忽略padding-bottom。
#### 3) overflow-x和overflow-y
>> - 如果overflow-x 和overflow-y 属性中的一个值设置为visible 而另外一个设置为scroll、auto 或hidden，则visible 的样式表现会如同auto。也就是说，
除非overflow-x 和overflow-y 的属性值都是visible，否则visible 会当成auto 来解析。换句话说，永远不可能实现一个方向溢出剪裁或滚动，另一方向内容溢出显示的效果。
#### 4) overflow与锚点定位
>> - #号定位表示置顶，如果后面跟着的是id名称，则可以定位到相应的元素位置
>>>>>> ![图4-4 定位地址](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE4-4%20%E5%AE%9A%E4%BD%8D%E5%9C%B0%E5%9D%80.png?raw=true)	
>> - page级锚点 使用更精练的代码表示就是：
		
		<a href="#1">发展历程></a>
		<a name="1"></a>		
		
		
#### 5) 锚点定位的本质
>> - 锚点定位行为的发生，本质上是通过改变容器滚动高度或者宽度来实现的
>> - 注意，这里说的是容器的滚动高度，而不是浏览器的滚动高度，这一点小小区分非常重要。
>> - 锚点定位也可以发生在普通的容器元素上，而且定位行为的发生是由内而外的。
>> - 其次就是设置了overflow:hidden 的元素也是可滚动的，这也是本小节的核心。说得更干脆点儿就是：overflow:hidden 跟overflow:auto 和overflow：scroll 的差别就在于有没有那个滚动条。元素设置了overflow:hidden 声明，里面内容高度溢出的时候，滚动依然存在，仅仅滚动条不存在！		
			
			
<h3 id='4.5'> 4.5 absolute绝对定位</h3>     
		
#### 1) 包含块的规则
>> - （1）根元素（很多场景下可以看成是<html>）被称为“初始包含块”，其尺寸等同于浏览器可视窗口的大小。
>> - （2）对于其他元素，如果该元素的position 是relative 或者static，则“包含块”由其最近的块容器祖先盒的content box 边界形成。
>> - （3）如果元素position:fixed，则“包含块”是“初始包含块”。
>> - （4）如果元素position:absolute，则“包含块”由最近的position 不为static的祖先元素建立，具体方式如下。如果该祖先元素是纯inline 元素，则规则略复杂：
>>>> - 假设给内联元素的前后各生成一个宽度为0 的内联盒子（inline box），则这两个内联盒子的padding box 外面的包围盒就是内联元素的“包含块”；
>>>> - 如果该内联元素被跨行分割了，那么“包含块”是未定义的，也就是CSS2.1规范并没有明确定义，浏览器自行发挥。否则，“包含块”由该祖先的padding box 边界形成。
>>>> - 如果没有符合条件的祖先元素，则“包含块”是“初始包含块”。		
>>>>>> ![图4-5 Firefox 和Chrome 跨行内联](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE4-5%20Firefox%E5%92%8CChrome%E8%B7%A8%E8%A1%8C%E5%86%85%E8%81%94%E5%AF%B9%E6%AF%94.png?raw=true)			
	
#### 2) 无依赖absolute 绝对定位
>> - 一个绝对定位元素，没有任何left/top/right/bottom 属性设置，并且其祖先元素全部都是非定位元素，其位置在本来应该出现的位置上，而且因为脱离文档流，不影响后续布局；下
>> - 应用场景：各类图标定位 超越常规布局的排版（突入起来的警告提示不影响布局）拉列表的定位 placehoder的效果		
#### 3) absolute可以不被overflow剪裁
>> - 绝对定位元素不总是被父级overflow 属性剪裁，尤其当overflow 在绝对定位元素及其包含块之间的时候。或者换句话说：如果overflow 不是定位元素，同时绝对定位元素和overflow 容器之间也没有定位元素，则overflow 无法对absolute 元素进行剪裁。如：
		
		<div style="position: relative;">
		<div style="overflow: hidden;">
		<img src="1.jpg" style="position: absolute;">
		</div>
		</div>	
		
#### 3) absolute 与clip
>> - clip 属性要想起作用，元素必须是绝对定位或者固定定位，也就是position 属性值必须是
absolute 或者fixed。clip 属性语法如下：		
		
		clip: rect(top, right, bottom, left)			
		
>> - clip 隐藏仅仅是决定了哪部分是可见的，非可见部分无法响应点击事件等；然后，虽然视觉上隐藏，但是元素的尺寸依然是原本的尺寸，在IE 浏览器和Firefox 浏览器下抹掉了不可见区域尺寸对布局的影响，Chrome 浏览器却保留了	
#### 4) absolute 的流体特性	
>> - 必要条件 在特定条件下才具有，这个条件就是“对立方向同时发生定位的时候”
>> - absolute 的margin:auto 居中
		
<h3 id='4.6'> 4.6 relative和fix</h3>     

#### 1) position:relative 才是大哥
>> - 相对自身定位偏移
>> - relative 的定位还有另外两点值得一提：相对定位元素的left/top/right/bottom的百分比值是相对于包含块计算的，而不是自身。注意，虽然定位位移是相对自身，但是百分比值的计算值不是。
>> - 当相对定位元素同时应用对立方向定位值的时候，也就是top/bottom 和left/right同时使用的时候，其表现和绝对定位差异很大。绝对定位是尺寸拉伸，保持流体特性，但是相对定位却是“你死我活”的表现，也就是说，只有一个方向的定位属性会起作用。而孰强孰弱。则是与文档流的顺序有关的，默认的文档流是自上而下、从左往右，因此top/bottom 同时使用的时候，bottom 被干掉；left/right 同时使用的时候，right 毙命。
#### 2) relative 的最小化影响原则
>> - “relative 的最小化影响原则”是张老师自己总结的一套更好地布局实践的原则，主要分为以下两部分：
>>>> - （1）尽量不使用relative，如果想定位某些元素，看看能否使用“无依赖的绝对定位”；
>>>> - （2）如果场景受限，一定要使用relative，则该relative 务必最小化。
>>>>>> ![图4-6 relative的最小化影响原则](https://github.com/hblvsjtu/CSS_Study/blob/ApplicationPrimary/CSSWorldPicture/%E5%9B%BE4-6%20relative%E7%9A%84%E6%9C%80%E5%B0%8F%E5%8C%96%E5%BD%B1%E5%93%8D%E5%8E%9F%E5%88%99.png?raw=true)				

#### 3) 强悍的position:fixed 固定定位

















