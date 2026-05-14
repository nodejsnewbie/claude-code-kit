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
claude-code-kit - Claude Code 技能包，提供 enhance-claude 核心技能和 9 个常用技能。

## 技术栈
- 类型: Claude Code 技能定义
- 格式: Markdown (SKILL.md)
- 配置: JSON (settings.json)

## 目录结构
```
enhance-claude/
├── SKILL.md          - 核心技能：分析项目并生成 CLAUDE.md
├── settings.json     - 权限配置
└── skills/           - 9 个常用技能
    ├── commit/
    ├── debug/
    ├── deploy-check/
    ├── docs/
    ├── pr/
    ├── refactor/
    ├── review/
    ├── security/
    └── test/
```

## 常用命令
```bash
# 安装技能（用户执行）
git clone https://github.com/nodejsnewbie/claude-code-kit.git
# 然后对 Claude 说："从 https://github.com/nodejsnewbie/claude-code-kit 安装技能"

# 推送更新
git add . && git commit -m "..." && git push
```

## 开发流程
1. 编辑/新增 SKILL.md
2. 本地测试技能效果
3. 提交: git commit
4. 推送: git push

## 技能编写规范
- 每个技能一个目录，包含 SKILL.md
- SKILL.md 使用 frontmatter 定义元信息
- 明确列出 allowed-tools
- 提供清晰的操作步骤

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
