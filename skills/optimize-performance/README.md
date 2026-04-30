# optimize-performance

利用 Chrome DevTools MCP 对页面加载性能进行分析，给出优化建议并在用户确认后自动修改代码，最后验证优化效果。

## 功能特性

- 自动检测 Chrome DevTools MCP 是否可用，未配置时提供静态分析建议并引导安装
- 使用 Lighthouse 审计和 Performance Trace 收集 Core Web Vitals 关键指标
- 以结构化报告展示性能分析结果，包含 LCP、FCP、CLS、INP、TTFB、SI 等指标
- 按优先级给出可落地的优化建议，说明每项优化预期提升的指标
- 用户确认后自动修改代码，完成性能优化
- 优化后再次测量性能，给出优化前后的指标对比和提升幅度报告

## 使用方式

对 Agent 说以下类似的话即可自动激活：

- "优化性能" / "页面性能" / "性能分析"
- "性能优化" / "页面加载优化" / "分析性能" / "提升性能"
- "optimize performance" / "performance analysis" / "improve performance"

## 安装

```bash
npx skills add https://github.com/chapaofan-zy/process-requirement --skill optimize-performance
```

## 执行流程

### 第一阶段：环境检测

1. 检测用户是否已配置 Chrome DevTools MCP
2. 已配置：询问目标页面 URL，进入下一阶段
3. 未配置：基于代码进行静态分析，给出初步建议，并引导安装 MCP

### 第二阶段：性能分析与展示

1. 使用 Lighthouse 审计收集性能评分
2. 使用 Performance Trace 记录页面加载过程
3. 收集 Core Web Vitals 关键指标（LCP、FCP、CLS、INP、TTFB、SI）
4. 以结构化报告展示分析结果

### 第三阶段：优化建议

1. 基于分析结果识别可优化项
2. 按对 Core Web Vitals 的影响程度排序
3. 列出每项优化的具体措施、涉及文件和预期提升指标
4. 等待用户确认要执行的优化项

### 第四阶段：代码修改

1. 按优先级逐项执行优化
2. 每项完成后说明修改内容
3. 确保修改不破坏现有功能

### 第五阶段：效果验证

1. 重新测量性能指标
2. 与优化前数据对比
3. 输出各项指标的提升幅度报告

## 文件结构

```text
skills/optimize-performance/
├── README.md
├── SKILL.md
└── references/
    └── performance-checklist.md
```
