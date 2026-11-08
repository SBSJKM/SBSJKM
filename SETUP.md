# 把这份主页发布到 GitHub

> 目标：10 分钟内得到一个「有设计感、能自证实力」的 GitHub 主页。
> 文件结构：`README.md`（主页正文）+ `assets/`（横幅 SVG、横幅预览图、社交预览图）+ `.github/workflows/snake.yml`（可选的贡献蛇）。

---

## 0. 先搞清楚一个规则

GitHub 只会在**一个特殊仓库**里渲染主页 README：

| 要求 | 说明 |
| --- | --- |
| 仓库名 | **必须和你的用户名完全一致**（你是 `SBSJKM`，仓库就叫 `SBSJKM`） |
| 可见性 | 必须是 **Public** |
| 文件位置 | 仓库根目录的 `README.md` |

满足这三条，打开 `https://github.com/你的用户名` 就会看到它。

---

## 1. 发布（两种方式，选一种）

### 方式 A：网页上传（不想碰命令行）

1. 打开 <https://github.com/new>，Repository name 填 `SBSJKM`，选 **Public**，**不要**勾选 "Add a README file"，点 Create repository。
2. 在新仓库页点 **Add file → Upload files**。
3. 把 `github-profile` 文件夹里的 `README.md`、`assets` 文件夹、`.github` 文件夹一起拖进去。
   > 注意：拖的是文件夹**里面的内容**，不要多套一层 `github-profile/`。
4. 填个 commit message，点 **Commit changes**。
5. 打开 <https://github.com/SBSJKM> 验收。

### 方式 B：命令行（推荐，后面改起来方便）

在 `github-profile` 目录下执行：

```bash
git init
git add .
git commit -m "feat: init profile README"
git branch -M main
git remote add origin https://github.com/SBSJKM/SBSJKM.git
git push -u origin main
```

如果远程仓库还是空的、`push` 报 `failed to push some refs`，先执行一次：

```bash
git pull --rebase origin main
```

> 你的机器上已经给 git 配了代理 `127.0.0.1:7897`。push 卡住/超时的时候，先确认代理软件正在运行；
> 不需要代理时可以临时 `git -c http.proxy= push`。

**登录方式**：push 时会弹浏览器授权；如果要求密码，去
`Settings → Developer settings → Personal access tokens → Fine-grained tokens` 建一个带 `Contents: Read and write` 权限的 token 当密码用。

---

## 2. 发布前检查

下面的信息已经按你的要求填好，不用再改：

| 位置 | 内容 |
| --- | --- |
| 姓名 | `fml`（没有使用真实姓名） |
| 学校 | 上海交通大学（SJTU） |
| 邮箱 | `sbsjkm13@sjtu.edu.cn`（页首徽章 + 关于我） |
| 用户名 | `SBSJKM`（统计卡片、徽章、贡献蛇里都是它） |
| 项目 | 只放了 `hil-vla-shared-control` |

还需要你确认两件事：

- 如果 GitHub 用户名不是 `SBSJKM`，请全局替换（README 里约 8 处）。
- 想再加项目，复制「精选项目」那一节的格式即可；`opengraph.githubassets.com/1/用户名/仓库名` 的路径也要一起改。

> **小提醒**：主页是给「不认识你的人」看的。项目描述里带上**量化结果**（31% → 100%、↓92.8%）比堆十个形容词有用得多。

---

## 3. 验收

- [ ] 打开 `github.com/SBSJKM`，横幅、徽章、统计卡片都能显示
- [ ] 切一次 **深色 / 浅色主题**，横幅和文字都正常
- [ ] 手机上看一遍（GitHub App 或手机浏览器），表格/图片没有溢出
- [ ] 所有链接点一遍，没有 404
- [ ] 「精选项目」里的仓库确实是公开的

---

## 4. 可选增强

### ① 贡献蛇（已开启）

`.github/workflows/snake.yml` 已经在跑，`output` 分支里有深浅两版 SVG，README 用 `<picture>` 按主题自动切换。

以后想改频率，编辑 `snake.yml` 里的 cron（默认每 12 小时）；想手动刷新就 Actions → Generate Snake → Run workflow。想关掉，把 README 里那段 `<picture>` 删掉即可。

> 免费额度：公开仓库的 Actions 不消耗配额。

### ② 贡献活动图

在「GitHub 数据」下面加一行：

```html
<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=SBSJKM&theme=tokyo-night&hide_border=true&area=true" alt="Activity Graph" />
</div>
```

### ③ 打字机效果 / 技术图标墙

- 打字机：<https://github.com/DenverCoder1/readme-typing-svg>
- 图标墙：<https://github.com/tandpfun/skill-icons>（`https://skillicons.dev/icons?i=py,pytorch,linux,docker,git`）

### ④ 博客文章自动同步

