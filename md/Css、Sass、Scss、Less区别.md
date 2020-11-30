<!--
 * @Author: tangdaoyong
 * @Date: 2020-11-30 11:24:51
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-11-30 11:27:14
 * @Description: file content
-->
# Css、Sass、Scss、Less区别

CSS（层叠样式表）是一门非程序式语言，入门学习使用非常直观方便，但是对于一些比较复杂或者重用性比较强的项目来说，因为CSS没有变量、函数、SCOPE（作用域），需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用，尤其对于非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码。为了方便前端开发的工作量，出现了sass和less。

SASS（英文全称：Syntactically Awesome Stylesheets）Sass 诞生于 2007 年，使用Ruby 编写，是一种对css的一种扩展提升，增加了规则、变量、混入、选择器、继承等等特性。可以理解为用js的方式去书写，然后编译成css。比如说，sass中可以把反复使用的css属性值定义成变量，然后通过变量名来引用它们，而无需重复书写这一属性值。

LESS（2009年开源的一个项目，受Sass的影响较大，但又使用CSS的语法，让大部分开发者和设计师更容易上手。LESS保留了css的任何功能，同时提供了多种方式能平滑的将写好的代码转化成标准的CSS代码，可以在任何使用随时切换到css的语法进行书写。

传统的css可以直接被html引用，但是sass和less由于使用了类似JavaScript的方式去书写，所以必须要经过编译生成css，而html引用只能引用编译之后的css文件，虽然过程多了一层，但是毕竟sass/less在书写的时候就方便很多，所以在我们使用sass/less之前，只要我们提前设置好，就可以直接生成对应的css文件，而我们只需要关心我们的sass/less文件即可。