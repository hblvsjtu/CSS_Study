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
## [二、构建HTML元素](#2)
### [2.1 元数据——文档结构元素](#2.1)
### [2.2 短语元素——标记文字](#2.2) 
### [2.3 流元素——组织内容](#2.3)
### [2.4 流元素——文档分节](#2.4)
## [三、表格元素](#3)
### [3.1 表格元素](#3.1)
### [3.2 制作不规则表格](#3.2)
## [四、表单元素](#4)
### [4.1 表格元素](#4.1)
### [4.2 配置表单](#4.2)
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


  
  
  
  
