---
id: 149
title: 一次白屏事故引发的反思——从“被动防守”到“主动抵御”
date: 2006-11-04T00:47:28+00:00
author: oasisfeng
layout: post
guid: http://blog.oasisfeng.com/2006/11/04/learn-from-halt/
permalink: /2006/11/04/learn-from-halt/
dsq_thread_id:
  - "250426574"
  - "250426574"
categories:
  - Development
  - Symbian
---
　　上周，FontRouter2开始了第一次小范围的Alpha测试，主要针对新版本的稳定性和兼容性。

　　起初，一切都进展的很顺利，直到一个朋友在它的N-Gage上升级了新版本后导致了一次不可逆转的灾难——“白屏”！而在这次残酷的事故面前，FontRouter2开发初期所精心设计的启动保护机制显得是如此脆弱和不堪一击……

<!--more-->　　虽然此次事故的教训非常惨痛（严重打击了这位积极支持Alpha测试的好友，并且有损FontRouter2的正面形象 &#8211; -!），但在认真反思了整个启动保护机制的设计后，我走出了“被动防守”思维的误区，重新规划了一个崭新的以“主动抵御”为标志的保护机制！

　　早前“被动防守”的保护机制主要基于以下两个特征：
  
　　**（1）动态跟踪启动各阶段的运行状态，连续3次启动失败后将在后续启动时阻止FontRouter2加载；
  
　　（2）通过在MMC卡根文件夹下创建一个特定名称的文件，可以在系统启动时阻止FontRouter2加载。**

　　表面看起来，以上策略已经算是较为完美了（正如我以前所自诩的），但问题就出在其“被动性”。FontRouter2倒是不再加载了，但真正引起白屏的罪魁祸首却并不是FontRouter2本身，而是一个有“缺陷”的字体文件。就好比你是一个网络管理员，当网络出现故障的时候，你应该做的并不是离开工作岗位，以示自己的清白，而是去找出故障的根源将其消灭。

　　为了体现积极的“主动抵御”，现规划的启动保护机制将具有如下新特征：

　　**检测到启动故障（或是MMC卡根文件夹下的特定文件）后，将禁止系统加载所有ROM以外的字体文件。**这样一来，任何非系统自带的字体文件都会被屏蔽掉，就完全等同于出厂时的字体设置了。

　　从这个问题本身发散开来，一个看似不起眼的启动保护机制，如果用心去做，也能挖掘出一些潜在的用户价值。例如，为了抵御除字体外其它未知软件因素引起的白屏，可以引入在必要时“自动格式化C盘”的机制（当然，这是需要严格的策略加以谨慎保护的），更体贴一点，还可以在格式化前自动将“联系人”、“个人事务”等重要信息转移到安全的地方（如MMC卡）。这样一来，即使手机出现意外无法启动的情况，也能保护重要数据不致因维修而丢失。