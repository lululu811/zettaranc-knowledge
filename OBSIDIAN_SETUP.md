---
title: Obsidian 配置说明
type: reference
tags:
  - meta
  - obsidian
  - 配置
created: 2026-04-18
last_updated: 2026-05-05
status: published
---
# Obsidian 配置说明

本知识库已预置统一的 Obsidian 配置和 CSS 样式,开箱即用。

## 已启用的核心插件

| 插件 | 用途 |
|------|------|
| Graph | 知识图谱可视化 |
| Backlink | 反链面板 |
| Page Preview | 悬浮预览 |
| Templates | 笔记模板 |
| Note Composer | 笔记合并/拆分 |
| Outline | 文档大纲 |
| Tag Pane | 标签面板 |
| Word Count | 字数统计 |

## 推荐安装的社区插件

首次打开 Vault 后,请前往 **Settings → Community plugins → Browse** 安装以下插件:

| 类别 | 插件 | 用途 |
|------|------|------|
| 查询 | **Dataview** | 数据查询与动态列表(`wiki/index.md` 仪表盘依赖此插件) |
| 查询 | **Omnisearch** | 全文搜索增强 |
| 效率 | **Templater** | 高级模板引擎 |
| 效率 | **QuickAdd** | 快速捕获与笔记创建 |
| 效率 | **Commander** | 自定义命令与工具栏 |
| 组织 | **Calendar** | 日历视图 |
| 组织 | **Periodic Notes** | 周期笔记(日/周/月/年) |
| 组织 | **Tag Wrangler** | 标签批量管理 |
| 视觉 | **Style Settings** | 主题样式微调 |
| 视觉 | **Callout Manager** | Callout 自定义管理 |
| 视觉 | **Hover Editor** | 悬浮编辑窗口 |
| 导航 | **Recent Files** | 最近打开文件 |

> 已安装的插件列表保存在 `.obsidian/community-plugins.json` 中。

## CSS 样式片段

位于 `.obsidian/snippets/`,已自动启用:

| 片段 | 说明 |
|------|------|
| `wiki-reading.css` | 阅读排版优化:标题层级、段落间距、引用块、表格 |
| `wiki-callouts.css` | Callout 美化:语义化颜色 + 左侧边条 |
| `wiki-components.css` | 组件增强:双链、外部链接、标签、图片、代码块 |

如需调整样式,可在 **Settings → Appearance → CSS Snippets** 中开关单个片段。

## 标准模板

位于项目根目录 `templates/`,包含 4 种页面类型:

| 模板 | 用途 | 关键区块 |
|------|------|---------|
| `entity.md` | 人物、公司、工具、产品等实体 | 基本资料、时间线、评价与影响 |
| `concept.md` | 概念、框架、方法论 | 定义、原理、类比、误区、应用场景 |
| `source.md` | 原始资料摘要 | 元信息、核心摘要、批注、可信度评估 |
| `synthesis.md` | 综合分析报告 | 研究问题、证据表、结论、行动建议 |

### 配置 Templater 使用模板

1. 安装 **Templater** 社区插件
2. 前往 **Settings → Templater**,设置 `Template folder location` 为 `templates`
3. 可选:设置 `Trigger Templater on new file creation` 为开启

### 手动使用模板

新建笔记时,按 `Ctrl/Cmd + P` 打开命令面板,搜索 "Templater: Open Insert Template Modal" 选择对应模板。

## Dataview 动态仪表盘

`wiki/index.md` 已预置 Dataview 查询,安装 Dataview 插件后自动生效:

- **最新来源**:自动列出最近摄入的 raw 资料
- **概念库/实体库/综合分析**:按类型动态聚合
- **待处理清单**:自动找出草稿状态、无来源的页面

如需创建新的主题地图(MOC),参考 `wiki/mocs/README.md` 中的 Dataview 查询模板。

## 推荐主题

本 CSS 片段不依赖特定主题,在默认主题下效果最佳。如需更换主题,建议:

- **Minimal** — 极简高定制(配合 Style Settings 使用)
- **Things** — 清爽语义化配色
- **AnuPpuccin** — 柔和护眼

## Web Clipper 与剪藏

- 浏览器扩展:https://obsidian.md/clipper
- 设置剪藏笔记保存路径为 `<本目录>/raw/01-articles/`(或其它 raw 子目录)
- 支持 Chrome、Edge、Firefox

> ⚠️ `raw/` 目录默认 git 忽略(原始素材仅作为本地事实来源,不入版本控制)。

## 首次使用步骤

1. 在 Obsidian 中打开本文件夹作为 Vault
2. 前往 **Settings → Community plugins**,关闭 Restricted mode
3. 按上表安装需要的社区插件(至少安装 **Dataview** 和 **Templater**)
4. 在 **Appear
## 核心摘要
空谷幽兰系列是Z哥在"空谷幽兰·知行社"发布的深度交易教程，共46篇。内容涵盖少妇战法、B1/B2/B3体系、坑口战法、单针下20/下30、双线战法、呼吸结构、三最原则、量比战法、B3战法、交易节奏等。这是最完整的体系输出，从心法到技法到实战全覆盖，新增概念密度最高。

## 关联连接
- [[Zettaranc]] — A股交易博主Z哥
- [[少妇战法]] — 基础交易心法
- [[坑口战法]] — 挖坑填坑理论
- [[单针下20]] — 补票战法
- [[单针下30]] — 单针策略迭代版
- [[双线战法]] — 白线黄线系统
- [[三最原则]] — 选股买股持仓心法
- [[量比战法]] — 开盘资金意图判断
- [[B3买点]] — 趋势中继确认
- [[呼吸结构]] — 量价节奏
ance → CSS Snippets** 中确认三个片段已启用
1. 配置 Templater 的模板文件夹为 `templates/`
2. 将原始资料放入 `raw/` 目录
3. 执行 `/ingest` 开始编译知识
