# Crazyflie编程

在本教程中，我们展示了更改Crazyflie中运行的软件（通常称为固件）所需的步骤。我们将展示如何修改源代码，如何构建它，最后下载并将其闪存到您的Crazyflie中。这些是编写自己的代码和改变Crazyflie行为的必要步骤。

本教程基于虚拟机，在虚拟机中安装、配置和设置了您所需的所有工具，使之变得非常简单。

我们假设您已经掌握了C语言的基本知识。



## 准备工作

对于本教程，您需要准备好：

​	*Crazyflie一个

​	*Crazyradio 2.0或CrazyradioPA（其中一个，建议Crazyradio 2.0）

​	*安装了虚拟机（VM）的计算机。

有关如何安装VM和Crazyradio的详细信息，请参阅Crazyflie2.X入门。

**注意：**由于虚拟机是Linux的AMD64安装，它不适用于苹果硅Mac（M1/2/…处理器）。在苹果硅mac上，您需要以本机方式安装这些工具。



## **启动虚拟机**

启动虚拟机以开始操作。它附带了您需要预先安装和配置的所有工具，使编程变得简单。

从本教程的这一点开始，所有步骤都指虚拟机中的操作。

## 更新源代码

双击桌面上的“update all projects”图标。这将从GitHub中提取所有项目的最新源代码。

![Update all projects icon](https://www.bitcraze.io/images/getting-started/update-all-projects-icon.png)

# 修改源代码

我们将从修改源代码开始。代码的更新是极简主义的，我们将把右前LED的颜色从红色改为绿色。

## 启动编辑器

预装的IDE（集成开发环境）是Visual Studio代码。双击桌面上的“Visual Studio代码”图标以启动它。

![vscode icon](https://www.bitcraze.io/images/getting-started/vscode-icon.png)

## 打开文件

使用“文件”菜单选择“打开文件夹…”并导航到“项目”文件夹，然后选择“crazyflie-firmware”文件夹并打开它。

![Project explorer](https://www.bitcraze.io/images/getting-started/vscode-open-folder.png)

导航到或搜索（CTRL+p）src/drivers/interface/led.h，然后单击打开它。

## 修改代码

找到这行代码

```c
#define SYS_LED          LED_RED_R
```

修改为

```c
#define SYS_LED          LED_GREEN_R
```

## 保存

通过“文件”菜单或按CTRL+S保存文件



# 构建源代码

现在是时候将源代码构建成可以下载到Crazyflie的二进制文件了。

有关开发Crazyflie固件的更多详细信息，您可以访问[此处的存储库文档](https://www.bitcraze.io/documentation/repository/crazyflie-firmware/master/)。

## 开始构建

如果vscode窗口底部没有命令行终端，您可以使用终端菜单并选择“新建终端”来访问bash终端窗口。

Crazyflie固件的构建系统基于make。

首先导航到crazyflie固件存储库的根文件夹。然后，您需要为固件创建一个默认配置文件：

```bash
$ make cf2_defconfig
```

如果你想为不同的平台构建固件，请查看crazyflie固件的构建说明。

然后，您可以通过在Visual Studio代码的终端窗口中发出以下命令来启动生成：

```bash
$ make
```

或者通过使用更多的cpu来加快构建速度

```bash
$ make -j 12
```

构建固件。您应该在一个成功的构建中看到以下内容：

```bash
$ make
  CLEAN_VERSION
  CC    sensors_mpu9250_lps25h.o
  CC    sensors_bmi088_bmp388.o
  CC    main.o
  CC    nvic.o
  CC    led.o
  CC    usblink.o
  CC    ledseq.o
  CC    freeRTOSdebug.o
  CC    pm_stm32f4.o
  CC    radiolink.o
  CC    system.o
  CC    usddeck.o
  CC    cfassert.o
  VTMPL version.c
  CC    version.o
  LD    cf2.elf
  COPY  cf2.hex
  COPY  cf2.bin
  DFUse cf2.dfu
Build for the CF2 platform!
Build 11:0864ef92245a (2021.03 +11) MODIFIED
Version extracted from git
Crazyloader build!
Flash |  242184/1032192 (23%),  790008 free | text: 236372, data: 5812, ccmdata: 0
RAM   |   71128/131072  (54%),   59944 free | bss: 65316, data: 5812
CCM   |   58380/65536   (89%),    7156 free | ccmbss: 58380, ccmdata: 0
```

## 上传Crazyflie固件

现在我们有了二进制文件，是时候将它们下载到Crazyflie并保存在闪存中了，通常称为闪存。我们新修改的固件版本将取代您当前安装的任何版本。如果你想回到官方固件，只需用[官方版本](https://github.com/bitcraze/crazyflie-firmware/releases)重新刷新Crazyflie。

### Crazyflie准备工作

关闭Crazyflie 2.X。

按住电源按钮3秒钟，在引导加载程序模式下启动它。两个蓝色指示灯都将闪烁。（其实按住3秒后，发现一个蓝色LED灯闪烁，赶快松开，这样两个蓝色LED灯就开始闪烁，进入可以上传固件的模式了)

### 上传固件

在终端窗口中键入：

```bash
$ make cload
```

“控制台”窗口中的打印输出显示进度，Crazyflie上的LED闪烁。

```bash
$ make cload
python3 -m cfloader  flash  cf2.bin stm32-fw
Restart the Crazyflie you want to bootload in the next
 10 seconds ...
 done!
Connected to bootloader on the Crazyflie (version=0x10)
Target info: nrf51 (0xFE)
Flash pages: 232 | Page size: 1024 | Buffer pages: 1 | Start page: 88
144 KBytes of flash available for firmware image.
Target info: stm32 (0xFF)
Flash pages: 1024 | Page size: 1024 | Buffer pages: 10 | Start page: 16
1008 KBytes of flash available for firmware image.
Flashing 1 of 1 to stm32 (fw): 242639 bytes (237 pages) ..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10..........10.......7
Reset in firmware mode ...
```

### 就是这样

当闪烁完成时，Crazyfile应该重新启动，并且Crazyflie的右前LED现在应该是绿色而不是正常的红色。

祝贺你的第一个Crazyflie黑客！



## 下一步

### 使用GDB进行调试

有关使用GDB调试Crazyflie固件的指南，请参阅此处的固件文档。

### 虚拟机的替代方案

在本教程中，我们使用了虚拟机，主要是因为它是最简单的入门方法。然而，还有另外两种编译代码的方法；在机器上安装工具链或使用Toolbelt。所有的解决方案都有其优缺点，但如果您计划进行一些认真的开发，那么可能值得研究所有的选项。