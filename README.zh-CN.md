<div align="center" width="100%">
  <h1>Linux 运维进阶挑战</h1>
  <h3>Linux Upskill Challenge 中文双语版</h3>
  <p><a href="README.zh-CN.md">简体中文</a> | <a href="README.md">English</a></p>
</div>

通过命令行学习远程 Linux 服务器的系统管理——一个面向想入行初级 Linux 系统管理员、DevOps 等岗位的人的免费月度课程。

**本项目是 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 的中文双语版**，基于上游开源课程翻译改造：

- 原课程由 Steve Brorens（@snori74）创作，现由 [Livia Lima](https://github.com/livialima) 维护，以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 开源；
- 中文版在此之上做了：全部课程的中文翻译（英文原版保留，站点可切换语言）、若干内容勘误（见 [TRANSLATING.md](TRANSLATING.md) 的勘误记录）、每课附命令速查表；
- 译文与修改同样以 CC BY 4.0 发布。

## 这是什么课？

- 目标：学会管理一台属于自己的远程 Linux 服务器
- 强度：一个月，每天 1–2 小时，Day 0 起步，全程动手
- 受众：零基础也行，Windows/Mac 用户友好；课程风格远比 RHEL 或 Linux Foundation 的培训随意
- 实验环境：推荐租一台便宜的 VPS，课程提供了 AWS / Azure / Google Cloud / DigitalOcean 免费或低价方案的详细指引，也有本地虚拟机方案

## READ THIS FIRST

先读 [课程机制与常见问题](docs/how-this-works.zh.md)（英文原版见 [docs/how-this-works.md](docs/how-this-works.md)）。

## 目录

* [Day 0](docs/00.zh.md) - **搭建你自己的服务器**：AWS、Azure、Google Cloud、DigitalOcean 与本地服务器的搭建指引
* [Day 1](docs/01.zh.md) - **认识你的服务器**：SSH 登录与 `ls`、`uptime`、`free`、`df -h`、`uname -a` 等基础命令；扩展部分讲公钥免密登录与 ssh 配置文件
* [Day 2](docs/02.zh.md) - **基础导航**：目录跳转、man 手册页、文件系统层级
* [Day 3](docs/03.zh.md) - **权限加身！**：`sudo`、时区、修改主机名
* [Day 4](docs/04.zh.md) - **安装软件、探索文件结构**：用 `apt` 装软件；看 `/etc/passwd`、`/etc/ssh/sshd_config` 和 `/var/log/auth.log`
* [Day 5](docs/05.zh.md) - **more 与 less**：翻页阅读、点文件、历史与 Tab 补全、nano 编辑器
* [Day 6](docs/06.zh.md) - **用 "vim" 编辑**：vim 的最基础知识与 `vimtutor`
* [Day 7](docs/07.zh.md) - **服务器与其服务**：装 Apache2、启停服务、改页面、读日志
* [Day 8](docs/08.zh.md) - **大名鼎鼎的 "grep" 与其他文本工具**：`grep`、`cut`、`awk`、`tail` 与管道
* [Day 9](docs/09.zh.md) - **深入网络**：`ss` 看端口、`nmap` 测试、`ufw` 防火墙
* [Day 10](docs/10.zh.md) - **计划任务**：`cron`、`at` 与 systemd 定时器
* [Day 11](docs/11.zh.md) - **查找文件**：`locate`、`find`、`grep`、`which`
* [Day 12](docs/12.zh.md) - **传输文件**：SFTP 的原理与客户端
* [Day 13](docs/13.zh.md) - **用户与用户组**：`adduser`、`visudo`，配置一个受限的"管理员帮手"
* [Day 14](docs/14.zh.md) - **权限归谁？**：权限、用户、用户组（扩展部分讲 ACL 与 SELinux）
* [Day 15](docs/15.zh.md) - **深入软件仓库**：软件源机制、snap 与 flatpak
* [Day 16](docs/16.zh.md) - **归档与压缩**：`tar` 与 `gzip`
* [Day 17](docs/17.zh.md) - **从源码构建**：`wget` 下载源码包、configure / make / install 及其安全与维护问题
* [Day 18](docs/18.zh.md) - **日志轮转**：`logrotate` 的配置与管理
* [Day 19](docs/19.zh.md) - **inode、符号链接与其他捷径**：inode、硬链接、软链接与 `stat`
* [Day 20](docs/20.zh.md) - **脚本编写**：shebang、权限与 `$PATH`，几个基于日志过滤的小脚本
* [Day 21](docs/21.zh.md) - **下一步？**：结业建议

## 参与贡献

- 发现翻译问题或内容错误：开 Issue 或直接提 PR；
- 翻译前请阅读 [TRANSLATING.md](TRANSLATING.md)（术语表与风格约定，新译文必须遵守）；
- 修改英文原版内容（勘误）时，需同步在 TRANSLATING.md 的勘误记录登记。

## 开源发布

准备把本仓库部署上线时，按 [RELEASING.md](RELEASING.md) 的清单检查：站点地址、评论区、统计 ID 等都指向原作者的项目，需要先替换成你自己的。
