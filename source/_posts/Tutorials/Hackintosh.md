---
title: '完美黑苹果从入门到购买白苹果'
date: '2021-9-20 10:01:00'
update: '2021-10-28 19:59:00'
description: '以XPS9360完美黑苹果为例，教程同样适用于其他电脑'
keywords: '黑苹果'
categories: '教程'
top_img: https://i.loli.net/2021/09/24/gm1PSCnUrHtAb2u.jpg
cover: https://i.loli.net/2021/09/24/gm1PSCnUrHtAb2u.jpg
---

## 为什么选择黑苹果？
### 为什么选择macOS？
这个问题，可以转化为，macOS有什么Windows10做不到的功能？
1. 苹果可以套牢用户的大杀器————iCloud。iCloud可以在你的iPhone、iPad之间同步几乎所有你跨设备操作时的数据：你的所有照片和视频、便签、通讯录、短信、提醒事项/日程、iCloud云盘中的文件、甚至所有你记不住的那些账号和密码（iCloud钥匙串）... 除此之外，iCloud还能让你可以跨平台复制粘贴文字、接听电话和FaceTime、让你的iPad变身无线扩展屏（随航功能），将iPhone/iPad上的画面或音乐投送到Mac（macOS 12）。 我认为，相比于华为那种将手机投屏到电脑，实现上述功能的做法，iCloud更加简洁
2. 可以使用一些苹果自有的专业软件：Final Cut Pro X——视频剪辑软件，可以使用很多仅限FCPX的插件；Logic Pro——强大的音乐制作软件。
3. iOS相比Android，用户付费率更高，App被盗版的可能性也更低，因此对小开发者而言，通常为iOS开发App的收入要高过为Android开发。而iOS开发，Xcode是必须的IDE，Xcode只能运行在macOS上。对我自己来说，Kite、Dash等工具可以辅助我编程，Xcode可以实时报错，简单的代码错误可以一键自动修改
4. 对于有其他苹果设备的用户而言，相比Win10，macOS对[AltStore](https://harlylee.github.io/2021/08/26/Tutorials/AltStore/)和AirPods等的兼容性更好

### 为什么选择黑苹果而不是白苹果？
> 黑苹果：指在非苹果生成并销售的设备上运行的macOS
> 白苹果：苹果销售的Mac电脑

我可以非常肯定地说，同价位黑苹果的性能远超白苹果，同时扩展性更强。
参考以下例子：

- MacBook Pro13 2015，8G内存+256G硬盘，CPU为i5-5257U（双核四线程，主频2.7Ghz，最高睿频3.1Ghz，3MB三级缓存），显卡为Iris Graphics 6100；参考跑分：Cinebench R20单核277分，多核706分

- 同价位我的XPS13 9360，8G内存+256G硬盘，CPU为i5-8250U（四核八线程，主频1.6Ghz，单核睿频最高3.4Ghz，全核睿频最高2.3Ghz，6MB三级缓存），显卡为UHD620；参考跑分：Cinebench R20单核348分，多核1509分

----


## 硬件的选择

### 我的选择
笔记本电脑：戴尔Dell XPS13 9360
CPU：intel i5-8250U
显卡：intel UHD620
内存：LPDDR3 8GB @1867Mhz
SSD：KIOXIA RC10 512GB
网卡：DW1560
声卡：alc256
显示器：13.3inch 1080P @60hz
扩展坞：Dell DA300（使用HDMI接口会发热严重，使用DP则不会）
BIOS版本：2.16.0

BIOS设置：
Disable C-States（如果你更换了硬盘，开启该选项可能导致win10卡死，[点此查看详情](https://blog.csdn.net/lzrreach/article/details/76359388/)）
Sata: AHCI
Disable Secure Boot
Enable VT
**Disable VT-D**
Disable SD card reader (可选，关闭节省0.5w功耗)

【2022/01/12更新：我换用了intel AX200网卡，具体将在网卡一节中讲到】




### 笔记本电脑
对英特尔CPU的型号而言，几乎所有使用6代酷睿至10代的型号都可以黑苹果（11代和12代不支持），**重点是能否寻找到能用的EFI**，通常热门型号好找一些。AMD锐龙APU的笔记本无法黑苹果，AMD笔记本独显可以识别但<u>无法使用</u>（比如惠普暗影精灵2Pro的6700HQ+RX460）。最好选择网卡可以更换的型号；部分无法更换的板载英特尔网卡可以驱动，但驱动并不像博通网卡一样完美。
NVIDIA独显在macOS 10.13.6以后的版本无法驱动。

### 台式电脑
建议在购买之前寻找有较完美EFI的主板型号，同样是热门型号容易找，有一个例外是部分华擎主板有很好的兼容性。12代酷睿CPU可以驱动，但<u>无法驱动小核心和核显</u>；AMD CPU可以冒仿型号后驱动，但可能有一些bug。虽然有一些NVIDIA显卡免驱，但显卡推荐选择AMD显卡，但要注意蓝宝石XFX等品牌的不刷BIOS无法驱动。如果是新上市的AMD显卡，关注最近几个版本的macOS更新日志即可查得从哪个版本开始支持该显卡。

[显卡推荐列表](https://win2mac.top/dc466dac.html)



### 网卡的选择

如果你是台式机，其实有线网卡就已经可以满足上网的需求了，而且大量有线网卡都可以被驱动
但是无线网卡除了WiFi功能外，通常还带有蓝牙功能，而如果你需要苹果设备之间的交互，比如使用隔空投送、接力、随航等，那就必须使用免驱或完美驱动的无线网卡。

**关于无线网卡的选购，可以看看这篇文章：**[黑苹果免驱无线网卡购买指南](http://k61.org/a7f5fe4a.html)
很多英特尔网卡可以被驱动，感谢[OpenIntelWireless](https://openintelwireless.github.io/)，网速可能能秒杀上面提到的博通网卡，几乎完美兼容，很多网卡焊死在主板上的笔记本可以不用USB网卡了

![一些常见网卡的驱动方法](https://images.weserv.nl/?url=https://article.biliimg.com/bfs/article/7900ae0c4f0d84cd4cc9485521ad2aa0270952a2.jpg)



【2022-01-12更新】

- 一些英特尔网卡可以靠AirportItlwm.kext或itlwm.kext驱动WiFi（需要定制USB驱动），推荐使用前者，后者需要搭配HeliPort使用

​	[intel网卡完整兼容列表](https://openintelwireless.github.io/itlwm/Compat.html) ｜ [下载AirportItlwm.kext和itlwm.kext](https://github.com/OpenIntelWireless/itlwm) | [下载HeliPort](https://github.com/OpenIntelWireless/HeliPort)

- macOS12 Monterey驱动蓝牙方法：

​	博通非苹果原装网卡，比如DW1560/BCM94352Z：更新Lilu至最新版本，添加[BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM)并禁用或删除BrcmBluetoothInjector.kext

​	英特尔网卡，比如AX200：更新Lilu至最新版本，添加[BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM)并禁用或删除 IntelBluetoothInjector.kext



#### 我的一些网卡使用体验

> 从开始折腾黑苹果到现在，我已经使用了2款intel网卡，2款博通网卡，我将在这里讲一下我使用它们的体验

1. DW1560（BCM94352Z）：分戴尔版、联想版、普通版等多个版本，一定要在选购前与卖家沟通好，区别貌似是戴尔版/联想版需要屏蔽某些针脚；kext中需要添加AirportBrcmFixup.kext，BrcmBluetoothInjector.kext，BrcmFirmwareData.kext，BrcmPatchRAM3.kext（根据系统版本选择BrcmPatchRAM1/2/3.kext）；所有白苹果和蓝牙相关的功能都可以正常使用，网卡的网速较差，蓝牙连接耳机信号很差，Windows下还会偶尔搜不到WiFi，需要在设备管理器中禁用再启用网卡
2. BCM943602CS：白苹果拆机网卡，需要搭配转接线/转接板使用（笔记本很难塞下，塞下可能后盖就无法完全合上了）；三天线，中间的是蓝牙天线，需要买一条额外的天线，笔记本自带的天线连两边的接口以保证WiFi信号的可用性；kext中无需添加任何东西，如果WiFi的连接速率过低或者无法识别到SSID或者国家代码是US，需要添加AirPortBrcmFixup.kext，并添加启动参数`brcmfx-country=#a`；Windows下信号和网速都很差，蓝牙更是几乎无法使用，而且需要安装驱动
3. intel 7265AC：添加AirportItlwm.kext，IntelBluetoothInjector.kext，IntelBluetoothFirmware.kext后可以驱动蓝牙和WiFi，macOS下网速较前两个网卡并没有太大提升，但Windows下的稳定性和速度有很大的提升；无法使用隔空投送、无线随航
4. intel AX200：在经过这一系列尝试后，我的最终选择。macOS Monterey添加AirportItlwm.kext，BlueToolFixup.kext，IntelBluetoothFirmware.kext后可以驱动蓝牙和WiFi，无法使用隔空投送、无线随航，但网速和蓝牙信号非常棒，Windows下的体验也很好；是这里面唯一的WiFi6+蓝牙5.1网卡，而且价格比免驱网卡便宜很多；推荐加10元升级AX210，支持WiFi6e，蓝牙5.2，而且最新版本的AirportItlwm.kext已经支持了AX210



----


## EFI的寻找

### OpenCore
因为我可以说只用过OC，所以这里只讨论它，而非Clover；推荐大家都使用OC

#### 升级OpenCore
> 如果不更新MacOS，一般不建议更新OC

更新方法请参考：https://www.bilibili.com/video/BV13U4y177QV
OC下载地址：https://github.com/acidanthera/OpenCorePkg/releases
OCC下载地址：https://mackie100projects.altervista.org/download-opencore-configurator/

- 我使用的配置config.plist的方法是用对应的新版OCC打开旧config.plist文件，更改一个参数然后保存，再改回去然后保存。该方法上面视频的up主不推荐使用
- 然后更改BIOS的启动路径，新建一个路径，指向EFI/OC/OpenCore.efi（我的电脑虽然老的启动路径也是这个，但是它始终认为该路径没有启动文件，然后会进入硬件自检-关机-硬件自检的死循环）

### kexts
kext是仿冒的Apple驱动，用以支持非苹果原装或官方兼容硬件，基本上OC和Clover都能使用

----



## OC配置文件编辑器

OC的配置文件（config.plist）本质上是一串无需编译的代码，因此这些编辑器只是将代码用图形化界面展示，便于查找和更改，本质上在修改里面的值的时候，还是在修改代码中的值
### 所有文本编辑器（VS Code、Notepad++等）
因为OC的配置文件本质上是代码，因此完全可以用文本编辑器修改
只不过使用时需要清楚地知道目标项的名字，才能搜索
>例如，跑码模式（啰嗦模式）是“boot-args”，需要添加的值是“-v”，如果该项已经有值了，那就在-v和该值间加空格；因为使用xml代码格式，项目值前后要加<项目名>和</项目名>，如下面的代码所示：

```xml
<key>7C436110-AB2A-4BBB-A880-FE41995C9F82</key>
	<dict>
		<key>boot-args</key>
		<string>darkwake=4 -v</string>
```

### OpenCore Configurator（简称OCC）
OC配置文件的官方编辑器，一定要注意OC版本和OCC版本的对应（不是对应版本的版本号相同）
可以用来在macOS中挂载EFI分区

[下载OCC](https://mackie100projects.altervista.org/download-opencore-configurator/)

### OC Auxiliary Tools（简称OCAT）
开源编辑器，支持macOS、Windows、Linux，注意OC版本和OCAT版本的对应
目前我还没搞明白如何像OCC一样双击config.plist打开，只能手动拖入config.plist，而且我也不知道如何用它挂载EFI分区

>Windows系统中可以用DiskGenius访问EFI分区，拷贝出config.plist，修改完再复制回去

[OCAT Github主页](https://github.com/ic005k/QtOpenCoreConfig) | [下载OCAT所有版本](https://github.com/ic005k/QtOpenCoreConfig/releases)

### ProperTree
跨平台plist编辑器，友人推荐给我的，我还没试过
[ProperTree Github主页](https://github.com/corpnewt/ProperTree)

----


## 安装macOS

### 全新安装（果黑小兵）
[黑果小兵的部落阁官网](https://blog.daliansky.net/)

### 恢复版安装（老吴黑苹果）
[点击这里查看教程](http://k61.org/Win10-macOS-hackintosh-Restore.html/)
[点击这里下载硬盘恢复版镜像包](http://k61.org/categories/%E9%95%9C%E5%83%8F/)

### Cc3.0安装器（@嘿我叫聪聪）
[视频教程和工具下载](https://www.bilibili.com/video/BV1iE41157Vd/)

### 使用跑码模式寻找方法解决无法进入系统的问题
> 上面 OC配置文件编辑器 - 所有文本编辑器（VS Code、Notepad++等）中有提到如何开启跑码模式
>
> 图形化界面的OC配置文件编辑器中在 NVRAM - 7C436110-AB2A-4BBB-A880-FE41995C9F82 - boot-args 的value处修改

[OpenCore引导-v各种卡及OC引导常见问题解决方案速查表合集](http://imacos.top/2021/01/19/0154/)
[OpenCore配置错误、故障与解决办法](https://blog.51cto.com/u_2035505/2488066/)

>请善用搜索引擎和[远景论坛](https://bbs.pcbeta.com/index.php?gid=86)
>
>*请注意自己的身体，不要熬夜折腾黑苹果呦*

### DVMT
我的XPS笔电安装好黑苹果之后需要启动DVMT.efi设置一下，否则会卡在苹果logo处

----


## 优化macOS

### 备份黑苹果系统
1. [下载解压安装Paragon17.4.3](https://cowtransfer.com/s/43b2f118da5a41)
2. [查看备份和恢复教程视频](https://www.bilibili.com/video/BV1Ly4y177om) 如果上面的下载链接失效，这个视频简介里还有下载链接

### 升级macOS
> 在大版本更新前，一定要确认一下你的硬件在下一个大版本中是否支持。之前有出现过网卡在下个大版本中不支持的情况

一般来说，确保你当前使用的OC版本支持最新版macOS，且kext也已经更新，就可以使用系统的OTA更新
（如果你之前以输代码等形式关闭了更新，可以在App Store里搜索macOS下载更新）
升级时会多次自动重启电脑，确保OC中有Macintosh HD启动项时选择该项启动，一般就可完成更新

[下载指定版本升级软件（仅macOS可运行）或镜像](https://sysin.org/blog/macOS/)

### 和Wi-Fi蓝牙有关功能的bug
有时候会出现无法使用某些与WiFi和蓝牙有关的功能，比如无法连接iPhone的WiFi热点，无法隔空投送，或无法无线随航。这时退出黑苹果和你的每个苹果设备的iCloud，再登陆同一个iCloud即可解决。
目前不知道这个bug出现的原因，大概率因为序列号出现变化导致（更换三码或某个苹果设备换新）

### 一些基本的设定
- **三码洗白之前不建议登录iCloud！** 因为可能导致封号
- 不要开启系统偏好设置-安全性与隐私-文件保险箱
- 不要开启查找我的Mac
- （默认开启）关闭系统偏好设置-电池-电池&电源适配器-如果可能，让硬盘进入睡眠&启用电能小憩
- （默认开启）关闭关机/重新启动选项下的“再次登录时重新打开窗口”

### 三码洗白

> CPU变频和使用FaceTime、iMssage的必要前提

[三码洗白视频教程](https://www.bilibili.com/video/BV1454y167ML/)

### CPU型号显示错误
[解决CPU型号显示错误教程](http://k61.org/unkown-CPU-fix-hackintosh.html/)
如果你的CPU是英特尔正常发售的型号，填写0即可正常识别；如果你的CPU是ES版本或者AMD的，需要填写型号代码；
请注意，OC Configurator中应填写十进制数，需要将以上教程中的十六进制数转化为十进制填写，例如i5的推荐代码0x0605应改为1541

### CPU变频和频率显示
[CPUFriend.kext的使用方法](https://www.136.la/jingpin/show-36559.html?ivk_sa=1025883j/)

### 系统macOS
- 这里将使用OTA升级macOS。因为这样可以最好地保存你的数据和洗白的三码等设置。
首先确保你已经升级到支持最新版本macOS的OC，并更新了kext。这里可以参考其他人的EFI。保证你在更新这些以后可以正常使用，然后便可像白苹果一样正常OTA升级。不过这里仍然推荐使用Paragon Hard Disk Manager进行备份，一旦出现问题，可以恢复至更新前的系统

### 仍然存在的一些小bug
> 我的XPS9360出现的小bug，你的设备不一定会出现，但解决方法可作为参考

1. 合盖睡眠后无法唤醒，风扇在转，但屏幕一直不亮    -解决方法：制作一个[Ubuntu](https://ubuntu.com/download/desktop)的U盘启动盘，在BIOS内优先启动U盘，选择体验Ubuntu，过一段时间后关机，再启动macOS即可解决
2. OC启动win10可能进入恢复模式    -解决方法：开机显示DELL logo时按F12，选Windows Boot Manager启动进入win10；不要用OC启动win10
4. macOS关机后自动重启    -解决方法：长按开机键关机。如果从自动重启里进入win10，可能导致CPU锁频0.4Ghz
5. 摄像头无法使用    -解决方法：添加[UVC2FaceTimeHD.kext](https://github.com/hoanX/xps13-9360-Hackintosh/tree/master/kexts/UVC2FaceTimeHD.kext)或[FaceTimeHD.kext](https://github.com/hoanX/xps13-9360-Hackintosh/tree/master/kexts/FaceTimeHD.kext)到EFI/OC/kext目录下
6. 耳机无法使用    -解决方法：使用[ComboJack](https://github.com/hackintosh-stuff/ComboJack)
----



## 自己的一点感想

m1 MacBook是真的香，等我有钱一定换（有钱谁还折腾黑苹果啊）

----



## 参考资料

- [黑果小兵的部落格](https://blog.daliansky.net/)
- [老吴黑苹果工作室](https://win2mac.top/)
- [@theQuert](https://github.com/theQuert/XPS-9360-macOS/)
- [@hoanX](https://github.com/hoanX/xps13-9360-Hackintosh/)