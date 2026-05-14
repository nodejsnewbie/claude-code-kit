---
name: cc-test
description: 运行相关测试，分析失败原因
tags: 测试, 质量, pytest
allowed-tools: Read, Grep, Glob, Bash(pytest *), Bash(python *)
---

# 运行测试

**核心原则：测试先行，失败即修。**

## 操作步骤

1. 识别变更文件：`git diff --name-only`
2. 找到对应测试文件（`test_*.py`、`*_test.py`）
3. 运行相关测试：`pytest <相关测试文件> -v`
4. 如果失败：分析报错，定位原因，修复后重跑

## 输出格式
- 通过：列出通过的测试数量和耗时
- 失败：列出失败的测试、断言信息、可能原因

## 扩展
- 无对应测试时，建议新增测试
- 覆盖率不够时，提示补充
