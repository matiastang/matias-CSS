<!--
 * @Author: tangdaoyong
 * @Date: 2021-04-27 14:43:39
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-04-27 15:13:38
 * @Description: @property
-->
# @property

[MDN @property](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@property)
[@property学习](https://mp.weixin.qq.com/s/-HWRarbEo6N6CBQNj7k6jA)

## 介绍

@property CSS at-rule是CSS Houdini API的一部分, 它允许开发者显式地定义他们的css自定义属性, 允许进行属性类型检查、设定默认值以及定义该自定义属性是否可以被继承。

@property 规则提供了一个直接在样式表中注册自定义属性的方式，而无需运行任何JS代码。有效的 @property 规则会注册一个自定义属性, 就像 CSS.registerProperty (en-US) 函数被使用同样的参数调用了一样。

## @charset
@color-profile
@counter-style
@document
@font-face
@font-feature-values
@import
@keyframes
@media
@namespace
@page
@property
@supports
@viewport