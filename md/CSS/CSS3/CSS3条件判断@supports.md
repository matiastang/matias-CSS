<!--
 * @Author: tangdaoyong
 * @Date: 2021-04-27 11:55:29
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-04-27 11:59:02
 * @Description: CSS3条件判断:@supports
-->
# CSS3条件判断:@supports

作用
@supports的作用是用来检测浏览器是否支持某CSS特性，一种渐进增强的实现方式
格式： @supports <条件规则> 
在支持某种css规则的情况下定义样式：
@supports(display: flex) {
  div {
    display: flex
  }
}
支持：或(or)、且(and)、非(not)
not
在不支持某种样式的情况下定义样式：
@supports not (display: flex) {
  div {
    float: left
  }
}
and
在同时支持多个条件的情况下定义样式(可以是3个4个等等)：
@supports (transform: translate3d(10px, 10px, 10px)) and (backface-visibility:hidden) {
  div {
    transform: translate3d(10px, 10px, 10px);
    backface-visibility:hidden
  }
}
or
在支持其中一种样式规则的情况下定义样式(可以是3个4个等等的其中一个)：
@supports (display: -moz-flex) or (display: -ms-flex) {
  div {
    display: -moz-flex;
    display: -ms-flex;
    display: flex
  }
}
## 兼容性
[兼容性](https://www.caniuse.com/)