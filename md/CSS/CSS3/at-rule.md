<!--
 * @Author: tangdaoyong
 * @Date: 2021-04-27 15:03:15
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-04-27 15:03:49
 * @Description: At-rule
-->
# At-rule

[MDN At-rule](https://developer.mozilla.org/zh-CN/docs/Web/CSS/At-rule)

一个 at-rule 是一个CSS 语句，以at符号开头, '@' (U+0040 COMMERCIAL AT), 后跟一个标识符，并包括直到下一个分号的所有内容, ';' (U+003B SEMICOLON), 或下一个CSS块，以先到者为准。

下面是一些 @规则, 由它们的标示符指定, 每种规则都有不同的语法:

@charset, 定义样式表使用的字符集.
@import, 告诉 CSS 引擎引入一个外部样式表.
@namespace, 告诉 CSS 引擎必须考虑XML命名空间。
嵌套@规则, 是嵌套语句的子集,不仅可以作为样式表里的一个语句，也可以用在条件规则组里：
@media, 如果满足媒介查询的条件则条件规则组里的规则生效。
@page, 描述打印文档时布局的变化.
@font-face, 描述将下载的外部的字体。 
@keyframes, 描述 CSS 动画的中间步骤 . 
@supports, 如果满足给定条件则条件规则组里的规则生效。 
@document, 如果文档样式表满足给定条件则条件规则组里的规则生效。 (推延至 CSS Level 4 规范)
条件规则组
就像属性值那样,每条@规则都有不同的语法. 不过一些@规则可以归为一类： 条件规则组. 这些语句使用相同的语法. 它们都嵌套语句，或者是规则或者是@规则。它们都表达： 它们所指的条件 (类型不同) 总等效于 true 或者 false，如果为 true 那么它们里面的语句生效。

条件规则组由CSS Conditionals Level 3 定义:

@media,
@supports,
@document. (推迟至 CSS Level 4 规范)
既然条件规则组可以嵌套语句, 那么嵌套层级不定。