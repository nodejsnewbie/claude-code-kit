---
name: cc-deploy
description: 上线前全面检查，确保项目可部署
tags: 部署, 检查, CI/CD, 质量
allowed-tools: Read, Grep, Glob, Bash(git *), Bash(pytest *), Bash(ruff *), Bash(mypy *)
---

# 上线前检查

**核心原则：全绿才敢上线。**

## 检查清单（按顺序）

1. **类型检查**：`mypy src/` → ✅ 或 ❌
2. **测试**：`pytest` → ✅ 或 ❌
3. **Lint**：`ruff check src/` → ✅ 或 ❌
4. **未提交改动**：`git status --porcelain` → ✅ 干净 或 ❌ 有未提交文件
5. **console.log / print 调试语句**：搜索 `print(` `logging.debug` `breakpoint()` → ✅ 或 ❌
6. **.env 引用**：搜索硬编码密钥/token → ✅ 或 ❌

## 输出格式

```
Deploy Check Results
====================
[✅] 类型检查: passed
[✅] 测试: 47 passed
[❌] Lint: 3 issues found
[✅] 未提交改动: clean
[✅] 调试语句: none found
[✅] 敏感信息: none found

Result: BLOCKED (1 failure)
```

## 注意事项
- 任何一步失败立即停止并报告
- 修复失败项后重新跑完整流程
