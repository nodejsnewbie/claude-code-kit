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

## Andrej Karpathy's Coding Skills

Behavioral guidelines to reduce common LLM coding mistakes.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

### 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

---

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

- 代码评审 → `.claude/skills/cc-review/SKILL.md`
- 提交代码 → `.claude/skills/cc-commit/SKILL.md`
- 部署检查 → `.claude/skills/cc-deploy/SKILL.md`
- 运行测试 → `.claude/skills/cc-test/SKILL.md`
- 生成 PR → `.claude/skills/cc-pr/SKILL.md`
- 调试排错 → `.claude/skills/cc-debug/SKILL.md`
- 代码重构 → `.claude/skills/cc-refactor/SKILL.md`
- 文档维护 → `.claude/skills/cc-docs/SKILL.md`
- 安全审查 → `.claude/skills/cc-security/SKILL.md`
```

## 输出示例

完成时输出：

```
CLAUDE.md 已生成/更新

包含内容：
- Andrej Karpathy's Coding Skills
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
