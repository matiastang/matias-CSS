<!--
 * @Author: tangdaoyong
 * @Date: 2021-06-21 22:31:04
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-06-21 22:40:28
 * @Description: Css水平、垂直居中
-->
# Css水平、垂直居中

## 水平居中
```css
<span id="father">
            水平居中-行内元素-父级为行内元素
        </span>
#father{
    width: 500px;
    height: 500px;
    background-color: #0000FF;
    /* 若该元素不为块级元素，则把这个元素当作块级元素处理 */
    display: block;
    text-align: center;
}
```

```css
<!-- 行内元素 -->
<!-- 且父元素为块级元素 -->
<div id="father">
    <span id="son">
        水平居中-行内元素-父级为块元素
    </span>
</div>
#father{
                width: 500px;
                height: 500px;
                background-color: #0000FF;
                text-align: center;
            }
```

```css
<!--如果子元素为块级元素，想要有包裹效果，父级元素必须是块级元素  -->
        <div id="father">
            <div id="son">
                水平居中-块级元素-子元素为定宽
            </div>
        </div>
#father{
    width: 500px;
    height: 500px;
    background-color: #0000FF;
    text-align: center;
}
#son{
                background-color: #FF0000;
                /* 间接的通过左右外边距自动挤出来一个居中的效果 */
                margin: 0 auto;
                width: 200px;
            }
```

```css
<div id="father">
    <div id="son">
        水平居中-块级元素-子元素为不定宽
    </div>
</div>
#father{
    width: 500px;
    height: 500px;
    background-color: #0000FF;
    text-align: center;
}
#son{
    background-color: #FF0000;
    /* 间接的通过左右外边距自动挤出来一个居中的效果 */
    display: inline;
}
```

## 垂直居中

```css
<div id="father">
            <span id="son">
                我是单行的行内元素
            </span>
        </div>
#father{
    width: 500px;
    height: 500px;
    background-color: #0000FF;
}
#son{
    background-color: #DC143C;
    /* 如果只有一行可以取巧，设置文本行高等于父容器的高度 */
    line-height: 500px;
}
```

```css
<div id="father">
            <span id="son">
                我是多行的行内元素
            </span>
        </div>
#father{
                width: 500px;
                height: 500px;
                background-color: #0000FF;
                /* 把父元素当作table中的一个格子 */
                display: table-cell;
                /* 单行也可以使用这种方式 */
                vertical-align: middle;
            }
            #son{
                background-color: #DC143C;
            }
```

```css
```

```css
```

## 水平垂直居中

### 宽度未知

```css
<div class="box">div1</div>
.box{
      position: fixed;
	  top:0;
	  right:0;
	  bottom:0;
	  left:0;
	  margin:auto;
	  background:#d00;
 }
```
```css
<div class="box">div1</div>
.box{
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%, -50%);
  background:#d00;
}
```
```css
<div class="box">
   <div class="content"> </div>
 </div>

.box {
     background: #FF8C00;
      width: 300px;
      height: 300px;
      display: flex;
      justify-content: center;
      align-items: center;
 }
.content {
      background: #F00;
      width: 100px;
      height: 100px;
 }
```
```css
<div class="box">
   <div class="content"> </div>
 </div>
.box {
	   background:#d00;
	   width: 1000px;
	   height: 200px;
	   display:table-cell;
	   vertical-align:middle;
	   text-align:center;
 }
 .content{
		   color: white;
		   background: blue;
		   display:inline-block;
 }
```