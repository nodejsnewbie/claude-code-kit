---
name: refactor
description: 重构代码，改善结构和可读性
tags: 重构, 代码质量, 清理
allowed-tools: Read, Edit, MultiEdit, Grep, Glob
---

# 代码重构

**核心原则：行为不变，结构更优。**

## 操作步骤

1. 分析目标代码，识别 code smell：
   - 过长函数（>50行）
   - 重复代码
   - 深层嵌套
   - 过多参数
   - 全局变量
2. 提出重构方案，说明每步改动
3. 逐步执行，每步确保测试通过
4. 对比重构前后

## 常用手法
- 提取函数（Extract Function）
- 内联函数（Inline Function）
- 重命名（Rename）
- 简化条件表达式
- 消除重复

## 注意事项
- 不改功能，只改结构
- 小步重构，每次改动一个点
- 重构前确保有测试覆盖
