<!--
 * @Author: tangdaoyong
 * @Date: 2021-04-27 14:48:15
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-04-27 15:00:52
 * @Description: CSS Houdini
-->
# CSS Houdini

[MDN CSS Houdini](https://developer.mozilla.org/en-US/docs/Web/Houdini)

## 介绍

Houdini是一组底层API，它们公开了CSS引擎的各个部分，从而使开发人员能够通过加入浏览器渲染引擎的样式和布局过程来扩展CSS。Houdini是一组API，它们使开发人员可以直接访问CSS对象模型（CSSOM），使开发人员可以编写浏览器可以解析为CSS的代码，从而创建新的CSS功能，而不必等待它们在浏览器中本地实现。

Houdini API
在下面，您可以找到指向涵盖Houdini框架下的API的主要参考页面的链接，以及指向指南的链接，这些指南可以在您需要学习如何使用它们的指南时为您提供帮助。

CSS解析器API
一个API，它更直接地公开CSS解析器，用于将任意类似CSS的语言解析为温和类型的表示形式。

目前尚未为此API编写任何指南或参考。
CSS属性和值API 
定义用于注册新CSS属性的API。使用此API注册的属性具有解析语法，该语法定义了类型，继承行为和初始值。

CSS属性和值API参考
CSS属性和值API指南
CSS类型的OM
将CSSOM值字符串转换为有意义的类型的JavaScript表示然后再转换可能会导致相当大的性能开销。CSS类型的OM将CSS值公开为类型化的JavaScript对象，以允许其执行性能。

CSS Typed OM参考
CSS Typed OM指南
CSS布局API 
该API旨在提高CSS的可扩展性，使开发人员能够编写自己的布局算法，例如砌筑或线捕捉。它尚未本地可用。

目前尚未为此API编写任何指南或参考。

CSS绘画API
为提高CSS的可扩展性而开发-允许开发人员编写JavaScript函数，这些函数可以通过paint()CSS函数直接绘制到元素的背景，边框或内容中。

CSS Painting API参考
CSS Painting API指南

工作台 
一个API，用于在渲染管道的各个阶段中运行脚本，而与主要的JavaScript执行环境无关。Worklets从概念上讲类似于Web Workers，并由呈现引擎调用并扩展呈现引擎。