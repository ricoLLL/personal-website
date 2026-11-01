# 个人网站维护说明

这个网站是英文、纯静态的学术主页，适用于 GitHub Pages。直接用 VS Code 编辑文件即可，无需安装 Node.js、框架或依赖。

## 文件分工

| 文件 | 内容 |
| --- | --- |
| `index.html` | 首页、自我介绍、研究方向、联系方式、论文入口和教育背景 |
| `research.html` | Working papers 的标题、合作者、摘要和论文链接 |
| `teaching.html` | 助教经历、课程及研究指导经历 |
| `cv.html` | 教育、经历、奖项、服务与技能的网页版 |
| `styles.css` | 四个页面共用的颜色、字体、布局和手机样式 |
| `assets/Lulin_Li_CV.pdf` | 提供的 CV 原件副本，网页的 CV 按钮指向这里 |
| `assets/favicon.svg` | 浏览器标签上的 L 图标 |
| `assets/profile-placeholder.svg` | 首页右侧的照片占位图 |
| `assets/papers/solar-renewable-energy-certificates.pdf` | SREC 论文全文，原始 43 页 PDF 的副本 |
| `assets/papers/platform-specialization-and-diversification.pdf` | 平台竞争论文全文，原始 28 页 PDF 的副本 |
| `.nojekyll` | 告诉 GitHub Pages 直接提供静态文件 |

## 本地编辑和预览

1. 在 VS Code 打开本文件夹。
2. 修改对应 HTML 文件，用 Ctrl+S 保存。
3. 在 Windows 文件资源管理器中右键 `index.html`，用 Edge 或 Chrome 打开。
4. 每次修改后刷新浏览器。各页面之间的导航及 PDF 链接都可以直接本地使用。

配色在 `styles.css` 顶部的 `:root` 中统一设置，深蓝色由 `--navy` 控制。

## 资料依据和后续更新

- 身份、学历、联系方式、论文、课程及奖项依据本次提供的两页 CV。保留 CV 中标注为 present 的日期。
- CV 只说明 Ph.D. 在读，因此主页使用 Ph.D. Student，没有推定 candidacy、毕业日期或 job-market 状态。
- 平台竞争论文的标题、作者和可展开摘要来自提供的 28 页论文原件；SREC 论文的信息来自提供的 43 页论文原件。两篇 PDF 均以原文件的逐字节副本保存。电动车论文的标题和合作者按 CV 保留。
- 首页右侧已留出 4:5 的照片位置，目前显示中性的线条占位图；添加真人照片的方法见下文。
- 下载的 PDF 是原件的逐字节副本，仍包含原 CV 中的电话等联系方式。
- 更新 CV 时，用同名文件替换 `assets/Lulin_Li_CV.pdf`，并同步修改各 HTML 页面相关文字。
- 更新论文时，首页与研究页都需要修改。页面导航在四个 HTML 文件中各有一份。

## 添加个人照片

1. 选择一张竖版照片，推荐宽高比例 4:5（例如 800×1000 像素）。
2. 把真实的 JPG 照片保存为 `assets/profile.jpg`。如果原文件是 PNG，请保留 `.png` 扩展名并同步修改下方路径。
3. 在 `index.html` 中找到 `class="portrait"` 的图片，把这一行改为：

```html
<img class="portrait" src="assets/profile.jpg" alt="Portrait of Lulin Li" width="320" height="400">
```

照片会自动填满框并按 4:5 裁切，不会拉伸变形。若人脸裁切位置需要调整，在 `styles.css` 的 `.portrait` 中修改 `object-position: center 30%`，例如改成 `center top`。

## 添加论文 PDF

把文件放到 `assets/papers/`，例如 `assets/papers/platforms.pdf`。把研究页对应论文的标题改成直接链接到 PDF：

```html
<h2><a href="assets/papers/platforms.pdf">论文完整标题</a></h2>
```

首页对应论文的标题链接也指向同一个 PDF，标题保留原有字体，鼠标悬停时显示下划线。无需另加 Paper/PDF 按钮。

## 上传到 GitHub

这次只编辑本地文件，没有自动提交、推送或发布。确认内容后，在此文件夹的 VS Code 终端中按顺序运行：

```powershell
git status
git add index.html research.html teaching.html cv.html styles.css assets .nojekyll EDITING.md
git commit -m "Build academic personal website"
git push
```

然后在 GitHub 仓库的 Settings → Pages 中，选择 Deploy from a branch、main、/(root)，保存。仓库当前关联的是 `https://github.com/ricoLLL/personal-website.git`。

## Cloudflare 域名

网站使用相对链接，兼容 GitHub 项目网址和将来的独立域名。买好域名后，先在 GitHub Pages 中设置 Custom domain，再在 Cloudflare 配置对应 DNS。当前没有创建 CNAME 文件或假定你已购买某个域名。

## 设计参考

- https://mengsong.net/ — 清晰导航和直接的学术简介。
- https://sites.google.com/view/feifanwang/about — 简洁的介绍和分页面结构。
- https://sites.google.com/view/xiaofeng-gong/home — 衬线标题和清晰的研究方向。
- https://keuncheol-lee.com/ — 独立的教育、研究和教学分区。

页面代码、配色和排版为本次重新设计；没有复制其他人的照片、简历或论文内容。
