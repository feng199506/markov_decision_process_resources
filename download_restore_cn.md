# 下载与恢复说明（马尔科夫决策过程与序贯决策资源库，2026-10-30）

## 发布内容

| 附件 | 说明 |
|---|---|
| `markov_decision_process_resources_20261030_batch001_cn_en.tar` | 资料库全文，1 个不压缩 tar 包（1,153,433,600 字节，9,998 个文件 + 3 个空目录） |
| `archive_index_cn.csv` | 包内每个文件的相对路径、大小和改动备注 |
| `windows_rename_map_cn.csv` | 为 Windows 改名的文件、为离线阅读改动或新增的文件明细 |
| `release_excluded_cn.csv` | 未随发布包提供的 8 本教材及官方获取地址 |
| `download_restore_cn.md` | 本说明 |
| `upload_report_cn.md` | 上传状态报告 |

包内有论文（12 个子方向的 `papers/`）、教材（`books/`）、课程讲义与课件包（`courses/`）、官方软件文档离线网页（`software_docs/`）、参考项目源码快照（`projects/`）、目录与登记 CSV、中文指南（`guides/`）和采集脚本（`scripts/`）。

## Windows 下恢复

1. 下载 tar 包，放到路径较短的目录，例如 `D:\mdp\`。包内最长相对路径 169 个字符，解压目录本身越短越好（建议不超过 60 个字符），否则可能超过资源管理器的 260 字符限制。
2. 解压（任选一种）：
   - Windows 10/11 自带命令：在该目录打开命令提示符，运行 `tar -xf markov_decision_process_resources_20261030_batch001_cn_en.tar`
   - 7-Zip：右键 →“提取到当前位置”。
3. 用浏览器（Edge、Chrome、Firefox）打开解压目录下的 **`index_cn.html`**。它是离线首页：列出全部指南、登记文件和 100 条目录条目，每条都链接到本地文件。

不需要联网，也不需要安装任何软件。

## 离线阅读

- **首页与指南**：`index_cn.html`；`README_cn.md`、`search_log_cn.md` 和 `guides/*.md` 都另有同名 `.html` 版本，可在浏览器中直接打开，公式用包内 MathJax 渲染，文中的路径可点击跳转。`.md` 原文中的路径也已改为相对链接（VS Code、Typora 等可点击）。
- **网页镜像**（`courses/*_html_en/`、`software_docs/*/`）：
  - 站内页面之间的绝对网址已改为相对链接，镜像内的页面可离线互相跳转；指向目录的链接已补上 `index.html`。
  - 原先从 CDN 加载的 MathJax 3 / MathJax 4（含字体）改为包内 `_offline_libs/` 的副本；Tedrake《Underactuated Robotics》讲义先加载本地 MathJax，联网时 CDN 只作后备。
  - 原站外部的样式表、脚本、图标、图片和网页字体（共 181 个文件）已下载到各镜像目录下按域名分的子目录，例如 RLlib 文档的图片和样式在 `software_docs/RLlib_docs_html_en/docs.ray.io/en/latest/_images/`、`_static/`。
- **只能联网使用的部分**（离线时不显示，但不影响正文）：YouTube 视频、wandb 实验报告内嵌框、站内搜索、统计脚本、Hypothesis 批注插件、RLlib 聊天组件；以及指向未保存页面的链接（这些仍是在线网址，联网时点击可打开原站）。上游已经失效的少数图标字体（TorchRL 的 Font Awesome 等）联网也无法显示。
- **目录链接**：首页和指南里指向项目目录（如 `projects/...`）或论文目录的链接，在浏览器中显示为文件列表，再点其中的文件即可。
- **PDF**：浏览器或任何 PDF 阅读器均可直接打开。

### 课件压缩包

`courses/` 下的 3 个 MIT OCW 官方课件包（`.zip`）保持原样，解压后打开其中的 `index.html` 即可离线浏览。6.041SC 包内最长路径约 188 个字符，请解压到很短的目录（例如 `D:\ocw\6041\`），以免超过 Windows 路径长度限制。

## Windows 兼容改动

只改发布包，本地原资料库未改动。明细见 `windows_rename_map_cn.csv`。

- 113 个文件名改名：含 `?` 等 Windows 不允许字符的网页镜像资源（主要是 `xxx.css?v=…`、字体文件）改为 `_`；OmniSafe 测试数据、OpenSpiel 回放文件等过长的名字截短为“前 12 个字符 + 原名哈希”。引用这些文件的 37 个网页/样式表已同步改写。
- 没有仅大小写不同的文件名；内层压缩包中没有 Windows 不允许的文件名和符号链接。

## 未随发布包提供的教材（8 本）

Boyd & Vandenberghe《Convex Optimization》和 Bertsekas 的 7 本书（Abstract DP、A Course in RL、Lessons from AlphaZero、Neuro-Dynamic Programming、Convex Optimization Theory、Dynamic Programming and Stochastic Control、Rollout/Policy Iteration）的 PDF 版权页声明“保留全部权利，未经出版社书面许可不得复制”，作者只在个人站点提供免费下载，没有授予再分发许可，因此不放进发布包。它们仍在本地资料库中；官方下载地址见 `release_excluded_cn.csv`，下载后放回 `books/` 目录即可。目录 `catalog_cn.csv` 中保留这些条目，离线首页中标为“未随发布包提供”。

## 校验

- `archive_index_cn.csv` 列出包内全部 10,001 个条目（9,998 个文件、3 个空目录）及字节数。
- 打包时校验过：tar 退出码为 0、包内列表与计划列表逐行一致；解压对比 `tar -d` 与打包快照无差异。
- 打包内容是 2026-10-30 02:31（中欧时间）资料库的完整拷贝快照，之后资料库的改动不在本次发布中。

## 轻量 Git 分支

Release 对应的 Git 分支 `release-lite-20261030` 只含目录、登记 CSV、指南、脚本和以上说明文件（不含 PDF、网页镜像和源码快照），便于在 GitHub 网页上浏览。资料全文以 Release 附件为准。
