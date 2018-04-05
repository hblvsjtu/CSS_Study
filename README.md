# CSS_Study  
  
  
### 作者：冰红茶  
### 参考书籍：《CSS权威指南》 版本2.1		

------  

   CSS，Cascade Style Sheet层叠样式表，负责html页面的美化工作。其实当初在学javascript权威指南第二部分的时候，就觉得应该补一下html和css权威指南方面的知识，才能更好地进行第二部分的学习^_ ^
  
## 目录

## [一、元素与选择器与导入样式表](#1)
### [1.1 元素](#1.1)
### [1.2 选择器](#1.2) 
### [1.3 选择器规则](#1.3) 
### [1.4 继承](#1.4)
### [1.5 层叠](#1.5)
### [1.6 导入样式表](#1.6)
## [二、值，颜色和单位](#2)
### [2.1 值](#2.1)
### [2.2 颜色](#2.2) 
### [2.3 单位](#2.3)
## [三、字体](#3)
### [3.1 字体属性](#3.1)
## [四、文本](#4)
### [4.1 文本属性](#4.1)
### [4.2 字间隔与字符间隔](#4.2)
### [4.3 其他文本操作](#4.3)
## [五、基本视觉格式化](#5)
### [5.1 基本框](#5.1)
### [5.2 水平格式化](#5.2)
### [5.3 垂直格式化](#5.3)
### [5.4 行布局](#5.4)
## [六、内边框、边距和边框](#6)
### [6.1 基本元素框](#6.1)
### [6.2 width和height](#6.2)
### [6.3 margin](#6.3)
### [6.4 border和padding](#6.4)
## [七、颜色和背景](#7)
### [7.1 浮动和定位](#7.1)
## [八、浮动和定位](#8)
### [8.1 浮动](#8.1)
### [8.2 定位](#8.2)
### [8.3 z轴上的位置z-index](#8.3)
### [8.4 固定定位和相对定位](#8.4)
## [九、表布局](#9)
### [9.1 表格式化](#9.1)
### [9.2 表大小](#9.2)
------  

    
<h2 id='1'> 一、元素与选择器与导入样式表 </h2>
<h3 id='1.1'>1.1 元素</h3>  

#### 1) 替换元素与非替换元素  
> - 替换元素即是那种用于填充图像，影片和音乐；
> - 非替换元素即是那种由用户代理（主要是浏览器）显示的内容，比如文字； 
#### 2) 元素显示角色  
> - 块级元素（block） 元素框独立，在元素框前后生成分隔符，大小等于1em；
> - 行内元素（inline） 元素框非独立  
>>>>>> ![图1-3 一些概念](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE1-3%20%E4%B8%80%E4%BA%9B%E6%A6%82%E5%BF%B5.png?raw=true)    


<h3 id='1.2'>1.2 选择器</h3>   

>> 选择器分为文档元素选择器，类选择器，ID选择器，属性选择器，后代选择器和伪类选择器；

#### 1) 规则结构  
> - CSS整体结构由选择器+声名块组成；
> - 有的属性可以接受多个关键字，每个关键字用空格分开；
> - 只有一种情况是例外的，用斜线分割字体大小和行高两个关键字，；  font的其他关键字都用空格分隔  
  
    h2{  
        font:large/150%;  
       sans-serif;  
    }       
    
>>>>>> ![图1-1 CSS规则结构](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE1-1%20CSS%E8%A7%84%E5%88%99%E7%BB%93%E6%9E%84.png?raw=true)   

#### 2) 分组  
> - 选择器的合并使用逗号“，”，表示A和B都是用同一个声明块；
> - 通配选择器，就用一个星号“\*”，代表所有的元素；
#### 3) 类选择器
> - 使用元素 + “.” + 类名，假如元素名为星号“\*”或者什么都不写，则对所有元素的类都适用，使用时将元素的class = “类名” 即可；
> - 多类选择器，元素名+ “.” + 类名1 + “.” + 类名2 + “.” + 类名n，然后在元素中，class = “类名1 类名2 类名n”，不同的类名用空格隔开，class中的值必须是多类选择器的子集或者它本身那才生效。
#### 4) ID选择器
> - 使用元素 + “#” + 元素ID值，假如元素名为星号“\*”或者什么都不写，则对所有元素的类都适用；
> - 实际上，浏览器通常并不检查HTML中ID的唯一性，这意味着如果你的HTML文档中设置了有多个相同的ID属性值的元素，就可能为这些元素应用相同的样式。但是这种行为是不正确的；
#### 5) 类选择器还是ID选择器？
> - 从纯语法上讲， “.” + 类名对XML文档不一定奏效，但是“#” + 元素ID值可以在任何文档语言中使用；
> - HTML对于类名和ID值是区分大小写的；
#### 6) 属性选择器
> - 使用元素 + "\[" + 属性名 + "\]"，假如元素名为星号“\*”或者什么都不写，则对所有元素的都适用;
> - 属性名可以同时使用，元素 + "\[" + 属性名1 + "\]" + "\[" + 属性名2 + "\]" + "\[" + 属性名n + "\]"，对同时具备属性名1和属性名2和属性名n的元素有效；
> - 属性名后面包含具体的属性值也可以，如  

    p[id="apple"]{  
      font:bold;  
    }  
    
> - 属性名部分属性值选择，使用元素 + "\[" + 属性名 + "\]" + “~” + “= 属性值”，如果忽略这个波浪号，这就需要属性值的完全匹配；
> - 字串匹配属性选择器，元素 + "\[" + 属性名 + "\]" + “^” + “= 属性值1”，属性值以属性值1开头；
> - 字串匹配属性选择器，元素 + "\[" + 属性名 + "\]" + “$” + “= 属性值1”，属性值以属性值1结尾；
> - 字串匹配属性选择器，元素 + "\[" + 属性名 + "\]" + “\*” + “= 属性值1”，以属性值1为子串；
#### 7) 后代选择器
> - A B{} 用两个或者多个空格（结合符）分隔开，表示作为A元素的后代的所有B元素，值得注意的是，这种方法选择的后代可以是隔代的，即意味着A元素的后代，乃至A元素的后代的后代，只要有B元素，那个B元素就会被选择；
> - A > B{} 用一个大于号（子结合符）作为选择，表示只选择A的直接后代。
> - A + B{} 用一个加号（相邻兄弟结合符）作为选择，选择的元素需要满足两个条件，1，A和B元素有共同父亲的；2，只会选择B不会选择A（选择性+有序）。
#### 8) 伪类选择器
> - 元素 + “：” + 伪类名
> - 结合伪类，元素 + “：” + 伪类名1 + “：” + 伪类名2 + “：” + 伪类名n，表示同时满足几个伪类；
> - 语言选择，元素 + “：”+lang(语言);
> - 设置首字母样式，元素 + “：”+first-letter;
> - 设置首行样式，元素 + “：”+first-line;
> - 设置之前和之后的元素样式，如下面的语句，相当于在h2元素之前添加两个“}”；    

    h2:before{    
      content:"}}";   
      color:silver;   
    }  
        
