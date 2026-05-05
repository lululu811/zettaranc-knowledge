# 语言设定与核心角色 (Global Rules)
- **语言指令**:无论输入何种语言,你必须始终使用**简体中文**进行思考、回复和知识库的编写。
- **角色定义**:你正在维护一个 **LLM Wiki**(根据 [Karpathy 的规范](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)),你的任务是将碎片化的信息编译成结构化、高度相互链接的 Obsidian 知识库。

# 数据范围 (Data Scope)
> ⚠️ **2026-04-26 起**:由于数据丢失,本知识库仅维护 **Zettaranc(知行小菜鸟)A股交易体系**。BOSS墨 / 三线文案 / 基本面 命名空间已移除,后续不再写入这些命名空间。

# 核心目录与权限边界 (Immutability & Architecture)
你必须严格遵守以下文件操作权限,这是不可逾越的底线:
- `/raw/` (不可变层 - Immutable):
  - **绝对只读**。这里存放原始素材、网页剪藏和自媒体文案。
  - **禁止修改或删除此目录下的任何文件**。它是事实的唯一来源。
- `/assets/` (媒体资产层):
  - 存放图片、PDF和媒体。引用时使用 Obsidian 标准语法 `![[文件名称.png]]`。
- `/wiki/` (编译输出层 - You Own This):
  - 这是你的专属工作区。你需要在此处创建、更新、提炼知识并解决矛盾。
  - **当前唯一命名空间**:`wiki/zettaranc/` — Zettaranc(知行小菜鸟)A股交易体系
  - 命名空间内部包含 `concepts/`、`entities/`、`sources/`、`syntheses/`、`index.md`、`log.md`

# Wiki 核心文件契约 (The Wiki Schema)
当你在 `/wiki/` 中工作时(尤其是执行写入操作后),必须维护以下基石:

1. **`wiki/index.md` (总目录)**:
   每次向 wiki 新增知识页后,必须同步更新此文件,将其按分类加入目录中。
   格式要求:`[[页面名称]] — 一句话描述`。
   - Entities/Concepts:使用 TitleCase 命名。
   - Sources/Syntheses:使用 kebab-case 命名。
   范例:
   ```markdown
   # Wiki Index
   ## Sources
   - [[摘要-source-slug]] — 该资料的核心主旨摘要。
   ## Entities
   - [[EntityName]] — 该实体的身份定义或核心功能。
   ## Concepts
   - [[ConceptName]] — 该概念或框架的核心定义。
   ## Syntheses
   - [[synthesis-slug]] — 该页面回答的复杂问题。
   ```

2. **`wiki/log.md` (操作日志)**:
   只能追加写入(Append-only)。每次操作后记录:`## [YYYY-MM-DD] <动作> | <操作简述>`。
   操作类型:ingest, query, lint, sync
   范例:
   ```markdown
   ## [2026-04-15] ingest | 引入示例资料
   - **变更**: 新增 [[摘要-example-article]]; 更新 [[index.md]]
   - **冲突**: 无
   ```

3. **内容分类**:
   - `wiki/zettaranc/concepts/`:存放概念、框架、方法论。
   - `wiki/zettaranc/entities/`:存放人物、公司、工具、产品。
   - `wiki/zettaranc/sources/`:存放从 `raw/` 提炼出的原始素材摘要。
   - `wiki/zettaranc/syntheses/`:存放针对复杂问题生成的深度研究报告。

   **Wikilink 命名**:Zettaranc 概念保持原名(如 `[[B1建仓波]]`),无需消歧后缀(因为已收缩为单一作者命名空间)。

4. **来源归因规则(2026-04-26 更新)**:
   raw/ 中所有来源均为整理者，不区分一手二手，按知识来源可信度排序:

   - **高可信度**:`raw/01-articles/知行小菜鸟/`、`raw/01-articles/大富翁小菜鸟/`（系统性整理，可信度高）
   - **中可信度**:`raw/01-articles/知行课代表/`、`raw/01-articles/复盘专用z/`（课程/直播整理）
   - **补充参考**:`raw/01-articles/TANGOO/`（学生笔记，作为补充参考）

   归因原则:
   - 所有来源均为 Zettaranc(Z 哥)交易体系的整理输出，不区分原创与整理
   - source 摘要文件需在标题与 frontmatter 中明确来源归因
   - 当同一概念被多个来源引用时，优先引用高可信度来源

5. **强制双向链接**:
   每一个 wiki 页面必须包含 `## 关联连接` 区域,使用 Obsidian 双链 `[[页面名称]]` 链接到其他相关概念。绝不能产生孤岛页面。

