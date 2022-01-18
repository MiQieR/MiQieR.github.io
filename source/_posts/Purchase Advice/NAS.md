---
title: '搭建NAS和家庭流媒体平台'
date: '2021-10-26 15:27:00'
update: '2021-10-26 17:45:00'
description: '综合价格、容量、噪音、使用体验和性能的最佳选择'
keywords: '数码产品'
categories: '选购建议'
top_img: https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/1a67f64ef5b4b6601bac685276a28be234a4ea13.jpg
cover: https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/1a67f64ef5b4b6601bac685276a28be234a4ea13.jpg
---



## 前言

**对大多数人而言，NAS没有什么意义**，电影电视剧可以看完就删，甚至在网盘里就可以看，连下载都不需要。但一定有人像我一样，网盘视频资源被封且不愿忍受网盘的龟速，想要收藏4K HEVC HDR DTS5.1电影，又买不起8T SSD，并且受不了3.5寸机械硬盘的噪音，那么，搭建自己的NAS，就是最佳的选择

----



## NAS硬件选择

关于NAS的硬件，我真的反复对比了很久，以下是我的一点观点，如有错误，欢迎指正：

1. Intel 1155平台太过古老，且主板难买
2. AMD推土机平台对黑群晖的兼容性不好（未来我可能将尝试黑群晖），而且性能太差
3. Intel 1151平台、AMD锐龙平台太贵
4. J1900、J4105、J3455功耗很棒，但是扩展性较差，带有4个SATA或可以转接为4个SATA的主板不便宜且难找，J1900的指令集还不完善，不能很好的运行虚拟机
5. 树莓派/智能路由：性能和扩展性就更差了，如果你有，可以试着玩玩，简单体验一下，但不建议长期使用，对主机和硬盘都是一种伤害

- **我手上有2条DDR3内存和一个PM961 128G M.2固态硬盘**，我希望尽可能利用上它们

- 星际蜗牛C款机箱是可以放下19x17cm的主板的，但是需要锯掉机箱的一小块，我不想锯机箱

最终，我选择了Intel 1150平台，即H81/B85主板，配合赛扬T后缀CPU，核显支持Intel QuickSync硬解码，同时功耗不高



以下是我选择的最终配置：