> - 伪元素选择器必须放在选择器的最后面
>>>>>> ![图1-2 链接伪类](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE1-2%20%E9%93%BE%E6%8E%A5%E4%BC%AA%E7%B1%BB.png?raw=true) 
>>>>>> ![图1-3 动态伪类a](https://raw.githubusercontent.com/hblvsjtu/CSS_Study/6da97dc10d2248db251897494712f8a29458d805/picture/%E5%9B%BE1-2%20%E5%8A%A8%E6%80%81%E4%BC%AA%E7%B1%BBa.png) 
>>>>>> ![图1-3 动态伪类b](https://raw.githubusercontent.com/hblvsjtu/CSS_Study/6da97dc10d2248db251897494712f8a29458d805/picture/%E5%9B%BE1-2%20%E5%8A%A8%E6%80%81%E4%BC%AA%E7%B1%BBb.png) 		

#### 9) 伪元素选择器
> - 跟伪类差不多，只是冒号改成了双冒号“：：”；		


<h3 id='1.3'>1.3 选择器规则</h3>  

#### 1) 特殊性值
> - 每个选择器的初始特殊性值为0，0，0，0；
> - 对于选择器的各个ID属性值，特殊性值 + 0，1，0，0；
> - 对于选择器的各个类属性值伪类属性值，特殊性值 + 0，0，1，0；
> - 对于选择器的各个元素和伪元素属性值，特殊性值 + 0，0，0，1；
> - 结合符和通配符对特殊性没有贡献；
> - 第一个0是为内联样式保留的，它的特殊性最高；
> - 特殊性越高的会覆盖特殊性越低的；
#### 2) 重要性!impotance
> - 放在声明块内分号的前面，如果放错位置了，整个声明会变得无效；
> - 如果将一个重要声明和一个费重要声明放在一起，胜出的总会是重要声明;  

    p{    
      font: red !importance;    
    }  
     
  
<h3 id='1.4'>1.4 继承</h3>  
 
> - 样式不仅应用到该元素，同时也会影响到该元素的后代；
> - 有一个例外，就是应用到body元素的背景样式，可以应用到html元素，相应地可以定义画布；
> - 有些属性是不能被继承的，比如外边框，内边框，背景和边框；
> - 零特殊性要比无特殊性要强，比如通配符\*的特殊性就要比继承值的要优先，因为继承值根本就没有特殊性；
> - 超链接样式要比继承值（无特殊性）要强； 
> - 有一条经验可供参考：与元素外观相关的样式（文字，颜色和字体）会被继承，与元素在页面上的布局相关的样式不会被继承。在样式表中使用inherit这个特别设立的值可以强行实施继承，如：		
		
		span{		
			border:inherit;		
		}		
		
		
<h3 id='1.5'>1.5 层叠</h3>  
 
> - 标志!impotance要比没有!impotance的要强；
> - 按照来源来分，!impotance的读者 > !impotance的创作人员（元素内嵌样式 > 文档内嵌样式 > 外部样式） > 创作人员（元素内嵌样式 > 文档内嵌样式 > 外部样式） > 读者 > 用户代理；
> - 其他的比较特殊性，如果特殊性相同，则比较出现时间，如果出现时间越晚，特殊性越强，一般认为导入的样式表的声明在前，主样式表的所有声明在后；
> - 伪类规则：LVHA，：link{} ：visit{} ：hover{} :active{}		
		
<h3 id='1.6'>1.6 导入样式表</h3>  		

> - 三种定义样式的方式：元素内嵌，文档内嵌和外部样式表；
> - 另外还有两种容易忽略的方式：浏览器样式（就是元素尚未设置样式的时候用户代理默认的样式）和用户样式（各个浏览器都允许用户定义自己的样式表，这种样式表统称为用户样式，以chrome为例，它会在用户个人配置信息目录中生成一个名为Default\User StyleSheet\Custom.css的文件。添加到这个文件中的任何样式都会被用于用户访问的所有网站）。所以才有了特殊性和重要性的优先级——层叠；
> - 在HTML文档中导入样式表最简单的做法莫过于如下：		
		
		<link rel="stylesheet" type="text/css" href="style.css"/>		
				
> - 那如果你想在CSS中导入另外的样式表，应该怎么做呢？一般用到"@import"语句，如：		
		
		@import "style2.css"; 		
		span{		
			border: dotted 1px block;		
		}		
		
> - 要注意的是"@import"语句必须出现在样式表的自己样式的上面，而"@import"语句的上面最多只能添加字符编码语句"@charset"		
		
		@charset "UTF-8";		
		@import "style2.css"; 		
		span{		
			border: dotted 1px block;		
		}		
		
		
------  		
		
		
<h2 id='2'> 二、值，颜色和单位 </h2>
<h3 id='2.1'>2.1 值</h3>     

#### 1) 整数和百分数
> - 好像没什么好讲的

<h3 id='2.2'>2.2 颜色</h3>    

#### 1) 规范中的17种颜色
>>>>>> ![图2-1 CSS规范定义的颜色_17](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE2-1%20CSS%E8%A7%84%E8%8C%83%E5%AE%9A%E4%B9%89%E7%9A%84%E9%A2%9C%E8%89%B2_17.png?raw=true) 
#### 2) RGB函数式记法
> - 百分数记法 rgb(75%,50%,50%);
> - 整数三元组记法（取值范围0~255） rgb(191,127,127)；
#### 2) RGBA函数式记法
> - 其实就是在RGB函数式记法的基础上增加了一个关于透明度的参数a（0代表全透明，1代表完全不透明）；
> - 整数四元组记法（取值范围0~255,0~1） rgba(191,127,127,0.4)；
#### 3) RGB十六进制记法
> - 十六进制记法其实就是用函数式记法的每一位数用一个十六进制数来表示，如：   

    h1{color: #FF0000;} /* set h1s to red */    
    或者是一种简写记法，你可以只写三位，比如ABC，然后浏览器会取每一位然后进行复制，变成AABBCC；    
    h1{color: #F00;} /* 跟上面那个是等价的 */  
    
> - 当然了，这就意味着并不是所有颜色都可以采用这种简写的方式；
>>>>>> ![图2-2 等价颜色表a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE2-2%20%E7%AD%89%E4%BB%B7%E9%A2%9C%E8%89%B2%E8%A1%A8a.png?raw=true) 
>>>>>> ![图2-2 等价颜色表b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE2-2%20%E7%AD%89%E4%BB%B7%E9%A2%9C%E8%89%B2%E8%A1%A8b.png?raw=true) 

<h3 id='2.3'>2.3 单位</h3>     

#### 1) 绝对长度单位
> - 英寸in;
> - 厘米cm
> - 毫米；
> - 点pt，1 in=72 pt，但是实际上现在的屏幕一英寸里面不止有72个像素，单位是PPI，有的可能有上百个；
> - 派卡pc，1 in=72 pt=12 pc。同上；
#### 2) 相对长度单位
> - em，em-height，常用的印刷单位，一般1 em = 14 pt,但是这个对应关系可以更改；
> - ex，x-height，代表着小写x的高度，一般是em的一半（不要问我，我也不知道这个一半是怎么来的），但是，这个状况比较复杂，因为不同的字体x的高度是不一样的，实际不好操作；
#### 3) [pt和px的区别:点击查看出处](https://www.douban.com/note/155032221/)
> - 字体大小的设置单位，常用的有2种：px、pt。这两个有什么区别呢？先搞清基本概念：
> - px就是表示pixel，像素，是屏幕上显示数据的最基本的点；
> - pt就是point，是印刷行业常用单位，等于1/72英寸。
> - 这样很明白，px是一个点，它不是自然界的长度单位，谁能说出一个“点”有多长多大么？可以画的很小，也可以很大。如果点很小，那画面就清晰，我们称它为“分辨率高”，反之，就是“分辨率低”。所以，“点”的大小是会“变”的，也称为“相对长度”。
> - pt全称为point，但中文不叫“点”，查金山词霸可以看到，确切的说法是一个专用的印刷单位“磅”，大小为1/72英寸。所以它是一个自然界标准的长度单位，也称为“绝对长度”。
> - 因此就有这样的说法，pixel是相对大小，而point是绝对大小。

------  

<h2 id='3'> 三、字体 </h2>
<h3 id='3.1'>3.1 字体属性</h3>  

>> 名字|初始值|应用于|继承性|百分数
>> -|-|-|-|-
>> font-family|用户代理指定的值|所有元素|有|无
>> font-weight|normal|所有元素|有|无
>> font-size|medium|所有元素|有|跟据父元素字体大小计算
>> font-style|normal|所有元素|有|无
>> font-variant|normal|所有元素|有|无
>> font-strectch|normal|所有元素|有|无
>> font-size-adjust|normal|所有元素|有|无
>> font|normal|所有元素|有|无

#### 1) 字体属性  
> - 
>>>>>> ![图3-2 字体加粗](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-8%20%E5%AD%97%E4%BD%93%E5%B1%9E%E6%80%A7.png?raw=true)   

#### 2) 通用字体系列font-family
> - 用户代理会选择从font-family系列中选取一种字体；
> - 为什么要这样做呢？我才是各个用户代理安装的字体都不一样，选择通用字体系列的话，它可以自己选择合适的字体，但是这样的话就无法确定不同客户代理到底会选择具体怎样的字体了；
> - 如果font-family中含有空格或者#或者$，则需要添加引号，其实双引号和单引号都可以，但是有一点需要注意的是不能跟外面的引号冲突，因为在HTML文档中style属性的值也是需要引号的，这两个引号不能相同就可以了；
> - 通用字体系列包括：Serif，Sans-serif,Monospace,Cursive,FanTasy;
> - 可以从中一次写下备选字体，让用户代理自己按照出现的先后使用，如：    

    p{    
    font-family:Times, TimesNR, 'New Century Schoolbook', Georgia, 'New York', serif;     
    }   
    
>>>>>> ![图3-1 通用字体系列](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-1%20%E9%80%9A%E7%94%A8%E5%AD%97%E4%BD%93%E7%B3%BB%E5%88%97.png?raw=true)   

#### 3) 字体加粗  
> - 加粗一共分为9级，从100到900；
>>>>>> ![图3-3 字体加粗](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-2%20%E5%AD%97%E4%BD%93%E5%8A%A0%E7%B2%97.png?raw=true)  

> - 继承，CSS规范中指出，每个数对应着一个加粗度，它至少与前一个数的加粗度相同；
> - 如果设置一个元素的加粗设置为bolder,用户代理首先必须确定从父元素继承的font-weight值，然后选择一个数，它对应于比所继承值更粗的一个字体加粗，而且在满足这个条件的所有数中，要选择一个最小的数。如果没有可用的字体，用户代理会把该元素加粗设置为下一个更大的数字值，除非这个值已经是900；
>>>>>> ![图3-9 特定字体假想指定](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-9%20%E7%89%B9%E5%AE%9A%E5%AD%97%E4%BD%93%E5%81%87%E6%83%B3%E6%8C%87%E5%AE%9A.png?raw=true)     
  
#### 4) 字体大小  
> - 绝对大小：xx-small,x-small,small,medium,large,x-large,xx-large;
> - 用户代理决定缩放因子，一般放大为1.5倍，缩小为0.66倍；
> - 继承，相对大小：百分数
>>>>>> ![图3-4 字体大小](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-3%20%E5%AD%97%E4%BD%93%E5%A4%A7%E5%B0%8F.png?raw=true)   

#### 5) 字体风格  
> - italic斜体，有点像手写；
> - oblique倾斜，就是普通的把字体倾斜个某个角度；
>>>>>> ![图3-5 字体风格](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-4%20%E5%AD%97%E4%BD%93%E9%A3%8E%E6%A0%BC.png?raw=true)   

#### 6) 字体变形  
> - 
>>>>>> ![图3-6 字体变形](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-5%20%E5%AD%97%E4%BD%93%E5%8F%98%E5%BD%A2.png?raw=true)  

#### 7) 字体拉伸  
> - 
>>>>>> ![图3-7 字体拉伸](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-6%20%E5%AD%97%E4%BD%93%E6%8B%89%E4%BC%B8.png?raw=true)  

#### 8) 字体调整  
> - 
>>>>>> ![图3-8 字体调整](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-7%20%E5%AD%97%E4%BD%93%E8%B0%83%E6%95%B4.png?raw=true)  

#### 9) 字体属性  
> - 如   
    
    h1{   
          font:italic 900 small-caps 30px Verdana, Helvetica, Arial, sans-serif;    
    }   
    
>>>>>> ![图3-8 字体调整](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE3-7%20%E5%AD%97%E4%BD%93%E8%B0%83%E6%95%B4.png?raw=true)  
> - 可以使用系统字体，如caption，icon，menu，message-box,  small-caption,  status-bar,如：   
    
    button{   
    font：caption;   
    }   
    
#### 10) 字体下载  
> - 采用这种方法，用户代理可以从文档中下载一个远程字体来使用，如：   
    
    @font-face{   
    font-family:"Scarborough Fair";   
    scr: url(http://www.example.com/fonts/ps/Scarborough.ps);   
    }   
        

------  

<h2 id='4'> 四、文本 </h2>
<h3 id='4.1'>4.1 文本属性</h3>    

>> 名字|初始值|应用于|继承性|百分数
>> -|-|-|-|-
>> text-indent|0|块级元素|有|相对于包含块的宽度
>> text-align|无|块级元素|有|无
>> line-height|normal|所有元素|有|相对于(父-优先)元素的字体大小
>> vertical-align|baseline|行内元素与表单元格|无|相对于line-height的大小
>> word-spacing|normal|所有元素|有|无
>> letter-spacing|normal|所有元素|有|无
>> text-transform|none|所有元素|有|无
>> text-decration|none|所有元素|无|无
>> white-space|none|所有元素|无|无

#### 1) 文本缩进  
> -  text-indent   可以是一个负数，负数表示悬挂缩进（一种段落格式，在这种段落格式中，段落的第二行和后续行缩进量大于第一行。悬挂缩进常用于项目符号和编号列表）；
> -  以前有人为了缩进，把图片嵌套进去作为空格，因为图片img也属于一种短语元素；
>>>>>> ![图4-1 文本缩进](https://raw.githubusercontent.com/hblvsjtu/CSS_Study/b4d1124a5e5a747392c85de296b6601c26d36c53/picture/%E5%9B%BE4-1%20%E6%96%87%E6%9C%AC%E7%BC%A9%E8%BF%9B.png)  
#### 2) 水平对齐  
> -  text-align 虽然可能会弄混text-align：center和<center>元素的作用，实际上他们呢是有明显的区别的，text-align：center不会控制元素的对齐，而只影响其内部的内容；<center>元素不仅可以影响文本，还可以把整个元素居中；
>>>>>> ![图4-2 文本对齐](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-2%20%E6%96%87%E6%9C%AC%E5%AF%B9%E9%BD%90.png?raw=true)   
  
#### 3) 垂直对齐  
> - line-height 指文本行基线之间的距离，而不是字体的大小，他确定了将各个元素框的高度增加或者减少多少。    
> - line-height=字体高度 + 2\*行间距； 
>>>>>> ![图4-3 文本对齐](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-3%20%E5%9E%82%E7%9B%B4%E5%AF%B9%E9%BD%90.png?raw=true)   
>>>>>> ![图4-4 行框图](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-4%20%E8%A1%8C%E6%A1%86%E5%9B%BE.png?raw=true)
> - 百分数是相对于font-size计算的
>>>>>> ![图4-5 line-height的继承](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-5%20line-height%E7%9A%84%E7%BB%A7%E6%89%BF.png?raw=true)
> - 继承font-size的时候是从父元素哪里继承的，而不是在子元素上计算的
>>>>>> ![图4-6 line-height的行高继承](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-6%20line-height%E7%9A%84%E8%A1%8C%E9%AB%98%E7%BB%A7%E6%89%BF.png?raw=true)
> - 为了避免这个问题，一种解决办法是为每个元素设置一个显式的line-height，但是这种方法不太实用，最好是指定一个数，由它设置缩放因子,这样所有的元素都会跟据自己的font-size计算line-height:    
    
    body{font-size:10px;}     
    div{line-height: 1;}    
    p{font-size: 18px;}     
        
#### 4) 垂直对齐文本  
> - 只针对行内元素和表格；
> - 居中对齐有点奇怪，middle会把行内元素框的中点与父元素基线上方0.5ex(1ex=0.5em=0.5\*font-size)处的一个点对齐；
>>>>>> ![图4-7 vertical-align](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-7%20vertical-align.png?raw=true)   
    
    
<h3 id='4.2'>4.2 字间隔和字母间隔</h3>  
  
#### 1) 字间隔
> - “字”的定义：任何非空白符字符组成的串，并由某种空白符包围。
> - 字符间隔有可能会受到text-align的影响，特别是两端对齐的时候；
>>>>>> ![图4-8 word-spacing.png](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-8%20word-spacing.png?raw=true)
#### 2) 字母间隔
> - 那就是字符或者字母之间的间隔喽。
> - 字符间隔有可能会受到text-align的影响，特别是两端对齐的时候，如果letter-spacing的值是normal的话，间距由text-align控制，如果letter-spacing的值是其他绝对或者相对的值的话，间距则由letter-spacing控制；
>>>>>> ![图4-9 letter-spacing](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-9%20letter-spacing.png?raw=true)  
    
<h3 id='4.3'>4.3 其他文本操作</h3>  
  
#### 1) 文本转换
> - 有两个好处：第一就是无需改动父元素的样式，即插即用；第二个就是方便修改；    

>>>>>> ![图4-10 text-transform](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-10%20text-transform.png?raw=true)    

#### 2) 文本装饰
> - 用于去除超链接中的下划线的时候就特别有用；   
    
    a{    
        text-decoration: none;    
     }    
        
        
>>>>>> ![图4-11 text-decoration](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-10%20text-transform.png?raw=true)    
#### 3) 文本阴影text-shadow
#### 4) 处理空白符white-space 
> - wrap一般用来处理换行；
>>>>>> ![图4-12 white-space](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE4-12%20white-space.png?raw=true) 
#### 5) 方向direction   

------  

<h2 id='5'> 五、基本视觉格式化 </h2>
<h3 id='5.1'>5.1 完整的框模型</h3>      

#### 1) 块级元素
> - 对一个元素而言，width指的是左内边界到右内边界的距离，height则是上内边界到下内边界的距离，其中内边距和外边距和边框会增加整个元素框的宽度，但是需要注意的是整个元素框的宽度和一个元素的宽度不是一回事；
>>>>>> ![图5-1 盒子模型](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-1%20%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B.png?raw=true) 
> - 正常流中块级元素的水平部分总和（外边距+边框+内边距+子元素width）等于父元素的width，比如div和他内部的文本；

<h3 id='5.2'>5.2 水平格式化</h3>		

#### 1) 非替代元素的水平格式化
> - 7个水平属性    
    
    父元素width    
        = 元素框的宽度     
        = margin-left + border-left + padding-left + 子元素width +  margin-right + border-right + padding-right     
               
> - 其中只有width，margin-left和margin-right可以设置auto，其余属性必须设置为特定的值或者0，而width必须设置为auto或者某种特定的非负值；
> - 如果width，margin-left和margin-right都被限制了（设置了某个值），但是他们的和并不等于元素框的宽度，这就说明格式化属性被过分限制了，此时margin-right会被强制设置为auto；
> - 如果margin-left和margin-right被设置为auto，则满足以下关系式，而且子元素会居中    
    
    margin-left = margin-right = （元素框的宽度 - 子元素width）/2    
    
> - 如果width和某个margin被设置为auto，则满足以下关系式，而且子元素会居中;     
    
    margin = 0;   
    子元素width = margin-other = width/2        
    
> - 如果width，margin-left和margin-right三个都被设置为auto，则满足以下关系式，而且子元素会居中 
    
    margin-left = margin-right = 0;   
    子元素width = 元素框的宽度;    
    
> - 除了margin-left和margin-right同时被设置为auto，他们其中一个被设置为auto，那么该值就会被设置为0；
> - 外边框被设置为负数也是合法的，只要7个属性加起来等于元素框宽度就可以了；
> - 当然了，你也可以使用百分数，该比例指的是占元素框宽度的比例；
#### 2) 替代元素的水平格式化
> - 非替代元素的水平格式化规则完全适用于替代元素的水平格式化，只有一点例外，当替代元素的width被设置为为auto的时候，该元素的width等于内容的固有宽度；
> - 如果非替代元素的宽度被设定不同于其固有宽度的时候，其宽度和高度就会按比例的缩；

<h3 id='5.3'>5.3 垂直格式化</h3>		

#### 1) 垂直格式化
> - 如果设置的height高于内容本身的高度的时候，就会产生一种虚假的视觉效果——额外的内边框；
> - 如果设置的height低于内容本身的高度的时候，浏览器一般会给你加一个滚动条；
> - 如果父元素没有设置绝对高度，而子元素设置了百分数高度，由于没有继承，所以子元素的百分数高度无效；
> - 垂直居中的遗憾：垂直居中不像水平居中，只要把两个外边同时设置为auto就可以，在垂直居中中，无论是只有一个外边框，还是两个外边框都同时为auto，他们都会被设置为0。所以，当两个外边框都被设置为auto的时候，得到的结果只会是子元素的高度占满整个元素框的高度；
> - 但是垂直居中也有办法，比如   
    
    <div height=6em>    
        <p height=50%>    
            冰红茶无法垂直居中   
        </p>    
     </div>    
            
    <div  style="height: auto; border-top: 1px solid; border-bottom: 1px solid;">   
        <p  style="background-color:yellow;">   
             冰红茶垂直居中，上下边距等于1em;    
        </p>    
    </div>    
            
> - 高度设置为auto的问题：对于正常的流元素，设置父元素高度为auto，如果父元素没有设置内边距或者边框，则父元素高度=子元素上下外边框的距离，此时会造成一个后果：子元素的外边距会超过父元素的外边界；否则，父元素高度=子元素上下外边距边界的距离； 
> - 合并垂直外边框 相邻外边框沿着数竖轴合并，换句话说，两个外边框中较小的一个会被较大的一个合并（或者说重叠）；
> - 负外边距 如果垂直外边距都设置为负值，浏览器会取这两个外边界绝对值的最大值；如果一个正外边距与一个负外边距合并，会从正外边距减去这个负外边距的绝对值（换句话讲，负值要增加到正值，所得到的就是元素间的距离）；如：   
    
    li{border-bottom: 20px;}    
    ul{border-bottom: -15px}    
    h1{border-top:-18px}    
    
>>>>>> ![图5-2 正负外边距合并](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-2%20%E6%AD%A3%E8%B4%9F%E5%A4%96%E8%BE%B9%E8%B7%9D%E5%90%88%E5%B9%B6.png?raw=true) 
> - 重叠顺序 最后讲一下关于重叠到底线是谁的问题，一般来讲，浏览器显示的顺序是从前往后的，所以后面的会覆盖前面的    

<h3 id='5.4'>5.4 行布局</h3>    

#### 1) 行布局
>> 由于行内元素没有设置内边距和外边距，所以边界会有些重叠；
>> 基本术语介绍：
>> 非替换元素：   行内框= inline-height=行间距+font-size(内容区高度)；   
>> 替换元素：     行内框=内容区高度=固有高度+外边距+边框+内边距;
>> 行框=max{行内框1，行内框1 ,行内框n} - min{行内框1，行内框1 ,行内框n};
>>>>>> ![图5-3 基本术语a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-3%20%E5%9F%BA%E6%9C%AC%E6%9C%AF%E8%AF%AD.png?raw=true)    
>>>>>> ![图5-3 基本术语b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-3%20%E5%9F%BA%E6%9C%AC%E6%9C%AF%E8%AF%ADb.png?raw=true)   
>>>>>> ![图5-4 确定行中个元素行内框的高度](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-4%20%E7%A1%AE%E5%AE%9A%E8%A1%8C%E4%B8%AD%E4%B8%AA%E5%85%83%E7%B4%A0%E8%A1%8C%E5%86%85%E6%A1%86%E7%9A%84%E9%AB%98%E5%BA%A6.png?raw=true) 

>> 行内元素的背景应用于内容区及所有内边距；
>> 行内元素的边框应用于内容区，内边距和边框；
>> 对于父元素，也可以设置inline-height的值，但是如果里面没有子元素的话，这是了也没有任何效果。当你设置了父元素inline-height的值，而且里面又有内容的时候，这个值会应用到各文本中的所有内容；    

#### 2) 行内非替换元素
>> 内容区高度可以大于行内框的高度，这种情况形成的条件是：vertical-align的值为top，inline-height是继承过来的，内容区的font-size比从父元素继承过来的inline-height要大；
>> 以上这种情况font-size比inline-height，就很容易产生文本的重叠。要解决这个问题，最好inline-height使用关于font-size的函数，比如采用单位em，1em的巧妙使用，或者在父元素那里设置inline-height的缩放因子(注意缩放因子的参考是本元素的font-size)为1，然后子元素继承。这两种方法本质上是一样的;
>>>>>> ![图5-6 文本重叠](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-6%20%E6%96%87%E6%9C%AC%E9%87%8D%E5%8F%A0.png?raw=true)
>> 当然了还有其他方法，比如一开始设置inline-height原始值是一个比较大的值，或者设置一个比较大的缩放因子，又或者增加子元素的属性，比如利用短语元素span设置内边框
>> vertical-align会改变内容区和行内框的位置（在基线附近偏移），从而改变整行的行框。
>> vertical-align影响的因素只有inline-height和基线位置；
>>>>>> ![图5-5 vertical-align的值](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-5%20vertical-align%E7%9A%84%E5%80%BC.png?raw=true)     
>> 外边距，边框，内边距不影响行高（也就是上下内外边距和边界，因为只有inline-height才会影响 ），但是会影响左右跟别的元素的距离（也就是左右内外边距和边界）
>> 外边距，边框，内边距虽然不影响行高和边界，但是如果给元素添加背景色（边框+内边距）的话，由于后面的元素会覆盖前面的元素，这也会产生遮盖。
>> 对于普通的行内文本而言，影响行高的只有inline-height，font-size和vertical-align；
#### 3) 行内替换元素
>> 用替换元素整体（包括内容，外边距，边框和内边距）来定义行内替换元素的行内框；
>> 负外边距会使替换元素的行内框小于正常的大小。负外边框是使行内替换元素挤入其他行的唯一办法。
>> 替换元素的行内框底端一般会比基线高一点点，这样有时候就很难看了
>>>>>> ![图5-7 行内替换元素位于基线上](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-7%20%E8%A1%8C%E5%86%85%E6%9B%BF%E6%8D%A2%E5%85%83%E7%B4%A0%E4%BD%8D%E4%BA%8E%E5%9F%BA%E7%BA%BF%E4%B8%8A.png?raw=true)     
>> 解决的办法还是有的，第一种方法：使行内替换元素属性变成block块级元素；第二种方法：把包含图像的表单元格的font-size和line-height都设置成跟替换元素等高的长度；第三种方法：使用负的border-bottom，把替换元素拉下去，但是这种方法有一个缺陷，就是容易纠枉过正，把替换元素拉到下一行去了，当然了有的浏览器只是把内容区的底端放到基线上，而忽略负的下边框距；
#### 4) 改变元素显示
>> list-item——ul的显示角色;
>>>>>> ![图5-8 display的属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-8%20display%E7%9A%84%E5%B1%9E%E6%80%A7.png?raw=true) 

> - 比较使用的一种技巧是利用角色的改变，把无序列表从纵向改成横向，如：
    
    <head>
	<title>form表单</title>
		<link rel="stylesheet" type="text/css" href="style.css"/>
		<style>
			ul li{
				display:inline;
				padding:0 0.33em;
				border-right: 1px solid;
			}
			ul li:first-child{
				border-left: 1px solid;
			}
		</style>
	</head>   
      
    </div>
      <ul>
        <li class="dis_block">冰红茶1</li>
        <li class="dis_block">冰红茶2</li>
        <li class="dis_block">冰红茶3</li>
        <li class="dis_block">冰红茶4</li>
        <li class="dis_block">冰红茶5</li>
      <ul>
    <div>   
    
>>>>>> ![图5-9 将显示角色由list-item改为inline](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-9%20%E5%B0%86%E6%98%BE%E7%A4%BA%E8%A7%92%E8%89%B2%E7%94%B1list-item%E6%94%B9%E4%B8%BAinline.png?raw=true)  

>> inline-block
> - 一般来讲，块元素的后代可以是行内元素，但是行内元素的后代不能是块元素。但是有时候我先要块元素作为行内元素使用怎么办？
> - 可以使用inline-block行内块元素，在行内可以实现块元素的特性，比如在段落文本行框中放入一个行内块元素，那么他的内容块底端就会默认与基线对齐，而且内部没有行分隔符，又可以使用height，width等块元素的特性。
> - 如果设置width为auto或者选择默认，那么行内块元素的内容框就会紧包着内容，但是也会有一个问题就是，行内块元素不会跨过多个文本行；
>>>>>> ![图5-10 inline-block](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE5-10%20inline-block.png?raw=true)   

>> run in
> - 使本元素（本元素原来默认是一个块级元素）成为下一个紧接着的元素（这个元素也默认是一个块级元素）的行内元素；   
> - 但是截至到目前2018-04-02我的chrome还不支持这个功能；    
    
    
    <h1 style="display: run in">    
      Run in text   
    </h1>   
    <p>   
      我是下一个块级元素   
    </p>    
        
          
------  

<h2 id='6'> 六、内边框、边距和边框 </h2>
<h3 id='6.1'>6.1 基本元素框</h3>    

>> 名字|初始值|应用于|继承性|百分数
>> -|-|-|-|-
>> width|auto|块级元素和替换元素|无|相对于包含块的宽度
>> height|auto|块级元素和替换元素|无|相对于包含块的宽度
>> margin|未定义|所有元素|无|相对于包含块的宽度
>> margin-four|0|所有元素|无|相对于包含块的宽度
>> border-style|对简写属性没有定义|所有元素|无|见各个属性
>> border-four-style|none|所有元素|无|无
>> border-width|对简写属性没有定义|所有元素|无|见各个属性
>> border-four-width|medium|所有元素|无|无
>> border-color|对简写属性没有定义|所有元素|无|见各个属性
>> border-four-color|元素的color颜色|所有元素|无|无
>> border|跟据单个属性|所有元素|无|无
>> padding|对简写属性没有定义|所有元素|无|相对于包含块的宽度
>> padding-four|0|所有元素|无|相对于包含块的宽度

<h3 id='6.2'>6.2 width和height</h3>		

#### 1) width和height  
> - width定义为左内边界到右内边界的距离，height定义为上内边界到下内边界的距离；
> - width和height不能用于行内非替换替换，那么问题就来了，这也是不是说就可以用在行内替换元素和块元素呢？

<h3 id='6.3'>6.3 margin</h3>			

#### 1) margin		  
> - 增加元素延伸空间的方法有三种，增加padding，增加margin或者同时增加padding和margin；
> - 背景最多延伸到元素的padding；
> - margin的尺寸可以同时定义上右下左TRBL（顺时针方向）中间用空格隔开；
> - 当然了，也有简便大的写法——值复制模式：如果缺左外边距的值，则使用右外边距的值；如果缺少下外边距的值，则使用上外边距的值；如果缺少右外边距的值，则使用上外边距的值；
> - margin百分数的设定是以父元素width为参考的;
> - 但是应该避免一种死循环就是，margin采用百分数的时候，margin-top和margin-bottom也会采用百分数，这时候元素外边框增加了，父元素的高度也被迫增加，由于父元素的高度增加，margin-top和margin-bottom也会增加，从而产生死循环；

<h3 id='6.4'>6.4 border和padding</h3>		

#### 1) border  
> - border位于元素外边距内，有三个属性可以修改：粗细（默认medium，2px），样式（默认none）和颜色（默认黑色，可以继承）；
> - 要使用border，就必须先声明样式，否则就是默认值none，none的话其他的粗细和颜色就没有意义了；
> - CSS规定背景可以应用到外边界之外，CSS2规定背景可以应用到内边距及其之内，CSS2规定背景可以应用到边框及其之内，
> - 样式（必须要声明，否则就是默认值none，none的话其他的粗细和颜色就没有意义了），粗细，和颜色同样可以同时定义上右下左TRBL（顺时针方向）中间用空格隔开；
> - 当然了，也有简便大的写法——值复制模式：	
>>>>>> ![图6-1 border-style](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE6-1%20border-style.png?raw=true)		
> - 边界的颜色也可以是透明的transparent
#### 2) padding  
> - 同理，没什么好讲的；		
          
------  

<h2 id='7'> 七、颜色和背景 </h2>

>> 名字|初始值|应用于|继承性|百分数
>> -|-|-|-|-
>> color|用户代理的值|所有元素|有|无
>> background-color|transparent|所有元素|无|无
>> background-image|none|所有元素|无|无
>> background-repeat|repeat|所有元素|无|无
>> background-position|0% 0%|块级元素和替换元素|无|相对于元素和原图像上相应的点
>> background-attacment|scroll|所有元素|无|无
>> background|跟据单个属性|所有元素|无|<background-position>允许的值
>> background-color|transparent|所有元素|无|


<h3 id='7.1'>7.1 颜色与背景</h3>		

#### 1) 总述 
> - 颜色分为前景和背景色；
#### 2) color
> - 前景包括元素的问版本和元素周围的边框，所以设置元素的颜色有两种方法：第一种是直接设置color，另一种是设置边框的颜色；
#### 3) background-image
> - 值为<url> | none |inherit，如：		
	
	body{		
		background-image: url(bg23.gif);		
	}		
			
> - 背景不能被继承，因为子元素也想有自己的个性；
> - 设置了 background-image后也还可以设置background-color，避免图片无法加载的时候可以显示别的东西，或者有些透明的图片需要跟背景一起才能表现某种效果；
#### 4) background-image
> - url();
#### 5) background-repeat
> - 可选的值包括repeat，repeat-x，repeat-y, no-repeat, inherit;
> - 默认的值是repeat；
#### 6) background-position
> - 用来给background-image定位用的;
> - 两个参数，一个是水平方向，另一个是垂直方向，如果只写一个，则默认垂直方向上是50%；
> - 如果参数是具体的绝对长度，则参考图片和元素框左上角的位置关系
>>>>>> ![图6-2 background-position](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE6-2%20background-position.png?raw=true) 如：		
		
		p{		
			background-image:url(bg23.gif);		
			background-position:left center; 		
			background-repeat:no-repeat;		
			background-color:white;		
		}		
		
#### 7) background-attachment
> - fix 背景图片相对于可视区是固定的，且不受滚动的影响；
> - scroll 背景图片相对于可视区不是固定的，受滚动的影响；
#### 8) background
> - 这个没什么好讲的，原理大家都懂；
> - 值得注意的是background-position属性的出现必须是成对的；		

------  

    
<h2 id='8'> 八、浮动和定位 </h2>		
		
>> 名字|初始值|应用于|继承性|百分数
>> -|-|-|-|-
>> float|none|所有元素|无|无
>> clear|none|块级元素|无|无
>> position|static|所有元素|无|无
>> top/right/bottom/left|auto|定位元素|无|包含块的高度和宽度
>> min-width/min-height|0|除了非替换行内元素和表元素以外的所有元素|无|包含块的宽度
>> max-width/max-height|none|除了非替换行内元素和表元素以外的所有元素|无|包含块的高度
>> overflow|visible|块级元素和替换元素|无|无
>> clip|auto|绝对定位元素|无|无
>> visibility|visable|所有元素|有|无
>> z-index|auto|定位元素|无|无

<h3 id='8.1'>8.1 浮动</h3>  

#### 1) float  
>>  值有left(最左)|right(最右)|none|inherit
>>  四周环绕包围；
>>  包含块的定义：最近的块级祖先元素；
>>  外边框不会与其他元素合并；
>>  前提：必须要提供width这个参数，否则宽度只有默认的一个字符，特别需要注意的是行内非替换元素，如普通文本；
>>  浮动的详细内幕：浮动元素的包含块是其最近块级父元素，浮动元素会生成一个块级框
> - 向左或向右浮动；
> - 避免浮动产生重叠；
> - 不同于气球，浮动元素不能一直浮动；
> - 使浮动元素一直在其之前浮动元素的下面；
> - 使浮动元素在其上下文内；
> - 如果没有足够的空间，浮动元素会被寄到一个新的行上；
> - 满足其他约束条件的前提下，浮动尽可能高；
> - 向左或者向右尽可能得远；
>>  虽然不准浮动元素的外边框覆盖父元素内的行内框和块框，但是如果存在浮动元素存在负边距的时候，就出现问题了：
> - 行内框与一个浮动元素重叠的时候，其边框，背景和内容都在浮动元素“之上”；
> - 块框与一个浮动元素重叠的时候，其边框和背景在该浮动元素“之下”，而内容在浮动元素“之上”显示；
>>  存在两种情况浮动元素会溢出父元素内边界：
> - 浮动元素存在负边距；
> - 浮动元素宽度或者高度比父元素大；
#### 2) clear  
>>  值有left(最左)|right(最右)|both|none|inherit
>>  作用是禁止浮动元素出现在其左边或者右边，如果存在浮动元素，则该元素必须出现在浮动元素的下面，不能有重叠；
>>  注意clear的作用域是块级元素，这就意味着行内元素和其他元素不能设置，还有<br>也不行，因为它是一个行内元素，如果强行需要的话，可以更改其display属性；
>>  设置了clear属性之后，上外边距很大可能会被强制调整；
>>  CSS2.1之后，引入了一个清除域（clearance）的概念：在元素上外边距之上增加额外的间隔，不允许任何浮动元素进入这个范围。这就意味着设置clear属性之后，该元素的外边距并没有改变，之所以会下移是因为这个清除域造成的；

<h3 id='8.2'>8.2 定位</h3> 		
		
#### 1) position  
>>  static | relative | absolute | fixed | inherit； 
>>  static，一切正常，块级元素生成矩形框，行内元素生成一个或者多个行框；
>>>>>> ![图7-1 定位position](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE7-1%20%E5%AE%9A%E4%BD%8Dposition.png?raw=true)		
		
>>  什么叫定位元素？position的值不是static，元素绝对定位的时候，会从文档流中完全删除，然后相对其包含块定位，其边界跟据偏移放置。通常在一开始的时候，没有显式设定的绝对定位元素，如果需要绝对定位的话，只能找根元素html。这就会非常的awkward。所以，为了避免这些比较尴尬的场景，需要设定参考定位元素，这就是relative了，如果不对它进行任何值的设置，他的特性其实跟static差不多，但是它可以被绝对定位元素用来作为包含块。这时候绝对定位元素就不需要被迫采用根元素html作为参考了：		
		
		p{		
			position:relative;		
		}		
				
				
>>  包含块的定义
> - 根元素的包含块是有用户代理建立的，在HTML中，根元素就是html元素
> - 对于非根元素，position的值为static或者relative，其包含块就是离它最近的块级框，表单元格或者行内祖先框的内容边界；
> - 对于非根元素，position的值为absolute，包含块必须满足要求：离非根元素最近的定位元素。然后假如包含块是块级元素，则包含块是最近定位父元素的边框；如果包含块是行内元素，则包含块是最近的定位父元素的内容边界。一句话说，absolute的非根元素的包含框是最近定位块级父元素的边框或者是最近定位行内父元素的内容边界。
> - 对于非根元素，position的值为fixed，则包含块就是视图区；
> - 如果没有祖先，则元素的包含块定义为初始包含块；
#### 2) 偏移属性offset
> - top | right | bottom | left 描述的是定位元素（上右下左）外边距边界距离包含块（上右下左）边界的距离；
> - 正值会导致定位元素往包含块中心偏移，负值则往外偏移，有可能会移除包含块之外；
> - 偏移过程中外边距，边框，内边距和内容都会在定位过程中移动；
> - 自动边偏移，假如top | right | left的任意一个值是auto（除开bottom），那么出现一种神奇的现象是，该元素就变成了类似relative，不要求父元素必须是定位元素，普通的正常流元素也可以，然后在他原来没有脱离文档流之前的位置，然后对齐。0的优先级比auto高，right的优先级比width低，left的优先级比width高，总体来讲，过度受限就会忽略right的值；
> - 非替换元素的自动边偏移，当left,width,right都设置为auto的时候，width为容纳文本的长度，然后当left设置为auto的时候，就relative了，左边靠拢，然后加上本身的width长度，如果右边也是auto的话，只能忽略掉了。因为需要符合一下公式，整体的效果就是往左对齐，当然了，如果你需要居中的话，可以设置左边距和右边距为auto，同时需要：		
		
		包含块width = 		
		left + margin-left + border-left + padding-left + 子元素width +  margin-right + border-right + padding-right + right		
				
				
#### 3) 定位元素的wid
th和height  
> - 定位元素的width和height在定位过程中可以不需要显式设置，默认是auto，然后就根据偏移属性进行设置，设置了偏移后，width和height就废掉了；
#### 4) 绝对定位元素的水平居中和垂直居中：
> - 在绝对定位元素中，如果left或right为auto，left或right就会相应的变成0，定位就会变成静态定位（所谓的静态定位，其实就是表现出按照没有绝对定位之前的位置摆放，但是其属性是绝对定位不变），或者绝对定位元素的width不确定，则margin-left和margin-right的auto会变成0，如果水平方向受限的话，margin-right会变成自适应，但是margin-left绝对会变成0。如果left或者right都不是auto，同时绝对定位元素有确定的width，margin-left和margin-right都是auto的话，margin-left = margin-right。这可以用来水平居中；
> - 在绝对定位元素中，如果top或bottom为auto，top或bottom就会相应的变成0，定位就会变成静态定位（所谓的静态定位，其实就是表现出按照没有绝对定位之前的位置摆放，但是其属性是绝对定位不变），或者绝对定位元素的height不确定，则margin-top和margin-bottom的auto会变成0，如果垂直方向受限的话，margin-bottom会变成自适应，但是margin-top绝对会变成0。如果top和bottom都不是auto，同时绝对定位元素的height确定，margin-top和margin-bottom都是auto的话则，margin-top = margin-bottom。这可以用来垂直居中；
#### 5) 注意：
> - 在绝对定位元素中，其定位作用的主要是偏移量，所以如果需要居中的话，包括水平也好，垂直的也好，也最好使用偏移量。而外边距只能用作辅助，所以无法使用margin-left：auto；margin-right：auto；的方式进行左右居中，最好是设置偏移量left和right等于相同的百分数，width设置为auto，从而确定定位元素的外边界的位置；
> - 在绝对定位元素中，子元素无法影响包含块的高度和宽度；
> - 在绝对定位元素中，当上右下左四个偏移量都设定好之后，可以使用margin：auto进行水平和垂直居中，值得赞许的是，连垂直居中都可以欸，要知道在正常文本流的垂直居中是不可以使用margin-top：auto和margin-bottom：auto进行的；
> - 在绝对定位元素中，垂直方向过度受限的时候，会忽略bottom的值；水平方向过度受限的时候，会忽略right的值；
#### 6) 高度的限制  
> - min or max 对高度的限制；
#### 7) overflow-内容溢出或者裁剪  
> - visible | hidden | scroll | auto | inherit
> - 其实就是当子元素溢出包含块的时候告诉用户代理如何处理的问题：
> - visible是默认值，hidden就是隐藏掉溢出的部分，scroll就是加一个滑动条，auto
#### 8) clip-内容裁剪  
> - rect(top, right, bottom, left) | auto | inherit
> - rect的语法很有特点，就是后面加的四个值都是用逗号隔开，但是在CSS2.0的规范中说有例子是不加逗号的，实际上加不加逗号都不要紧，但是还是建议加一下。因为这样更加容易读，这也是CSS2.1推荐的做法；
> - rect四个值的参考是元素左上角的点；
> - rect应用的元素是绝对定位元素；
> - 但是绝对定位元素有一个缺点是不好确定宽度和长度，这就需要显式定义width和height；
#### 8) visibility-可见性
> - visible | hidden | collapse | inherit

<h3 id='8.3'>8.3 z轴上的位置z-index</h3> 		

#### 1) z-index
>>  auto | <integer> | inherit；
> - 应用于定位元素；
> - 可以改变元素的覆盖顺序，较高的z-index值可以覆盖较低的z-index值；
> - z-index值可以是负数，那就被覆盖的更底下了； 
> - z-index值是分维数的，； 同一级（同一个父元素）的元素的z-index互相比较，即先比较父元素最早的那个z-index值，最后再比较自己的z-index值；
> - z-index值如果是负数，跟据CSS2.1，该元素不能放在父元素的也不能背景之下；	
		
<h3 id='8.4'>8.4 固定定位和相对定位</h3> 		

#### 1) 固定定位fixed
> - 固定元素的包含块是视窗，元素会完全从文档流中去除；
#### 2) 相对定位relative
> - 对于非根元素，position的值为static或者relative，其包含块就是离它最近的块级框，表单元格或者行内祖先框的内容边界；那么，他自己也会变成一个包含块（无论它本身是否是一个块状元素或者是一个行内元素），同时他会在原来的位置生成一个包含块（这个块不会消失，并且会继续影响其他非定位元素）作为参考；
>>>>>> ![图7-2 position_relative](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE7-2%20position_relative.png?raw=true)		

------  

    
<h2 id='9'>九、表布局 </h2>		
		
>> 名字|初始值|应用于|继承性|百分数
>> -|-|-|-|-
>> display|inline|所有元素|无|无
>> caption-side|top|display值为table-caption的元素|无|无
>> border-collapse|separate|display值为table或者inline-table的元素|有|无
>> border-spacing|0|display值为table-cell的元素|有|无
>> table-layout|auto|display值为table或者inline-table的元素|有|无


<h3 id='9.1'>9.1 表格式化</h3>  

#### 1) display表显式值  
> - table 制定一个元素定义一个块级表；
> - inline-table 制定一个元素定义一个内行级表；
> - table-row 一行  table-row-group 一组行 ；
> - table-column 一列  table-column 一组列 ；
> - cell 单个单元格；
> - table-caption 单个总标题；
>>>>>> ![图8-1 display](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE8-1%20display.png?raw=true)	

>>>>>> ![图8-2 table常用的标签](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE8-2%20table%E5%B8%B8%E7%94%A8%E7%9A%84%E6%A0%87%E7%AD%BE.png?raw=true)		

#### 2) border-collapse表单元格边框
> - collapse | separate | inherit
> - collapse 合并单元格边框用的，要不然每个单元格都有自己的边框，看起来连接的部分就有两条线，含难看（分隔边框模型）；
#### 3) border-spacing边框间距
> - 可以指定两个值，分别是水平方向的间距和垂直方向的间距；
> - 当然了，你用一个值也可以，就代表水平方向和垂直方向的间距都是同一个值；
> - 要注意的是，这要应用与表元素，而不是单个单元格或者行或者列元素；
#### 4) caption-side
> - top | bottom
> - 放标题的位置；
#### 5) 分隔单元格边框模型

#### 6) 合并边框模型
>>>>>> ![图8-3 合并边框模型](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE8-3%20%E5%90%88%E5%B9%B6%E8%BE%B9%E6%A1%86%E6%A8%A1%E5%9E%8B.png?raw=true)
>>>>>> ![图8-4 布局公式](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE8-4%20%E5%B8%83%E5%B1%80%E5%85%AC%E5%BC%8F.png?raw=true)
> - 边框合并，不是重合，而是只画一个，这要看那个占上风。要看那种边框类型border-style占上风，优先级最高；
> - hidden > double > solid > dashed > dotted > ridge > outset > groove > inset > none;
> - 如果边框的样式一样，只是颜色不同，颜色的优先级跟据元素类型来，cell > row > row group > colume > colume group > table ;
> - 如果连以上都不能分辨的话，只能优先考虑最上最左边框的颜色；
#### 7) 表层
> - CSS定义了6个不同的层；
>>>>>> ![图8-5 表层.png](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE8-5%20%E8%A1%A8%E5%B1%82.png?raw=true)

<h3 id='9.2'>9.2 表大小</h3>  

#### 1) table-layout表布局  
> - auto | fixed | inherit
> - auto自动布局，这个布局比较复杂
> - fixed固定布局
> - 对齐 vertical-align top | middle | bottom |baseline
 
 
 

















