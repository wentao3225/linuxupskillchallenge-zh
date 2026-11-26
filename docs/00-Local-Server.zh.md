---
comments: true
---
# 第 0 天 - 搭建你自己的本地服务器

请先回到[第 0 天 - 获取你自己的服务器](00.md)看看有哪些选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云端（DigitalOcean、Linode、Vultr 这类厂商）](00-VPS-small.md)
* [云端（AWS、Azure、Google Cloud 这类厂商）](00-VPS-big.md)

**提示**：可以看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=643s)里的完整演示。这个视频覆盖了各种可能的搭建方式（VirtualBox 本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## 没有信用卡，想在云端创建服务器可就难了

我们通常推荐 Amazon AWS 的免费套餐（Free Tier）或 Digital Ocean——但两者都要求你有信用卡。Microsoft Azure、Google 的 GCP 以及 [Low End Box](https://lowendbox.com/) 上列出的绝大多数厂商也都是如此。

有些厂商接受 PayPal 或比特币——但通常来说，没有信用卡的人往往这些也没有。

**警告**：如果你在这方面搜得太深，很可能会撞上一堆骗人的、假冒的、诈骗性质的网站。虽然我们已经尽力把它们从下面的链接里剔除了，但还是请当心！不用多说也知道，这些链接没有一条是“联盟推广”（affiliate）链接，我们也从中拿不到任何回扣 :-)

### 能当（或近似当）信用卡用的卡

* 借记卡
* <https://www.paysafecard.com/>
* privacy.com（仅限美国）

## 但如果我压根不想用云厂商呢？完全可以只用本地虚拟机

你完全可以在家用服务器上跑完整个课程，所有命令的表现和在云服务器上一模一样。不过，不暴露在“荒野”里，你也就体会不到真正的系统管理员每天要面对的是什么。

如果你在自己的机器上开虚拟机，按最低要求来就行：1GHz CPU 核心、1GB 内存、5GB 磁盘空间。之后想怎么调，全看你心情（以及手头有多少硬件）。

我们的建议是：有条件就用云服务器，体验最完整，但别被它束缚住。**这是你自己的服务器。**

## 下载 Linux ISO

