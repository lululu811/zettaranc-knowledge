# Maps of Content (MOC)

MOC（内容地图）是主题层级的导航入口。每个 MOC 是一个中心节点，通过 Dataview 动态聚合相关笔记。

## 已有 MOC

| MOC | 用途 | 聚合规则 |
|-----|------|---------|
| [[MOC-技术]] | 技术概念、工具、框架 | `tags` 包含"技术" |
| [[MOC-商业]] | 商业模式、市场、公司 | `tags` 包含"商业" |
| [[MOC-人物]] | 人物、学者、投资人 | `entity_type = person` |
| [[MOC-待整理]] | 尚未分类的页面 | 无任何 MOC 出链 |

## 创建新 MOC 的方法

1. 在 `wiki/mocs/` 下新建文件，命名格式 `MOC-主题名.md`
2. 使用 `type: map` frontmatter
3. 用 Dataview 查询自动列出相关页面

## Dataview 查询模板

**按标签聚合**：
```dataview
TABLE type, last_updated
FROM "wiki"
WHERE contains(tags, "标签名")
SORT last_updated DESC
```

**按类型聚合**：
```dataview
TABLE entity_type, last_updated
FROM "wiki/entities"
WHERE entity_type = "person"
SORT last_updated DESC
```

**按出链关系聚合（查找引用某 MOC 的页面）**：
```dataview
LIST
FROM "wiki"
WHERE contains(file.outlinks, [[MOC-主题名]])
SORT file.name ASC
```

## 命名规范

- 文件名：`MOC-<中文主题名>.md`
- frontmatter `title`：`MOC-主题名`
- 使用 TitleCase 命名风格
