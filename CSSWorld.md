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
## [三、表格元素](#3)
### [3.1 表格元素](#3.1)
### [3.2 制作不规则表格](#3.2)
## [四、盒尺寸的四大家族](#4)
### [4.1 替换元素及其特性](#4.1)
### [4.2 content的特性](#4.2)
### [4.3 input元素和fieldset元素和button元素](#4.3)
### [4.4 定制input元素](#4.4)
### [4.5 其他表单元素及输入验证](#4.5)
## [五、嵌入内容](#5)
### [5.1 嵌入图像](#5.1)
### [5.2 嵌入另一张HTML文档](#5.2)
### [5.3 通过插件嵌入内容](#5.3)
### [5.4 嵌入数字表现形式](#5.4)
## [六、理解DOM](#6)
### [6.1 理解DOM](#6.1)
### [6.2 使用audio元素](#6.2)
## [六、使用多媒体](#6)
### [6.1 使用video元素](#6.1)
### [6.2 使用audio元素](#6.2)
## [七、使用canvas元素](#7)
### [7.1 理解DOM](#7.1)
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
		
	
























