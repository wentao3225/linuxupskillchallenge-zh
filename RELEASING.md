# 开源发布清单（RELEASING）

本仓库 fork 自 [livialima/linuxupskillchallenge](https://github.com/livialima/linuxupskillchallenge)，
改造为中文双语版。公开上线前，把所有"指向原作者"的配置换成你自己的，否则评论、统计和站点元数据都会打到原仓库上。

## 1. mkdocs.yml

| 项目 | 现状 | 要改成 |
| --- | --- | --- |
| `site_url` | `https://linuxupskillchallenge.org/` | 你的站点域名（如 `https://你的用户名.github.io/仓库名/`） |
| `repo_name` / `repo_url` / `edit_uri` | livialima/linuxupskillchallenge | 你的仓库 |
| `extra.analytics` | Google Analytics `G-LKF1067ZTR`（原作者的） | 换成你自己的 property，或整段删掉 |
| `extra.social` | 指向原作者的 Discord/YouTube/LinkedIn 等 | 换成你的社区链接，或删除 |
| `copyright` | 原作者版权信息 | 保留原作者署名，可加"中文版由 XXX 维护" |

## 2. 评论区（overrides/partials/comments.html）

giscus 脚本当前指向原作者的仓库：

- `data-repo` / `data-repo-id` / `data-category` / `data-category-id`：在你自己的仓库开启
  Discussions → 安装 [giscus app](https://giscus.app/zh-CN) → 用 giscus 官网生成新的一组值替换。
- `data-lang="en"`：面向中文读者建议改为 `zh-CN`（两种语言页面共用一套配置，折衷方案）。

## 3. 许可与署名（不可省略）

- `LICENSE`（CC BY 4.0）**保持不变**；
- 站点 `copyright` 与每篇译文页脚已含原作者署名，不要删；
- README 中注明：基于上游项目翻译改造、上游仓库地址、本仓库的差异（翻译+勘误）。

## 4. GitHub 仓库设置

- Settings → Pages → Source 选择 **GitHub Actions**（仓库已带 `.github/workflows/ci.yml`，推送到 main/master 会自动 `mkdocs gh-deploy`）；
- 仓库可见性公开（CC BY 4.0 要求署名但允许商用，公开是惯例）；
- 建议开 Issues 方便读者报翻译问题。

## 5. CI 注意

- `ci.yml` 的 deploy 任务已包含 `mkdocs-static-i18n`（requirements.txt 已同步）；
- 若把站点部署到 `用户名.github.io/仓库名/` 子路径，需在 mkdocs.yml 加 `site_dir` 无关的 `use_directory_urls` 保持默认即可，但 giscus 的 `data-mapping="pathname"` 天然兼容。

## 6. 上线前自查

- [ ] `mkdocs build --strict` 本地零警告
- [ ] 双语切换、暗色模式、评论区都点一遍
- [ ] README（中英）链接可点
- [ ] 全局搜索 `linuxupskillchallenge.org` 与 `livialima`，确认该换的都换了、该留的署名都留着
- [ ] 首页写明"每月第一周一起跟课"的中文社群入口（如有）
