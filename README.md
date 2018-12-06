# MSI-GL62MVR-macOS-Clover
经测试可用的CLOVER引导程序，不是我弄出来的，在GL62MVR 7RFX上测试半年工作正常无硬件损坏。<br>
可以让你的电脑顺利引导三大主流操作系统:Windows系列/macOS/Linux系列<br>
注意：此过程及其繁杂，一般人折腾不来（我是为了避免购买昂贵性能又差的macbook）,我也没有条件再次录制整个过程。

相关视频：https://www.bilibili.com/video/av35630371/
![alt screenshot](https://raw.githubusercontent.com/Attect/MSI-GL62MVR-macOS-Clover/master/CLOVER/misc/screenshot3.png)

## 电脑硬件配置
我的电脑的配置具体请看：https://us.msi.com/Laptop/GL62MVR/Specification <br>
大致为：<br>
CPU:Intel i7-7700HQ<br>
GPU:Nvidia Geforce GTX 1060 6GB<br>
内存:16GB (8x2)<br>
硬盘:512GB SSD + 1TB HDD<br>
芯片组:Intel HM175<br>
~~这样的性能的配置苹果的价格在2万元以上，我这台8千~~

## 推荐掌握技能
掌握以下技能将有助于你碰到问题时自行解决
1. 原始Windows安装过程
1. 原始Linux安装过程
1. 磁盘文件系统
1. Linux shell
1. EFI shell

完全没用的技能：
1. 使用GHOST安装Windows操作系统

## 可用效果
1. 引导Windows Boot Manager
1. 引导Grub
1. 引导macOS及相关安装程序

其中Windows及Grub没有任何毛病。

## macOS 黑苹果效果
括号内为我电脑的配置<br>我并没有测试所有的东西
1. 支持核心显卡（Intel® HD Graphics 630）
1. 支持Nvidia独立显卡 (Nvidia Geforce GTX 1060)
1. 支持双显卡切换
1. 支持外接显示屏,多屏显示模式切换
1. 支持USB-HUB
1. 支持睡眠（合盖）
1. 支持电源管理
1. 支持自带屏幕亮度调整
1. 支持系统自动更新
1. 支持自带摄像头
1. 支持自带触摸板

以下为不支持的：<br>
1. 不支持Killer无线模块，蓝牙和Wifi不可用，AirDrop自然就没有
1. USB 3.0貌似不是满带宽的
1. 不支持声音输出切换，无论是外接显示屏接口还是自带耳机孔，你只能通过自带喇叭听声音（且及其刺耳），或许有个USB声卡能够解决。

未知的:<br>
1. NVME硬盘支持性未知

## 三操作系统推荐安装步骤
因为我只操作过一次，只推荐这么做。<br>
你最好结合其他教程一起看下面的步骤，我有省略，因为是半年前的事情了。

1. 抹除硬盘上的所有分区
1. 使用Windows 10安装程序，创建GPT分区表，同时请手动调整EFI分区大小为512MB（默认操作会给很小）
1. 划分三个操作系统所在分区，顺序为:Windows/Linux/macOS，大小请自定，无需格式化
1. 正常安装Windows 10
1. 跟随 https://www.tonymacx86.com/threads/unibeast-install-macos-mojave-on-any-supported-intel-based-pc.259381/ 制作macOS的USB安装，同时也将Clover写进去。我就不翻译了。那么中间提到需要一个macOS，你可以借一台苹果的电脑或者Win10中使用虚拟机跑一个。
1. 安装时注意系统分区为你硬盘上最后一个（我曾经试过不是最后一个，结果安装程序把之后一个分区也抹了）
1. 安装完macOS后，确保你能在插着USB的情况下正常启动你本机硬盘上的macOS系统
1. 拔掉USB，启动进入Windows系统，将本项目的CLOVER文件夹想办法放入EFI分区的EFI文件夹内
1. 由于这个笔记本的主板不会自动搜索EFI，需要使用EasyEFI将Clover注册到主板上
1. 重启，进入BIOS，选择启动Clover优先
1. 测试成功后，启动Windows，去弄Linux的安装U盘
1. Linux安装一切照常，注意别忘了安装Grub引导
1. 全部装好后，Clover会自动扫描出三个操作系统，大功告成。


## macOS系统大更新步骤
1. AppStore中正常下载更新，然后重启。
1. 重启后Clover会多出一个带Install的macOS选项，选择它
1. 进入安装更新后，会重启，你有可能会再次看到Install选项，继续选择它
1. 你可能会操作上两步多次，直到Install选项消失，否则进入系统后会告知更新失败
1. 完成

## macOS的Recovery
Clover下按F3就好，会出现一个番茄图标

## 其它
1. 主题是别处弄来的，所有Ext分区都显示为Ext3，我懒得改图了，视频中的Ext3其实是Ext4
1. 其实这套配置是针对外星人R7笔记本电脑的，当初看了一下配置一致，就拿来用了
1. 如果你觉得这套配置太旧，可以尝试使用 https://github.com/jianghaizhi/DELL-Alienware-Aurora-R7-macOS
