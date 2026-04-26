# zettaranc-knowledge — Zettaranc A股交易体系知识库

> 基于 [Karpathy Wiki 模式](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 构建的结构化知识图谱,聚焦 **Zettaranc(知行小菜鸟)A股交易体系**。

## 📦 项目地址

| 仓库 | 地址 | 说明 |
|------|------|------|
| **GitHub(主仓库)** | https://github.com/lululu811/zettaranc-knowledge.git | 主开发仓库,完整内容 |
| **Gitee(国内镜像)** | https://gitee.com/chenleizzzz/zettaranc-knowledge.git | 国内访问加速镜像 |

> ⚠️ **关于 Gitee 镜像**:Gitee 公开仓库审核较严,部分 skill 配置/Agent 提示词内容暂时无法在 Gitee 公开。如需完整访问请使用 GitHub 主仓库;Gitee 镜像主要供国内用户镜像同步知识内容。

### 克隆方式

```bash
# 国外/科学上网环境
git clone https://github.com/lululu811/zettaranc-knowledge.git

# 国内环境(知识内容部分)
git clone https://gitee.com/chenleizzzz/zettaranc-knowledge.git
```

## ⚠️ 数据丢失说明

**2026-04-26 起**:本仓库原本包含 4 个作者命名空间(Zettaranc / BOSS墨 / 三线文案 / 基本面),共 83 个概念、4 篇 syntheses。因数据丢失,**仅保留 Zettaranc 部分**。

已移除的命名空间:

| 命名空间 | 原概念数 | 说明 |
|---------|---------|------|
| `wiki/boss_mo/` | 14 | BOSS墨 宏观交易:盈亏比驱动+刻舟求剑 |
| `wiki/sanxian/` | 12 | 三线文案大锅饭 宏观地缘:版本更新+G2博弈 |
| `wiki/jibenmian/` | 15 | 知识星球 产业基本面跟踪 |

后续暂时只维护 Zettaranc 一人知识库,其他作者体系待数据恢复或重新整理。

## 知识库规模

| 命名空间 | 概念 | 来源 | 实体 | Syntheses | 原始素材 | 说明 |
|---------|------|------|------|-----------|---------|------|
| **Zettaranc** | 63 个 | 7 个 | 6 个 | 2 篇 | 407 篇 | A股交易体系:短线/长线操作手册 |

### 来源构成(7 个 source 摘要)

| 类型 | source | 体量 | 时间跨度 |
|-----|--------|------|---------|
| 一手原创 | [[摘要-zhihang-精水流深-batch-01]] | 34 篇 | 早期核心 |
| 一手原创 | [[摘要-zhihang-知行课代表-batch-02]] | 56 篇 | 课代表笔记 |
| 一手原创 | [[摘要-zhihang-空谷幽兰-batch-03]] | 46 篇 | 深度教程 |
| 一手原创 | [[摘要-zhihang-复盘专用z-batch-04]] | 49 篇 | 直播复盘 |
| 一手原创(延续) | [[batch-09-zhixing-extension]] | 58 篇 | 2025-11 → 2026-04 |
| 二级整理(学生) | [[batch-05-tangoo-notes]] | 62 篇 | 2025-06 → 2026-04 |
| 二级整理(舰长班) | [[batch-06-dafuweng-systems]] | 185 篇(战法核心 30 篇) | 2025-08 → 2026-04 |

## Zettaranc 体系概览

以 **白线黄线系统** 和 **砖形图** 为两大核心工具,围绕以下流程构建:

| 环节 | 核心工具 | 关键概念 |
|------|---------|---------|
| 择时 | [[活跃市值]]、[[白线黄线系统]] | 择时永远大于选股 |
| 选股 | [[三最原则]]、[[顺周期轮动]] | 只选最美、只买最强、只拿最硬 |
| 买点 | [[B1建仓波]]、[[B2突破]]、[[B3买点]] | J值筛选、两个30%原则 |
| 卖出 | [[S1信号]]、[[DSZ战法]] | 卖出三铁律、半仓放飞 |
| 持仓 | [[去弱留强]]、[[底仓与动态仓]] | 底仓守信仰,动态仓守纪律 |
| 风控 | [[防守哲学]]、[[交易闭环]] | 穿越牛熊靠防守,不靠进攻 |
| 心法 | [[交易心理]]、[[周期与人性]] | 装睡的拔河,周线格局定方向 |

> 完整索引见 [wiki/zettaranc/index.md](wiki/zettaranc/index.md)

## 目录结构

```
├── raw/                          # 原始素材层(只读,不可修改)
│   └── 01-zettaranc/             # 5 个子目录,共 407 篇原始文章
│       ├── 知行小菜鸟/           # Z 哥本人(精水流深/空谷幽兰/延续)
│       ├── 知行课代表/           # Z 哥课代表笔记
│       ├── 复盘专用z/            # Z 哥直播复盘
│       ├── TANGOO/               # 渣A小学生(Z哥学生二级笔记)
│       └── 大富翁小菜鸟/         # 大富翁小菜鸟号(Z哥粉丝/舰长班整理)
│
├── wiki/                         # 结构化知识库(编译输出层)
│   ├── zettaranc/                # Zettaranc命名空间
│   │   ├── concepts/             # 63 个概念
│   │   ├── entities/             # 6 个实体(作者+资金画像)
│   │   ├── sources/              # 7 个来源摘要
│   │   ├── syntheses/            # 短线/长线操作手册
│   │   ├── index.md
│   │   └── log.md
│   │
│   ├── index.md                  # 总目录
│   └── log.md                    # 全局操作日志
│
├── assets/                       # 图片与媒体资产
├── CLAUDE.md                     # 维护规范(AI Agent 指令)
└── CHANGELOG.md                  # 版本变更记录
```

## 来源权重规则

当不同来源对同一概念描述存在差异时,按以下优先级处理:

### 一手原创(Z哥本人,权威)
1. **精水流深** — 核心体系输出,最权威
2. **空谷幽兰** — 深度教程,详细解释
3. **知行小菜鸟延续(2025-11→2026-04)** — 体系最新前沿(AI控盘世界观/知行交易模块)
4. **复盘专用z** — 直播复盘,实战性强但口语化

### 二级整理者(粉丝/学生,需归因)
5. **大富翁小菜鸟号** — Z 哥舰长班整理,最完整教科书级二级文献(归因为"Z 哥语料 + 整理者"双名)
6. **TANGOO(渣A小学生)** — Z 哥学生课堂笔记体,部分作者私货需明确标注(搬砖策略 / 宏观闭环豆包对话)
7. **知行课代表** — 付费笔记整理,体系化但为二手

冲突标注示例见 `wiki/zettaranc/concepts/B1建仓波.md`、`wiki/zettaranc/concepts/对称VA战法.md`、`wiki/zettaranc/concepts/白线黄线系统.md` 中的 `## 知识冲突` / `[!caution]` 区块。

## 使用方式

### Obsidian

1. **打开知识库**:Obsidian → Open folder as vault → 选择本目录
2. **附件设置**:设置 → 文件与链接 → 附件默认存放路径设为 `assets/`
3. **关系图谱**:打开 `wiki/index.md` → 点击右上角关系图谱图标,查看知识网络连接
4. **Mermaid 图**:安装 Mermaid 插件或使用 Obsidian 内置渲染(需开启安全模式允许本地渲染)

详见 [obsidian-config.md](obsidian-config.md)

### 推荐插件

| 插件 | 用途 |
|------|------|
| Web Clipper | 网页剪藏新文章到 raw/ 目录 |
| Dataview | 基于 YAML frontmatter 查询 |
| Canvas | 思维导图与概念图 |
| Excalidraw | 手绘风格图表 |
| Advanced Tables | Markdown 表格增强编辑 |

## 知识库维护

本项目由 Claude Code 自动维护,遵循以下规范:

- 新增知识后自动更新对应命名空间的 `index.md` 和 `log.md`
- 知识冲突时保留双方说法,在 `## 知识冲突` 区块对比(使用 `[!caution]` Callout)
- 所有 wiki 页面必须包含 `## 关联连接` 区域,使用 `[[双链]]` 链接
- 新增概念页面后必须同步更新总目录 `wiki/index.md`
- 所有页面包含 YAML frontmatter(title, type, tags, sources, last_updated)

维护规范详见 [CLAUDE.md](CLAUDE.md)

## 版本历史

| 版本 | 日期 | 内容 |
|------|------|------|
| v0.5.0 | 2026-04-26 | 全量摄入 TANGOO/大富翁/知行延续 305 篇,新增 21 概念 + 5 实体 + 3 source |
| v0.4.0 | 2026-04-26 | 数据丢失,移除 BOSS墨/三线文案/基本面命名空间,仅保留 Zettaranc |
| v0.3.0 | 2026-04-19 | Wiki全面美化:Callout + Mermaid + 受益标的表格 |
| v0.2.0 | 2026-04-19 | 多作者命名空间重构:新增BOSS墨/三线文案/基本面 |
| v0.1.0 | 2026-04-18 | 知识库初始化,151篇文章提炼40+概念 |

详见 [CHANGELOG.md](CHANGELOG.md)

## 联系作者

如对知识库内容、Zettaranc 交易体系或 AI + 金融研究方向感兴趣,欢迎扫码关注个人公众号交流:

<p align="center">
  <img src="assets/wechat-qrcode.jpg" alt="个人公众号二维码" width="240" />
</p>

> 微信扫描上方二维码即可添加。

## License

知识内容源自作者公开分享的体系与研报,仅供学习研究使用。
