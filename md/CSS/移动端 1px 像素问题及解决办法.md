<!--
 * @Author: tangdaoyong
 * @Date: 2021-06-21 22:23:36
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-06-21 22:24:43
 * @Description: 移动端 1px 像素问题及解决办法
-->
# 移动端 1px 像素问题及解决办法

前言：`在移动端web开发中，UI设计稿中设置边框为1像素，前端在开发过程中如果出现border:1px，测试会发现在某些机型上，1px会比较粗，即是较经典的 移动端1px像素问题。`

作者推荐使用第 6、7 方案。

一、为什么会有1px问题
要处理这个问题，必须先补充一个知识点，就是设备的 物理像素[设备像素] & 逻辑像素[CSS像素]；

物理像素：
移动设备出厂时，不同设备自带的不同像素，也称硬件像素；

逻辑像素：
即css中记录的像素。

在开发中，为什么移动端CSS里面写了1px，实际上看起来比1px粗；了解设备物理像素和逻辑像素的同学应该很容易理解，其实这两个px的含义其实是不一样的，UI设计师要求的1px是指设备的物理像素1px，而CSS里记录的像素是逻辑像素，它们之间存在一个比例关系，通常可以用 javascript 中的 window.devicePixelRatio 来获取，也可以用媒体查询的 -webkit-min-device-pixel-ratio 来获取。当然，比例多少与设备相关。

在手机上border无法达到我们想要的效果。这是因为 devicePixelRatio 特性导致，iPhone的 devicePixelRatio==2，而 border-width: 1px; 描述的是设备独立像素，所以，border被放大到物理像素2px显示，在iPhone上就显得较粗。

二、解决方案
1、 媒体查询利用设备像素比缩放，设置小数像素；

优点：简单，好理解
缺点：兼容性差，目前之余IOS8+才支持，在IOS7及其以下、安卓系统都是显示0px。

IOS8+下已经支持带小数的px值，media query 对应 devicePixelRatio 有个查询值 -webkit-min-device-pixel-ratio；

1.）css可以写成这样：

