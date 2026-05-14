---
name: cc-commit
description: 提交代码，自动分组并生成符合规范的 commit message
tags: Git工作流, 提交, 版本控制
allowed-tools: Bash(git *)
---

# 提交代码

**核心原则：原子提交，语义清晰。**

## 操作步骤

1. 运行 `git status` 和 `git diff --staged` 了解待提交内容
2. 按逻辑分组，每组一个 commit
3. commit message 格式：`type(scope): description`
   - type: feat/fix/refactor/docs/test/chore
   - scope: 可选，模块名
   - description: 简洁英文，祈使句
4. 提交后输出摘要：几组改动，各改了什么

## 分组原则
- 同一功能的改动放一起
- 重构和功能实现分开
- 测试和被测代码可以同组
