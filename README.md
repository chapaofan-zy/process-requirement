# Agent Skills Collection

一组用于 Claude Code 的 Agent Skills，帮助规范化软件开发流程。

## Skills 列表

| Skill | 说明 | 触发词示例 |
| ----- | ---- | --------- |
| [process-requirement](skills/process-requirement/) | 编码前引导结构化的需求分析与沟通 | "新需求"、"需求分析"、"帮我做个功能"、"new feature" |
| [create-skill](skills/create-skill/) | 引导规范地创建 Agent Skill | "创建 skill"、"写个 skill"、"new skill" |
| [setup-environment](skills/setup-environment/) | 引导开发环境的检测、分析与安装指导 | "安装环境"、"配置环境"、"setup environment" |

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

## setup-environment

引导用户完成开发环境的检测、分析与安装指导，推荐最佳安装方式，确保用户清楚每一步的影响。

**核心流程**：需求沟通 → 环境检测 → 安装方案 → 执行与验证

**功能特性**：

- 自动引导需求沟通，明确用户需要安装的环境类型和版本要求
- 检测当前系统已有环境，识别缺失或需更新的依赖
- 分析项目配置文件，自动识别依赖清单
- 为每个待安装项推荐最佳安装方式，并说明推荐理由和备选方案
- 详细说明每步操作的作用、预期结果和潜在风险
- 逐步引导安装，每步完成后即时验证结果

## 安装

```bash
# 安装所有 skills
npx skills add https://github.com/chapaofan-zy/process-requirement

# 安装指定 skill
npx skills add https://github.com/chapaofan-zy/process-requirement --skill process-requirement
npx skills add https://github.com/chapaofan-zy/process-requirement --skill create-skill
npx skills add https://github.com/chapaofan-zy/process-requirement --skill setup-environment

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

**setup-environment**：

- "安装环境" / "配置环境" / "搭建环境"
- "环境设置" / "装一下环境" / "初始化环境"
- "开发环境" / "装个依赖" / "环境有问题"
- "setup environment" / "install environment" / "dev setup"

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
    ├── create-skill/
    │   ├── README.md
    │   ├── SKILL.md
    │   └── references/
    │       ├── skill-spec.md
    │       └── skill-checklist.md
    └── setup-environment/
        ├── README.md
        ├── SKILL.md
        └── references/
            └── environment-checklist.md
```

## License

MIT
