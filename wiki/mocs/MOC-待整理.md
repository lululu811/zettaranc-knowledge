---
title: MOC-待整理
type: map
tags: [MOC, 待整理, 孤儿]
last_updated: 2026-05-05
---

# 🗂️ MOC-待整理

> 聚合所有尚未被任何主题 MOC 引用、或缺失关键 frontmatter 字段的页面。这是知识库的"质量监控站"。

## 📊 Dataview 动态聚合

> [!warning]+ 没有反向链接的孤儿页面
> ```dataview
> LIST
> FROM "wiki/zettaranc"
> WHERE length(file.inlinks) = 0
>   AND type != "index"
>   AND type != "map"
> SORT file.name ASC
> ```

> [!warning]+ frontmatter 缺失关键字段的页面
> ```dataview
> LIST "缺失:" + (status = null ? "status " : "") + (created = null ? "created " : "")
> FROM "wiki/zettaranc"
> WHERE type != null
>   AND (status = null OR created = null)
> SORT file.name ASC
> ```

> [!danger]+ 长期草稿(超过 30 天未完成)
> ```dataview
> LIST
> FROM "wiki/zettaranc"
> WHERE status = "draft"
>   AND last_updated < date(today) - dur(30 days)
> SORT last_updated ASC
> ```

> [!info]+ 没有任何 MOC 出链的页面
> ```dataview
> LIST
> FROM "wiki/zettaranc"
> WHERE type = "concept"
>   AND !contains(file.outlinks, [[MOC-战法策略]])
>   AND !contains(file.outlinks, [[MOC-工具体系]])
>   AND !contains(file.outlinks, [[MOC-资金筹码]])
>   AND !contains(file.outlinks, [[MOC-心法哲学]])
> SORT file.name ASC
> ```

---

## 📚 手动条目(临时收纳)

> 在此手动登记一些有疑问、待分类、待合并的页面。处理完成后从此移除。

- _暂无_

---

## 🛠️ 处理流程

1. **孤儿页面** → 给页面添加至少 1~2 条 `[[相关概念]]` 双链
2. **缺字段页面** → 用 `/lint` 自动检查并补全 created/status
3. **长期草稿** → 决定:推进发布 / 合并到其它页 / 直接删除
4. **无 MOC 出链** → 在页面 `## 关联连接` 区追加 `[[MOC-xxx]]` 引用

---

## 🔗 关联 MOC

- [[MOC-战法策略]]
- [[MOC-工具体系]]
- [[MOC-资金筹码]]
- [[MOC-心法哲学]]
