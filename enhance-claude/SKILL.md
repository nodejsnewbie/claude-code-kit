---
name: enhance-claude
description: 分析项目并生成/增强 CLAUDE.md，提供项目上下文和开发指引
tags: 配置, 初始化, 文档, 项目设置
allowed-tools: Read, Glob, Grep, LS, Write, Edit, Bash(git *)
---

# 增强 CLAUDE.md

**核心原则：根据项目特点，生成实用的上下文文件。**

## 何时使用

- 新项目初始化
- 现有项目缺少 CLAUDE.md
- 项目结构变更后更新 CLAUDE.md

## 操作步骤

### 1. 分析项目结构

```bash
# 检测语言和框架
ls -la
cat package.json / requirements.txt / go.mod / Cargo.toml / pom.xml 2>/dev/null

# 查看目录结构
find . -type f -name "*.ts" -o -name "*.py" -o -name "*.go" -o -name "*.rs" | head -20
ls -la src/ lib/ app/ 2>/dev/null

# 检查现有配置
cat .gitignore
cat Makefile / Taskfile.yml 2>/dev/null
ls -la .github/workflows/ 2>/dev/null
```

### 2. 检查现有 CLAUDE.md

```bash
cat CLAUDE.md 2>/dev/null
```

如果已存在，识别缺失部分并补充。如果不存在，生成完整文件。

### 3. 生成 CLAUDE.md

根据分析结果，生成包含以下内容的 CLAUDE.md：

```markdown
# CLAUDE.md

## 项目概述
[项目名称] - [简短描述]

## 技术栈
- 语言: [主语言]
- 框架: [框架名称]
- 包管理: [npm/pip/cargo/...]
- 测试: [测试框架]

## 目录结构
```
src/          - 源代码
tests/        - 测试
docs/         - 文档
```

## 常用命令
```bash
# 开发
npm run dev

# 测试
npm test

# 构建
npm run build

# 代码检查
npm run lint
```

## 开发流程
1. 创建分支: git checkout -b feature/xxx
2. 开发并测试
3. 提交: git commit
4. 推送并创建 PR

## 代码规范
- [根据项目特点列出]

## 常用操作
执行以下操作时，先读对应的 SKILL.md 再按流程操作：

- 代码评审 → `.claude/skills/review/SKILL.md`
- 提交代码 → `.claude/skills/commit/SKILL.md`
- 部署检查 → `.claude/skills/deploy-check/SKILL.md`
- 运行测试 → `.claude/skills/test/SKILL.md`
- 生成 PR → `.claude/skills/pr/SKILL.md`
- 调试排错 → `.claude/skills/debug/SKILL.md`
- 代码重构 → `.claude/skills/refactor/SKILL.md`
- 文档维护 → `.claude/skills/docs/SKILL.md`
- 安全审查 → `.claude/skills/security/SKILL.md`
```

## 输出示例

完成时输出：

```
CLAUDE.md 已生成/更新

包含内容：
- 项目概述
- 技术栈
- 目录结构
- 常用命令 (x 条)
- 开发流程
- 代码规范
- 常用操作（9 个技能）
```

## 注意事项

- 只包含实际存在的内容，不要猜测
- 常用命令从 package.json scripts / Makefile 中提取
- 如果项目已有 CLAUDE.md，合并而非覆盖
- 确保引用的 skills 路径正确
