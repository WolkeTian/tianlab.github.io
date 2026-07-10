# 使用本仓库部署学术实验室网站

本文面向不熟悉编程的实验室负责人、教师、学生助理和行政人员，说明如何使用当前 al-folio 仓库，在 GitHub Pages 上发布并持续维护实验室网站。

整套流程可以只通过 GitHub 网页完成。GitHub 会自动生成网站，不需要在个人电脑上安装 Ruby、Node.js、Docker 或其他开发工具。

## 一、先了解最终结果

这个仓库同时保存网站内容和自动部署设置。日常维护者主要编辑文字、图片和论文数据；每次保存到 `main` 分支后，GitHub 会自动生成网页并发布到 `gh-pages` 分支。

对于当前名为 `tianlab.github.io` 的仓库，推荐作为实验室的根网站使用：

| 项目 | 推荐值 |
| --- | --- |
| GitHub 用户或组织名 | `tianlab` |
| 仓库名 | `tianlab.github.io` |
| 网站地址 | `https://tianlab.github.io` |
| `_config.yml` 中的 `url` | `https://tianlab.github.io` |
| `_config.yml` 中的 `baseurl` | 留空，但保留 `baseurl:` 这一行 |

如果实际 GitHub 组织名不是 `tianlab`，应把上述名称替换为真实的 GitHub 用户名或组织名。仓库名、`url` 和最终网址必须相互对应。

> 不要直接编辑 `gh-pages` 分支。它是自动生成的网站成品，下一次部署时会被重新覆盖。网站源内容应始终在 `main` 或 `master` 分支维护。

## 二、准备工作

开始前，请确认：

1. 实验室有一个 GitHub 用户账号或组织账号。
2. 当前仓库位于该账号或组织下，并且维护者对仓库有管理权限。
3. 网站准备公开的文字、成员照片、实验室标志、论文信息和联系方式已经过审核。
4. 图片、PDF 和成员资料中不包含家庭住址、私人电话号码、未公开项目、访问令牌或其他敏感信息。

如需从 al-folio 原始模板新建网站，应使用 GitHub 的 **Use this template**，不要使用 Fork。当前仓库已经存在时，无需重新创建。

## 三、认识需要维护的内容

日常维护通常只涉及以下位置：

| 网站内容 | 文件或文件夹 | 用途 |
| --- | --- | --- |
| 网站名称、网址、语言和功能开关 | `_config.yml` | 全站总设置 |
| 首页 | `_pages/about.md` | 实验室简介、负责人照片、通知和精选论文 |
| 导航栏 | `_pages/*.md` 文件开头 | 控制页面是否显示以及显示顺序 |
| 实验室成员 | `_pages/profiles.md` 和成员介绍文件 | 成员照片、简介、办公室等信息 |
| 研究方向或项目 | `_projects/` | 每个文件代表一个研究项目 |
| 新闻与通知 | `_news/` | 首页短消息和通知 |
| 论文列表 | `_bibliography/papers.bib` | 以 BibTeX 格式保存论文 |
| 论文 PDF | `assets/pdf/` | 供论文列表中的 PDF 按钮使用 |
| 论文预览图 | `assets/img/publication_preview/` | 论文列表中的缩略图 |
| 其他图片 | `assets/img/` | 头像、实验室照片、项目图片等 |
| 联系方式和学术主页 | `_data/socials.yml` | 邮箱、Google Scholar 等链接 |
| 博客 | `_posts/` | 较长的动态、活动记录或技术文章 |
| 教学内容 | `_teachings/` | 课程与教学材料 |
| 自动部署 | `.github/workflows/deploy.yml` | GitHub 自动构建和发布网站 |

本仓库采用 al-folio v1 插件化结构。页面样式和运行组件由插件提供。普通内容维护时，不需要新增或复制 `_layouts`、`_includes`、`_sass`、JavaScript 或主题构建文件。

## 四、通过 GitHub 网页编辑文件

大多数内容都可以使用相同方法修改：

1. 打开 GitHub 上的仓库，确认左上角分支为 `main` 或 `master`。
2. 找到要编辑的文件并打开。
3. 点击右上角铅笔图标 **Edit this file**。
4. 修改内容后，使用 **Preview** 检查排版。
5. 点击 **Commit changes**。
6. 填写简短说明，例如“更新实验室简介”，然后保存到当前主分支。

上传图片或 PDF 时：

1. 进入目标文件夹，例如 `assets/img/`。
2. 点击 **Add file**，再选择 **Upload files**。
3. 拖入文件并提交。

建议文件名只使用小写英文字母、数字和短横线，例如 `zhang-san.jpg`、`robot-learning.pdf`。不要使用空格。GitHub Pages 区分大小写，因此 `Lab.jpg` 和 `lab.jpg` 会被视为两个不同文件。

