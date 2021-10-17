# mi8 刷机

## res

* rom 下载
* <xiaomirom.com>

## 解bl锁

* 百度小米解bl锁
    * 先登录
    * 下载工具解锁

## 注册表

* <https://miuiver.com/press-any-key-to-shutdown/>

```shell
@echo off
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "osvc" /t REG_BINARY /d "0000" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "SkipContainerIdQuery" /t REG_BINARY /d "01000000" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "SkipBOSDescriptorQuery" /t REG_BINARY /d "01000000" /f
pause
```

## 刷机

* miflash 2018.5.28