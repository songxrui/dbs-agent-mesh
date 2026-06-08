# EXAMPLE_02: 反面案例 — 管线断裂：Phase 间无数据传递

## 反例
```
声称: "用 dbs-agent-mesh 跑了商业模式诊断全流程"
实际操作: 
  Phase 1 → dbs-diagnosis
  Phase 2 → dbs-benchmark (跳过了 deconstruct 和 goal)
  Phase 3 → dbs-save
```

## 为什么是反例
1. **跳过 Phase**: 缺少 deconstruct 和 goal → 管线不完整
2. **无数据传递**: diagnosis 的输出没有传给 benchmark → 每个 phase 是独立诊断而非串联
3. **顺序错误**: benchmark 在 decision 之前但 goal 被跳过 → 用户不知道"对标是为了什么"
4. **存档过早**: 只跑了 3 个 phase 就存档 → 结论不完整

## 正确做法
- 严格按流水线定义执行，不允许跳过 Phase
- 每个 Phase 必须接收上一 Phase 的输出作为输入
- 存档必须在完整流水线结束后
- 如果用户中途终止 → 存档当前进度并标注"未完成"

## skill-overseer 检测方式
- 检查 TOOL_LEDGER: Phase 调用序列是否完整
- 检查 Phase 间是否有输出→输入传递记录
- 检查存档是否在完整流水线后
