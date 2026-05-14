# enhance-claude

Claude Code 技能包：分析项目并生成 CLAUDE.md，附带 9 个常用技能。

## 包含内容

**核心技能**
| Skill | 用途 |
|-------|------|
| `/enhance-claude` | 分析项目，生成/增强 CLAUDE.md |

**常用技能**
| Skill | 用途 |
|-------|------|
| `/cc-review` | 代码评审，按严重程度输出 checklist |
| `/cc-commit` | 提交代码，自动分组生成 commit message |
| `/cc-deploy` | 上线前检查，逐项验证 |
| `/cc-test` | 运行相关测试，分析失败原因 |
| `/cc-pr` | 生成 PR 描述 |
| `/cc-debug` | 调试排错，定位问题 |
| `/cc-refactor` | 代码重构建议 |
| `/cc-docs` | 更新文档和 docstring |
| `/cc-security` | 安全审查，检查密钥泄露 |

## 安装

对 Claude Code 说：

```
从 https://github.com/nodejsnewbie/claude-code-kit 安装技能
```

Claude 会自动把所有 SKILL.md 复制到 `~/.claude/skills/`。

## 使用

### 生成 CLAUDE.md

在任意项目中说：

- "加强 CLAUDE.md"
- "初始化 CLAUDE.md"
- "为这个项目生成 CLAUDE.md"

Claude 会分析项目结构，生成包含以下内容的 CLAUDE.md：

- Andrej Karpathy's Coding Skills
- 项目概述
- 技术栈
- 目录结构
- 常用命令
- 开发流程
- 代码规范
- 常用操作（引用其他技能）

### 使用其他技能

- "cc-review 一下代码"
- "cc-commit 提交代码"
- "cc-deploy 检查部署"
- "cc-debug 这个报错"

## 目录结构

```
enhance-claude/
├── skills/
│   ├── enhance-claude/SKILL.md
│   ├── cc-review/SKILL.md
│   ├── cc-commit/SKILL.md
│   ├── cc-deploy/SKILL.md
│   ├── cc-test/SKILL.md
│   ├── cc-pr/SKILL.md
│   ├── cc-debug/SKILL.md
│   ├── cc-refactor/SKILL.md
│   ├── cc-docs/SKILL.md
│   └── cc-security/SKILL.md
├── settings.json
└── README.md
```

## 自定义

- 修改 `skills/` 下的 SKILL.md 调整流程
- 修改 `settings.json` 调整权限
