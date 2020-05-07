# Clover 95% 完美黑苹果

>By n0T
>
>Blog：blog.n0T.top
>
>感谢 各位黑果大佬 的无私分享
>
>包括但不限于：
>
>[远景论坛](http://bbs.pcbeta.com/forum-561-1.html)	[黑果小兵的部落阁](https://blog.daliansky.net/)	[xjn819](https://blog.xjn819.com/)	[LeoForBest](https://blog.csdn.net/LeoForBest)

## EFI 分享

> [GitHub](https://github.com/n0TToday/HackMac-Clover)

## 硬件配置

|    类型    |               名称                |
| :--------: | :-------------------------------: |
|    CPU     |          `Intel i5-8400`          |
|    内存    |     `金士顿 2400MHz 8GB` * 2      |
|    主板    |      `技嘉 B360m Gaming HD`       |
|    BIOS    |               `F12`               |
|    声卡    |             `ALC887`              |
|    网卡    |          `Realtek 8118`           |
|    显卡    |        `RX 580 8G 2304SP`         |
| 蓝牙+Wi-Fi |           `BCM94360CS2`           |
|   磁盘 1   | 系统盘：`三星 970 EVO Plus 250GB` |
|   磁盘 2   |    `金士顿 250GB SATA SSD` * 2    |
|   磁盘 3   |     `西部数据 4TB 监控机械盘`     |

## 功能实现

- 解锁了BIOS的`CFG Lock`，更换 `AptioMemoryFix-64.efi` ，解决内存问题
- UEFI 添加 `EmuVariableUefi.efi`，解决 睡眠、关机重启 问题
- 定制 `USB端口` 
- 定制 `AMD显卡接口`
- CPU 变频正常
- 蓝牙、Wi-Fi 免驱
- 声卡输入输出正常
- 隔空投送 正常
- 显卡免驱，支持双硬解
- 开启 HiDPI
- 休眠正常
- ……

## 待解决

- ~~对 NTFS 的读写操作~~

  1. 安装 `FUSE for Mac`

  2. 使用 `brew` 安装 `ntfs-3g`

  3. **关闭 `SIP`**

  4. **挂载系统目录 `sudo mount -uw /`**

  5. 替换系统 NTFS 文件

     ```shell
     sudo mv /sbin/mount_ntfs /sbin/mount_ntfs.orig        
     sudo ln -s /usr/local/sbin/mount_ntfs /sbin/mount_ntfs
     ```

  6. 重新启动

- 关机时 卡程序坞（macOS Bug）

- ……（遇到再说）

## Clover 配置

- 引导参数
  - `-lilubetaall`
  - `debug=0x100`
  - `-disablegfxfirmware`
  - `-no_compat_check`
  - `slide=0`
- ACPI
  - DSDT
    - H_EC to EC
    - HDAS to HDEF
    - HECI to IMEI
    - GFX0 to IGPU
    - EHC1 to EH01
    - EHC2 to EH02
  - Fixes
    - 修复关机
- 设备设置
  - AppleALC 注入 id `1`
- 引导界面
  - 隐藏
    - Preboot
    - Recovery
    - Legacy
  - 主题
    - Catalina
- 显卡设置
  - FBname：`Guariba`
  - 注入 AMD
- 内核补丁
  - 解除 USB 端口 15 限制
- 机型
  - MacPro 7,1（2019）

## UEFI&Kexts

### UEFI

- ApfsDriverLoader.efi
- AppleImageCodec.efi
- AptioMemoryFix-64.efi
- AudioDxe.efi
- DataHubDxe.efi
- EmuVariableUefi.efi
- FSInject.efi
- HFSPlus.efi
- MemoryAllocation.efi
- NvmExpressDxe.efi
- PartitionDxe.efi
- VirtualSmc.efi

### Kexts

- AHCI_3rdParty_SATA.kext
- SMCLightSensor.kext
- AHCI_3rdParty_eSATA.kext
- SMCProcessor.kext
- AppleALC.kext
- SMCSuperIO.kext
- GenericUSBXHCI.kext
- USBPorts.kext
- HoRNDIS.kext
- VirtualSMC.kext
- Lilu.kext
- VoodooPS2Controller_v1.9.2.kext
- NoTouchID.kext
- WhateverGreen.kext
- RealtekRTL8111.kext
- XHCI-300-series-injector.kext
- SMCBatteryManager.kext

## 系统截图

![HackMac](http://cdn.n0t.top/img/HackMacSnippets.png)