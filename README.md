# Agent Skills Collection

一组用于 Claude Code 的 Agent Skills，帮助规范化软件开发流程。

## Skills 列表

| Skill | 说明 | 触发词示例 |
| ----- | ---- | --------- |
| [process-requirement](skills/process-requirement/) | 编码前引导结构化的需求分析与沟通 | "新需求"、"需求分析"、"帮我做个功能"、"new feature" |
| [create-skill](skills/create-skill/) | 引导规范地创建 Agent Skill | "创建 skill"、"写个 skill"、"new skill" |

## process-requirement

在编码前引导结构化的需求分析与沟通，确保充分理解需求后再动手开发。

**核心流程**：需求沟通 → 影响分析 → 文件变更计划 → 实现

**功能特性**：

- 自动引导需求沟通，提出澄清问题，反复迭代直到用户满意
- 扫描代码库，生成文件变更计划（新增 / 修改 / 删除）
- 每个阶段都需要用户明确确认才能继续
- 内置按领域分类的提问模板（前端、后端、数据库、集成、缺陷修复、重构）
- 实现过程中发现计划外变更会主动停下来征求用户意见

## create-skill

引导用户规范地创建 Agent Skill，确保产出的 skill 结构完整、质量合格。

**核心流程**：Skill 定位与设计 → SKILL.md 编写 → 参考文件编写 → 生成文件

**功能特性**：

- 引导明确 skill 定位：目标用户、核心问题、与已有 skill 的关系
- 设计触发机制：中英文触发词、避免误触发
- 按规范生成 SKILL.md：frontmatter、工作流程、规则
- 内置 Skill 结构规范和质量检查清单
- 每个阶段都需要用户确认才能继续

## 安装

```bash
# 安装所有 skills
npx skills add https://github.com/chapaofan-zy/process-requirement

# 安装指定 skill
npx skills add https://github.com/chapaofan-zy/process-requirement --skill process-requirement
npx skills add https://github.com/chapaofan-zy/process-requirement --skill create-skill

# 全局安装
npx skills add https://github.com/chapaofan-zy/process-requirement -g
```

## 使用方式

安装后，对 Agent 说出对应的触发词即可自动激活相应 skill：

**process-requirement**：

- "新需求" / "需求分析" / "帮我做个功能"
- "开发功能" / "实现功能" / "开始开发"
- "帮我写" / "加个功能" / "改一下"

**create-skill**：

- "创建 skill" / "新建 skill" / "写个 skill"
- "create skill" / "new skill" / "add skill"
- "写个技能" / "加个技能"

## 项目结构

```text
├── README.md
├── LICENSE
└── skills/
    ├── process-requirement/
    │   ├── README.md
    │   ├── SKILL.md
    │   └── references/
    │       └── question-templates.md
    └── create-skill/
        ├── README.md
        ├── SKILL.md
        └── references/
            ├── skill-spec.md
            └── skill-checklist.md
```

## License

MIT
