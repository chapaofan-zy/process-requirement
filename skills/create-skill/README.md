# create-skill

引导用户规范地创建 Agent Skill，确保产出的 skill 结构完整、描述清晰、触发词准确、工作流程合理。

## 功能特性

- 引导明确 skill 定位：目标用户、核心问题、与已有 skill 的关系
- 设计触发机制：中英文触发词、避免误触发
- 按规范生成 SKILL.md：frontmatter、工作流程、规则
- 自动生成参考文件（如需要）
- 自动更新项目根目录 README.md
- 内置 Skill 结构规范和质量检查清单
- 每个阶段都需要用户确认才能继续

## 执行流程

### 第一阶段：Skill 定位与设计

1. 明确 skill 定位（目标用户、核心问题、与现有 skill 的关系）
2. 设计触发机制（中英文触发词、避免误触发）
3. 定义工作流程（阶段划分、确认节点、参考文件需求）

### 第二阶段：SKILL.md 编写

1. 编写 frontmatter（name、description、metadata）
2. 编写正文（概述、工作流程、规则）
3. 展示完整内容给用户审阅

### 第三阶段：参考文件编写（如需要）

1. 确定参考文件清单
2. 逐一编写，结构化、易解析
3. 展示给用户确认

### 第四阶段：生成文件与更新项目

1. 创建 skill 目录和文件
2. 生成 skill 独立的 README.md
3. 更新项目根目录 README.md（Skills 列表、功能介绍、安装命令、使用方式、项目结构）
4. 验证文件结构和内容完整性

## 安装

```bash
npx skills add https://github.com/chapaofan-zy/process-requirement --skill create-skill
```

## 使用方式

安装后，对 Agent 说以下类似的话即可自动激活：

- "创建 skill" / "新建 skill" / "写个 skill"
- "create skill" / "new skill" / "add skill"
- "写个技能" / "加个技能"

## 文件结构

```text
skills/create-skill/
├── README.md
├── SKILL.md
└── references/
    ├── skill-spec.md
    └── skill-checklist.md
```
