---
id: 231
title: 借尸招魂——WinXP 12小时抢救实录
date: 2007-04-08T19:55:49+00:00
author: oasisfeng
layout: post
guid: http://blog.oasisfeng.com/2007/04/08/rescue-my-winxp-in-12-hours/
permalink: /2007/04/08/rescue-my-winxp-in-12-hours/
dsq_thread_id:
  - "250427194"
  - "250427194"
categories:
  - Computer
  - Linux
---
前两天实在被nForce3的驱动程序折腾疯了，甚至于走火入魔到自己mod起驱动程序来。话说这nVidia发布的早期驱动确实bug不少，手术过程中一不留神就会遭致“机瘫Win亡”的惨剧。昨晚，我的[新WinXP](http://blog.oasisfeng.com/2006/12/09/mourn-for-my-winxp/)第一次面临了安装以来最严酷的生死考验。

**4月7日·晚9时许**

不记得在哪一次修改完驱动组合后，重启WinXP，硬盘哗啦啦的一路高歌猛进，可输入输出设备却似乎跟不上节奏了。显示器首先鸣警：无信号输入，紧接着发现键盘也不听使唤了，Caps Lock/Num Lock尽皆失灵。初看起来不过是又一次寻常的mod失败，Reset并启动安全模式，收拾残局准备下一次尝试。不过，事情似乎没那么简单，这一次罢工的影响远超出我的预料，Safe Mode倒是能进入，也见到了“和蔼”的欢迎提示，不过该死的键盘和鼠标依旧失灵……

**晚10时**

安全模式的失效意味着WinXP第一道应急防线的彻底沦陷，看来不得不放弃前沿阵地而启用灾难救援预案了。首先想到的是“故障恢复控制台”，Oh, my god! 上次重装WinXP后竟然把这项重要的安全工程给遗漏了，而现在甚至连一张WinXP的安装光盘都找不到（估计是搬家时给漏掉了……）。无奈，只得放弃ERC，出动老将VFloppy for NTFS——这位曾数次助我化险为夷的显赫功臣。正所谓祸不单行，VFloppy竟然向我回禀“NTFS分区挂载失败……”，Shit! 没想到向来无往不利的VFloppy偏偏这个时候失灵了。

就在快要陷入无助之境时，突然忆起上次重装WinXP的时候顺带在第二硬盘上兴建了一个“Area 51”：一套Ghost版的WinXP，平日一直封存起来，只待灾难来临时成为酝酿最后反击的基地。于是，我用颤抖的双手启动了“Area 51”的硬盘引导，片刻之后，我终于不得不承认，现实就是现实，远没有科幻电影中的情节那般激动人心和荡气回肠，因为我看到的只有一个孤冷的提示：“NTLDR missing&#8230;”（弦外音：后备营救系统就好比灭火设施，万万不可放松日常检查！X< ）

**晚10时30分**

很久没有如此背水一战了，在诸般手段尽皆失灵后，我从光盘包里找到了最后的一条救命稻草 —— 一张友人相赠尚未开封的“Ubuntu Linux 64-bit”光盘。用这张“Linux Live CD”引导系统后，终于见到了久违的Linux Desktop。有了这个完整的Linux平台，我总算可以放手实施救援行动了！

**晚10时50分**

检查了一下WinXP的系统文件夹和启动日志，初步判断可能是PCI总线驱动程序的问题，需要替换回官方的版本。但开始着手替换文件时才发现原来Ubuntu自带的NTFS支持是“只读”的，不得以又去网上找了一个支持完全读写功能的ntfs-3g。因为所用Linux是64bit的缘故，没有现成的安装包可用，只好自己手动编译。折腾完这一堆麻烦事儿后，已经累的不行了。

**晚12时30分**

替换了驱动程序文件，依旧没有任何起色。看来今天是解决不了问题了，索性直接关掉电脑睡觉去，说不定早上一觉醒来，发现XP还是那个可爱的XP，眼下的一切不过是一场噩梦罢了~（非典型Matrix臆想症……）

**4月8日·上午8时15分**

被闹铃唤醒后，打开电脑，更衣，洗漱。回头面对屏幕时才想起我的WinXP尚处于生死未卜的境地，原来真是不只是一场噩梦……

既然排除了驱动文件损坏的可能性，那么问题的焦点自然而然的锁定在注册表，看来多半是在安装驱动程序过程中的异常重启对注册表造成了严重创伤。好在我常备有ERUNT……等等，还是先虔诚的祈祷一番再启用它吧，免得又遭遇如VFloppy和“Area 51”同样的厄运。斋戒祝祷完毕后，打开ERUNT，哗，好家伙，竟然悄无声息的吞掉了我1个多G的C盘空间，难怪前些日子发觉C盘剩余空间日渐苍白呢。暂且抛开怨念，眼下毕竟还指望着它救命那。

试着用前一天上午的备份恢复了注册表的System分支（注：硬件驱动相关的问题可以不必恢复Software分支，以减少对系统的负面影响），重启，切换回WinXP引导。数分钟的沉闷之后，终于再一次见到了我那纷乱不堪的桌面。这种感觉，正如古人所云：一日不见，如隔三秋……

**上午9时左右**

重新安装了Remix 11.10的nForce驱动程序后，WinXP终于又回复了往昔的宁静与安详。全然看不出刚刚所经历的这一番生死劫难。

God forgive me~ 再也不玩危险的mod了……