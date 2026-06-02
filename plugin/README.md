# Zettaranc Knowledge — Claude Code Skill

[Zettaranc（知行小菜鸟）](https://github.com/chenleiitaz/zettaranc-knowledge) A股交易体系的 Claude Code Skill 版本。安装后你的 Claude Code 即可查询完整的交易规则、分析买卖信号、摄入新素材到知识库。

## 知识体系

```
87 个概念 | 6 个实体 | 8 个来源摘要
├── 01-体系总览（5）   — 三模块架构、交易哲学
├── 02-底层工具（11）  — KDJ、筹码、白线黄线、砖形图
├── 03-买卖信号（15）  — B1/B2/B3/S1/DSZ 等核心信号
├── 04-战法策略（17）  — 少妇/坑口/双枪/量比等战法
├── 05-资金仓位（9）   — 仓位管理、止损纪律
├── 06-市场筹码（14）  — 主线判断、题材分析
├── 07-心法哲学（14）  — 交易心理、纪律执行
└── 08-操作手册（2）   — 短线/长线操作流程
```

## 安装方式

### Claude Code Plugin Marketplace

```
/plugin marketplace add chenleiitaz/zettaranc-knowledge
/plugin install zettaranc@zettaranc-knowledge
```

### npx skills（跨 Agent）

```bash
npx skills add https://github.com/chenleiitaz/zettaranc-knowledge
```

### 手动安装

将 `skills/zettaranc/` 目录复制到你的项目 `.claude/skills/` 下：

```bash
cp -r skills/zettaranc /path/to/your/project/.claude/skills/
```

## 使用示例

### 查询交易规则

```
你: B1建仓波的判断标准是什么？
Claude: [从知识库中检索 B1 相关内容，给出精确回答]
```

### 分析买卖信号

```
你: 这只票出现了 J 值 -15，是不是 B1 信号？
Claude: [基于知识库规则分析，给出判断和注意事项]
```

### 摄入新素材

```
你: 把这篇文章导入知识库
Claude: [执行 ingest 流程，提炼核心信息，创建/更新页面]
```

## 文件结构

```
plugin/
├── .claude-plugin/
│   ├── plugin.json            # 插件元数据
│   └── marketplace.json       # Marketplace 上架信息
├── skills/
│   └── zettaranc/
│       ├── SKILL.md           # 核心技能文件（体系总览+工作流）
│       └── references/
│           ├── 01-信号系统.md  # B1/B2/B3/S1/DSZ 详细规则
│           ├── 02-战法策略.md  # 少妇/坑口/双枪/量比等战法
│           ├── 03-工具体系.md  # KDJ/筹码/砖形图等工具
│           ├── 04-心法哲学.md  # 交易心理/纪律/资金管理
│           └── 05-ingest-workflow.md  # 摄入工作流
├── README.md
└── LICENSE
```

## 许可证

MIT License

## 致谢

交易体系来自 [Zettaranc（知行小菜鸟）](https://space.bilibili.com/) 的 A 股交易教学。