6. **矛盾处理原则**:
   如果新摄入的知识与旧知识冲突,不要静默覆盖。在页面中新建 `## 知识冲突` 区块(或使用 `> [!caution]` Callout),将两种说法都保留并做对比。

# 工作流指令说明 (Workflows / Skills)
当被要求执行以下操作时,请遵循核心逻辑(由专用 Agent Skills 接管):
- `/ingest <路径>`:读取指定的 `raw/` 文件,将其核心价值提炼并整合到 `wiki/zettaranc/` 目录的相关概念/实体中。同步更新 `wiki/zettaranc/index.md`、`wiki/zettaranc/log.md` 与总目录 `wiki/index.md`。
- `/query <问题>`:通过读取 `wiki/index.md` 寻找相关文件,进行深度阅读后综合回答,并在回答中必须使用 `[[wikilink]]` 标注引用来源。
- `/lint`:全局扫描 `wiki/` 目录,找出孤岛页面(没有双链)、死链(链接不存在的页面)以及存在逻辑冲突的地方,并向我报告。

# 页面 Frontmatter (YAML) 规范
所有生成的 wiki 页面**必须**包含以下完整 YAML 头部。缺少任一必填字段将导致 Dataview 查询失效。

```yaml
---
title: "页面标题"                    # 必须:页面标题
type: concept | entity | source | synthesis | map   # 必须:页面类型
tags: [标签1, 标签2]                # 必须:至少一个标签
sources: []                          # 可选:关联的来源文件路径列表
raw_source: raw/01-articles/xxx.md # ingest 时必填:原始素材路径
created: YYYY-MM-DD                  # 必须:创建日期
last_updated: YYYY-MM-DD             # 必须:最后更新
status: draft | published            # 必须:草稿/已发布
ingested: true                       # ingest 页面必须为 true
ingestion_version: 1                 # ingest 页面每次更新 +1
# --- 以下为各类型可选字段 ---
# concept:    complexity (low / medium / high)
# entity:     entity_type (person / company / product / tool / organization / location / other)
# source:     credibility (low / medium / high), source_type (article / paper / book / video / podcast / lecture / other)
# synthesis:  confidence (low / medium / high), research_question
---
```

> [!warning]+ 字段完整性检查清单
> 创建或更新页面时,逐项确认:
> - [ ] `title` 非空
> - [ ] `type` 为五选一(concept / entity / source / synthesis / map)
> - [ ] `tags` 至少一个
> - [ ] `created` 和 `last_updated` 格式为 YYYY-MM-DD
> - [ ] `status` 为 draft 或 published
> - [ ] 若为 ingest 来源页:`raw_source`、`ingested: true`、`ingestion_version` 必填
> - [ ] 各类型可选字段尽量补齐(complexity / entity_type / credibility / confidence)以激活 Dataview 仪表盘

# MOC (Map of Contents) 维护
MOC 是主题导航页,弥补 8 层目录的"穿透式分类"(同一概念可能跨多个层级)。

- 路径:`wiki/mocs/MOC-<领域>.md`
- 命名:中文领域名,Zettaranc 当前 4 个主题 MOC:
  - [[MOC-战法策略]] — 03-买卖信号 + 04-战法策略
  - [[MOC-工具体系]] — 02-底层工具
  - [[MOC-资金筹码]] — 05-资金仓位 + 06-市场筹码
  - [[MOC-心法哲学]] — 01-体系总览 + 07-心法哲学 + 08-操作手册
  - [[MOC-待整理]] — 孤儿页面与缺字段页面的质量监控站
- frontmatter:`type: map`
- 内容:Dataview 自动聚合 + 静态目录 fallback
- 维护:新建/更新概念页时,同步在合适的 MOC `## 静态目录` 块中追加链接

# 命名规范

| 类型 | 命名风格 | 示例 |
|------|---------|------|
| concept | TitleCase / 中文原名 | `[[B1建仓波]]`、`[[白线黄线系统]]`、`[[少妇战法]]` |
| entity | TitleCase | `[[Zettaranc]]`、`[[国家队]]`、`[[麒麟会]]` |
| source | kebab-case | `[[摘要-zhihang-精水流深-batch-01]]`、`[[batch-09-zhixing-extension]]` |
| synthesis | 中文原名 / kebab-case | `[[短线交易操作手册]]`、`[[长线交易操作手册]]` |
| MOC | TitleCase 中文 | `[[MOC-战法策略]]`、`[[MOC-工具体系]]` |
