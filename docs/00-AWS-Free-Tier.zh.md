---
comments: true
---
# 第 0 天 - 创建你自己的服务器 - 使用 AWS 免费套餐（Free Tier）

请回看[第 0 天 - 搞到一台自己的服务器](00.md)，了解你的各种选择：

* [本地服务器/虚拟机](00-Local-Server.md)
* [在云上（DigitalOcean、Linode、Vultr 等厂商）](00-VPS-small.md)
* [在云上（AWS、Azure、Google Cloud 等厂商）](00-VPS-big.md)

> **译注**：云厂商的价格、免费额度与控制台界面变动频繁，本文细节可能过时，请以官方页面为准。

**提示**：可以看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=2892s)里的完整演示。这个视频覆盖了很多种可能的搭建方式（VirtualBox 本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## AWS 免费套餐，真的始终免费吗？

AWS 免费套餐（Free Tier）的设计初衷，是让新用户在注册 AWS 后的 12 个月内、在一定用量限制下，免费探索和试用各种 AWS 服务。12 个月免费期一到，或者你的用量超出了免费额度，就按标准的按量付费（pay-as-you-go）服务费率收费。如果你符合条件，还可以通过 Educate 套餐（Educate Pack）延长免费使用期。

## 通过 AWS Educate 套餐注册

* 前往 AWS Educate 网站：https://aws.amazon.com/education/awseducate/
* 点击页面右上角的 “Join AWS Educate”（加入 AWS Educate）按钮。
* 选择最符合你身份的选项——学生还是教育工作者。
* 填写姓名、电子邮箱、学校或机构名称等必要信息，创建 AWS Educate 账户。
* 账户创建好之后，你就可以使用 AWS Educate Starter Account（入门账户）：内含 100 美元的 AWS 赠金（Promotional Credits）、25 项以上 AWS 服务的免费使用权限，还有帮你上手 AWS 的自学实验（lab）和教程。

请注意，AWS Educate 计划面向的是想学习云计算和 AWS 服务的学生与教育工作者。要获得参与资格，你需要提供学生或教育工作者身份的证明。

## 注册 AWS

注册过程相当简单——只需提供你的电子邮箱和一个自选密码，外加一个用于双因素认证（2FA，即第二种身份验证方式）的手机号。
你还需要提供 VISA 或其他信用卡信息。

* 支持计划（Support Plan）选择 “Basic Plan/Free”（基础计划/免费）

注销后重新登录，然后依次选择：

* 顶部菜单里的 Services（服务）
* 服务列表中的 EC2

用 AWS 的话说，我们要创建的服务器是一台 “EC2 compute instance”（EC2 计算实例）——现在点击 “Launch Instance”（启动实例）。接下来会列出若干镜像（image）选项，选一个名称里带 “Ubuntu Server LTS” 的。
在下一屏选择实例类型——通常只有 “t2.micro” 符合免费套餐资格，用它就挺好，然后选择 “review and Launch”（审核并启动）。
在审核页面会看到 “Security Groups”（安全组）选项——它其实是 AWS 默认提供的防火墙配置。总体上这是件好事，但本课程需要我们的服务器完全暴露在外，所以我们要把它改成实质上不设防的状态，操作如下：

* 选择 “Configure Security Group”（配置安全组）
* 选择 “Add Rule”（添加规则）
* 类型（Type）选 “All traffic”（所有流量），来源（Source）选 “Anywhere”（任意位置）

这会把所有端口、所有协议都对任意来源开放。对生产服务器来说这么做并不明智，但这正是本课程想要的。

现在点击 “Launch”（启动）。提示你提供密钥对（key pair）时，创建一个即可。

你的服务器实例这时应该已经启动，可以按下面的路径登录：

* Services → EC2 → Running instances → Connect

## 通过 SSH 远程访问

在账户控制面板里，你应该能看到这台服务器的 “Public IPv4 address”（公有 IPv4 地址）或类似条目——这就是它在互联网上的唯一 IP 地址，之后你就要通过 SSH（Secure Shell 协议）用它来连接服务器。具体怎么连，第一课会讲。

这个视频 [How to Set Up AWS EC2 and Connect to Linux Instance with PuTTY](https://www.youtube.com/watch?v=kARWT4ETcCs) 对整个过程讲得很清楚。

你将以 `ubuntu` 用户登录。该用户已被加入 `adm` 和 `sudo` 用户组，在 Ubuntu 系统上，这意味着它既可以读取各种日志，也可以在需要时通过 _sudo_ 命令“成为 root（根用户）”。

## 你现在是系统管理员了

输入下面的命令，确认你能执行管理任务：

```bash
sudo apt update
```

（按常理这条命令会要求你输入密码确认，但由于你用的是公钥认证，系统从未让你设置过密码——而且 AWS 已经把 `sudo` 配置成对 `ubuntu` 用户不要求密码。）

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