## 五、填写网站基本信息

打开 `_config.yml`，优先修改文件顶部的网站信息。对于当前根网站，可参考：

```yaml
title: Tian Lab
first_name:
middle_name:
last_name:
contact_note: >
  如需合作或访问实验室，请通过下方邮箱联系我们。
description: >
  Tian Lab 学术实验室官方网站，介绍研究方向、团队成员、论文成果和最新动态。
keywords: research lab, academic laboratory, Tian Lab
lang: zh-CN

url: https://tianlab.github.io
baseurl:
```

注意事项：

- `title` 建议填写实验室正式名称，它会作为网站的重要标识。
- `description` 用一两句话说明实验室研究领域，便于搜索引擎和分享预览识别网站。
- `url` 不要在末尾添加 `/`。
- 根网站的 `baseurl` 必须留空，但不能删除这一行。
- 带有冒号、井号或特殊符号的短文本，建议用英文双引号包住。
- 同一层级使用相同缩进。不要随意移动行首空格。

如果仓库不是 `tianlab.github.io`，而是普通项目仓库，例如 `lab-website`，则应使用：

```yaml
url: https://tianlab.github.io
baseurl: /lab-website/
```

这时最终地址是 `https://tianlab.github.io/lab-website/`。

## 六、制作实验室首页

首页是 `_pages/about.md`，因为该文件中设置了 `permalink: /`。建议首页依次包含：

1. 实验室中英文名称。
2. 一段简短定位，例如研究领域和所属机构。
3. 负责人或实验室主图。
4. 三到五个核心研究方向。
5. 最新通知。
6. 精选论文。
7. 联系方式。

文件开头由两行 `---` 包围的区域是页面设置，称为“页头”。不要删除这两行。常用设置包括：

```yaml
profile:
  align: right
  image: prof_pic.jpg
  image_circular: false

selected_papers: true
social: true

announcements:
  enabled: true
  scrollable: true
  limit: 5
```

将首页图片上传到 `assets/img/`，然后让 `image` 的文件名与实际文件完全一致。页头之后的普通文字就是首页正文，可以直接使用 Markdown 编写：

```markdown
我们关注人工智能、机器人与跨学科计算研究。

## 研究方向

- 具身智能
- 机器学习
- 人机协作
```

## 七、设置导航栏

导航栏由 `_pages/` 中每个页面开头的设置决定：

```yaml
title: people
nav: true
nav_order: 2
```

- `title` 是导航栏显示名称，可以改成中文，例如 `团队成员`。
- `nav: true` 表示显示在导航栏。
- `nav: false` 表示页面仍可保留，但不显示在导航栏。
- `nav_order` 数字越小，位置越靠前。数字不要重复。

实验室网站可采用以下顺序：

| 页面 | 建议标题 | 建议顺序 |
| --- | --- | --- |
| `_pages/about.md` | 首页 | 首页本身通常不需要单独排序 |
| `_pages/profiles.md` | 团队成员 | 1 |
| `_pages/projects.md` | 研究方向 | 2 |
| `_pages/publications.md` | 论文成果 | 3 |
| `_pages/news.md` | 最新动态 | 4 |
| `_pages/teaching.md` | 教学 | 5 |

如果实验室暂时不需要博客、个人简历、代码仓库或书架，可以将对应页面的 `nav` 改为 `false`。先隐藏比直接删除文件更容易恢复。

## 八、添加实验室成员

成员总览页是 `_pages/profiles.md`。每位成员通常需要：

1. 一张放在 `assets/img/` 的照片。
2. 一个放在 `_pages/` 的个人介绍文件。
3. 在 `profiles.md` 中增加一段成员配置。

可以先复制现有的 `_pages/about_einstein.md`，将副本命名为 `about-zhang-san.md`，再替换其中的文字。随后在 `profiles.md` 的 `profiles:` 下加入：

```yaml
- align: right
  image: zhang-san.jpg
  content: about-zhang-san.md
  image_circular: false
  more_info: >
    <p>教授、实验室负责人</p>
    <p>某某大学某某学院</p>
```

第二位成员可以使用 `align: left`，让页面左右交替。每位成员块的缩进必须与现有示例保持一致。

建议个人介绍包含姓名、职称、研究方向、个人主页和公开邮箱。不要公开私人手机号、家庭地址或未经本人同意的照片。

## 九、添加研究方向和项目

`_projects/` 中每个 Markdown 文件代表一个项目。最省事的方法是复制现有项目文件，再替换标题、简介、图片和正文。

文件开头可使用：

