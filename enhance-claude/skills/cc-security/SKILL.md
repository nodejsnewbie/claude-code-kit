---
name: cc-security
description: 安全审查，检查密钥泄露和常见漏洞
tags: 安全, 审计, 漏洞, 密钥
allowed-tools: Read, Grep, Glob
---

# 安全审查

**核心原则：不留后门，不泄露密钥。**

## 检查清单

1. **密钥泄露**：搜索硬编码的 API key、token、密码
   - `Grep "api_key" "token" "password" "secret"`
   - 检查 `.env` 是否被提交到 git
2. **依赖安全**：检查已知漏洞依赖
   - `pip audit` 或 `safety check`
3. **常见漏洞**：
   - SQL 注入：字符串拼接 SQL
   - 路径遍历：未过滤用户输入的文件路径
   - 命令注入：`os.system()` / `subprocess` 直接拼接用户输入
   - 不安全反序列化：`pickle.loads` 处理不可信数据
4. **权限检查**：文件权限是否过宽（如 777）

## 输出格式

```
Security Audit Report
=====================
[🔴] CRITICAL: 硬编码 AWS secret key in src/config.py:23
[🟡] WARNING: subprocess 使用 shell=True in src/utils.py:45
[🟢] INFO: 建议为 API endpoint 添加 rate limiting

Result: 1 critical, 1 warning, 1 info
```

## 注意事项
- Critical 问题必须立即修复
- 环境变量引用检查 `.env.example` 是否完整
