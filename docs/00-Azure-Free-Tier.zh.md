---
comments: true
---
# 第 0 天 - 创建你自己的服务器 - 使用 Azure 免费额度（Free Credits）

请回看[第 0 天 - 搞到一台自己的服务器](00.md)，了解你的各种选择：

* [本地服务器/虚拟机](00-Local-Server.md)
* [在云上（DigitalOcean、Linode、Vultr 等厂商）](00-VPS-small.md)
* [在云上（AWS、Azure、Google Cloud 等厂商）](00-VPS-big.md)

> **译注**：云厂商的价格、免费额度与控制台界面变动频繁，本文细节可能过时，请以官方页面为准。

**提示**：可以看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=7020s)里的完整演示。这个视频覆盖了很多种可能的搭建方式（VirtualBox 本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## 注册 Azure

注册过程相当简单——只需提供你的电子邮箱和一个自选密码，外加一个用于双因素认证（2FA，即第二种身份验证方式）的手机号。Azure 对“企业”邮箱（比如工作邮箱或你自己的域名邮箱）有时会比较挑剔。如果是这种情况，就用注册页面上的链接新建一个 @outlook 或 @gmail.com 账户。
你还需要提供 VISA 或其他信用卡信息。

* 点击 “start building in azure”（开始在 Azure 中构建）
* 点击 “Deploy a virtual machine”（部署虚拟机）
* 点击 “Create a linux virtual machine”（创建 Linux 虚拟机）
* 搜索并选择 Ubuntu Server LTS
* 机型（size）选 Standard `D2s_v3`——就本课程的时长而言，试用额度应该能轻松覆盖它的费用
* 认证方式（authentication）确保选了 “SSH Public Key”（SSH 公钥），且 SSH Public Key source（SSH 公钥来源）选了 “generate new key pair”（生成新密钥对）
* “allow selected ports”（允许的端口）暂时保持 “ssh (22)”
* 点击 “Review + Create”（审阅并创建）
* Azure 会生成并下载用于 SSH 登录这台机器的私钥文件——
* （Windows）在 Windows 上双击打开该文件，密钥就会被添加到这台机器的证书存储（cert store）里
* （Mac OS X 和 Linux）运行命令 `sudo ssh-add -K /link-to-downloaded-file`
* 注意：如果上面的命令不管用，就去掉 `sudo` 再试。如果出现权限相关的错误，先运行 `chmod 400 filename`
* 用 `ssh azureuser@PUBLICIP` 连接这台机器

接下来，把这台机器的所有端口完全向互联网开放：

* 打开 <https://portal.azure.com/#home>
* 选择 “Virtual Machines”（虚拟机）
* 选中你刚创建的虚拟机，在设置窗格（settings pane）中选择 “Networking”（网络）
* 点击 “Inbound Port Rules”（入站端口规则）和 “Add inbound port rule”（添加入站端口规则）
* 把 “source port ranges”（源端口范围）和 “destination port ranges”（目标端口范围）都设为 `*`，“Source”（源）和 “Destination”（目标）都设为 “any”（任意）；确认协议（protocol）设为 “any”、操作（action）设为 “allow”（允许）；优先级（priority）设为 100，再取一个合适的名称
* 点击 “Outbound port rules”（出站端口规则）和 “add outbound port rule”（添加出站端口规则）
* 把 “source port ranges”（源端口范围）和 “destination port ranges”（目标端口范围）都设为 `*`，“Source”（源）和 “Destination”（目标）都设为 “any”（任意）；确认协议（protocol）设为 “any”、操作（action）设为 “allow”（允许）；优先级（priority）设为 101，再取一个合适的名称

这会把所有端口、所有协议都对任意来源开放。对生产服务器来说这么做并不明智，但这正是本课程想要的。

## 通过 SSH 远程访问

确认你的机器处于 “running”（运行中）状态（如果不是，点击 “start”（启动）），然后通过 “connect -> ssh”（连接 -> SSH）下拉菜单，按其中的说明连接。

你将以 `azureuser` 用户登录。该用户已被加入 `adm` 和 `sudo` 用户组，在 Ubuntu 系统上，这意味着它既可以读取各种日志，也可以在需要时通过 _sudo_ 命令“成为 root（根用户）”。

## 你现在是系统管理员了

输入下面的命令，确认你能执行管理任务：

```bash
sudo apt update
```

（按常理这条命令会要求你输入密码确认，但由于你用的是公钥认证，系统从未让你设置过密码——而且 Azure 已经把 `sudo` 配置成对 `azureuser` 用户不要求密码。）

接着：

```bash
sudo apt upgrade -y
```

不用太纠结这些命令的输出和提示信息，但成功与否应该一目了然。（遇到询问时，按默认选项回应即可。）在 Ubuntu Linux 系统上，强制安装更新靠的就是这些命令，而且只有管理员才能执行。

**重启**

如果这轮首次更新检查发现了内核（kernel）更新，系统可能会要求你重启。这是整个课程里少有的几次需要重启服务器的场合之一，所以更新完成后就重启吧：

```bash
sudo reboot now
```

至此，你的服务器已经全部配置完毕，可以开始课程了！

请注意：

* 这台服务器正在运行，而且完全暴露在整个互联网面前
* 管理它的责任完全落在你一个人身上
* 你刚刚装好了最新更新，所以目前应该是安全的

要退出登录，输入 `logout` 或 `exit`。

## 课程结束后

在课程的这一个月里让这台 VM（虚拟机）一直开着运行应该是安全的，但你随时可以 **Stop**（停止）实例。不过要注意，停止之后它仍会计入账单。

等到不再需要这台 VM 时，就 **Terminate/Destroy**（终止/销毁）实例。

**现在你已经准备好开始挑战了。[第 1 天](01.md)，出发！**

> **中文译本说明**：本页为 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 中文版，英文原文以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布，原作者 Steve Brorens，现由 Livia Lima 维护。译文与勘误亦以 CC BY 4.0 发布，详见仓库根目录的 TRANSLATING.md。

部分权利保留。许可条款见[这里](https://github.com/livialima/linuxupskillchallenge/blob/master/LICENSE)
