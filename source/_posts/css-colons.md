---
title: 🙌CSS中一个冒号和两个冒号有什么区别
lang: zh-CN
direction: rtl
date: 2017.06.12 20:29:29
tags:
  - CSS
---

在平时工作中用到伪类选择器的时候一个冒号和两个冒号貌似都是可以的，所以两者到底有什么区别呢，我们先来看下`W3C`关于`CSS3`选择器的规范中有一段描述： 

>　　A pseudo-element is made of two colons (::) followed by the name of the pseudo-element. 
　　This :: notation is introduced by the current document in order to establish a discrimination between pseudo-classes and pseudo-elements. For compatibility with existing style sheets, user agents must also accept the previous one-colon notation for pseudo-elements introduced in CSS levels 1 and 2 (namely, :first-line, :first-letter, :before and :after). This compatibility is not allowed for the new pseudo-elements introduced in CSS level 3. 

简单翻译一下，大意就是，伪元素由双冒号和伪元素名称组成。双冒号是在当前规范中引入的，用于区分伪类和伪元素。但是伪类兼容现存样式，浏览器需要同时支持旧的伪类，比如  `:first-line`、`:first-letter`、`:before`、`:after`等。那么问题来了，什么是伪类？什么是伪元素？

`w3c`对两者的定义：
> CSS 伪类用于向某些选择器添加特殊的效果。
CSS 伪元素用于将特殊的效果添加到某些选择器。

可以明确两点，第一两者都与选择器相关，第二就是添加一些“特殊”的效果。这里特殊指的是两者描述了其他 css 无法描述的东西。伪类可以独立于文档的元素来分配样式，且可以分配给任何元素，逻辑上和功能上类类似，但是其是预定义的、不存在于文档树中且表达方式也不同，所以叫伪类。伪元素所控制的内容和一个元素控制的内容一样，但是伪元素不存在于文档树中，不是真正的元素，所以叫伪元素。

### 伪类：
`:first-child`, `:link:`, `vistited`, `:hover:`, `active:focus`, `:lang`, `:not(s)`, `：root`等...

### 伪元素：
`:first-line`, `:first-letter`, `:before`, `:after`, `:placeholder`, `:selection`

***

⚠️ 如果你的网站只需要兼容webkit、firefox、opera等浏览器，建议对于伪元素采用双冒号的写法，如果不得不兼容IE浏览器，还是用CSS2的单冒号写法比较安全。如果自己不确定的话可以针对某些需要兼容的属性有两种属性。

### 伪类和伪元素的区别：

#### 伪类

伪类选择元素基于的是当前元素处于的状态，或者说元素当前所具有的特性，而不是元素的id、class、属性等静态的标志。由于状态是动态变化的，所以一个元素达到一个特定状时，它可能得到一个伪类的样式；当状态改变时，它又会失去这个样式。由此可以看出，它的功能和class有些类似，但它是基于文档之外的抽象，所以叫伪类。

**E:link** 
> 伪类将应用于未被访问过的链接，与:visited互斥。

**E:hover** 
> 伪类将应用于有鼠标指针悬停于其上的元素。

**E:active** 
> 伪类将应用于被激活的元素，如被点击的链接、被按下的按钮等。

**E:visited** 
> 伪类将应用于已经被访问过的链接，与:link互斥。

**E:focus** 
> 伪类将应用于拥有键盘输入焦点的元素。

**E:first-child** 
> 伪类将应用于元素在页面中第一次出现的时候。

**E:lang** 
> 伪类将应用于元素带有指定lang的情况。

e.g.

```html
<p lang="zh">中国</p>
<p lang="en">english</p>
```
```css
p:lang(zh-cmn-Hans) {
  color: #f00;
}
p:lang(en) {
  color: #090;
}
```

**E:not(s)**
> 匹配不含有s选择符的元素E。

```css
/* 列表中除最后一项外的所有列表项加一条底边线 */
.demo li:not(:last-child) {
  border-bottom: 1px solid #ddd;
}
```

**E:root**
> 匹配E元素在文档的根元素。

```css
/* 非IE文本将为black，IE9及以上为purple，IE8为yellow，IE7为blue，IE6为red */
.test {
  color: black;
  color: yellow\0;
  *color: blue;
  _color: red;
}
html:root .test {
  color: purple\0;
}
```

*** 

#### 伪元素
与伪类针对特殊状态的元素不同的是，伪元素是对元素中的特定内容进行操作，它所操作的层次比伪类更深了一层，也因此它的动态性比伪类要低得多。实际上，设计伪元素的目的就是去选取诸如元素内容第一个字（母）、第一行，选取某些内容前面或后面这种普通的选择器无法完成的工作。它控制的内容实际上和元素是相同的，但是它本身只是基于元素的抽象，并不存在于文档中，所以叫伪元素。

**E::first-letter**
> 伪元素的样式将应用于元素文本的第一个字（母）。

**E::first-line**
> 伪元素的样式将应用于元素文本的第一行。

**E::before**
> 在元素内容的最前面添加新内容。

**E::after**
> 在元素内容的最后面添加新内容。

e.g.

```css
/* 清楚浮动 */
.clearfix::before, .clearfix::after {
  content:"";
  display:table;
}
.clearfix::after {
  clear:both;
}
.clearfix {
  zoom:1; /* For IE 6/7 (trigger hasLayout) */
}
```

**E::placeholder**
> 用于控制表单输入框占位符的外观，它允许开发者/设计师改变文字占位符的样式，默认的文字占位符为浅灰色。

e.g.

```css
input::-webkit-input-placeholder {
  color: #999;
}
input:-ms-input-placeholder { /* IE10+ */
  color: #999;
}
input:-moz-placeholder { /* Firefox4-18 */
  color: #999;
}
input::-moz-placeholder { /* Firefox19+ */
  color: #999;
}
```

**E::selection**
> 定义元素被选择时的background-color，color及text-shadow(IE11尚不支持定义该属性)。

e.g.

```css
/* 将选中字体的颜色设置为#f00，背景颜色设置为#000 */
p::-moz-selection{background:#000;color:#f00;}
p::selection{background:#000;color:#f00;}
```