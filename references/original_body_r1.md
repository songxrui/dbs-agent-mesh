---
name: dbs-agent-mesh
description: "DBSkill多skill管线编排引擎。不只是一个路由——创建多skill顺序执行计划，前一个skill的输出作为后一个的输入，形成完整的诊断-分析-决策-执行流水线。触发词：/dbs-agent-mesh、深度诊断、全流程、从头到尾、完整分析、串联诊断。不适用：单skill可解决→dbs-orchestrator; 快速路由→dbs-orchestrator。正例：'帮我从头到尾分析这个商业模式'→触发; '/dbs-agent-mesh 我的知识付费项目'→触发。反例：'我该用哪个skill'→不触发→dbs-orchestrator; '帮我诊断一下'→不触发→dbs-diagnosis。"
version: "1.0.0 | R1: 2026-06-08 | incubated from: 15 dbs skills deep pattern synthesis | model: DeepSeek v4 Pro"
---

# dbs-agent-mesh R1 — 多 Skill 管线编排引擎

> 孵化来源: 深度结合 15 个 dbs skill + dbs-orchestrator + content-alchemist 的工作流模式，抽象出多 skill 管线编排。

## 一句话定义

不只是路由到单个 skill——创建多 skill 顺序执行计划，前一个 skill 的输出作为后一个的输入，形成完整的「诊断→分析→拆解→决策→执行→复盘」闭环。

## 4 条核心流水线

### 流水线 A: 商业模式深度诊断
```
dbs-diagnosis (消解问题)
  → dbs-deconstruct (拆关键概念)
    → dbs-goal (审计目标)
      → dbs-benchmark (找对标)
        → dbs-decision (做选择)
          → dbs-action (执行)
            → dbs-save (存档)
```

### 流水线 B: 内容生产全流程
```
dbs-content (诊断内容方向)
  → dbs-content-system (结构化素材)
    → dbs-deconstruct (拆核心概念)
      → dbs-hook (优化开头)
        → dbs-xhs-title (多平台标题)
          → dbs-ai-check (去AI味)
            → dbs-report (汇总)
```

### 流水线 C: 学习到行动
```
dbs-learning (学习路径)
  → dbs-deconstruct (拆关键概念)
    → dbs-benchmark (找案例)
      → dbs-good-question (形成问题)
        → dbs-slowisfast (慢方法判断)
          → dbs-action (执行)
```

### 流水线 D: 项目迁移 + 结构化
```
dbs-agent-migration (审计迁移)
  → dbs-content-system (内容结构化)
    → dbs-report (迁移报告)
      → dbs-save (保存)
```

## 执行协议

### Step 1: 接收需求
用户描述想完成的事（不限术语，自然语言即可）

### Step 2: 匹配流水线
从 4 条预设流水线中选择最匹配的，或创建自定义流水线

### Step 3: 制定执行计划
```
执行计划:
  Step 1: /dbs-{skill1} → 预期产出: {X}
  Step 2: /dbs-{skill2} (以上一步{X}为输入) → 预期产出: {Y}
  Step 3: ...
  预计耗时: {N} 步 × {M} 分钟/步 ≈ {总时间}
```

### Step 4: 逐步执行
- 每步执行完停下来展示结果
- 用户确认后进入下一步
- 如果某步产出不满足预期 → 回到该步重做，不进下一步

### Step 5: 汇总报告
所有步骤执行完后，自动调用 dbs-report 生成汇总报告

## 与其他 skill 联动

```
dbs-agent-mesh (管线编排)
    │
    ├──→ dbs-orchestrator (单skill路由)
    ├──→ dbs-report (汇总)
    ├──→ dbs-save (存档)
    └──→ workflow-architect (持久化自定义管线)
```

## 验证清单

- [ ] 流水线匹配正确（4预设或自定义）
- [ ] 每步产出被下一步引用
- [ ] 用户每步确认
- [ ] 汇总报告已生成
- [ ] 全程 ≤1 次返工

## G1-G6

| 门禁 | 状态 |
|------|------|
| G1 ≤10KB | ✅ |
| G2 触发层 | ✅ |
| G3 可执行(4管线+5Step) | ✅ |
| G4 验证 | ✅ |
| G5 失败兜底(返工机制) | ✅ |
| G6 安全 | ✅ |
