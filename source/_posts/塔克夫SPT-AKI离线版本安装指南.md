---
title: 塔克夫SPT-AKI离线版本安装指南
date: 2024-08-25 09:39:20
tags: SPT-AKI
---

# 逃离塔克夫SPT-AKI离线版本安装指南

> SPT-AKI 3.9.8版本(2024/8/20)  

### SPT-AKI 永远不会正式实施任何多人游戏或合作游戏功能。

#### 以下是 SPT 团队不会考虑实施合作游戏的几个原因：
- 有悖于 SPT 的目标，即允许离线（单人）进行 EFT，与他人一起游戏从来都不是目标，因此该项目被命名为”单人塔可夫”。
- SPT 是对 EFT 离线突袭模式的修改，在突袭后会保存配置文件数据。
- “SPT 服务器”只是一个将个人资料保存到硬盘的系统，同时还模拟了贸易商、跳蚤市场、藏身处等。
- BattleState Games 是 EFT 的开发商，如果加入 COOP，他们很可能会在巨大的法律压力下废除该项目。SPT 将立即停止存在。
- SPT 以外的人曾多次尝试创建 COOP 系统，但都因其复杂性而失败。
## 安装离线版本之前，请确保您的电脑配置满足要求
|配件|	最低配置|	推荐配置|
|----|---------|-----------|
|操作系统|	Windows 10（64 位）|	Windows 11（64 位）|
|处理器|	双核处理器 2.4 GHz (9代Intel i3)，2.6 GHz (AMD Athlon, Phenom II)|	四核处理器 3.2 GHz (11代Intel i5, i7)，3.6 GHz (AMD FX, Athlon)|
|显卡|	DX11 兼容显卡，带 1 GB 内存	|DX11 兼容显卡，带 4 GB 或更多内存|
|内存|	16 GB	| 32 GB|
|磁盘空间|	35 GB 以上	|45 GB 以上|
|声卡|	DirectX 兼容声卡	|DirectX 兼容声卡|
## 下载客户端
1. 逃离塔克夫离线论坛： https://sns.oddba.cn/bbs/spt-r  
2. 进入论坛后，点击最新版本。
>  oddba论坛每月1日免费注册账号，且下载不需要登录。
3. 滚动到页面下面，找到服务端选项，选择适合你的下载方式，下载客户端。（约25GB）
4. 于此同时，下载服务端。滚动到页面上面，选择适合你的下载方式，下载服务端（约90MB）
## 安装游戏
### 以下在你的电脑C盘根目录下操作（也可在别的盘根目录下）：  
1. 在根目录下新建文件夹`EFT`，进入EFT文件夹，以下简称“游戏根目录”
2. 将下载好的Client.xxxx 解压到游戏根目录中。
3. 解压Client完毕后，将下载好的SPT-x.x.x 解压到游戏根目录中
> **注意，与Client文件在同一个文件夹下，不要在Client文件中新建文件夹！**  
>  解压完毕后，你的SPT文件应该和Client文件在同一个文件夹下
4. 运行一次SPT.Server。

## 运行游戏
1. 在游戏根目录下（EFT）运行SPT.Server，等待服务加载完毕。
2. 当服务加载完毕后，打开SPT.Launcher,新建档案，开始游戏。
    ### 过正版校验 
    >如果你打算先试玩离线版再购买正版，可以先过正版校验。  
    >如果你有oddba论坛账号的话，可以在https://sns.oddba.cn/140782.html 下载一键过正版验证脚本。
    >如果没有账号，就跟着我手动过验证。
    >请确保你的资源管理器打开了显示文件扩展名，在资源管理器中，上栏选择`查看->显示->文件扩展名`
    1. 在C盘根目录下新建文件夹`Install_EFT`。
    2. 在`Install_EFT`文件夹中再新建文件夹`BattlEye`。
    3. 在`BattlEye`文件夹中新建文件`BEClient_x64.dll`里面可为空。
    4. 回退到上一目录（`C:\Install_EFT`）
    5. 新建文件`ConsistencyInfo`，里面可为空(无扩展名)
    6. 新建文件`Uninstall.exe`，里面可为空
    7. 新建文件`UnityCrashHandler64.exe`，里面可为空
    8. 新建文件`WinPixEventRuntime.dll`，里面可为空
    9. 新建文本文件，将以下值复制到文件中
    ``` bash
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\EscapeFromTarkov]
    "UninstallString"="C:\\Install_EFT\\Uninstall.exe"
    "InstallLocation"="C:\\\\Install_EFT"
    ```
    重命名为`install_EFT.reg`，双击，将值添加到注册表中。  
    至此，过正版验证完毕。

## 注意事项
1. 在以后游戏中，先运行SPT.Server，再运行SPT.Launcher
2. 存档都将放在本地电脑中

## 工具
1.存档修改器：https://github.com/SkiTles55/SPT-AKI-Profile-Editor/releases  
选择Spt-Aki.Profile.editor.zip 解压安装即可。

2.离线修改器：https://github.com/sailro/EscapeFromTarkov-Trainer/releases/tag/installer-3.0  
下载installer.zip 解压到游戏根目录中（C:\EFT）双击安装即可。  
如果需要中文汉化，跳过上一步。  
下载installer.zip 解压到游戏根目录中（C:\EFT），在游戏根目录中（C:\EFT），在地址栏输入`cmd`，回车打开cmd窗口，输入`install -l zh-cn`命令安装汉化版本。
{% note info fa-info %}
**注意，离线修改器只可在离线版本中使用，不可在正式版中使用！会被反作弊检测到！在正式版中使用所造成的一切后果，本教程不承担任何责任！**
{% endnote %}