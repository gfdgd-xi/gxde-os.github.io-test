# 如何安装 GXDE？

## 镜像安装



镜像站下载（教育网联合镜像站）：https://mirrors.cernet.edu.cn/GXDE/ISO/

官方下载： https://repo.gxde.top/ISO/

镜像源列表：[点击这里查看](mirrors.md)

旧版/不常用架构版本存档：https://pan.baidu.com/s/1dsJSUhHiMg4tPHTq9IDpJw?pwd=GXDE 提取码: GXDE

Sourceforge：https://sourceforge.net/projects/gxde-os/files


i386、mips64el 架构的安装方法可以参考：[APT 源安装](#apt-源安装)

GXDE 仍不完美，请在安装前确认 [FAQ](faq.md) 中的事项，包括了 Nvidia 显卡驱动安装指南等

---

小白安装：若不会分区，可空出一块磁盘，在安装时选择整块磁盘安装即可。

EFI 安装：必须分一块格式为 vfat/fat32 的分区，挂载点选择 /boot/efi，剩余可按需求分区  

安装镜像锁屏密码：`live`  

### 日构建镜像
如果你想下载日构建镜像，可以访问：https://sourceforge.net/projects/gxde-os-daily/  
日构建镜像无法保证可以正常安装、使用等，如需日用请下载上方的稳定版镜像  


## APT 源安装
> amd64、arm64 等已经有 ISO 安装镜像的，建议使用 ISO 安装  
> 目前支持 i386、amd64、arm64、mips64、loong64 和 riscv64 架构（riscv64 下未测试）   
> i386、amd64、arm64、mips64 支持在 Debian 13/12 下安装使用，loong64 支持在 Debian Port、Loongnix 25 下安装使用，riscv64 支持在 Debian Sid 下使用，loong64 和 riscv64 架构用户**一定要加内测源**    
> loong64 Debian Port 系统安装镜像：https://cdimage.debian.org/cdimage/ports/tests/


使用 deb 包安装 APT 源：

| 目标系统代号 | 支持发行版 | deb 包下载地址 |
| --- | --- | --- |
| lizhi | Debian 13 | https://repo.gxde.top/gxde-os/lizhi/g/gxde-source/ |
| bixie | Debian 12 | https://repo.gxde.top/gxde-os/bixie/g/gxde-source/ |
| meimei | Loongnix 25 | https://repo.gxde.top/gxde-os/meimei/g/gxde-source/ |

::: warning
**请根据自己的系统版本下载对应的包，否则安装时会出现依赖错误**
:::

:::warning
**从 GXDE 2025 开始直接基于 Debian backports 构建，在您安装 `gxde-source` 包后将会自动添加 Debian Backports 源**
:::

安装之后，执行以下命令安装 GXDE 桌面环境：

```bash
sudo apt update

sudo apt install aptss

sudo apt install gxde-testing-source -y  # 添加内测源，Debian Sid/Port 用户一定要用，amd64、mips64、i386、arm64 和 Loongnix 25 用户可忽略

sudo aptss update

sudo aptss install gxde-desktop gxde-desktop-extra -y

sudo aptss install spark-store -y  # 此命令不支持 i386、mips64、riscv64 架构用户

```

执行完毕后，重启电脑即可。

> `aptss` 可以加速在 GXDE 系统源的下载速度，但如果您的性能低下导致 `aptss` 运行缓慢到无法接受，可换成 `apt`

**GXDE与KDE有可能的冲突，请不要同时安装它们，这可能会带来错误**

## 在 Docker 使用 GXDE
> RDPDocker是一个带有X11个和桌面环境的Docker镜像构建和容器创建工具，支持创建Ubuntu、Debian、ArchLinux、Fedora系统，支持Lingmo、GNOME、Xfce4、X11、SSH等环境。同时，允许用户通过NoMachine、RDP、VNC、SSH等方式远程访问容器。本工具以非虚拟化和极低开销的情况下，实现了多用户共享一台主机的办法，同时创建极快，随用随开，并且只占用内存、磁盘极少的空间，只需要主机安装Docker即可，支持无桌面的Linux服务器、WSL2、LXC、安卓手机运行。

具体可见：https://github.com/PIKACHUIM/RDDocker  

![RDPDocker 图1](/RDDocker/Manager.jpg)
![RDPDocker 图2](/RDDocker/Remote.jpg)

## 在 Android 上使用 GXDE
### 在小小电脑上使用 GXDE
> 给所有安卓 arm64 设备的“PC 应用引擎”平替。

小小电脑 `1.0.19` 开始支持 GXDE，该版本与小小电脑团队合作开发，仍处于测试阶段  
如需反馈 bug，可至 https://github.com/Cateners/tiny_computer/issues/129  

::: warning
如果你想从v1.0.10及以后的版本升级，请务必在启动后进行重置启动命令(在高级设置)和重新安装引导包(在全局设置)操作，否则新功能可能无法使用。  

默认情况下，即使更新了本软件，引导包、快捷指令、容器系统也并不会被更新。  

软件只支持arm64设备，默认用户tiny密码tiny，vnc端口5904密码12345678，novnc端口36082，pulseaudio端口4718，Termux X11占用端口7897；本软件不会和termux冲突。  
:::

下载链接：  
镜像站下载（推荐）：https://mirrors.sdu.edu.cn/GXDE/APK/   
Github 下载（选择带 gxde 后缀的 APK）：https://github.com/Cateners/tiny_computer/releases

> 注：如果界面操作卡顿可以在控制中心 -> 个性化 关闭特效模式，假若控制中心无法开启可尝试在 GXDE 自带的系统助手的工具箱内升级到最新版本

小小电脑项目地址：https://github.com/Cateners/tiny_computer  

![](/tiny-computer.jpg)

### 在 Neo Desktop 使用 GXDE
> 一个超级启动器，支持搭配 AR 眼镜，或者物理显示器，让设备实现多屏异显。

具体可参见：https://nightmare.press/  
![Neo Desktop](/neodesktop/0.jpg)


### 在 Termux PRoot 或其他安卓设备上安装

请查看 https://bbs.deepin.org.cn/post/279414
