# dbs-agent-mesh 测试用例

## TC01: 完整流水线 A — 商业模式诊断
**输入**: "我的产品卖不动，从头到尾分析"
**预期管线**: dbs-diagnosis→deconstruct→goal→benchmark→decision→action→save
**通过条件**: 7 个 Phase 依次执行，每 Phase 的输入来自上一 Phase 的输出

## TC02: 完整流水线 B — 内容生产
**输入**: "帮我做一次完整的内容策略诊断"
**预期管线**: dbs-content→content-system→dbs-benchmark→dbs-hook→save
**通过条件**: Phase 间输出→输入传递不中断

## TC03: 中途断线恢复
**输入**: 管线执行到 Phase 4 时模拟"会话中断"
**预期**: 下次 dbs-restore 从 Phase 4 继续，不重头开始
**通过条件**: dbs-save 保存了中间状态

## TC04: 跳 Phase 检测
**输入**: 管线有 7 Phase，但实际只执行了 3 个
**预期**: 识别为不完整管线，标注缺失 Phase
**通过条件**: 不完整 ≠ 完成，需要继续或显式终止

## TC05: 与 dbs-orchestrator 边界
**输入**: "我该用哪个 dbs skill"
**预期**: 不触发 agent-mesh，转给 orchestrator
**通过条件**: 单 skill 路由 ≠ 多 skill 管线
