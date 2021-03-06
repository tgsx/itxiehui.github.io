---
title: Web前端的发展及应用
date: 2016-04-30 13:29:51
tags: [编程,Web,前端]
---

###  **一、简单明了的早期时代**

这个也称为web 1.0时代，非常适合创业型不分前后端，经常3-5个人就可以搞定所有的开发，基本上是服务端给什么，浏览器就展现什么（由web server层控制）

<!--more-->

![](http://ww4.sinaimg.cn/mw690/006rmJyDgw1f3eo1nk8alj30mw0egdgr.jpg)

**好处**

简单明了，本地起一个Tomcat或者Apache 就能开发了，只要业务不太复杂就都还好。

**弊端**

但业务太多了，变得复杂了，server越来越多，开发人员增多时，就会遇到以下的一些问题

1. **Service 越来越多，调用关系变复杂，前端搭建本地环境不再是一件简单的事。**
2. **Jsp 等代码的可维护性越来越差。**

jsp 非常强大，可以内嵌Java代码。这种强大使得前后端的职责不清晰，jsp就变成了一个灰色地带，经常会出现为了赶项目等各种紧急的需求，会在jsp里糅杂了大量业务代码，这种积攒到一定程度，往往会打来大量的维护成本。

![](http://ww1.sinaimg.cn/mw690/006rmJyDgw1f3eo1p7t0zj30n60eqq46.jpg)

###  **二．后端为主的MVC时代**

为了降低复杂度，以后端为出发点，有了web server层的框架升级，这就是后端的MVC时代。

![](http://ww4.sinaimg.cn/mw690/006rmJyDgw1f3eo1qgdqtj30n70eejsc.jpg)

从上面的图可以看出来代码的维护性得到了明显的好转，MVC是个非常好的协作模式，从框架层面让开发者懂得什么是代码，应该写在什么地方，这使得模板里写不了Java代码，但功能看起来变弱了，正是这种限制使得了前后端分工更清晰，但任然会有问题存在：

#### **1. 前端开发重度依赖开发环境**

这种框架下，前后协作有两种模式：**一种是前端写demo，写好后让后端去套模板。**（淘宝）

好处：很明显，demo可以本地开发，很高效，不足是还要后端套模板，有可能会套错，而且还要前端确定，来回沟通调整的成本较大。

**另一种协作的模式是前端负责浏览器的所有开发和服务器端的view层模板开发，支付宝是这种模式。**

好处：UI相关的代码都是前端去写就好，后端不用太关注，

弊端：前端开发严重绑定后端的环境，环境成为影响前端开发效率的重要因素。

#### **2. 前后端职责依旧纠缠不清**

Velocity模板还是挺强大的，变量 逻辑，宏等特性，依旧可以通过拿到上下文变量来实现各种业务逻辑。这样只要前端弱势一点，往往会被后端要求拿到的上下层写出不少业务代码，还有一个灰色地带是controller，页面路由等功能应该前端最关注的，但是由后端来实现了。

### **三  Ajax 的SPA时代**

2005年Ajax正式提出，加上CDN开始大量用静态资源储存，于是就出现了javascriptd的SPA时代。

![](http://ww3.sinaimg.cn/mw690/006rmJyDgw1f3eo1r2j2hj30ms0eldh5.jpg)

特点：这种模式下，前后端的分工就非常清晰了，前后端的关键协作点是Ajax接口，看起开很好，但回头看看，这与jsp时代区别不大。复杂程度从服务端的jsp里移到了浏览器得到JavaScript，浏览器变得复杂，类似Spring MVC ，这个时代开始出现浏览器端的分层架构：

![](http://ww2.sinaimg.cn/mw690/006rmJyDgw1f3eo1qucepj30n70ekmy6.jpg)

对于SPA，有几个重要的挑战

**1. 前后端接口的约定：**

如果后端的接口一趟糊涂，后端的业务模型不够稳定，那这样前端开发会很痛苦。

**2. 前端开发的复杂度调控：**

SPA应用大多数以功能交互型为主，JavaScript代码过十万行很正常。大量js代码的组织与view层的绑定等，都不是容易的事情。

### **四．前端为主的MV\*时代**

为了降低前端开发的复杂度，例如：

![](http://ww1.sinaimg.cn/mw690/006rmJyDgw1f3eo1rzkr4j30mr0eqq41.jpg)

好处：

**1. 前后端职责很清晰**

前端在浏览器端工作，后端在服务端工作。

**1. 前端开发的复杂问题可控**

前端代码很重，但合理的分层，让前端代码各司其职。

**3. 部署相对独立**

产品可以快速改进。

不足：

**1. 代码不能复用，例如后端依旧需要对数据做出各种校验。**

**2. SPA不能满足所有需求，依旧存在大量页面应用。**

###  **五．Node带来的全栈时代**

前端为主的MV\*模式解决了很多很多问题，但依旧不足，然后Node.js兴起了，JavaScript开始有能力运行在服务端，这就研发了一种新的模式：

![](http://ww2.sinaimg.cn/mw690/006rmJyDgw1f3eo1s5wuzj30gi0h040e.jpg)

在这种情况下，前后端职责很清晰。对前端来说，两个UI层各司其职：

1. **Front-end UIlayer 处理浏览器层的展现逻辑。**通过CSS渲染样式，通过JavaScript添加交互功能，HTML的生成也可以放在这层，具体看应用场景。

2. **Back-end UI layre处理路由，模板，数据获取等。**通过路由，前端可以自主把控URL Design，这样无论是单页面还是多页面应用，前端都可以自由调控，后端也可以摆脱对展现的强关注，可以专心于业务逻辑的开发。

与JSP比较，全栈模式看起来是一种回归，也的确是一种原始的开发模式的回归，不过是一种螺旋上升的回归。

Node全栈时代面临的挑战：

1. 需要前端对服务端编程有更进一步的认识
2. Node层与Java层的高效通信。Node模式下，都在服务器端
3. 对部署，运维层面的熟练，需要更多知识点和实操经验。


----------------

><span style="font-size:12px">本文标题: <a href="{{ permalink }}">{{ title }}</a>
文章作者: <a href="http://itxiehui.github.io/">徐伟生</a>  
许可协议: <img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png" /><a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">©署名-非商用-相同方式共享 4.0</a></span>