# CSS3.0新增的特性  
  
  
### 作者：冰红茶  
### 参考书籍：《HTML5权威指南》 第三部分第16章~第24章		

------  

   CSS3.0在2.1的基础上新增很多的特性，如弹性盒子布局，过渡动画和变换属性，圆角等，这些新的特性给设计者带来了很多方便的地方，比如设置垂直居中等等。面向新的时代，学习和比较新的特性显得非常的必要^_ ^
  
## 目录

## [一、简明参考](#1)
### [1.1 CSS选择器简明参考](#1.1)
### [1.2 属性简明简明参考](#1.2)
## [二、CSS选择器](#2)
### [2.1 属性选择器](#2.1)
### [2.2 元素选择器](#2.2) 
## [三、边框与背景](#3)
### [3.1 圆角](#3.1)
### [3.2 边框](#3.2)
### [3.3 背景](#3.3)
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

<h2 id='1'> 一、简明参考 </h2>
<h3 id='1.1'>1.1 CSS选择器简明参考</h3>		

>> *（引自《HTML5权威指南》）*

#### 1) CSS选择器简明参考  
>>>>>> ![图9-1 CSS选择器简明参考a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-1%20CSS%E9%80%89%E6%8B%A9%E5%99%A8%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83a.png?raw=true)		
>>>>>> ![图9-1 CSS选择器简明参考b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-1%20CSS%E9%80%89%E6%8B%A9%E5%99%A8%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83b.png?raw=true)		


<h3 id='1.2'>1.2 属性简明简明参考</h3>  

#### 1) 边框和背景属性  
>>>>>> ![图9-2 边框与属性简明参考a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-2%20%E8%BE%B9%E6%A1%86%E4%B8%8E%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83a.png?raw=true)		
>>>>>> ![图9-2 边框与属性简明参考b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-2%20%E8%BE%B9%E6%A1%86%E4%B8%8E%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83b.png?raw=true)		
>>>>>> ![图9-2 边框与属性简明参考c](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-2%20%E8%BE%B9%E6%A1%86%E4%B8%8E%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83c.png?raw=true)
>>>>>> ![图9-2 边框与属性简明参考d](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-2%20%E8%BE%B9%E6%A1%86%E4%B8%8E%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83d.png?raw=true)

#### 2) 基本的盒子属性
>>>>>> ![图9-3 盒子属性简明参考a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-3%20%E7%9B%92%E5%AD%90%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83a.png?raw=true)		
>>>>>> ![图9-3 盒子属性简明参考b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-3%20%E7%9B%92%E5%AD%90%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83b.png?raw=true)			

#### 3) 布局属性
>>>>>> ![图9-4 布局属性简明参考](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-4%20%E5%B8%83%E5%B1%80%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83.png?raw=true)		

#### 4) 文本属性
>>>>>> ![图9-5 文本属性简明参考](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-5%20%E6%96%87%E6%9C%AC%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83.png?raw=true)		 

#### 5) 过渡，动画和变换属性
>>>>>> ![图9-6 过渡，动画和变换属性简明参考a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-6%20%E8%BF%87%E6%B8%A1%EF%BC%8C%E5%8A%A8%E7%94%BB%E5%92%8C%E5%8F%98%E6%8D%A2%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83a.png?raw=true)		
>>>>>> ![图9-6 过渡，动画和变换属性简明参考b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-6%20%E8%BF%87%E6%B8%A1%EF%BC%8C%E5%8A%A8%E7%94%BB%E5%92%8C%E5%8F%98%E6%8D%A2%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83b.png?raw=true)			

#### 6) 其他属性
>>>>>> ![图9-7 其他属性简明参考](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-7%20%E5%85%B6%E4%BB%96%E5%B1%9E%E6%80%A7%E7%AE%80%E6%98%8E%E5%8F%82%E8%80%83.png?raw=true)			

------		

		
<h2 id='2'> 二、CSS选择器 </h2>
<h3 id='2.1'>2.1 属性选择器</h3>  

