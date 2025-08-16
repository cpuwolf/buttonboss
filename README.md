# Quickmadesim 设备驱动插件

本插件为 Quickmadesim 硬件设备的 X-Plane 11/12 驱动程序，提供 USB 连接支持。 它具有强大的可扩展性，您可以自行添加更多机型。内置的 Lua 语言引擎，让编程初学者也能轻松上手。

官方网站：
*   [https://x-plane.vip/quickmade/](https://x-plane.vip/quickmade/)
*   支持 X-Plane 11/12/MSFS2020/2024，详情请访问：[https://www.quickmadesim.com/?page_id=194&lang=en](https://www.quickmadesim.com/?page_id=194&lang=en)

## 主要特性

*   **对游戏帧率 (FPS) 无影响**
*   **摇杆按键自动分配**：免去手动设置上百个按键的烦恼
*   **旋转编码器加速**
*   **内置 Lua 语言引擎**
*   **便捷的调试功能**：无需重启 X-Plane 即可即时重载 Lua 脚本文件
*   **与飞机冷舱和黑屏状态同步**
*   **与飞机模拟故障同步**
*   **跨平台运行**：支持 Windows、Linux 和 Mac
*   **原生支持 Apple ARM 架构**

## 游戏兼容性列表

请参阅此在线文档了解详细的兼容性列表：
[https://docs.qq.com/sheet/DWERFQnRmVUFZeHBi?tab=00...](https://docs.qq.com/sheet/DWERFQnRmVUFZeHBi?tab=00...)

## 软件下载

您可以从以下地址下载最新版本的插件：
[https://github.com/cpuwolf/Quickmadedevice/releases](https://github.com/cpuwolf/Quickmadedevice/releases)

## 便捷的安装程序

我们提供了一个安装程序，使安装过程更加简便。

![qmdev 安装程序](img/qmdevinstaller.gif)

## Lua 开发文档

更多关于 Lua 脚本开发的文档，请访问我们的 Wiki 页面：
[https://github.com/cpuwolf/Quickmadedevice/wiki](https://github.com/cpuwolf/Quickmadedevice/wiki)

## 软件截图

<img width="354" alt="截屏2023-10-30 08 16 39" src="https://github.com/cpuwolf/Quickmadedevice/assets/1320329/d13b6540-eba4-422a-98b9-1ef75fbf75c9">

![qmdev 设置界面](img/qmdev_setup.jpg)![零帧率影响](img/nocost.jpg)

### 在 Linux/MacOS 上安装

#### MacOS 安装步骤
1.  从 [https://www.java.com/en/download/](https://www.java.com/en/download/) 下载并安装 Java。
2.  打开“终端”并执行以下命令：
    ```
    java -jar Qmdev_Setup.jar
    cd <...>/X-Plane 12/Resources/plugins/qmdev
    xattr -dr com.apple.quarantine *
    ```

#### Ubuntu 18.04 安装步骤
```
sudo apt install openjdk-11-jre
java -jar Qmdev_Setup.jar
```

#### Linux 手动配置

编辑 hidraw 设备访问权限：
```
sudo vim /etc/udev/rules.d/99-joysticks.rules
```
添加以下内容：
```
KERNEL=="event*", NAME="input/%k", MODE="0666", GROUP="input"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", MODE="0666", GROUP="input"
```

#### Linux 内核贡献
修复了 Linux 内核对摇杆最大按键数的限制。详情请见：
[https://patchwork.kernel.org/patch/11657985/](https://patchwork.kernel.org/patch/11657985/)

## 版本信息

### V6.3
*   **重要提示：** 此更新需要您更新 QFCU 固件：[https://www.quickmadesim.com/?page_id=658&lang=en](https://www.quickmadesim.com/?page_id=658&lang=en)
*   **核心变更：**
    *   修复了 Qmdev 核心读取 Dataref 数值错误的 bug
    *   更新至 X-Plane SDK 4.0.1
    *   修复了一个 USB 日志错误
*   **Lua 脚本变更：**
    *   增加了对默认 XP12 A333 的 QFCU 支持
    *   更新了 Toliss Airbus XP12 的 QFCU 亮度和电源逻辑
    *   更新了 IXEG B737 classic plus XP12 的 QMCP737C 自动油门 LED 灯
    *   更新了 ZIBO B737 XP12 的 QCDU EXEC 灯
    *   以及更多针对 Flightfactor、Toliss 和 JarDesign 等机型的修复和更新

### V6.1
*   在读取 lua 文件时增加了弹出窗口提示

### V6.0
*   原生支持 MacOS M1
*   移除了所有 .cfg 文件，其内容已整合进 lua 脚本

### V5.0
*   移除了对 FlyWithLua 的依赖，以解决其导致的帧率下降问题
*   引入了内置的 ulua 引擎

### V2.0
*   进一步优化了性能
*   在 .cfg 文件中增加了新的关键字 DFKEY
*   增加了 disfast dataref 用于临时禁用快速按键
*   增加了对 QCDU、QG1K 设备的支持

## 开发者指南

如果您想学习如何编写自己的 .lua 脚本文件，请参阅我们的开发者文档：
[https://github.com/cpuwolf/Quickmadedevice/wiki/Qmdev-.lua-files](https://github.com/cpuwolf/Quickmadedevice/wiki/Qmdev-.lua-files)