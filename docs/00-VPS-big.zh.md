---
comments: true
---
# 第 0 天 - 在云端创建你自己的服务器

请先回到[第 0 天 - 获取你自己的服务器](00.md)看看有哪些选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云端（DigitalOcean、Linode、Vultr 这类厂商）](00-VPS-small.md)
* [云端（AWS、Azure、Google Cloud 这类厂商）](00-VPS-big.md)

**提示**：[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ)里有完整的实操演示，覆盖了很多种可能的搭建方式（VirtualBox 本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud），可以帮你选型。

## 开通 VPS（虚拟专用服务器）账号 { #intro }

注册相当简单——填上你的邮箱和自己选的密码就行，另外要提供一个用于双因素认证（2FA）或其他二次验证方式的手机号。你还需要提供信用卡信息。

### 对比

> **译注**：云厂商价格与免费额度变动频繁，以官方页面为准。

| 厂商 | 实例类型 | vCPU | 内存 | 存储 | 价格* | 试用额度 |
| --- | --- | --- | --- | --- | --- | --- |
| [AWS](https://aws.amazon.com/free/) | t2.micro | 1 | 1 GB | 8 GB SSD | $18.27 | 免费套餐（Free Tier）1 年 |
| [Azure](https://azure.microsoft.com/free/) | B1 | 1 | 1 GB | 30 GB SSD | $12.26 | $200 / 30 天 + 免费套餐 1 年 |
| [GCP](https://cloud.google.com/free/docs/free-cloud-features) | e2-micro | 1 | 1 GB | 10 GB SSD | $7.11 | $300 / 90 天 |
| [Oracle](https://www.oracle.com/cloud/free/) | VM.Standard.E2.1.Micro | 1 | 1 GB | 45 GB SSD | $19.92 | $300 / 30 天 + Always Free 服务 |

* *预估价格*

顺带一提：IBM Cloud 能躲多远躲多远。它家没什么好价，而且据往期学员反馈，它的 Linux 虚拟机被定制魔改得太多，有些命令的表现会和预期不符。

### 教育优惠计划

* AWS Educate：[https://aws.amazon.com/education/awseducate/](https://aws.amazon.com/education/awseducate/)
* Azure for Students：[https://azure.microsoft.com/en-gb/free/students/](https://azure.microsoft.com/en-gb/free/students/)
* Google Cloud for Students：[https://cloud.google.com/edu/students](https://cloud.google.com/edu/students)
* Oracle Academy Cloud Program：[https://academy.oracle.com/en/solutions-cloud-program.html](https://academy.oracle.com/en/solutions-cloud-program.html)

## 创建虚拟机

各家 VPS 的流程大同小异，这里给出几个分步教程：

* [用 AWS 创建虚拟机](00-AWS-Free-Tier.md)
* [用 Azure 创建虚拟机](00-Azure-Free-Tier.md)
* [用 GCP 创建虚拟机](00-Google-Cloud.md)

### 用 Oracle Cloud 创建虚拟机

* 在左侧边栏菜单选择 “Compute, Instances”（计算 → 实例）。
* 点击 *Create Instance*（创建实例）。
* 取个主机名——默认生成的那些实在不好看。
* **Placement**（位置）：会自动选离你最近的区域。
* **Change Image**（更改镜像）：选 “Ubuntu” 镜像，并挑最新的 LTS（长期支持版）版本。
* **Change Shape**（更改配置）：点 “Specialty and previous generation”，然后选 *VM.Standard.E2.1.Micro*——1GB 内存 / 1 CPU、符合 Always Free 条件的那一项。
* **Add SSH Keys**（添加 SSH 密钥）：选 “Generate a key pair for me”，把私钥下载下来，之后用它连接 SSH。你也可以[添加一个自己在本地生成的新公钥](https://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/compute-iaas/generating_ssh_key/generate_ssh_key.html#summary)。
* 创建（Create）。

## 首次登录

选中你的实例，点击 “SSH”，会打开一个新的控制台窗口。想以 root（根用户）身份操作，先在命令行输入 `sudo -i passwd` 设置 root 密码，然后输入 `su` 加你刚设的密码登录。注意：无论手敲还是粘贴，密码都不会显示出来。

## 通过 SSH 远程访问

在账号的控制面板里，你应该能看到服务器的 “Public IPv4 address”（公网 IPv4 地址）或类似条目——这是它在互联网上的唯一 IP 地址，也是你日后通过 SSH（Secure Shell 协议）连接它的入口。SSH 的详细内容会在第一课讲。

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

### 那 *root* 用户呢？

大厂的套路和小 VPS 不一样：他们不允许你直接用 root 连接。别担心，**root** 在系统里依然存在，只是厂商一开始就帮你建好了管理员用户，你不必跟 root 打交道。

## 你已经是系统管理员了

输入下面的命令，确认你能执行管理任务：

```bash
sudo apt update
```

（按常理这条命令会要求你确认密码，但你一直在用公钥认证，系统从没让你设过密码——而且 AWS 已经为 `ubuntu` 用户配置了免密码 `sudo`。）

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

* 这台服务器正在运行，并且完全暴露在整个互联网面前
* 管理它的责任完全在你一个人
* 你刚装好了最新更新，所以眼下应该是安全的

退出登录时，输入 `logout` 或 `exit`。

## 用完之后

挑战期间让虚拟机跑满一个月问题不大，但你随时可以 **Stop**（停止）实例——不过注意，停止之后照样计费。

不再需要这台虚拟机时，就 **Terminate/Destroy**（终止/销毁）实例。

**现在你已经准备好开始挑战了。[第 1 天](01.md)，走起！**

> **中文译本说明**：本页为 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 中文版，英文原文以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布，原作者 Steve Brorens，现由 Livia Lima 维护。译文与勘误亦以 CC BY 4.0 发布，详见仓库根目录的 TRANSLATING.md。

部分权利保留。许可条款见
[这里](https://github.com/livialima/linuxupskillchallenge/blob/master/LICENSE)
