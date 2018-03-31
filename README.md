# CSS_Study  
  
  
### 作者：冰红茶  
### 参考书籍：《CSS权威指南》
------  

   CSS，Cascade Style Sheet层叠样式表，负责html页面的美化工作。其实当初在学javascript权威指南第二部分的时候，就觉得应该补一下html和css权威指南方面的知识，才能更好地进行第二部分的学习^_ ^
  
## 目录

## [一、元素与选择器](#1)
### [1.1 元素](#1.1)
### [1.2 选择器](#1.2) 
### [1.3 选择器规则](#1.3) 
### [1.4 继承](#1.4)
### [1.5 层叠](#1.5)
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
## [五、嵌入内容](#5)
### [5.1 嵌入图像](#5.1)
### [5.2 嵌入另一张HTML文档](#5.2)
### [5.3 通过插件嵌入内容](#5.3)
### [5.4 嵌入数字表现形式](#5.4)
## [六、理解DOM](#6)
### [6.1 理解DOM](#6.1)
------  

    
<h2 id='1'> 一、元素与选择器 </h2>
<h3 id='1.1'>1.1 元素</h3>  

#### 1) 替换元素与非替换元素  
> - 替换元素即是那种用于填充图像，影片和音乐；
> - 非替换元素即是那种由用户代理（主要是浏览器）显示的内容，比如文字；
#### 2) 元素显示角色  
> - 块级元素（block） 元素框独立，在元素框前后生成分隔符
> - 行内元素（inline） 元素框非独立  

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

<h3 id='1.3'>1.3 选择器规则</h3>  

#### 1) 特殊性值
> - 每个选择器的初始特殊性值为0，0，0，0；
> - 对于选择器的各个ID属性值，特殊性值 + 0，1，0，0；
> - 对于选择器的各个类属性值，特殊性值 + 0，0，1，0；
> - 对于选择器的各个元素和伪类属性值，特殊性值 + 0，0，0，1；
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
 
<h3 id='1.5'>1.5 层叠</h3>  
 
> - 标志!impotance要比没有!impotance的要强；
> - 按照来源来分，!impotance的读者 > !impotance的创作人员 > 创作人员 > 读者 > 用户代理；
> - 其他的比较特殊性，如果特殊性相同，则比较出现时间，如果出现时间越晚，特殊性越强，一般认为导入的样式表的声明在前，主样式表的所有声明在后；
> - 伪类规则：LVHA，：link{} ：visit{} ：hover{} :active{}     

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
    

 
 
 
 
 
 

