用 [blog-post-workflow](https://github.com/gautamkrishnar/blog-post-workflow)，把 RSS 地址填进去，主页就会自动列出最新文章。

### ⑤ 统计卡片加载慢？

`github-readme-stats.vercel.app` 在中国大陆经常超时。两个办法：

1. Fork [anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats)，在 Vercel 一键部署，然后把 README 里的域名换成你自己的。
2. 或者干脆删掉统计卡片——主页的可信度主要来自项目，不来自绿色方块。

> 另外：公共实例**读不到私有仓库的贡献**，`count_private=true` 只有在自建并配置 token 时才生效。

### ⑥ 英文版

复制一份 `README.en.md`，在各自顶部加一行切换链接：

```markdown
[English](./README.en.md) | [中文](./README.md)
```

---

## 5. GitHub 学生认证（Global Campus / Student Developer Pack）

**一句话**：认证一次，GitHub Pro、Copilot Pro、JetBrains 全家桶、云服务器额度、免费域名等一堆东西全部免费，每年续一次。

### 5.1 能拿到什么（常见权益，以官网为准）

| 类别 | 内容 |
| --- | --- |
| GitHub 自家 | **GitHub Pro**（更多 Actions 额度、分支保护等）、**Copilot Pro 免费** |
| 开发工具 | JetBrains 全家桶、Frontend Masters、Educative、DataCamp、Bootstrap Studio |
| 云与部署 | DigitalOcean $200、Microsoft Azure $100、MongoDB Atlas 额度 |
| 域名与设计 | Namecheap `.me` / `.tech` 免费一年；Notion、Figma、Canva 教育版 |
| 其他 | 1Password、Sentry、TestMail 等 |

### 5.2 申请步骤

1. 打开 <https://github.com/education>，登录后点 **Join GitHub Global Campus**（学生入口）。
2. 填写：学校（用英文名搜索选择）、学位类型、专业、**预计毕业时间**。
3. 选择验证方式，二选一：
   - **学校邮箱**（`@xxx.edu.cn` 之类）：最快，通常几分钟内通过；
   - **上传证明文件**：学生证、在读证明、成绩单、学费缴费单都可以。
4. 提交，等邮件通知。

### 5.3 中国学生的实操经验

- **优先用学校邮箱**，很多 `.edu.cn` 能直接过；学校不给学生开邮箱时再走材料审核。
- 材料要同时满足四点，缺一容易被拒：
  1. 有你的**姓名**（建议用拼音，和 GitHub 资料一致）
  2. 有**学校全称**
  3. 有**当前日期或有效期**（最好是近 3 个月内开具的）
  4. 有**公章 / 注册章**，照片清晰不反光
- **在读证明**开中英双语版最稳；学信网《教育部学籍在线验证报告》英文版可以作为辅助材料。
- 学校列表里搜不到时，选 "Other" 手动填英文全称（如 `XX University`）。
- 毕业时间填**预计毕业**，别填成已经过去的日期。
- 审核时间：邮箱验证即时；人工审核一般几个工作日，高峰期可能 1–2 周。
- 被拒了不要反复盲投：先核对上面四点，换一种材料（比如学生证 → 在读证明）再提交；仍然不行就找 GitHub Support。

### 5.4 通过之后

1. 收到确认邮件后，去 <https://github.com/settings/billing> 确认显示 **Pro**。
2. 开启 Copilot：<https://github.com/settings/copilot> → 选择 **Copilot Pro**（学生免费）。
3. 学生身份**每年要重新验证**一次，注意邮件提醒。

> ⚠️ 不要借用他人的学生证或邮箱。GitHub 会做交叉核验，查实会封号，得不偿失。

---

## 6. 常见坑

| 现象 | 原因 |
| --- | --- |
| 主页不显示 README | 仓库名 ≠ 用户名，或仓库是 Private，或文件名不是 `README.md` |
| 图片裂开 | 路径大小写不一致（GitHub 服务器区分大小写）；或文件没一起上传 |
| 徽章显示 `invalid` | shields 参数里的中文/空格没做 URL 编码，改用英文或 `%20` |
| 统计卡片空白 | 公共服务被墙 / 首次访问慢，等几秒刷新，或按 4.⑤ 自建 |
| 修改后主页没变 | 浏览器缓存，`Ctrl + F5`；或改动没 push 成功 |
| Actions 跑失败 | 仓库 Settings → Actions → General 里允许 workflow 写入（Read and write permissions） |

---

## 7. 顺手把仓库也收拾一下

主页只是门面，别人点进来看到的是**仓库**：

- **About**：填一句话 description + 官网链接 + topics，例如
  `robot-learning`、`vision-language-action`、`imitation-learning`、`isaac-lab`、`teleoperation`
- **Social preview**：Settings → Social preview，上传 `assets/social-preview.png`（1280×640，已为你生成）
- **LICENSE**：MIT 最省事；论文类代码可以用 Apache-2.0
- **README 模板**：一句话是什么 → 效果图/GIF → 快速开始 → 结果表格 → 引用
- **Release / Tag**：给能跑的版本打 v0.1.0，比一堆 commit 更有说服力

---

## 8. 还可以做什么

- **GitHub Pages 个人主页**：`用户名.github.io` 仓库 + 静态站点，把简历、论文、博客放上去
- **论文/笔记仓库化**：把 `论文/`、`知识笔记/` 里成体系的内容整理成公开仓库，是很好的能力证明
- **Profile 里放「Now」板块**：现在在做什么，比罗列历史更能让人想联系你
