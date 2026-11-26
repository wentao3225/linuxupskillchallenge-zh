---
comments: true
---
# 第 0 天 - 在云端创建你自己的服务器（但更便宜）

请先回到[第 0 天 - 获取你自己的服务器](00.md)看看有哪些选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云端（DigitalOcean、Linode、Vultr 这类厂商）](00-VPS-small.md)
* [云端（AWS、Azure、Google Cloud 这类厂商）](00-VPS-big.md)

**提示**：[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ)里有完整的实操演示，覆盖了很多种可能的搭建方式（VirtualBox 本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud），可以帮你选型。

## 开通 VPS（虚拟专用服务器）账号

注册即刻完成——填上邮箱和自己选的密码就进来了！不过，要想创建虚拟机，你可能还得在账号设置里提供信用卡信息（或其他用于计费的信息）。

### 对比

> **译注**：云厂商价格与免费额度变动频繁，以官方页面为准。

| 厂商 | 实例类型 | vCPU | 内存 | 存储 | 价格 | 试用额度 |
| --- | --- | --- | --- | --- | --- | --- |
| [Digital Ocean](https://www.digitalocean.com/) | Basic Plan | 1 | 1 GB | 25 GB SSD | $6.00 | $200 / 60 天 |
| [Linode](https://www.linode.com/) | Nanode 1GB | 1 | 1 GB | 25 GB SSD | $5.00 | $100 / 60 天 |
| [Vultr](https://www.vultr.com/) | Cloud Compute - Regular | 1 | 1 GB | 25 GB SSD | $5.00 | $250 / 30 天 |

想了解更多：

* [Digital Ocean 新手入门](https://docs.digitalocean.com/products/getting-started/)
* [Linode 新手入门](https://www.linode.com/docs/products/platform/get-started/)
* [Vultr 入门与常见问题](https://www.vultr.com/resources/faq/)

## 创建虚拟机

各家 VPS 的流程大同小异，这里给出分步教程：

### 用 Digital Ocean 创建虚拟机（Droplet）

* 在左侧边栏选择 “Manage, Droplets”（管理 → Droplet）。（“droplet” 是 Digital Ocean 给服务器起的可爱小名！）
* 点击 *Create > Droplet*（创建 → Droplet）。
* **Choose Region**（选择区域）：选离你最近的。注意，价格可能因区域而异。
* **DataCenter**（数据中心）：用默认的（它会替你挑一个）。
* **Choose an image**（选择镜像）：选 “Ubuntu” 镜像，挑最新的 LTS（长期支持版）版本。
* **Choose Size**（选择规格）：Basic Plan（共享 CPU）+ Regular，点选 1GB 内存 / 1 CPU / 25GB SSD 磁盘的那一项。
* **Choose Authentication Method**（选择认证方式）：选 “Password”，为 root（根用户）账号设一个强密码。
* *注意：服务器一挂上互联网，立刻就会招来大批机器人，试图对 root 密码进行“暴力破解”。密码一定要够强！*
* **或者，想更安全一点**：选 “SSH Key”，然后[添加一个自己在本地生成的新公钥](https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/)。
* 取个主机名——默认生成的那些实在不好看。
* 创建（Create Droplet）。

### 用 Linode 创建虚拟机（Node）

* 点击 *Create Linode*（“linode” 是 Linode 给服务器起的可爱小名）。
* **Choose an Distribution**（选择发行版）：选 “Ubuntu” 镜像，挑最新的 LTS 版本。
* **Choose Region**（选择区域）：选离你最近的。注意，价格可能因区域而异。
* **Linode Plan**（套餐）：Shared CPU + Nanode 1GB。这一档是 1GB 内存 / 1 CPU / 25GB SSD 磁盘。
* **Linode Label**（标签）：取个主机名——默认生成的那些实在不好看。
* **Choose Authentication Method**（选择认证方式）：在 “Root Password” 里为 root 账号设一个强密码。
* *注意：服务器一挂上互联网，立刻就会招来大批机器人，试图对 root 密码进行“暴力破解”。密码一定要够强！*
* **还有，想更安全一点**：点 “Add An SSH Key”，[添加一个自己在本地生成的新公钥](https://www.linode.com/docs/guides/use-public-key-authentication-with-ssh/)。
* 创建（Create Linode）。

### 用 Vultr 创建虚拟机

* 在左侧边栏选择 “Products, Instances”（产品 → 实例）。（这家没起可爱小名。）
* 点击 *Deploy Server*（部署服务器）。
* **Choose Server**（选择服务器）：Cloud Compute (Shared vCPU) + Intel Regular Performance。
* **Server Location**（服务器位置）：选离你最近的。注意，价格可能因区域而异。
* **Server image**（服务器镜像）：选 “Ubuntu”，挑最新的 LTS 版本。
* **Server Size**（服务器规格）：点选 1GB 内存 / 1 CPU / 25GB SSD 磁盘的那一项。
* **SSH Keys**（SSH 密钥）：点 “Add New”，[添加一个自己在本地生成的新公钥](https://www.vultr.com/docs/deploy-a-new-server-with-an-ssh-key/)。
* *注意：Vultr 不提供只用 root 密码认证的选项，所以你必须创建一个 SSH 密钥。*
* **Server Hostname & Label**（主机名与标签）：给你的服务器取个主机名。
* **取消勾选** “Auto Backups”（自动备份）。课程用不到它，只会多扣钱。
* 部署（Deploy Now）。

## 首次登录（控制台备用方案）

我们打算用 SSH 访问服务器，但如果这一步因为某些原因卡住了，还有一种办法：用控制台（console）进去：

* Digital Ocean：[Droplet 控制台](https://docs.digitalocean.com/products/droplets/how-to/connect-with-console/)
* Linode：[LISH 控制台](https://www.linode.com/docs/products/compute/compute-instances/guides/lish/)
* Vultr：[Web 控制台](https://www.vultr.com/docs/vultr-web-console-faq/)

## 通过 SSH 远程访问

在账号的控制面板里，你应该能看到服务器的 “Public IPv4 address”（公网 IPv4 地址）或类似条目——这是它在互联网上的唯一 IP 地址，也是你日后通过 SSH（Secure Shell 协议）连接它的入口。SSH 的详细内容会在第一课讲。

* **Digital Ocean**：点击 *Networking* 标签页中的 *Public Network > Public IPv4 Address*
* **Linode**：点击 *Network* 标签页中的 *IP Addresses > IPv4 - Public*
* **Vultr**：点击 *Settings* 标签页中的 *Public Network > Address*

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

## 创建一个日常使用的管理员账号

最佳实践之一是不要远程用 “root” 登录，所以我们来创建一个普通用户账号，但它有权在需要时“变身 root”，像这样：

```bash
adduser snori74
```

```bash
usermod -a -G admin snori74
```

```bash
usermod -a -G sudo snori74
```

（当然，把 `snori74` 换成你自己的名字！）

*这个*账号才是你以后登录和操作服务器用的账号。它已被加入 `adm` 和 `sudo` 用户组——在 Ubuntu 系统上，这意味着它可以读取各种日志，并能在需要时通过 _sudo_ 命令“变身 root”。

要用新用户登录，可以先把 [SSH 密钥从 root 复制过来](https://askubuntu.com/questions/1218023/copying-ssh-key-from-root-to-another-user-on-same-machine/1218026#1218026)。

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