前往 [Ubuntu](https://ubuntu.com/download/server) 官方页面，下载目前最新的 LTS（长期支持版）版本。

**注意**：下载的是 **server**（服务器）版本，不是 **desktop**（桌面）版本。

## 用 VirtualBox 创建虚拟机

* [用 VirtualBox 创建本地 Linux 服务器（视频）](https://youtu.be/nKcfhI1B4mA)

安装好 [VirtualBox](https://www.virtualbox.org/) 之后：

* 点击 *Machine > New*
* 给虚拟机取个名字，*Type* 选 Linux，然后点 *Next*。
* 调整硬件：1024MB 内存和 1 个 CPU（这是最低配置，宿主机允许的话可以多给点）。点 *Next*。
* 虚拟硬盘：2.5GB 是底线，5GB 比较合适。点 *Next*。
* 点 **Finish**——但还没完。
* 新建的虚拟机会出现在虚拟机列表里，选中它。
* 点击 *Machine > Settings*
* 点击 *Storage*，右键 Controller IDE，点击 *Optical Drive*。
* 如果列表里已经能看到你下载的 Linux ISO，直接选它；没有就点 *Add*，在自己的目录里找到它，再点 *Choose*。
* 点击 *Network*，把网卡改成 **Bridged Adapter**（桥接模式）。
* 点 *OK*
* 点 **Start**，或者 *Machine > Start > Normal Start*。

## 安装 Linux

几秒钟后欢迎界面就会加载出来。每一屏底部都有 DONE 和 BACK 两个按钮。用**方向键**和**回车键**选择选项；对所选内容满意后，用方向键移到 DONE 上，按**回车**进入下一屏。

* **Welcome Screen**：选择你的语言
* **Keyboard Configuration**：选择键盘类型
* **Choose type of install**：选择 _Ubuntu Server (minimized)_。它自带你需要的大部分软件包，又不臃肿，装起来也更快。

**关于 Ubuntu Server minimized 的说明**：这是 Ubuntu Server 的精简版。最大的优点是资源占用低——相比标准版 Ubuntu Server，它占用的磁盘空间、内存和 CPU 都更少，非常适合硬件有限的环境。不过它也缺少不少便利工具和默认软件包，之后可能得手动补装。这倒不是什么大问题，真要说反而能逼你多练命令行。但如果你不想折腾、硬件也够用，那就预留 2GB 内存和 20GB 磁盘，直接装完整的标准版 Ubuntu Server。

* **Network Connections**：如果你按前面的说明给虚拟机配好了 **bridged adapter**（桥接模式），基本不用操心——安装器会自动从你本地网络的路由器获取 DHCP 设置，你只要选 DONE 就行。
* **Configure Proxy**：如果你的系统需要 http 代理才能上网，就填入代理地址，否则直接选 DONE。
* **Configure Ubuntu archive mirror**：保持默认，选 DONE。
* **Guided Storage Configurations**：我们要用掉分配给这台虚拟机的全部存储空间，所以选 **Use the Entire Disk**（使用整块磁盘）。
* **Storage Configuration**：保持标准存储配置，选 DONE。弹出确认时别慌——这只会动虚拟机的磁盘，不会碰你电脑的磁盘。
* **Profile Setup**：填入你的名字、服务器名、用户名和密码。这个用户将是你在系统里的 `administrator` 用户（即拥有 `sudo` 权限的用户），所以千万别忘了这个密码。
* **Update to Ubuntu Pro**：选 No，先跳过。
* **SSH setup**：勾选 Install OpenSSH server——之后你就要靠它连接服务器。
* **Featured Server Snaps**：这些软件包眼下都不重要，直接选 DONE。
* **Installing System**：接下来等几分钟，让系统装完。你可以“作弊”提速：跳过更新的下载，稍后当页面底部出现 **Cancel update and Reboot** 时选它；首次开机后再把更新补完。安装完成后系统会自动重启。

## 首次登录

第一次重启后，屏幕上会出现一个黑底界面，提示输入 `login`——这时就用安装时创建的用户名和密码登录。

注意：输入密码时屏幕上什么都不会显示，连 `******` 都没有——放心，它确实在接收输入。

如果需要知道虚拟机的 IP 地址，在控制台里输入：

```bash
ip address
```

输出里的 `inet` 就是 IP 地址。用 SSH 连接时会用到它。

## 通过 SSH 远程访问

如果你用的是 Windows 10 或 11，可以按[用系统自带 SSH 客户端连接](https://youtu.be/Z46YbczqbiE)的视频操作。更老的 Windows 版本可能需要安装第三方 SSH 客户端（比如 [PuTTY](https://youtu.be/pWDHUlvcAsg)），并生成一对 [SSH 密钥](https://youtu.be/4jakCV5JYx0)。

如果你用的是 Linux 或 macOS，打开终端并运行：

```bash
ssh username@ip_address
```

或者带上 SSH 私钥：

```bash
ssh -i private_key username@ip_address
```

输入密码（如果你的 SSH 私钥设了口令，就输入口令）

搞定！你已经远程登录自己的服务器了。

## 你已经是系统管理员了

输入下面的命令，确认你能执行管理任务：

```bash
sudo apt update
```

然后：

```bash
sudo apt upgrade -y
```

这些命令的输出和提示信息不用细究，但成败与否应该一目了然。（遇到询问时选默认项即可。）在 Ubuntu Linux 系统上强制安装更新靠的就是这两条命令，而且只有管理员才能执行。

**重启**

如果这次首次更新检查发现了内核更新，系统可能会提示你重启。这是少数几次你需要重启服务器的场合之一，所以更新完成后就照做：

```bash
sudo reboot now
```

你的服务器现在已经准备就绪，可以开始课程了！

请注意：

* 这台服务器虽然在运行，但没有暴露到互联网上——也就是说，别人无法尝试连接它。我们建议保持这个状态。把一台服务器暴露在云端是一回事，把你家的整个网络暴露出去就是另一回事了。为了你自己的安全，别这么做。

退出登录时，输入 `logout` 或 `exit`。

## 用完之后

不用服务器的时候想把它关掉，直接输入：

```bash
sudo shutdown now
```

或者在 VirtualBox 界面里点 _Force Shutdown_（强制关机）。

## 其他一些选择

* [用 WSL 在 Windows 上安装 Linux](https://learn.microsoft.com/en-us/windows/wsl/install)
* [把旧电脑改造成 Linux 服务器](https://dev.to/jayesh_w/this-is-how-i-turned-my-old-laptop-into-a-server-1elf)
* [在树莓派上安装 Ubuntu Server](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview)
* [在 Docker 容器里跑 Linux](https://docs.docker.com/engine/containers/run/)

**现在你已经准备好开始挑战了。[第 1 天](01.md)，走起！**

> **中文译本说明**：本页为 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 中文版，英文原文以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布，原作者 Steve Brorens，现由 Livia Lima 维护。译文与勘误亦以 CC BY 4.0 发布，详见仓库根目录的 TRANSLATING.md。

部分权利保留。许可条款见
[这里](https://github.com/livialima/linuxupskillchallenge/blob/master/LICENSE)
