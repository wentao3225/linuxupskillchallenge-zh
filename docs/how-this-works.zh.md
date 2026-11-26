# 建议先读这一篇：运作方式与常见问题

## 资源

* [课程官网](https://LinuxUpskillChallenge.org)
* [课程完整源码](https://github.com/livialima/linuxupskillchallenge)
* [教学视频与补充视频](https://www.youtube.com/@livia2lima/search?query=linuxupskillchallenge)
* [Lemmy 上的每月课程](https://programming.dev/c/linuxupskillchallenge)
* [Reddit 上的每月课程](https://www.reddit.com/r/linuxupskillchallenge/)
* [Discord 聊天室](https://discord.gg/linux-upskill-challenge-682046666928685068)

## 运作方式

### 简而言之

* 完全免费、开源
* 聚焦实用技能
* 大量动手实操，全程在命令行上完成
* 每月第一个周一开课
* 持续 20 个工作日（周一至周五）
* 经常指向精选的外部链接，扩展当天的话题
* 远没有 RHEL 或 Linux Foundation 的培训那么“正式”

### 前提要求

* 每节课投入 1-2 小时、坚持一个月，但也可以按自己的节奏来
* 一台云上的 Ubuntu Linux 服务器（推荐），或者有办法自己搭建一台本地 Linux 服务器。_- 关于如何搭建的完整说明，见“第 0 天”的几篇课文。_
* 具备基本的电脑使用能力——不要求有任何 Linux 基础，但你应该能比较熟练地操作自己的 Windows/Mac 电脑，并且懂得排查自己系统上的问题。_- 这是一门只聚焦 Linux 的课程；访问 Linux 服务器所需的 Windows/Mac 设置也有说明，但它们不是重点。_

## 常见问题（FAQ）

### 这门课适合我吗？

本课程主要面向两类人：

1. 希望在业内获得 Linux 相关工作的 Linux 用户，比如初级 Linux 系统管理员、DevOps 相关岗位及类似工作；
2. 想扩展自己的知识、以便能管理 Linux 服务器的 Windows 服务器管理员。

不过，也有很多人愉快地用这门课来**提升自己的 Linux 命令行技能**，或者**第一次学 Linux**——这也完全可以。

### 上了这门课，我能通过 LPIC/RHCA/LFCS/Linux+ 认证吗？

**不能！这不是任何 Linux 认证考试的备考课程。**它当然能帮到你，但如果你的目标就是考证，请去找更对口的认证培训。

### 需要在什么地方注册吗？还是每天读帖跟着做就行？

不需要注册。跟着学、分享你的经历就好。

### 完成挑战后会拿到证书吗？

目前没有证书。不过如果你愿意，也可以去 [Lemmy](https://programming.dev/c/linuxupskillchallenge)、[Reddit](https://www.reddit.com/r/linuxupskillchallenge/) 或 [Discord](https://discord.gg/linux-upskill-challenge-682046666928685068) 上炫耀一番。

### 什么时候开始？

课程总是在**每月的第一个周一**开始。课程的一个关键设计是：内容以 20 节小课的形式交付，每个工作日一节，月月如此。

### 要花多长时间？该投入多少小时？

取决于你的经验和投入程度，每节课预计要花 1-2 小时。头几天相当基础，可能几分钟就能完成，不过一般都会有一些“扩展”内容给你加点料。

### 我刚听说这个挑战，可它已经进行到第 X 天了。要等到下个月再开始吗？

想等就等。学习材料[全年可得](https://github.com/livialima/linuxupskillchallenge)，所以你完全可以按自己的节奏来。

### 我真的需要一台云服务器吗？ { #do-i-really-need-a-cloud-based-server }

需要。如果你属于目标受众（见上文），那就确实应该。这样一台服务器远在别处、对整个互联网的攻击敞开着，恰恰因此才“动起真格”。学会搭建这样一台 VPS（虚拟专用服务器），对任何系统管理员来说也是一项实用技能。

**NEW!** 现在你可以跳过这整个环节，直接使用我们的 [Killercoda 场景](https://killercoda.com/linux-upskill-challenge)。请注意它仍处于测试阶段，可能存在一些限制。

几家服务商搭建合适服务器的说明都写在“第 0 天”课文里。你尽可以用别的服务商，但请确保使用 Ubuntu LTS（最好是最新版本），并且要么使用公钥认证，要么使用一个*长、强、唯一*的密码（我们也提供了相应的操作说明）。

当然，你也完全可以用本地虚拟机、树莓派甚至只是 WSL 来替代——这些用来完成课程内容都没问题。只是要记住你会因此错过什么。

### 可我没有信用卡（或不想用信用卡）来开通 AWS/Azure/GCP 服务器，怎么办？

请阅读[第 0 天 - 搭建你自己的本地服务器](00-Local-Server.md)。云厂商还有其他选择，支付方式也不止一种。但如果都不合适，就试试自己创建一台本地虚拟机吧。

### 可要是我就是不想用云厂商呢？我家里就有服务器/虚拟机。

那就用你自己的服务器/虚拟机。

### 你们为什么极力推荐租用云服务器？！为什么不把虚拟机路线作为推荐选项？！（换句话说：这门课这么定是错的/糟糕的）

哥们儿，消消气。如果这条要求都能冒犯到你，这门课对你来说可能就太基础了。请便。

但如果你真想知道背后的逻辑，也请考虑 3 点：

1. 人们在本地资源上可能受限。这包括没法随心所欲地用一台个人电脑来安装 VirtualBox、硬件性能不足以流畅跑虚拟化，甚至根本没有电脑。而云端一台很轻量的服务器，让你可以从任何访客设备——包括智能手机——来完成挑战。许多学生有 Azure 账号，可以借用学校电脑访问。大多数 VPS 头 1-2 个月的虚拟机用量是免费的。用云当然有风险，但我们努力在不砍掉这个选项的前提下应对它，好让需要它的人仍然用得上。
2. 每家云厂商都有自己的文档、支持体系和足够庞大的用户群，新手的大部分问题都能找到答案。它们够流行，YouTube 上有数百个视频和其他资料专门讲解最基本的配置问题，而且很多都做得简单易懂。想自建本地服务器或虚拟机时，现实就不是这样了。社区当然存在，但文档通常更干巴，也更小众。
3. 想要完整的系统管理员体验，你就得在远程服务器上干活，这是事实。你当然可以在本地网络的安全围墙里，用自己那台安全的小虚拟机模拟这种感觉，但这里推荐的厂商都有足够的保险机制，让你既能把玩虚拟机，又不至于一夜之间烧光额度。“云上恐怖故事”涉及的通常是挑战里根本不会碰到的服务/产品。这里不是关键业务系统。不用的时候，随时把虚拟机关掉就行。

> **译注**：云厂商价格与免费额度变动频繁，以官方页面为准。

**一句话总结**：这是一门聚焦 Linux 的课程。把时间花在争论“_在哪跑_”而不是“_怎么用_”的细节上，就偏离了这门课的初衷。[第 0 天](00.md)就是带你迈出第一步的，它永远算不上完备，请自行斟酌取用。

### 为什么是 Ubuntu？我可以用别的发行版吗？ { #why-ubuntu-can-i-use-another-distro }

讲义以 Ubuntu Server LTS（最新版本）为准，要把其他发行版的说明和差异都写进来会很乱（至少眼下如此）。如果你用的是 Debian 或其他基于 Debian 的发行版（Mint、Pop!OS、Kali），那几乎没什么区别，因为它们的结构是一样的。

但如果你选的是 RedHat 系发行版（Fedora、CentOS、AlmaLinux）或 Arch、Gentoo、OpenSUSE 这类发行版，各种差异（比如 apt、yum、pacman 的不同）就得靠你自己理解并应对了。

如果这些名字对你来说全都陌生，那你还不该挑发行版——先去读 [Linux Journey](https://labex.io/lesson/linux-history) 的第一课吧。

### 我已经在用[自己的某个 Linux 版本]了，怎么参加？

大多数课里用的命令其实并不限于 Ubuntu。所以用你自己的发行版照样能从挑战中受益，还可以凭借现有的 Linux 经验回答别人的问题、做出贡献。

### 服务器不用的时候，要不要停止或销毁它？

就免费额度的 VPS 而言，本课程的负载不会超出任何限额。挑战期间可以让它一直开着，但最好留个心眼（也就是说，之后别忘了它的存在，否则厂商就要开始向你收费了）。

> **译注**：云厂商价格与免费额度变动频繁，以官方页面为准。

### 我注意到有一次内核更新，但没人说要重启。

重启就是了。这是少数几个你确实需要重启服务器的场合之一，放手去做。
用的命令是 `sudo reboot now`

### 我还有疑问！该怎么办？！

欢迎在 [Lemmy](https://programming.dev/c/linuxupskillchallenge)、[Reddit](https://www.reddit.com/r/linuxupskillchallenge) 上提问或留言，或者到 [Discord 服务器](https://discord.gg/linux-upskill-challenge-682046666928685068)里聊天。

如果你愿意为教材做贡献，也有条件做到（比如有 GitHub 账号），可以直接向源码仓库[提交 issue](https://github.com/livialima/linuxupskillchallenge/issues/new/choose)。

## 致谢

了不起的 [Steve Brorens](https://snori74.blogspot.com/2020/06/succession-planning-for.html) 是 Linux Upskill Challenge 背后的缔造者和主脑。这门课曾经是付费课程，但从 2020 年起，得益于他的慷慨，它变得免费且完全开源。遗憾的是，[他已与世长辞](https://www.reddit.com/r/linuxupskillchallenge/comments/mki3uw/rest_in_peace_snori74/)，但在此之前，他已经安排好课程在自己身后继续运转。
我们想念你，snori。

[Livia Lima](https://bio.link/livialima) 是目前维护这套教材的人。欢迎去 [Mastodon](https://fosstodon.org/@livialima) 或 [LinkedIn](https://www.linkedin.com/in/livialima/) 上给她打个招呼。

> **中文译本说明**：本页为 [Linux Upskill Challenge](https://linuxupskillchallenge.org/) 中文版，英文原文以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 发布，原作者 Steve Brorens，现由 Livia Lima 维护。译文与勘误亦以 CC BY 4.0 发布，详见仓库根目录的 TRANSLATING.md。