```yaml
---
layout: page
title: 具身智能
description: 面向开放环境的感知、决策与控制
img: assets/img/embodied-ai.jpg
importance: 1
category: research
---
```

- `importance` 数字越小，通常越靠前。
- `category` 可用于将项目分组，例如统一使用 `research`。
- `img` 是项目封面图路径。
- 第二个 `---` 之后写项目介绍、代表成果、合作单位和相关链接。

删除模板示例前，建议先把至少一个示例改造成真实项目并成功发布，以免误删必要格式。

## 十、发布新闻和通知

首页短通知保存在 `_news/`。可以复制现有的 `announcement_1.md`，使用新的日期和正文：

```yaml
---
layout: post
date: 2026-07-10 09:00:00+0800
inline: true
related_posts: false
---

实验室一篇新论文被某某会议接收。
```

日期使用 `年-月-日`，中国时区可写为 `+0800`。未来日期的内容可能不会立即显示。

较长的活动报道、招生说明或技术文章可以放在 `_posts/`。博客文件名应使用 `YYYY-MM-DD-title.md` 格式，例如 `2026-07-10-open-day.md`。

## 十一、维护论文列表

论文数据保存在 `_bibliography/papers.bib`。这是标准 BibTeX 文件，通常可以从论文数据库、期刊网站或文献管理软件导出，再粘贴到文件末尾。

一个简化示例如下：

```bibtex
@article{zhang2026robot,
  title    = {A Sample Paper Title},
  author   = {Zhang, San and Li, Si},
  journal  = {Journal of Example Research},
  year     = {2026},
  doi      = {10.0000/example.2026.001},
  url      = {https://doi.org/10.0000/example.2026.001},
  pdf      = {zhang2026robot.pdf},
  preview  = {zhang2026robot.jpg},
  selected = {true}
}
```

字段说明：

- `zhang2026robot` 是唯一标识，不能与其他论文重复。
- `author` 建议使用 `姓, 名 and 姓, 名` 的形式连接多位作者。
- `pdf` 只写文件名，对应文件放在 `assets/pdf/`。
- `preview` 只写文件名，对应图片放在 `assets/img/publication_preview/`。
- `selected = {true}` 表示该论文还会出现在首页精选论文中。
- 每个字段后通常需要逗号，最后一个字段可以不加逗号。

论文页 `_pages/publications.md` 已经会自动读取 `papers.bib`，一般不需要逐篇编辑该页面。

`_config.yml` 中的 `scholar` 区域当前仍是模板作者姓名。若希望在论文列表中突出实验室负责人或成员姓名，应把其中的 `last_name` 和 `first_name` 改为真实姓名写法，并与 BibTeX 中的作者拼写保持一致。

## 十二、管理图片和附件

建议按以下规则管理素材：

- 成员照片和普通图片：`assets/img/`
- 论文预览图：`assets/img/publication_preview/`
- 论文和公开附件：`assets/pdf/`
- 项目图片：可放在 `assets/img/`，并使用能说明内容的文件名

发布前检查：

1. 图片方向正确，没有明显裁切错误。
2. 人像和活动照片已经获得公开授权。
3. 图片不包含身份证件、门禁卡、白板机密信息等内容。
4. 大图已适当压缩，避免单张照片达到数十 MB。
5. 文件路径、大小写和扩展名完全一致。
6. PDF 已移除不应公开的批注、作者隐私信息或修订记录。

## 十三、配置联系方式

打开 `_data/socials.yml`，替换模板中的示例邮箱、Google Scholar 标识和其他链接。没有使用的项目可以删除或在行首加 `#` 暂时关闭。

例如：

```yaml
email: lab@example.edu
scholar_userid: 真实的_Google_Scholar_ID
rss_icon: true
```

基础部署不需要 Personal Access Token，也不要把 GitHub 密码、访问令牌、邮箱密码或第三方服务密钥写入任何仓库文件。

## 十四、启用 GitHub 自动部署

这一部分通常只需由仓库管理员设置一次。

### 1. 允许自动部署写入发布分支

1. 打开 GitHub 仓库。
2. 进入 **Settings**。
3. 依次进入 **Actions**、**General**。
4. 找到 **Workflow permissions**。
5. 选择 **Read and write permissions**。
6. 点击 **Save**。

如果 GitHub 提示 Actions 尚未启用，先进入仓库的 **Actions** 页面并启用它。仓库已经包含 `.github/workflows/deploy.yml`，不需要自行新建工作流。

### 2. 触发第一次部署

在 `main` 或 `master` 分支提交一次内容修改，例如更新 `_config.yml`。随后：

1. 打开仓库的 **Actions** 页面。
2. 点击左侧的 **Deploy site**。
3. 等待最新任务显示绿色对勾。
4. 第一次构建通常需要几分钟。

