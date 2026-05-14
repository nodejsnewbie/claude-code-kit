# CLAUDE.md

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
