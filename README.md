
# 奎克质造设备插件 (Qmdev)

这是为 X-Plane 11/12、MSFS 2020/2024 设计的奎克质造 (QuickmadeSim) 设备USB驱动软件。
它拥有强大的扩展性，插件内置了对编程初学者十分友好的 Lua 语言引擎，让您可以轻松为自己的飞机添加支持。



**官方网站与支持:**
*   跨平台支持 (X-Plane 11/12/MSFS2020/2024): https://www.quickmadesim.com/?page_id=194&lang=en

# 功能特性

*   **零性能影响**：对游戏帧率 (FPS) 毫无影响。
*   **飞行设备按键自动分配**：告别手动设置成百上千个按键的痛苦。
*   **丝滑切换飞机**：告别全网络四处寻找配置文件的痛苦。
*   **旋转按钮加速**：优化您的操作体验。
*   **内置Lua语言引擎**：简单易用，方便自定义。
*   **轻松调试**：无需重启 X-Plane 即可即时重载 Lua 脚本，加快开发流程。
*   **飞机状态同步**：支持飞机的冷舱和暗舱状态同步。
*   **模拟故障同步**：支持飞机模拟的故障状态同步。
*   **跨平台运行**：完美支持 Windows, Linux 和 Mac 系统。
*   **原生Apple ARM支持**：为苹果M系列芯片提供原生支持。

## 游戏兼容性列表

请通过以下链接查看详细的兼容性列表：
[奎克质造设备游戏兼容性列表](https://docs.qq.com/sheet/DWERFQnRmVUFZeHBi?tab=00...)

## 下载

您可以从以下地址获取最新版本的插件：
[最新版本下载](https://gitee.com/cpuwolf/Quickmadedevice/releases)

## 安装程序

我们提供了简单易用的安装向导。

![奎克质造设备安装程序](img/qmdev_mac_install.gif)

## 安装说明

### 在 MacOS 上安装

#### **MacOS 安装步骤**
1.  解压缩installer_6_8_mac.zip
2.  打开“终端”并执行以下命令，可以允许没给苹果缴费的开发者：
    ```bash
    xattr -cr installer_6_8_mac.app
    ```
3. 运行installer_6_8_mac.app

### 在 Linux 上安装

#### **Ubuntu 18.04 安装步骤**
1. 运行installer_6_8_lin

#### **Linux 设备无法找到的手动配置**

您需要编辑 hidraw 设备的访问权限。
```bash
sudo vim /etc/udev/rules.d/99-joysticks.rules
```
将以下内容添加至文件中：
```
KERNEL=="event*", NAME="input/%k", MODE="0666", GROUP="input"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", MODE="0666", GROUP="input"
```

#### **Linux 内核贡献**
我们修复了 Linux 内核对摇杆最大按键数的限制，详情请见：
[Linux 内核补丁](https://patchwork.kernel.org/patch/11657985/)

## 截图

![轻松调试](img/menu_reload.png)
![零性能影响](img/nocost.jpg)

## 重大版本信息

### **V6.3**

*   **核心变更**:
    *   修复了读取DataRef数值错误的核心bug。
    *   更新至 X-Plane SDK 4.0.1。
    *   修复了一个USB日志错误。
*   **Lua脚本变更**:
    *   为 QFCU 添加了对默认 XP12 A333 的支持。
    *   更新了多款机模（Toliss, IXEG, ZIBO, Flightfactor, JarDesign）在XP12下的设备逻辑和功能修复。
    *   **注意**: 此更新需要您同步更新 QFCU 固件: [固件更新地址](https://www.quickmadesim.com/?page_id=658&lang=en)

### **V6.1**
*   增加了读取Lua文件时的弹出窗口提示。

### **V6.0**
*   增加了对 MacOS M1 芯片的原生支持。
*   移除了所有 .cfg 配置文件，相关内容已整合进 Lua 脚本。

### **V5.0**
*   移除了对 FlyWithLua 的依赖，以解决其带来的性能损耗问题。
*   引入了内置的 ulua 引擎。

### **V2.0**
*   进一步优化性能。
*   为 .cfg 文件添加了新的关键字 `DFKEY`。
*   增加了 `disfast` dataref，用于临时禁用快速按键。
*   增加了对 QCDU, QG1K 设备的支持。

## 面向开发者

### **如何编写您自己的 .lua 脚本文件**

我们欢迎您为自己喜欢的机模编写脚本！详细的开发者文档请参考我们的 Wiki：
[Qmdev .lua 文件编写指南](https://gitee.com/cpuwolf/Quickmadedevice/wiki/Qmdev-.lua-files)

### **更多Lua开发者文档**

[访问开发者文档中心](https://gitee.com/cpuwolf/Quickmadedevice/wiki)