#### 1) 元素属性选择器  
> - \[attr^="val"\]； 属性值开头含有字符串val;
> - \[attr$="$val"\]； 属性值结尾含有字符串val;
> - \[attr*="^val"\]； 属性值含有字符串val;
#### 2) 兄弟选择器  
> - 普通兄弟选择器 <第一个选择器> ~ <第二个选择器>；
> - 拥有相同父元素而且在第一个选择器后面出现的兄弟元素；
 
<h3 id='2.2'>2.2 元素选择器</h3>   

#### 1) 结构性伪类选择器  
>> 根元素选择器：root 用于整个文档根元素<html>的选择；		
>> 子元素选择器
> - :last-chhild 选择父元素最后一个子元素；
> - :only-chhild 选择父元素唯一一个子元素；
> - :only-of-type 选择父元素唯一一个子元素类型；
> - :nth-chhild(n) 选择父元素第n个子元素；
> - :nth-last-chhild(n) 选择父元素倒数第n个子元素；
> - :nth-of-type 选择父元素定义类型的第n个的全部子元素；
> - :nth-last-of-type 选择父元素定义类型的倒数第n个的全部子元素；
>> UI伪类选择器
>>>>>> ![图9-10 UI伪类选择器](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE9-10%20UI%E4%BC%AA%E7%B1%BB%E9%80%89%E6%8B%A9%E5%99%A8.png?raw=true)			

>> 否定选择器 :not(<选择器>) 选择器的否定，即取反；
>> empty选择器 :empty 没有子元素的元素；
>> target选择器 :target URL片段标识符指向的元素；			
		
------		
		
		
<h2 id='3'> 三、边框与背景 </h2>
<h3 id='3.1'>3.1 圆角</h3>  

#### 1) 圆角
> - border-radius: 50% 20px 25% 5em / 25% 15px 25% 5em //四个水平半径/四个垂直半径
>>>>>> ![图10-1 圆角属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-1%20%E5%9C%86%E8%A7%92%E5%B1%9E%E6%80%A7.png?raw=true)		

<h3 id='3.2'>3.2 边框</h3>

#### 1) 用图像作边框
> - border-radius: 50% 20px 25% 5em / 25% 15px 25% 5em //四个水平半径/四个垂直半径
>>>>>> ![图10-2 border-image](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-2%20border-image.png?raw=true)
> - 切分的图像的尺寸
>>>>>> ![图10-3 切分的图像](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-3%20%E5%88%87%E5%88%86%E7%9A%84%E5%9B%BE%E5%83%8F.png?raw=true)
> - 切分的图像的重复方式
>>>>>> ![图10-4 切分的图像的重复方式](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-4%20%E5%88%87%E5%88%86%E7%9A%84%E5%9B%BE%E5%83%8F%E7%9A%84%E9%87%8D%E5%A4%8D%E6%96%B9%E5%BC%8F.png?raw=true)
#### 2) 创建盒子阴影box-shadow
> - 应用于边框的位置，而不是外边界；
>>>>>> ![图10-5 box-shadow属性a](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-5%20box-shadow%E5%B1%9E%E6%80%A7a.png?raw=true)
>>>>>> ![图10-5 box-shadow属性b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-5%20box-shadow%E5%B1%9E%E6%80%A7b.png?raw=true)		

<h3 id='3.3'>3.3 布局</h3>

#### 1) 创建多列布局
>>>>>> ![图10-6 创建多列布局](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-6%20%E5%88%9B%E5%BB%BA%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80.png?raw=true)		

#### 2) 创建弹性布局
>>>>>> ![图10-7 -webkit弹性盒属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-7%20-webkit%E5%BC%B9%E6%80%A7%E7%9B%92%E5%B1%9E%E6%80%A7.png?raw=true)		
>>>>>> ![图10-8 弹性盒布局](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-8%20%E5%BC%B9%E6%80%A7%E7%9B%92%E5%B8%83%E5%B1%80.png?raw=true)		

