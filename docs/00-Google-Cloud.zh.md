---
comments: true
---
# 第 0 天 - 创建你自己的服务器 - 使用 Google Cloud Platform 免费套餐（Free Tier）

请回看[第 0 天 - 搞到一台自己的服务器](00.md)，了解你的各种选择：

* [本地服务器/虚拟机](00-Local-Server.md)
* [在云上（DigitalOcean、Linode、Vultr 等厂商）](00-VPS-small.md)
* [在云上（AWS、Azure、Google Cloud 等厂商）](00-VPS-big.md)

> **译注**：云厂商的价格、免费额度与控制台界面变动频繁，本文细节可能过时，请以官方页面为准。

**提示**：可以看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=8778s)里的完整演示。这个视频覆盖了很多种可能的搭建方式（VirtualBox 本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## 注册 GCP

注册过程相当简单——只需提供你的电子邮箱和一个自选密码，外加一个用于双因素认证（2FA，即第二种身份验证方式）的手机号。
你还需要提供 VISA 或其他信用卡信息。

* 选择 “Compute Engine”（计算引擎），点击 “VM Instances”（虚拟机实例）
* 创建一个新实例
* 区域（region）随便选你想要的
* 在机器配置（Machine Configuration）里，系列（series）选 “E2”，机器类型（machine type）选 “e2-micro”
* 把启动磁盘（boot disk）改为 “Ubuntu LTS”

创建好自己的服务器之后，我们需要把所有端口、所有协议都对任意来源开放。对生产服务器来说这么做并不明智，但这正是本课程想要的。

进入你的 GCP 主页，依次打开 Networking > VPC Network > Firewall > Create Firewall（网络 > VPC 网络 > 防火墙 > 创建防火墙）

把 “Direction of Traffic”（流量方向）设为 “Ingress”（入站）
把 “Target”（目标）设为 “All instances in the network”（网络中的所有实例）
把 “Source Filter”（来源过滤条件）设为 “IP Ranges”（IP 范围）
把 “Source IP Ranges”（来源 IP 范围）设为 `0.0.0.0/0`
把 “Protocols and Ports”（协议和端口）设为 “Allow All”（全部允许）
创建，然后重复上述步骤再新建一条防火墙规则，并把 “Direction of Traffic”（流量方向）设为 “Egress”（出站）

## 首次登录

选中你的实例并点击 “SSH”，会打开一个新的窗口控制台。要取得 root（根用户）身份，在命令行输入 `sudo -i passwd`，然后设置你自己的密码。接着输入 `su` 和你的密码登录。注意：无论键入还是粘贴，密码都不会显示出来。

## 通过 SSH 远程访问

如果你打算用第三方工具（比如 PuTTY）访问服务器，也可以参考 <https://cloud.google.com/compute/docs/connect/standard-ssh>。

## 你现在是系统管理员了

输入下面的命令，确认你能执行管理任务：

```bash
sudo apt update
```

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
