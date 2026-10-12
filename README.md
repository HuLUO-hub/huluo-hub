# Hu Luo 个人学术主页

适用于 `huluo-hub.github.io` 的单页学术 CV 网站。保留暖白与深绿配色，采用固定桌面版式，无菜单栏、手机专用布局和 CV 下载入口。排列顺序：个人介绍（融合研究兴趣）→ 教育与工作经历 → 论文与稿件 → 专利 → 奖励。学校采用中英文名称；四个机构均保留标志，具体素材出处见来源说明。

教育与经历采用参考图片中的紧凑双栏结构：左侧 Education、右侧 Experience。默认显示机构、中文名、学位／职位和时间，点击 “More about education & experience” 展开全部机构介绍与经历说明，再次点击可收起。复旦使用蓝色矢量校徽，西交使用红色透明底校徽，具体素材来源见 `ASSET_SOURCES.md`。

## 先预览

直接用浏览器打开 `site/index.html`。全部内容和图片均使用本地文件，无需安装依赖。点击 WeChat 展示微信号；论文和专利各先展示 10 条，点击 More 展开全部。旧版分页面地址会自动跳转到主页相应位置。

如需本地服务器，可在本文件所在目录运行：

```powershell
python -m http.server 8000 --directory site
```

然后访问 `http://localhost:8000`。

## 发布到 GitHub Pages

目标地址为 `https://huluo-hub.github.io/`，对应用户确认的新 GitHub 账号 `HuLUO-hub`。个人主页链接已同步更新为 `https://github.com/HuLUO-hub`。本地配置已完成，仍需按以下步骤在 GitHub 上创建仓库并发布。

### 推荐：上传完整项目并自动构建

1. 登录 GitHub 账号 `HuLUO-hub`，在该账号下创建公开仓库 `huluo-hub.github.io`。如果该仓库已经存在，请先保留原有内容，按需合并。
2. 将本目录的内容放到仓库根目录，保留 `.github/workflows/pages.yml`、`build.py`、`content.json` 和 `site/` 的结构。不要把整个项目再嵌套到一层文件夹，也不要只上传 ZIP 文件。
3. 在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。
4. 将文件提交至 `main` 分支。若首次上传早于 Pages 设置完成，在 **Actions → Build and deploy academic website** 中点击 **Run workflow**。
5. 等部署任务成功后，访问 `https://huluo-hub.github.io/`。首次发布可能需要等待几分钟。

如果通过网页上传文件时没有上传隐藏的 `.github` 文件夹，可在 GitHub 的 **Add file → Create new file** 中创建 `.github/workflows/pages.yml`，粘贴本地同名文件内容。

### 简易方案：只上传已生成的网页

如果暂时不想使用自动构建，将 `site/` **里面**的所有文件和 `assets/` 文件夹直接上传到仓库根目录，然后在 **Settings → Pages** 中选择 **Deploy from a branch → main → /(root)**。

采用这一方案时，不需要上传 `build.py`、`content.json` 或工作流文件。以后修改资料后，需要重新生成并上传网页。

## 后续维护

- `content.json`：个人介绍、经历、论文、专利、奖励和外部链接。
- `site/assets/portrait.jpg`：照片；替换时建议保持 4:5 比例。
- `site/assets/style.css`：配色、字体和固定桌面布局。
- `build.py`：页面结构与构建入口。
- `site/assets/logos/`：学校、公司和民非机构官方标志；来源见 `ASSET_SOURCES.md`。
- `site/assets/research/`：三篇一作期刊论文的原创研究示意图；已明确标注 Research schematic，并非论文实验原图。

修改 `content.json` 后执行 `python build.py` 生成网页。自动构建方案会在每次提交后执行这一步。不要只修改自动生成的 HTML，否则下一次构建会覆盖修改。

个人介绍在 `intro_paragraphs` 中，每个字符串是一段，可以直接换成自己的英文介绍。`wechat` 是点击展开的微信号。

论文记录的 `status` 可使用 `Published`、`Major revision`、`Under review` 或 `Submitted`。每条记录独立显示其状态，不把在审论文显示为已发表。年份不详时保持 `null`。`publication_order` 决定展示顺序，必须包含每条论文的 ID 且不重复；前 10 条为默认显示内容，其余折叠在 More 中。

`authors`、`display_venue`、`summary`、`expertise` 分别控制作者、期刊信息、介绍和能力关键词。三篇代表性期刊论文由 `image` 指向图片，并用 `image_alt` 提供文字说明；`selected` 标明这里选定的一作代表作。关键在审一作论文使用 `key_manuscript: true`，显示标题、投稿期刊、状态和一段介绍。`doi` 只填写 DOI 本身；无 DOI 的两篇会议论文使用 `url` 跳转作者公开的 arXiv 原文。

替换图片时可使用 SVG、PNG 或 JPG。若换成论文原图，请同步将 `build.py` 中的图注 Research schematic 改为准确的图片说明，并更新素材来源。

专利 `status` 使用 `Published`、`Granted` 或 `Filed`。中文申请公开和授权分开显示。

## 内容来源与待补充项

根据用户提供的英文 CV 整理，共包含 18 条论文或稿件、17 条专利或申请、8 条奖励。原始 Word 没有放入网站或此项目。微信号按用户明确提供的信息设置为 18995477896。

- 照片直接提取自提供的 CV。
- 学位写作 Ph.D. studies，避免把在读经历误写成已获得学位。
- 按 CV 的分组与文字，前 10 条论文暂标记为 Published，其余 8 条列为在审或已投稿稿件；这不是独立文献核验结果。第 13 条只明确提供投稿信息，使用 Submitted。
- 专利状态照录 CV，没有独立核验法律状态。英文专利标题来自 CV。
- Google Scholar 页面访问返回 429 限流，无法读取，故没有加入引用次数、h-index 或额外论文。已保留用户提供的 Scholar 链接。
- 10 篇已发表论文均已配置原文链接：8 个 DOI，2 个作者公开的 arXiv 页面。新增 DOI 依据出版社页面或 Crossref 元数据确认。
- Pattern Recognition 论文根据正式卷期更新为 2026 年第 172 卷、112327；DOI 中的 2025 保持不变。Seeing Touch from Motion 的作者顺序按 arXiv 页面调整。
- 已去掉稿件编号。一条 IEEE Transactions on Medical Robotics and Bionics 记录中的 `2576-3202` 疑似期刊 ISSN，未作为文章页码展示。
- 三篇期刊代表作介绍依据公开摘要或作者稿；在审论文和多数专利的介绍仅概述 CV 标题中的研究范围，没有添加未提供的性能结论或权利要求。详细来源及边界见 `CONTENT_SOURCES.md`。
- 后续适合补充：论文完整作者列表、最终卷期页码和发表状态、论文配图、代码仓库、项目演示、导师信息、个人中文姓名及其余内容的中英文切换。

## 验证范围

新版检查内容数量、原文链接、机构标志、单页顺序、本地资源引用、微信号和 More 的展开与收起。两类折叠区均使用原生 HTML，可用键盘操作，也不依赖 JavaScript。奖励不足 10 条时全部显示，新增超过 10 条后同样出现 More。

GitHub Pages 工作流已配置，但尚未在远程仓库运行。网站没有部署完成的声明；正式发布后需要检查一次线上页面和 HTTPS。

官方发布说明：https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages
