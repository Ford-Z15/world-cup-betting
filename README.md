# 世界杯预测 · World Cup Betting Skill

基于**六专家圆桌辩论 + 概率模型 + EV 扫描**的世界杯投注策略分析工具，Claude Code skill。

## 安装

```bash
claude plugins install github.com/Ford-Z15/world-cup-betting
```

## 触发方式

- `/world-cup-betting` 或 `/世界杯下注`
- 对话中提及「世界杯投注」「世界杯怎么押」
- 给出对阵+赔率表时自动触发

## 方法论

| 组件 | 说明 |
|------|------|
| **六专家圆桌** | 纳特·西尔弗（贝叶斯）、纳西姆·塔勒布（尾部风险）、迈克尔·莫布森（技能vs运气）、菲利普·泰特洛克（超预测）、阿尔塞纳·温格（战术分析）、马修·贝纳姆（博彩市场）——并行独立分析+交叉辩论 |
| **概率合成** | 方向层→比分层→总进球层三级合成，标注 80% 置信区间 |
| **全品种 EV 扫描** | 对胜平负、让球盘、总进球、比分、半全场逐行计算期望值，扣除庄家抽水 |
| **四层过滤** | 多维度交叉验证 + CI 厚度检查 + 悲观校准测试 + 市场效率一致性 |
| **终审表决** | 五位专家两轮审计+投票（下注/不下注/半仓/试探仓） |

## 核心纪律

- 薄 edge 不下注
- CI 宽度超出 edge 时不下注  
- 悲观校准 EV 为负不下注
- 防守信号跨比赛强度环境折扣（S/A/B/C 级）

## 结构

```
world-cup-betting/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── world-cup-betting/
│       └── SKILL.md
├── CLAUDE.md
├── .gitignore
└── README.md
```

## 作者

Ford-Z15
