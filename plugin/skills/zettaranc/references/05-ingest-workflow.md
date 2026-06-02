> 本文件从 `.claude/skills/ingest/SKILL.md` 提炼而成，供 Zettaranc Skill 按需加载。

# 摄入工作流（Ingest Workflow）

将原始素材（raw/）编译到知识库（wiki/zettaranc/）的标准化流程。

## 目录约定

| 目录 | 用途 | 权限 |
|------|------|------|
| `raw/01-zettaranc/` | 待处理素材（收件箱） | 只读 |
| `raw/09-archive/` | 已处理归档 | 禁止读取 |
| `wiki/zettaranc/sources/` | 资料摘要 | 可写 |
| `wiki/zettaranc/entities/` | 实体页面 | 可写 |
| `wiki/zettaranc/concepts/` | 概念页面 | 可写 |
| `wiki/zettaranc/syntheses/` | 综合分析 | 可写 |

## 来源可信度分级

| 级别 | 来源目录 | 说明 |
|------|---------|------|
| **高** | 知行小菜鸟/、大富翁小菜鸟/ | 系统性整理，可信度高 |
| **中** | 知行课代表/、复盘专用z/ | 课程/直播整理 |
| **补充** | TANGOO/ | 学生笔记，补充参考 |

## 触发方式

- `/ingest` — 扫描 raw/ 所有子目录，处理未归档文件
- `/ingest <path>` — 处理指定文件
- 自然语言："把这个资料摄入知识库"、"导入这篇文章"

## 8 步编译流水线

```
源文件 → 1.检查状态 → 2.读取内容 → 3.提炼核心 → 4.创建摘要
      → 5.网络化(实体/概念) → 6.更新索引 → 7.归档 → 8.更新状态
```

### 步骤 1：检查状态

读取 `.claude/ingest-state.json`，计算文件哈希，对比历史记录：
- `archived` 且哈希一致 → **跳过**
- `modified` 或无记录 → **继续编译**

### 步骤 2：读取源文件

- `.md` 文件：完整读取
- `.pdf` 文件：尝试提取文本，失败则记录元信息

### 步骤 3：提炼核心

提取三要素：
- **核心主旨**（1-2 句话）
- **实体**（人物、公司、工具、产品）
- **概念**（框架、方法论、理论）

### 步骤 4：创建来源摘要

在 `wiki/zettaranc/sources/` 创建摘要文件，文件名 `摘要-{slug}.md`。

Frontmatter 必须包含：
```yaml
type: source
credibility: high | medium | supplementary
ingested: true
ingestion_version: 1
raw_source: raw/01-zettaranc/xxx.md
```

### 步骤 5：知识网络化

对提取的每个实体/概念：
1. **不存在** → 创建新页面
2. **已存在** → 增量合并（追加新信息，不覆盖）
3. **发现冲突** → **暂停**，报告用户，等待决策

增量合并规则：
- `last_updated` → 更新为当前时间
- `ingestion_version` → +1
- `raw_source` → 追加到 `sources` 数组，不覆盖
- 保留所有现有内容和链接

### 步骤 6：更新全局注册表

- 更新 `wiki/index.md`（添加新页面到对应分类）
- 追加 `wiki/log.md`（Append-only 操作日志）

### 步骤 7：归档源文件

确认所有输出页面已创建后，将源文件移动到 `raw/09-archive/`。
**绝对禁止修改源文件内容。**

### 步骤 8：更新状态记录

更新 `.claude/ingest-state.json` 中的文件记录，状态设为 `archived`。

## 冲突处理流程

```
发现冲突 → 暂停 → 报告用户 → 选择处理方式 → 继续
```

用户选择：
- **A)** 保留新旧两者，标注为"知识冲突"
- **B)** 用新知识覆盖旧知识
- **C)** 放弃本次 ingest

## 状态文件格式

`.claude/ingest-state.json`：
```json
{
  "version": 1,
  "last_full_scan": "ISO时间",
  "files": {
    "raw/01-zettaranc/xxx.md": {
      "hash": "文件哈希",
      "status": "pending | modified | archived | failed",
      "ingested_at": "ISO时间",
      "outputs": ["wiki/zettaranc/sources/摘要-xxx.md"]
    }
  }
}
```

## Frontmatter 标记（必须）

每个通过 ingest 创建/更新的 wiki 页面必须包含：
```yaml
ingested: true
raw_source: raw/01-zettaranc/xxx.md
ingestion_version: 1
```

## 关键注意事项

- 绝对不读取 `raw/09-archive/` 下的任何文件
- 所有页面必须包含 `## 关联连接`，不能产生孤岛
- 使用简体中文
- 实体用 TitleCase，概念/来源用 kebab-case
- Zettaranc 概念保持原名（如 `[[B1建仓波]]`），无需消歧后缀