工作流成功后，仓库中会出现 `gh-pages` 分支。不要在该分支手工修改内容。

### 3. 指定 GitHub Pages 发布来源

1. 打开 **Settings**。
2. 进入 **Pages**。
3. 在 **Build and deployment** 中，将 **Source** 设为 **Deploy from a branch**。
4. 将分支设为 `gh-pages`，目录设为 `/ (root)`。
5. 保存并等待 GitHub Pages 完成发布。

最后访问 `https://tianlab.github.io`。第一次发布或刚修改 Pages 设置时，页面可能需要几分钟才可访问。

## 十五、以后如何更新网站

日常更新可以固定为以下流程：

1. 在 `main` 或 `master` 分支编辑文字或上传素材。
2. 使用清楚的提交说明，例如“新增王老师简介”或“更新 2026 年论文”。
3. 打开 **Actions**，确认 **Deploy site** 为绿色对勾。
4. 打开正式网站，检查电脑和手机显示效果。
5. 如未立即看到更新，等待几分钟后强制刷新浏览器。

建议指定至少两名维护者，并约定：

- 重要内容由另一人复核后发布。
- 成员离组、联系方式变化和招生信息到期时及时更新。
- 每学期检查一次失效链接、过期通知和不再公开的附件。
- 不在 `gh-pages` 分支维护内容。
- 不随意修改 `.github/workflows/`、`Gemfile`、`Gemfile.lock` 或主题插件设置。

## 十六、常见问题

### Actions 显示红色叉号

先打开失败的 **Deploy site** 任务，查看第一个报错步骤。最常见原因是：

- **Workflow permissions** 没有设置为 **Read and write permissions**。
- `_config.yml` 缩进错误，或删除了必要的冒号。
- 新增页面开头缺少成对的 `---`。
- `papers.bib` 中缺少逗号、花括号不成对，或论文标识重复。

### 网站能打开，但样式或图片丢失

优先检查 `_config.yml` 中的 `url` 和 `baseurl`：

- 根网站：`url: https://tianlab.github.io`，`baseurl:` 留空。
- 项目网站：`url: https://tianlab.github.io`，`baseurl: /仓库名/`。

再检查图片路径、文件名大小写和扩展名是否完全一致。

### 网站显示 404

确认：

1. **Deploy site** 已成功。
2. **Settings > Pages** 使用 `gh-pages` 分支和 `/ (root)` 目录。
3. 访问地址与仓库名一致。
4. 第一次部署后已经等待几分钟。

### 新论文没有显示

检查论文是否位于 `_bibliography/papers.bib`，BibTeX 花括号和逗号是否完整，以及论文标识是否唯一。PDF 或预览图缺失通常不会阻止论文文字显示，但相应按钮或缩略图会不可用。

### 修改后看不到变化

先确认 Actions 已完成，再等待几分钟并刷新。浏览器可能保留旧页面，可使用无痕窗口检查正式网站。

## 十七、发布前检查清单

- [ ] 网站名称、简介、所属机构和联系方式正确
- [ ] `_config.yml` 中的 `url` 与实际 GitHub Pages 地址一致
- [ ] 根网站的 `baseurl:` 已保留并留空
- [ ] 首页已移除模板人物、模板文字和示例地址
- [ ] 成员照片和简介已获本人同意
- [ ] 示例项目、示例论文和无关导航已替换或隐藏
- [ ] 论文 PDF 和图片可以正常打开
- [ ] 手机和电脑上均检查过首页、成员页和论文页
- [ ] Actions 中的 **Deploy site** 显示绿色对勾
- [ ] Pages 发布来源为 `gh-pages` 和 `/ (root)`
- [ ] 仓库中没有密码、令牌、私人资料或未公开成果

## 十八、可选：使用自定义域名

如果实验室已有域名，例如 `lab.example.edu`，可在 GitHub 的 **Settings > Pages > Custom domain** 中填写域名，并按学校信息中心或域名服务商的要求配置 DNS。

为避免自动部署后域名设置丢失，可在仓库根目录创建名为 `CNAME` 的文件，文件中只写一行域名：

```text
lab.example.edu
```

DNS 配置由学校或域名服务商管理，具体记录值应以对方提供的信息为准。域名切换完成前，保留 `https://tianlab.github.io` 作为检查地址。

## 延伸阅读

- [快速开始](QUICKSTART.md)
- [安装与部署说明](INSTALL.md)
- [完整定制说明](CUSTOMIZE.md)
- [常见故障排查](TROUBLESHOOTING.md)
- [v1 仓库与插件边界](BOUNDARIES.md)
