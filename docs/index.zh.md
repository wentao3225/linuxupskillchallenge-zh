# Linux Upskill Challenge
## 学习用命令行管理远程 Linux 服务器所需的技能。

这是一个为期一个月的课程，面向那些渴望在业内获得 Linux 相关工作的人——初级 Linux 系统管理员、DevOps 相关岗位及类似工作。课程以服务器和命令行为核心，但基本上不预设任何先备知识，起步非常平缓——无论你是 Windows 或 Apple 用户，还是已经在以某种形式使用 Linux 的人，都能轻松跟上。

**Linux Upskill Challenge 是免费开源的——并且永远如此。**
如果这个课程帮到了你，欢迎支持它的持续维护：[捐赠](https://www.buymeacoffee.com/livialima) 或 [赞助](https://github.com/sponsors/livialima)。

所有核心学习材料全年可得。无需订阅、无需注册——除了你的时间，不花你一分钱！

### 课程讲些什么？

1. 把 Linux 学到足以管理自己的服务器
2. 重点在实用技能
3. 大量动手实操
4. 用一个月习得技能，每天投入 1-2 小时
5. 大量精选的外部链接
6. 远没有 RHEL 或 Linux Foundation 的培训那么“正式”

## 从这里开始

首先，看看 [FAQ，了解挑战的运作方式](how-this-works.md)，你的大部分问题都能在那里得到解答。

还有一个 Linux 用户组（LUG）关于本课程的演讲，配有幻灯片、播客和视频资料：[KWLUG Meeting - Linux Upskill Challenge](https://kwlug.org/node/1381)

如果你跃跃欲试，就需要一台属于自己的、暴露在互联网上的服务器——不过我们也提供了完整的说明，教你如何免费或低价把它搭起来。

课程在每月的第一个周一重新开始，所以就算第一轮没能跟上也不必担心！

## 目录

* [运作方式与常见问题](how-this-works.md) - 请务必先读这一篇！
* [第 0 天](00.md) - **搭建你自己的服务器**：如何在 AWS、Azure、Google Cloud、Oracle Cloud、Digital Ocean、Linode、Vultr 上搭建你的实验环境，以及在本地服务器上搭建！
* [第 1 天](01.md) - **认识你的服务器**：从 `ssh` 登录和几条简单命令开始，比如 `ls`、`uptime`、`free`、`df -h`、`uname -a`。扩展部分讲如何用公钥实现免密登录，以及 `ssh` 配置文件。
* [第 2 天](02.md) - **基本导航**：基本导航操作、手册页（man page）、文件层级
* [第 3 天](03.md) - **权力之旅！**：使用 `sudo`、`uptime`、时区，修改你的主机名
* [第 4 天](04.md) - **安装软件、探索文件结构**：用 `apt` 查找并安装软件；用 `mc` 浏览文件系统；查看 `/etc/passwd`、`/etc/ssh/sshd_config` 和 `/var/log/auth.log` 的内容
* [第 5 天](05.md) - **或多或少……**：使用 `more`、`less` 并在其中翻页浏览；点文件（dotfile）、历史记录、Tab 补全，以及 `nano` 文本编辑器的使用
* [第 6 天](06.md) - **用“vim”编辑**：学习 `vim` 最精要的知识，也可以借助 `vimtutor`
* [第 7 天](07.md) - **服务器与其服务**：安装 Apache2、停止与启动、修改内容、阅读日志
* [第 8 天](08.md) - **“恶名在外”的 grep 与其他文本处理工具**：上手 `grep`、`cat`、`more`、`less`、`cut`、`awk`、`tail` 这类文本工具——当然还有管道。（顺带向 `awk` 和 `sed` 挥挥手）
* [第 9 天](09.md) - **深入网络**：用 `ss` 查看开放端口（顺带提一句 `netstat`），安装 `nmap` 并测试；安装 `ufw`，进行配置、启用和测试等。讨论作为系统管理员的安全责任。
* [第 10 天](10.md) - **计划任务**：涵盖 `cron`、`at` 和 systemd 定时器
* [第 11 天](11.md) - **查找东西……**：用 `locate`、`find`、`grep`、`which` 查找东西
* [第 12 天](12.md) - **传输文件**：SFTP 这门技术、各类客户端，以及上行与下行拷贝
* [第 13 天](13.md) - **用户与用户组**：用 `adduser`、`visudo` 设置一个受限的“帮手”来管理我们的主机
* [第 14 天](14.md) - **谁有权限？**：权限、用户、用户组（ACL 和 SELinux 放在扩展部分）
* [第 15 天](15.md) - **深入软件仓库……**：更详细地介绍软件仓库、如何启用“Multiverse”、PPA 在 Ubuntu 中的角色，以及如何启用 PPA 并从中安装
* [第 16 天](16.md) - **归档与压缩**：理解并使用 `tar` 和 `gzip`
* [第 17 天](17.md) - **从源码构建**：从源码安装。讨论：用 `wget` 获取 tarball，用 `tar` 解包，然后 configure、make、install。还会讨论安全与维护问题。
* [第 18 天](18.md) - **日志、监控与排障**：日志管理与日志轮转，`logrotate`
* [第 19 天](19.md) - **inode、符号链接及其他捷径**：inode、硬链接、符号链接与 `stat`
* [第 20 天](20.md) - **脚本编写**：理解 Linux 中脚本是如何工作的：shebang、权限与 $PATH。基于我们一直在做的日志过滤，写几个简单的示例脚本。还有供进一步探索的资源。
* [第 21 天](21.md) - **接下来呢？**：以一些建议为课程收尾。

> **中文译本说明**：本页为 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 中文版，英文原文以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布，原作者 Steve Brorens，现由 Livia Lima 维护。译文与勘误亦以 CC BY 4.0 发布，详见仓库根目录的 TRANSLATING.md。