.border { border: 1px solid #999 }
@media screen and (-webkit-min-device-pixel-ratio: 2) {
    .border { border: 0.5px solid #999 }
}
@media screen and (-webkit-min-device-pixel-ratio: 3) {
    .border { border: 0.333333px solid #999 }
}
2.）js 可以写成这样：
<body><div id="main" style="border: 1px solid #000000;"></div></body>
<script type="text/javascript">
    if (window.devicePixelRatio && devicePixelRatio >= 2) {
        var main = document.getElementById('main');
        main.style.border = '.5px solid #000000';
    }
</script>
二者任选其一；

2、设置 border-image 方案

缺点：需要制作图片，圆角可能出现模糊

.border-image-1px {
    border-width: 1px 0px;
    -webkit-border-image: url("border.png") 2 0 stretch;
    border-image: url("border.png") 2 0 stretch;
}
border-width：指定边框的宽度，可以设定四个值，分别为上右下左border-width: top right bottom left。
border-image：该例意为：距离图片上方2px（属性值上没有单位）裁剪边框图片作为上边框，下方2px裁剪作为下边框。距离左右0像素裁剪图片即没有边框，以拉伸方式展示。
3、background-image 渐变实现

除了使用图片外，当然也能使用纯css来实现，百度糯米团就是采用的这种方案。
缺点：因为每个边框都是线性渐变颜色实现，因此无法实现圆角。

.border {
      background-image:linear-gradient(180deg, red, red 50%, transparent 50%),
      linear-gradient(270deg, red, red 50%, transparent 50%),
      linear-gradient(0deg, red, red 50%, transparent 50%),
      linear-gradient(90deg, red, red 50%, transparent 50%);
      background-size: 100% 1px,1px 100% ,100% 1px, 1px 100%;
      background-repeat: no-repeat;
      background-position: top, right top,  bottom, left top;
      padding: 10px;
}
原理：将原本1个物理像素的边框大小利用线性渐变分割成几个部分（百分比控制），实现小于1像素效果。

linear-gradient：指定线性渐变，接受大于等于3个参数，第一个为渐变旋转角度，第二个开始为渐变的颜色和到哪个位置（百分比）全部变为该颜色，该例子中，第一句就是，渐变方向旋转180度，即从上往下（默认为0度从下往上），从红色开始渐变，到50%的位置还是红色，再渐变为继承父元素颜色。

4、box-shadow

利用阴影也可以实现，优点是没有圆角问题，缺点是颜色不好控制

div {
    -webkit-box-shadow: 0 1px 1px -1px rgba(0, 0, 0, 0.5);
}
box-shadow属性的用法：box-shadow: h-shadow v-shadow [blur] [spread] [color] [inset]
参数分别表示: 水平阴影位置，垂直阴影位置，模糊距离， 阴影尺寸，阴影颜色，将外部阴影改为内部阴影，后四个可选。该例中为何将阴影尺寸设置为负数？设置成-1px 是为了让阴影尺寸稍小于div元素尺寸，这样左右两边的阴影就不会暴露出来，实现只有底部一边有阴影的效果。从而实现分割线效果（单边边框）。

5、viewport + rem

该方案是对上述方案的优化，整体思路就是利用viewport + rem + js 动态的修改页面的缩放比例，实现小于1像素的显示。
缺点：以为缩放涉及全局的rem单位，比较适合新项目，对于老项目可能要涉及到比较多的改动。

在页面初始化时，在头部引入原始默认状态如下：

<meta name="viewport" id="WebViewport" content="initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no">
接下来的任务就是js的动态修改缩放比 以及 实现rem根元素字体大小的设置。

var viewport = document.querySelector("meta[name=viewport]")
if (window.devicePixelRatio == 1) {
    viewport.setAttribute('content', 'width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no')
} 
if (window.devicePixelRatio == 2) {
    viewport.setAttribute('content', 'width=device-width, initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5, user-scalable=no')
} 
if (window.devicePixelRatio == 3) {
    viewport.setAttribute('content', 'width=device-width, initial-scale=0.333333333, maximum-scale=0.333333333, minimum-scale=0.333333333, user-scalable=no')
} 
var docEl = document.documentElement;
var fontsize = 10 * (docEl.clientWidth / 320) + 'px';
docEl.style.fontSize = fontsize;
6、transform: scale(0.5) 方案 - 推荐: 很灵活

1.) 设置height: 1px，根据媒体查询结合transform缩放为相应尺寸。
div {
    height:1px;
    background:#000;
    -webkit-transform: scaleY(0.5);
    -webkit-transform-origin:0 0;
    overflow: hidden;
}
2.) 用::after和::befor,设置border-bottom：1px solid #000,然后在缩放-webkit-transform: scaleY(0.5);可以实现两根边线的需求
div::after{
    content:'';width:100%;
    border-bottom:1px solid #000;
    transform: scaleY(0.5);
}
3.) 用::after设置border：1px solid #000; width:200%; height:200%,然后再缩放scaleY(0.5); 优点可以实现圆角，京东就是这么实现的，缺点是按钮添加active比较麻烦。
.div::after {
    content: '';
    width: 200%;
    height: 200%;
    position: absolute;
    top: 0;
    left: 0;
    border: 1px solid #bfbfbf;
    border-radius: 4px;
    -webkit-transform: scale(0.5,0.5);
    transform: scale(0.5,0.5);
    -webkit-transform-origin: top left;
}
7、媒体查询 + transfrom 对方案1的优化


/* 2倍屏 */
@media only screen and (-webkit-min-device-pixel-ratio: 2.0) {
    .border-bottom::after {
        -webkit-transform: scaleY(0.5);
        transform: scaleY(0.5);
    }
}
/* 3倍屏 */
@media only screen and (-webkit-min-device-pixel-ratio: 3.0) {
    .border-bottom::after {
        -webkit-transform: scaleY(0.33);
        transform: scaleY(0.33);
    }
}