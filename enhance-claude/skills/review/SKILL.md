---
name: review
description: 适用于完成任务、实现主要功能或合并代码前，验证工作是否符合要求
tags: 代码评审, Git工作流, 代码验证, 开发流程
allowed-tools: Read, Grep, Glob, Bash(git *)
---

# 发起代码评审

**核心原则：尽早评审，经常评审。**

## 何时发起
- 完成任务或主要功能后（强制）
- 合并到 main 前（强制）
- 遇到瓶颈需要新视角时（可选）

## 操作步骤

1. 获取变更范围：`git diff --stat` 了解改了哪些文件
2. 按严重程度审查：
   - CRITICAL：逻辑错误、空指针、竞态条件、安全漏洞
   - WARNING：N+1 查询、缺少错误处理、性能隐患
   - INFO：命名、垃圾代码、TODO
3. 输出 checklist，按严重程度分组
4. 结尾总结："X critical, Y warnings, Z info"

## 注意事项
- 不因"代码很简单"跳过评审
- 严重问题立即修复后再继续
- 次要问题记录留待后续
