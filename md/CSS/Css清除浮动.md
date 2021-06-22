<!--
 * @Author: tangdaoyong
 * @Date: 2021-06-21 22:05:35
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-06-21 22:23:44
 * @Description: Css清除浮动
-->
# Css清除浮动

清除浮动float (:after方法)
1. 什么时候需要清除浮动？清除浮动有哪些方法？
（1）对元素进行了浮动（float）后，该元素就会脱离文档流，浮动在文档之上。在CSS中，任何元素都可以浮动。浮动元素会生成一个块级框，而不论它本身是何种元素。
float主要流行与页面布局，然后在使用后没有清除浮动，就会后患无穷。
先看实例：
<div class="outer">
<div class="div1">1</div>
<div class="div2">2</div>
<div class="div3">3</div>
</div>
.outer{ border:1px solid #ccc; background:#fc9; color:#fff; margin:50px auto; padding:50px;}
.div1{ width:80px; height:80px; background:#f00; float:left; }
.div2{ width:80px; height:80px; background:blue; float:left; }
.div3{ width:80px; height:80px; background:sienna; float:left; }

 如上图所示，是让1、2、3这三个元素产生浮动所造成的现象。
下面看一下，如果这三个元素不产生浮动，会是什么样子?
.outer{ border:1px solid #ccc; background:#fc9; color:#fff; margin:50px auto; padding:50px;}
.div1{ width:80px; height:80px; background:#f00; /*float:left;*/ }
.div2{ width:80px; height:80px; background:blue;/* float:left; */}
.div3{ width:80px; height:80px; background:sienna;/* float:left;*/ }

如上图所示，当内层的1/2/3元素不浮动，则外层元素的高是会被自动撑开的。
所以当内层元素浮动的时候，就出现以下影响：
背景不能显示；边框不能撑开；margin设置值不能正确显示。
（2）清除浮动
方法一：添加新的元素，应用 **clear:both**;
复制代码
<div class="outer">
<div class="div1">1</div>
<div class="div2">2</div>
<div class="div3">3</div>
<div class="clear"></div>
</div>
复制代码
.outer{ border:1px solid #ccc; background:#fc9; color:#fff; margin:50px auto; padding:50px;}
.div1{ width:80px; height:80px; background:#f00; float:left; }
.div2{ width:80px; height:80px; background:blue; float:left; }
.div3{ width:80px; height:80px; background:sienna; float:left; }
.clear{ clear:both; height:0; line-height:0; font-size:0; }


方法二：父级div定义 overflow:auto;（主意：是父级div，也就是这里的 div.outer）。

<div class="outer over-flow">
<div class="div1">1</div>
<div class="div2">2</div>
<div class="div3">3</div>
</div>
 
.outer{ border:1px solid #ccc; background:#fc9; color:#fff; margin:50px auto; padding:50px;}
.div1{ width:80px; height:80px; background:#f00; float:left; }
.div2{ width:80px; height:80px; background:blue; float:left; }
.div3{ width:80px; height:80px; background:sienna; float:left; }
.over-flow{ overflow:auto; zoom:1;  } //zoom:1;是在处理兼容性问题


原理：使用overflow属性来清除浮动有一点需要注意，overflow属性共有三个属性值：hidden，auto，visible。我们可以使用hidden和auto值来清除浮动，但切记不能使用visible值，如果使用这个值，将无法达到清除浮动效果，其他两个值都可以。
overflow 属性规定当内容溢出元素框时发生的事情。
方法三：据说最高大上的方法，:after方法。（注意：作用于浮动元素的父亲）。
 原理：利用:after和:before来在元素内部插入两个元素块，从而达到清除浮动的效果。其实现原理类似于clear:both方法，只是区别在于:clear在html中插入一个div.clear标签，而outer利用其伪类clear:after在元素内部增加一个类似于div.clear的效果。
.outer { zoom:1; } //为了兼容性，因为ie6/7不能使用伪类，所以加上此行代码。
.outer:after { clear:both;content:'';display:block;width:0;height:0;visibility:hidden; }
 

 其中clear:both;指清除所有浮动；content:' . '；display:block; 对于FF/Chrome/opera/IE8不能缺少，其中content()取值也可以为空。visibility:hidden;的作用是允许浏览器渲染它，但是不显示出来，这样才能实现清除浮动。 
利用伪元素，就可以不再HTML中加入标签。

:after 的意思是再.outer内部的最后加入为元素:after，

首先要显示伪元素，所以display:block，

然后为伪元素加入空内容，以便伪元素中不会有内容显示在页面中，所以， content:""；

其次，为使伪元素不影响页面布局，将伪元素高度设置为0，所以， height:0，

最后，要清除浮动，所以，clear:both。