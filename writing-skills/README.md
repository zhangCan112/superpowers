# Writing Skills - 独立版

这是一个从 [superpowers](https://github.com/stevensacks/superpowers) 项目中抽取的独立 skill，用于帮助您编写高质量的 AI Agent Skills。

## 什么是 Skill？

Skill 是针对已验证技术、模式或工具的参考指南。Skills 帮助 AI 助手找到并应用有效的方法来解决问题。

**Skills 是：** 可复用的技术、模式、工具、参考指南

**Skills 不是：** 关于你如何解决某个问题的叙述

## 安装

### Claude Code

将此文件夹复制到您的 Claude Code skills 目录：

```bash
# 创建 skills 目录（如果不存在）
mkdir -p ~/.claude/skills

# 复制 writing-skills 到该目录
cp -r writing-skills ~/.claude/skills/
```

### 其他 AI 工具

根据您使用的 AI 工具的文档，将此 skill 放置到相应的 skills 目录中。

## 目录结构

```
writing-skills/
├── SKILL.md                        # 主文档 - Skill 编写指南
├── anthropic-best-practices.md     # Anthropic 官方最佳实践
├── testing-skills-with-subagents.md # 使用子 agent 测试 skills
├── persuasion-principles.md        # 说服原则（用于设计有效的 skills）
├── graphviz-conventions.dot        # Graphviz 流程图规范
├── render-graphs.js                # 渲染流程图的脚本
├── README.md                       # 本文件
└── examples/
    └── CLAUDE_MD_TESTING.md        # 测试示例
```

## 核心概念

### TDD 映射到 Skill 创建

| TDD 概念 | Skill 创建 |
|-------------|----------------|
| **测试用例** | 使用子 agent 的压力场景 |
| **生产代码** | Skill 文档 (SKILL.md) |
| **测试失败 (RED)** | Agent 在没有 skill 时违反规则（基线） |
| **测试通过 (GREEN)** | Agent 在有 skill 时遵守规则 |
| **重构** | 在保持合规的同时关闭漏洞 |

### 核心原则

**如果你没有看到 agent 在没有 skill 的情况下失败，你就不知道 skill 是否教对了东西。**

## SKILL.md 结构

```markdown
---
name: Skill-Name-With-Hyphens
description: Use when [specific triggering conditions and symptoms]
---

# Skill Name

## Overview
这是什么？用 1-2 句话说明核心原则。

## When to Use
[如果不明显，使用小型内联流程图]

症状和用例的项目符号列表
何时不使用

## Core Pattern (for techniques/patterns)
前后代码对比

## Quick Reference
常见操作的表格或项目符号

## Implementation
简单模式使用内联代码
大型参考或可复用工具使用链接

## Common Mistakes
哪里出错 + 修复方法

## Real-World Impact (可选)
具体结果
```

## 描述字段最佳实践

**关键：描述 = 何时使用，而非 skill 做什么**

```yaml
# ❌ 不好：总结工作流程
description: Use when executing plans - dispatches subagent per task with code review

# ✅ 好：只有触发条件
description: Use when executing implementation plans with independent tasks
```

## 工具

### 渲染流程图

如果您安装了 graphviz，可以使用 `render-graphs.js` 将 skill 中的流程图渲染为 SVG：

```bash
# 需要先安装 graphviz
# macOS: brew install graphviz
# Linux: apt install graphviz

./render-graphs.js path/to/skill-directory
./render-graphs.js path/to/skill-directory --combine  # 合并所有图表
```

## 进一步阅读

- `SKILL.md` - 完整的 skill 编写指南
- `anthropic-best-practices.md` - Anthropic 官方的 skill 编写最佳实践
- `testing-skills-with-subagents.md` - 如何测试您的 skills
- `persuasion-principles.md` - 使 skills 更有效的心理学原则

## 许可证

MIT License - 详见原始 [superpowers](https://github.com/stevensacks/superpowers) 项目。

## 致谢

此 skill 来源于 [superpowers](https://github.com/stevensacks/superpowers) 项目，由 Stevensacks 创建和维护。