#### 3) 创建表格布局
> - 优点：自动调整单元格大小，行是由该行中内容最高的单元格决定的，列是由该列内容中最宽的单元格决定的。
>>>>>> ![图10-10 表格布局CSS代码](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-10%20%E8%A1%A8%E6%A0%BC%E5%B8%83%E5%B1%80CSS%E4%BB%A3%E7%A0%81.png?raw=true)		
>>>>>> ![图10-11 表格布局HTML代码](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-11%20%E8%A1%A8%E6%A0%BC%E5%B8%83%E5%B1%80HTML%E4%BB%A3%E7%A0%81.png?raw=true)
>>>>>> ![图10-12 表格布局效果图](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE10-12%20%E8%A1%A8%E6%A0%BC%E5%B8%83%E5%B1%80%E6%95%88%E6%9E%9C%E5%9B%BE.png?raw=true)		
		
------		
		
		
<h2 id='4'> 四、设置文本样式 </h2>
<h3 id='4.1'>4.1 文本属性</h3>  

#### 1) 对齐方式text-justify
> - 使用前提：text-align的值为justify；
> - 该功能主要用于处理不同语言之间的文字留空问题；
>>>>>> ![图11-1 text-justify属性的值](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE11-1%20text-justify%E5%B1%9E%E6%80%A7%E7%9A%84%E5%80%BC.png?raw=true)		
		
#### 2) 文本阴影text-shadow
> - 使用前提：text-align的值为justify；
> - 该功能主要用于处理不同语言之间的文字留空问题；
>>>>>> ![图11-1 text-justify属性的值](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE11-1%20text-justify%E5%B1%9E%E6%80%A7%E7%9A%84%E5%80%BC.png?raw=true)		

#### 3) 使用web字体
> - @font-face；
> - 该功能主要用于处理不同语言之间的文字留空问题；
>>>>>> ![图11-3 web网络字体](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE11-3%20web%E7%BD%91%E7%BB%9C%E5%AD%97%E4%BD%93.png?raw=true)		
		
------		
		
		
<h2 id='5'> 五、过渡，动画和变换 </h2>
<h3 id='5.1'>5.1 使用过渡</h3>  

#### 1) transition
> - 主要用在鼠标悬停：hover伪类元素中变化的细节；
> - 属性排列的顺序依次是property duration timing-function transition-delay;
>>>>>> ![图12-1 transition属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-1%20transition%E5%B1%9E%E6%80%A7.png?raw=true)		
> - 过渡属性的值用逗号隔开，这样过渡效果才会同时出现;
> - 一般在一开始的时候，浏览器是不会应用过渡样式的，只有当元素样式发生变化之后，才会应用。因此可以利用这个特点进行反向过渡，其实就是加了个延迟时间而已，使得原来返回的时候不会那么突兀;
> - 还有一点需要注意的是，并不是所有主流浏览器都支持这个特性，比如IE就不支持了，所以要加前缀；
>>>>>> ![图12-2 transition使用代码b](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-2%20transition%E4%BD%BF%E7%94%A8%E4%BB%A3%E7%A0%81b.png?raw=true)
>>>>>> ![图12-2 transition使用代码](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-2%20transition%E4%BD%BF%E7%94%A8%E4%BB%A3%E7%A0%81.png?raw=true)		
> - transition-timing-function属性，设定变化的曲率，预设的是四个点控制的三次贝塞尔曲线；
>>>>>> ![图12-3 transition调速曲线](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-3%20transition%E8%B0%83%E9%80%9F%E6%9B%B2%E7%BA%BF.png?raw=true)		

#### 2) animation动画
> - 主要用在鼠标悬停：hover伪类元素中变化的细节；
> - 简写属性排列的顺序依次是animation-name animation-duration animation-timing-function animation-delay animation-iteration-count;
>>>>>> ![图12-4 animation属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-4%20animation%E5%B1%9E%E6%80%A7.png?raw=true)		
> - 添加关键帧
>>>>>> ![图12-4 animation属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-4%20animation%E5%B1%9E%E6%80%A7.png?raw=true)			
>>>>>> ![图12-4 animation属性](https://github.com/hblvsjtu/CSS_Study/blob/master/picture/%E5%9B%BE12-4%20animation%E5%B1%9E%E6%80%A7.png?raw=true)	




