主板：[华擎B85M-itx](https://www.asrock.com/mb/Intel/B85M-ITX/index.cn.asp?cat=Download&os=BIOS)（4xSATA3+eSATA，HDMI，千兆网卡，PCIe3.0x16，4x USB3.1Gen1，扩展能力拉满）

CPU：Intel [G3240T](https://www.cpu-monkey.com/en/cpu-intel_pentium_g3240t) @2.7Ghz （2C2T，TDP 35W，CPU性能介于[J3455](https://www.cpu-monkey.com/en/cpu-intel_celeron_j3455)和[J4105](https://www.cpu-monkey.com/en/cpu-intel_celeron_j4105)之间，核显性能比二者稍强，但比二者硬解码器少）

内存：DDR3 4G @1600Mhz + DDR3 2G @1333Mhz （从家里报废的775平台电脑上拔下来的）

机箱：星际蜗牛C款，带200W 1U电源，有一个全高PCIe槽位

硬盘：光威猛将120G SATA3固态硬盘（选这个是因为主板无法从M.2硬盘启动，我也懒得刷BIOS）

​			PM961 128G M.2固态硬盘，配合淘宝10元包邮的PCIe转M.2转接板

​			日立 3TB 7200转 64M 3.5寸机械硬盘（翻新清零盘，主要是便宜）

散热：AVC 28cm 铜芯散热器，风扇是4pin带温控的

（路由器/交换机：ASUS RT- AC88U）

> 机箱自带的90x25mm风扇和1U电源的小风扇太吵了，等我有时间必给他俩换了

最终总价格来到了843r（本来想把价格控制在600左右的，现在我的钱包在滴血）

----



## 系统的选择

我不希望使用我的其他电脑难以读写的文件系统，加上懒得折腾黑群晖和Docker，我有iCloud也不需要群晖的备份功能，因此我最终选择了Windows系统

具体的系统版本是**Windows 10 LTSC x64** ｜ [下载LTSC](https://msdn.itellyou.cn/)

因为觉得Windows Server没什么必要；LTSC比普通Windows 10精简掉了很多功能，内存占用降低了至少500MB，且容易激活（KMS），更新也少，系统稳定，还有家庭版Win10没有的远程桌面功能

以后有时间也许会尝试虚拟机跑黑群晖和Docker，届时再更新

----



## 搭建家庭流媒体平台

> 本来是想选择JellyFin的，奈何JellyFIn的硬解码实在是弱鸡，界面也不好看，甚至一度大量错误识别我的电影和电视剧，出于无奈，最终选择了Emby

### 效果展示：

![Emby主页](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/3c9fd36700b086f8d047cd7e012d6605b860b664.png)

![Emby电影](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/3228932d1aba4e024a24b1a1d453bb9a3f63d025.png)

![Emby电视剧](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/cc63fa76d37070221380787932dca65a41eb6d53.png)



### Emby Server

我使用的Emby Server版本：[官方原版](https://emby.media/windows-server.html)

安装Emby豆瓣刮削器：[百度贴吧教程](https://tieba.baidu.com/p/6555598271) ｜ [Github下载](https://github.com/AlifeLine/Emby.Plugins.Douban)

添加hosts：`13.224.161.90 api.themoviedb.org`



### 削刮影片信息

使用tinyMediaManager（tMM）刮削影片信息

> 注意，最新版本tMM对一些功能添加了限制，需要会员才能使用，所以这里建议使用老版本：3.1.7

[下载tMM 3.1.7](https://wwr.lanzoui.com/iPzvsvsx7kj) ｜ [tMM安装及使用教程](https://www.bilibili.com/video/BV1x541147i2)



### 客户端和App

因为客户端/App是可以调用Emby Server的硬解码的，而没有购买Emby Premiere的话，是无法使用App、硬解码、和下载功能的

[Emby使用全攻略](https://howtogayemby.911997.xyz/) ｜ 这是为Emby公益服使用者提供的教程，因为我们自己搭建了Emby Server，因此只需要看该网页“在各种设备上使用”的教程

通过我的使用，这里推荐：

iOS：使用 Shadowrocket 破解Emby App （不推荐使用AltStore+EmbyPro.ipa）

> **注意，这里只是使用了Shadowrocket的脚本功能，虽调用了VPN功能，但并未涉及翻墙（仅使用VPN API）。这里不推荐使用任何翻墙功能或软件，请遵守相关的法律法规，践行社会主义核心价值观**

Android：[修改版官方客户端](https://github.com/rartv/EmbyPublic/releases/download/0.0.6/Emby.for.Android.3.1.73.Cracked.apk)

Windows 和 macOS待测试对比

----



## Windows远程桌面

使用Windows远程桌面可以更方便地管理NAS ｜ [详情](https://support.microsoft.com/zh-cn/windows/%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2-5fe128d5-8fb1-7a23-3b8a-41e636865e8c)

> 注意，**要为NAS在路由器上设置一个固定IP**，在华硕/梅林固件路由器上这样设置：路由管理界面 - 内部网络(LAN) - DHCP服务器 - 启用手动指定功能 - 选择NAS并添加 - 应用本页面设置

----



## 将NAS的硬盘映射到其他电脑

除了可以更方便且低延迟地管理NAS文件（Windows远程桌面有肉眼可见的延迟），还能便于上传下载

[视频教程（在视频20分36秒开始）](https://www.bilibili.com/video/BV1dy4y1C7we)

----



## 后记

从几个月之前，我就在筹划组装自己的NAS了，如今终于完成了，终于可以舒服地看片了，嘿嘿😁

有时间再补图吧