# 翻译与本地化约定（TRANSLATING）

本仓库是 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 的中英双语版。
英文原文是唯一事实来源；中文译文与本文件约定都服务于"让中文读者学到一样的东西"。

## 许可与署名

- 原课程内容基于 **CC BY 4.0** 发布：原作者 Steve Brorens（@snori74），现维护者 Livia Lima（@livialima）。
- 翻译属于 CC BY 4.0 允许的演绎行为。每篇译文页脚必须保留署名声明（见下文"译文页脚"）。
- 对原文内容的**修改**（勘误、过时内容替换）同样允许，但必须在"勘误记录"中登记，做到可追溯。

## 文件组织

- 站点使用 [mkdocs-static-i18n](https://ultrabug.github.io/mkdocs-static-i18n/) 插件的 **suffix 模式**：
  - 英文原文文件**保持原样不动**（`docs/01.md`），方便随时和上游同步；
  - 中文译文加 `.zh` 后缀：`docs/01.zh.md`；
  - `mkdocs.yml` 中 `nav` 只写英文文件名，中文导航由插件的 `nav_translations` 提供标题。
- 新增一篇译文时：复制原文为 `NN.zh.md`，翻译，文末补译文页脚，然后跑 `mkdocs build --strict` 验证。
- 未翻译的页面在中文站点会自动回退显示英文，不会 404，所以翻译可以一篇一篇来。

## 术语表

命令名、代码、文件路径一律不译。概念术语按下表保持全站一致：

### 栏目标题标准译法

每日课程的结构栏目按此统一（此前各批次存在分裂，整合时以此为准修正）：

| 原文栏目 | 标准译法 |
| --- | --- |
| INTRO | 引言 |
| YOUR TASKS TODAY | 今日任务 |
| USING A SSH CLIENT（等大写步骤节） | 按语义意译，如"使用 SSH 客户端" |
| INSTRUCTIONS | 操作步骤 |
| EXTENSION | 扩展 |
| RESOURCES | 资源 |
| TROUBLESHOOT AND MAKE A SAD SERVER HAPPY! | 排障练习：让"伤心服务器"重新开心！ |
| CREDITS | 致谢 |
| Requirements | 前提要求 |

### 引号与标点

- 正文中引用词语统一用**中文弯引号**（""），不用 ASCII 直引号；代码、命令、行内代码内保持原样。

| 英文 | 中文 | 备注 |
| --- | --- | --- |
| server / remote server | 服务器 / 远程服务器 | |
| sysadmin | 系统管理员 | |
| shell | shell | 不译 |
| command line | 命令行 | |
| prompt | 提示符 | |
| root | root（根用户） | 首次出现括注 |
| sudo | sudo | 不译 |
| repository / repo | 软件仓库 / 仓库 | |
| package | 软件包 | |
| PPA | PPA | 不译 |
| permission | 权限 | |
| ownership | 属主 | |
| user / group | 用户 / 用户组 | |
| symlink (symbolic link) | 符号链接 | |
| hard link | 硬链接 | |
| inode | inode | 不译 |
| filesystem | 文件系统 | |
| mount | 挂载 | |
| log | 日志 | |
| log rotation | 日志轮转 | |
| cron / crontab | cron / crontab | 不译 |
| scheduled task | 计划任务 | |
| systemd timer | systemd 定时器 | |
| kernel | 内核 | |
| distro / distribution | 发行版 | |
| LTS | LTS（长期支持版） | 首次出现括注 |
| VPS | VPS（虚拟专用服务器） | 首次出现括注 |
| SSH | SSH | 不译 |
| host key | 主机密钥 | |
| public key / private key | 公钥 / 私钥 | |
| firewall | 防火墙 | |
| port | 端口 | |
| daemon | 守护进程 | |
| service | 服务 | |
| process | 进程 | |
| archive | 归档 | |
| compress | 压缩 | |
| source code | 源码 | |
| build / compile | 构建 / 编译 | |
| man page | 手册页（man page） | 首次出现括注 |
| dotfile | 点文件 | |
| environment variable | 环境变量 | |
| script | 脚本 | |
| shebang | shebang | 不译 |
| terminal | 终端 | |
| session | 会话 | |
| hardening | 加固 | |
| Extension（课程栏目） | 扩展 | |
| swap | swap（交换空间） | 首次出现括注 |
| load average | 负载均值 | |

## 行文风格

1. **人称**：对读者用"你"，还原原文轻松直接的口吻；原文的冷幽默要保留，不要译成说明文。
2. **中英混排**：中文与英文单词、数字之间加一个空格；标点用全角。
3. **代码**：命令、选项、路径、配置片段原样保留，用反引号或代码块；行内代码不加空格包裹（如 `ls -l`）。
4. **首次出现的概念**：中文后括注英文，如"符号链接（symlink）"；之后直接用中文。
5. **章节标题**：原文全大写栏目名照译（INTRO → 引言、YOUR TASKS TODAY → 今日任务、EXTENSION → 扩展、RESOURCES → 资源），保持小节结构一一对应，锚点链接用英文原文标题生成的锚点。
6. **外链**：URL 一律不动；链接文字翻译。视频链接保留英文原题（点开是英文内容），可在后面加中文说明。
7. **版本号、日期、产品名**：保持原样（Ubuntu 24.04、AWS、DigitalOcean 等）。
8. **站内课次链接**：中文译文里指向其他课文的链接用相对路径（如 `[第 3 天](03.md)`），i18n 插件会自动把读者带到对应语言的版本；原文指向官方站的绝对链接（`https://linuxupskillchallenge.org/NN/`）在译文中一律改用相对路径。
9. **锚点**：译文小节标题如被站内链接引用，用 attr_list 显式指定与英文版相同的锚点，如 `## 服务器基本信息 { #general-information-about-the-server }`。
10. **推广链接**：原文中带推广跟踪码的链接（如 Solar-PuTTY 的 `solarwinds.sjv.io` 跳转链）一律去掉，只保留官方直链；这是本 fork 的明确取舍。

## 对原文的修改（勘误）

翻译不等于照搬错误。发现原文硬伤时：

1. 英文原文**同样修改**（本仓库是独立 fork，允许修订），改动能小则小；
2. 中文译文在相应位置加 `> **译注**：……` 说明与原文的差异及原因；
3. 在本文件末尾的"勘误记录"表登记一行，写明日期、文件、问题、处理方式。

### 勘误记录

| 日期 | 文件 | 问题 | 处理 |
| --- | --- | --- | --- |
| 2026-11-25 | docs/15.md | "26.04 is Jammy" 笔误：Jammy 是 22.04 的代号 | 改为 22.04，加译注 |
| 2026-11-25 | docs/01.md | 网络接口查看命令先讲 `ifconfig` 后讲 `ip address`，顺序与现代 Ubuntu 相反 | 调整为先 `ip address`，`ifconfig` 作为旧命令提及 |
| 2026-11-25 | docs/19.md | 用 SysV 时代的 `/etc/rc2.d`、runlevel 讲软链接示例 | 保留示例但补充 systemd 语境的译注说明 |
| 2026-11-25 | docs/06.md | 文内链接 `#option-1---alias-vim`、`#option-2---install-vim` 指向的锚点不存在 | 两个小节标题补 attr_list 显式锚点；`#instructions` 同步补 |
| 2026-11-25 | docs/00-VPS-big.md | 06.md 以 `00-VPS-big.md#intro` 引用本页但无此锚点 | 开篇 H2 "Signing up with a VPS" 补 `{ #intro }` |
| 2026-11-25 | docs/01.zh.md、docs/00-VPS-small.zh.md | 原文含返佣推广链（Solar-PuTTY `*.sjv.io`、DigitalOcean/Linode/Vultr refer 链） | 译文换官方直链；2026-11-26 英文原版同步清理（01.md 删 Solar-PuTTY 项、00-VPS-small.md 三条换官方直链） |
| 2026-11-25 | docs/13.md | 首个用户分组描述过时：现代 Ubuntu 上 `adm` 组管日志读取、`admin` 是遗留空组 | 段落后补英文说明（含 `groups` 自查命令），中文侧已有译注 |
| 2026-11-25 | docs/11.md、docs/12.md | linux.com 教程路径迁移、ArsTechnica `.ars` 路径退役、ssh.com SFTP 迁至 academy | 均替换为验证过的现行 URL，中英同步 |
| 2026-11-25 | docs/00-Google-Cloud.md | connecting-advanced 页退役、`#thirdpartytools` 锚点消失 | 换为现行等效页 standard-ssh，中英同步 |
| 2026-11-26 | docs/10.md | crontab 语法图星期字段写 0–7、正文条目写 0–6，前后不一致（0=7 均为周日） | 正文改为 0–7（与图及 Ubuntu man 5 crontab 一致），中文侧已有译注 |
| 2026-11-26 | docs/02、03、04、14、15、16.md | 9 处外链失效：gsp.com 404、slant.co 526、impish 手册页 404、craigmbooth 404、RHEL7 PDF 重定向、help.ubuntu.com 社区 Wiki 退役 ×4、manned.org ×2、catcode.com 路径消失、Medium 反爬存疑 | 全部替换为经 web_fetch 验证的现行页（ss64、DigitalOcean ×3、linuxize、manpages noble、Red Hat 现行页、ubuntu.com/server/docs、man.archlinux.org ×2），中英同步；docs.redhat.com 一条因抓取器 403 未能直接复验 |
| 2026-11-26 | docs/00-Local-Server.md、docs/how-this-works.md | docs.microsoft.com 旧域、Medium 反爬链、Linux Journey 整站迁移（2026-06 官方公告 → LabEx） | 分别换为 learn.microsoft.com、docs.docker.com/engine/containers/run/、labex.io/lesson/linux-history，中英同步 |
| 2026-11-26 | docs/18.md | library.linode.com 整库下线，logrotate 指南 404 | 换为 Akamai techdocs 现行承接页（含 Rotate logs 小节），中英同步；其余 4 条疑似链经实测存活未动 |

## 译文页脚

每篇 `.zh.md` 文末（原版权声明之前）加入：

```markdown
> **中文译本说明**：本页为 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 中文版，英文原文以
> [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布，原作者 Steve Brorens，现由 Livia Lima 维护。
> 译文与勘误亦以 CC BY 4.0 发布，详见 [TRANSLATING.md](https://github.com/<你的用户名>/<你的仓库名>/blob/master/TRANSLATING.md)。
```

仓库 URL 在开源发布前替换成实际地址。

## 验证清单（每篇译文完成后）

- [ ] `mkdocs build --strict` 无警告
- [ ] 文内锚点、站内链接在中文页面上可跳转
- [ ] 术语与上表一致
- [ ] 文末已加译文页脚
- [ ] 对原文的修改已登记"勘误记录"
