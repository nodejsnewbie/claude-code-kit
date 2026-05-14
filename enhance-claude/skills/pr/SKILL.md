---
name: pr
description: 生成详细的 Pull Request 描述
tags: PR, Git工作流, 代码评审
allowed-tools: Bash(git *)
---

# 生成 PR 描述

**核心原则：让 reviewer 一眼看懂改动。**

## 操作步骤

1. 对比当前分支与目标分支：`git diff main...HEAD --stat`
2. 分析关键改动、影响范围
3. 输出 Markdown 格式的 PR 描述

## PR 模板

```markdown
## 变更摘要
- 改了什么，为什么改

## 改动细节
- 关键文件和逻辑变更

## 影响范围
- 哪些模块受影响
- 是否有 breaking change

## 测试计划
- 如何验证改动
- 需要手动测试的场景

## Checklist
- [ ] 代码已 review
- [ ] 测试已通过
- [ ] 文档已更新（如需要）
```
