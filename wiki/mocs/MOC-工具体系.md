---
title: MOC-工具体系
type: map
tags: [MOC, 底层工具, 指标, 技术]
last_updated: 2026-05-05
---

# 🔧 MOC-工具体系

> 聚合 Zettaranc 体系下所有「底层技术工具」类知识。涵盖白线黄线、砖形图、MACD、量价关系、N 型结构、关键 K 等买卖判断的基础设施。

## 📊 Dataview 动态聚合

> [!abstract]+ 底层工具概念(按更新日期)
> ```dataview
> TABLE
>   complexity AS "复杂度",
>   last_updated AS "最后更新",
>   status AS "状态"
> FROM "wiki/zettaranc/concepts/02-底层工具"
> WHERE type = "concept"
> SORT last_updated DESC
> ```

> [!tip]+ 标签聚合(工具 / 指标 / 技术分析)
> ```dataview
> LIST
> FROM "wiki/zettaranc"
> WHERE contains(tags, "工具") OR contains(tags, "指标") OR contains(tags, "技术")
> SORT file.name ASC
> ```

---

## 📚 静态目录(Dataview Fallback)

### 两大核心工具

- [[白线黄线系统]] — 基于白线黄线相对位置判断趋势
- [[砖形图]] — 4 天情绪循环的红绿砖变盘点判断

### 趋势线 / 均线类

- [[知行趋势线]] — BBI 升级版,白线+黄线四种情形
- [[N型结构]] — 所有走势的底层基石,高低点抬高框架

### MACD 系列

- [[MACD三大用法]] — DIF 0 轴判多空 + 顶底背离 + 金叉空死叉多陷阱
- [[顶底背离体系]] — Z 哥 MACD 完整方法论
- [[MACD共振战法]] — 砖形图与 MACD 双共振

### 量价关系

- [[量价关系四类]] — 放量/缩量/平量/地量四态识别
- [[关键K]] — 90% K 线是垃圾,只有关键 K 决定走势
- [[暴力K]] — 关键 K 高阶形态(归在战法策略)
- [[倍量柱]] — 今日量 ≥ 昨日量 × 2,关键 K 的核心量能特征
- [[天量柱]] — 近 30~60 日最大成交量,主升浪启动或见顶的极端信号

### 元概念

- [[活跃市值]] — 判断多空区间的核心择时指标
- [[有序与无序]] — K 线二元状态元理论

---

## 🔗 关联 MOC

- [[MOC-战法策略]] — 工具的下游应用(B1/B2/少妇/嘀嘀等都基于这些工具)
- [[MOC-资金筹码]] — 工具与资金博弈的连接(主力出货/筹码战争)
- [[MOC-心法哲学]] — 工具使用心法(如金叉空/死叉多陷阱的认知)
