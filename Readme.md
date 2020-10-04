# **Hackintosh EFI  OC060 for  MSI B450m mortar max**

## **配置信息**

| 主板 | B450m mortar max           |
| :--: | -------------------------- |
| CPU  | AMD 3600X 4.3GHz           |
| 内存 | 8G*2  3600MHz DDR4         |
| SSD  | 西数SN750 500G             |
| 显卡 | AMD Radeon RX5600XT        |
| 声卡 | ALC892                     |
| 网卡 | RTL8168/8111/8112+ DW1820A |

## 关于Opencore

​	 Hackintosh 下一个引导工具，最初诞生于HermitCrabs实验室，现在由Acidanthera接手，其目的是创造一个更加严谨的模组化的轻量引导系统 。与此同时，还有使用Clover作为引导工具，但是越来越多的kext不支持Clover，因此选用OC作为引导工具。

## 进展

- 引导方式

  Opencore 支持，版本号060

- 系统支持

  ​	理论支持10.15下的所有系统，主要原因为

  1. ​	5600XT的显卡驱动在10.15.2以后的系统才能正确识别
  2. ​    DW1820a的驱动为10.5版本专用

  ​	如果不考虑以上俩点，那么理论上支持10.15.6以下所有的系统

- 电源管理

  采用AMDRyzenCPUPowerManagement，支持变频和电源功率查看

  睡眠和唤醒：关闭bios里面的串行端口即可支持睡眠唤醒

- 显卡5600XT

  ​	驱动参考xjin大佬的[5700xt的专享优化贴](http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1839725&highlight=5700xt)，可以通过win下的适配器类型和显卡属性获取到显卡的ROM和EFI-version从而驱动显卡，由于5600xt是5700的阉割版，因此直接将model 改成W5700X(实际只是想偷懒)。

- 硬盘

  没有SATA接口的硬盘，无法测试，但是系统报告中出现有AHCI的识别信息

- USB

  USB3.0接口正常使用，最大速率为5gbps

- 声卡

  使用AppleALC模拟声卡，目前正常使用，无任何启动问题

- 网卡

  有线网卡：RTL8111网卡，正常工作，目前没有断连问题

  无线网卡：DW1820a （驱动参考[黑果小兵的DW1820a驱动贴](https://blog.daliansky.net/DW1820A_BCM94350ZAE-driver-inserts-the-correct-posture.html)）

  ​	wifi 和蓝牙都都可以正常驱动，冷热启动都没有出现问题

  PS：无线网卡的最新消息是intel大多数网卡都可以驱动，具体实际情况请参考远景论坛和国外开发者论坛的intel无线网卡贴，USB网卡也可以替代使用；相关驱动开发项目地址：WiFi [itlwm](https://github.com/zxystd/itlwm)（项目众多，这是其中之一），蓝牙 [IntelBluetoothFirmware](https://github.com/zxystd/IntelBluetoothFirmware)

  

## 系统相关

​	Windows 和 macOS 时间不同步

- Windows 中打开命令行，输入 Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_DWORD /d 1
- 重启到 macOS，联网同步时间，再次进入 Windows 即可正常显示时间


   MacOS的声音调节如果出现跳动的问题，并且在停止调节后图标仍然出现跳音量的情况，可以尝试进入bios的setting->超级IO配置->关闭里面的并行串口。重启后进入系统后应该就OK了

​	

## 相关

感谢各位大佬们为hackintosh做出的贡献



## 

​	









