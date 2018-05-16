---
title: 🚨Web开发者需要知道的CSS Tricks
lang: zh-CN
direction: ltl
date: 2018.03.02 20:29:29
tags:
  - CSS
  - CSSTricks
  - Shape
  - Flexbox
  - Layout
  - Effect
  - Animation
  - Experiment
  - Github
---

![图片描述](https://segmentfault.com/img/bV8leu?w=2700&h=1500)

作为一名Web开发者，CSS是必备技能之一，我一直以为自己对CSS的掌握已经够用了，直到读Lea Verou的《CSS揭秘》时，我发现自己充其量就算个会打CS的选手，书中针对我们常见的网页设计难题从不同的角度提出了多种实用又优雅的解决方案，在这里强烈的推荐给每一位从事前端相关的开发者，相信你一定会有所收获。

为了以后可以更爽的复制粘贴，笔者把自己的收获和工作中常用的一些CSS小样式总结成这份文档，一共包含43个CSS的小样式（持续更新…）。文档还有很多不足的地方，还请各位多多指教，如果觉得对你有一点帮助，欢迎大家一起来完善?~

## What's included ##

### 边框与背景 ###

 - [半透明边框][2] 
 - [多重边框][3]
 - [边框内圆角][4]
 - [背景定位][5]
 - [条纹背景][6]
 - [1px 线/边][7]

### 常见形状 ###

 - [圆与椭圆][8]
 - [平行四边形][9]
 - [切角效果][10]
 - [简易饼图][11]
 - [提示气泡][12]
 - [其他多边形][13]

### 视觉效果 ###

 - [常见投影][14]
 - [不规则投影][15]
 - [毛玻璃效果][16]
 - [斑马条纹][17] 
 - [文字特效][18]
 - [环形文字][19]
 - [插入换行][20]
 - [图片对比控件][21]

### 用户体验 ###

 - [选择合适的鼠标光标][22]
 - [扩大可点击区域][23]
 - [自定义复选框][24]
 - [自定义单选框][25]
 - [输入框完美居中][26]
 - [通过阴影弱化背景][27]
 - [通过模糊弱化背景][28]
 - [自定义文字下划线][29]
 - [自定义scroll滚动条][30]

### 结构布局 ###

 - [全背景等宽内容居中][31]
 - [绝对底部][32]
 - [水平垂直居中][33]
 - [圣杯布局][34]
 - [双飞翼布局][35]
 - [类订单布局][36]
 - [Flex 布局][37]

### 动画过渡 ###

 - [弹跳效果][38]
 - [弹性过度][39]
 - [闪烁效果][40]
 - [打字效果][41]
 - [抖动效果][42]
 - [无缝平滑效果][43]
 - [延轨迹平滑效果][44]

文档中代码支持实时调试预览，若有疑问或者建议请直接在文档下方留言，如果你有更有趣更实用的技巧，欢迎PR~

文档：[You-need-to-know-css][45]

Github：[LHammer/You-need-to-know-css][46]

<br><br>

  [2]: https://lhammer.cn/You-need-to-know-css/#/translucent-borders
  [3]: https://lhammer.cn/You-need-to-know-css/#/multiple-borders
  [4]: https://lhammer.cn/You-need-to-know-css/#/inner-rounding
  [5]: https://lhammer.cn/You-need-to-know-css/#/extended-bg-position
  [6]: https://lhammer.cn/You-need-to-know-css/#/stripes-background
  [7]: https://lhammer.cn/You-need-to-know-css/#/one-pixel-line
  [8]: https://lhammer.cn/You-need-to-know-css/#/ellipse
  [9]: https://lhammer.cn/You-need-to-know-css/#/parallelogram
  [10]: https://lhammer.cn/You-need-to-know-css/#/bevel-corners
  [11]: https://lhammer.cn/You-need-to-know-css/#/pie-chart
  [12]: https://lhammer.cn/You-need-to-know-css/#/poptip
  [13]: https://lhammer.cn/You-need-to-know-css/#/polygon
  [14]: https://lhammer.cn/You-need-to-know-css/#/single-projection
  [15]: https://lhammer.cn/You-need-to-know-css/#/irregular-projection
  [16]: https://lhammer.cn/You-need-to-know-css/#/frosted-glass
  [17]: https://lhammer.cn/You-need-to-know-css/#/zebra-stripes
  [18]: https://lhammer.cn/You-need-to-know-css/#/text-effects
  [19]: https://lhammer.cn/You-need-to-know-css/#/circular-text
  [20]: https://lhammer.cn/You-need-to-know-css/#/line-breaks
  [21]: https://lhammer.cn/You-need-to-know-css/#/image-slider
  [22]: https://lhammer.cn/You-need-to-know-css/#/mouse-cursor
  [23]: https://lhammer.cn/You-need-to-know-css/#/extend-hit-area
  [24]: https://lhammer.cn/You-need-to-know-css/#/custom-checkbox
  [25]: https://lhammer.cn/You-need-to-know-css/#/custom-radio
  [26]: https://lhammer.cn/You-need-to-know-css/#/input-align
  [27]: https://lhammer.cn/You-need-to-know-css/#/shadow-weaken-background
  [28]: https://lhammer.cn/You-need-to-know-css/#/blurry-weaken-background
  [29]: https://lhammer.cn/You-need-to-know-css/#/text-underline
  [30]: https://lhammer.cn/You-need-to-know-css/#/scrollbar
  [31]: https://lhammer.cn/You-need-to-know-css/#/fluid-fixed
  [32]: https://lhammer.cn/You-need-to-know-css/#/sticky-footer
  [33]: https://lhammer.cn/You-need-to-know-css/#/centering-known
  [34]: https://lhammer.cn/You-need-to-know-css/#/holy-grail-layout?v=1
  [35]: https://lhammer.cn/You-need-to-know-css/#/double-wing-layout?v=1
  [36]: https://lhammer.cn/You-need-to-know-css/#/class-order-layout
  [37]: https://lhammer.cn/You-need-to-know-css/#/flexbox-layout
  [38]: https://lhammer.cn/You-need-to-know-css/#/bounce
  [39]: https://lhammer.cn/You-need-to-know-css/#/elastic
  [40]: https://lhammer.cn/You-need-to-know-css/#/blink
  [41]: https://lhammer.cn/You-need-to-know-css/#/typing
  [42]: https://lhammer.cn/You-need-to-know-css/#/shake
  [43]: https://lhammer.cn/You-need-to-know-css/#/smooth
  [44]: https://lhammer.cn/You-need-to-know-css/#/circular-smooth
  [45]: https://lhammer.cn/You-need-to-know-css/#/
  [46]: https://github.com/l-hammer/You-need-to-know-css