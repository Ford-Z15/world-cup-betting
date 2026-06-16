# 世界杯预测

## 项目约定

- 思考过程用中文展示
- 投注策略使用 `/world-cup-betting` skill，严格遵循其十一→步流程
- 赛后追踪写入 `betting-tracker.md`
- 每轮更新 Brier Score 累计
- 关键经验教训写入 `lessons.md`

## 文件结构

- `betting-tracker.md` — 每轮投注记录和赛果对照
- `lessons.md` — 跨轮次可迁移的经验教训
- 对话中的临场分析以 Claude 判官总结为准

## 项目目标

| 指标 | 值 |
|------|-----|
| 启动资金 | 2,000 元 |
| 目标收入 | 20,000 元 |
| 目标倍数 | 10× |
| 时间窗口 | 世界杯全程（6.11 – 7.19，约 5 周） |
| 剩余比赛 | ~92 场（104 场总计 − 已赛约 12 场） |

### 路径估算

- 当前进度：200 元投入 → +156 元（+78%），三轮
- 所需：9 轮平均 +30% EV 的复利 → 2,000 × 1.3^9 ≈ 21,200
- 单轮仓位：100-300 元（5-15% 资金），高信心轮次可到 20%
- 核心约束：**不因目标激进降 edge 门槛**。宁可错过目标，不押薄 edge

## GitHub 同步

- 仓库地址：`github.com/Ford-Z15/world-cup-betting`
- Skill 有两个副本：
  - **全局**：`~/.claude/skills/world-cup-betting/SKILL.md`（日常使用，Claude Code 实时加载）
  - **项目**：`skills/world-cup-betting/SKILL.md`（GitHub 版本，供他人安装）
- **发布流程**：修改全局 skill → 验证可用 → 复制到项目 → `git push`

```bash
# 发布新版本
cp ~/.claude/skills/world-cup-betting/SKILL.md skills/world-cup-betting/SKILL.md
git add -A && git commit -m "简述改了什么" && git push
```

## 验证

- 每轮赛后 24 小时内更新 tracker
- Brier Score 累计 < 0.20 为合格线
- 每周对比实际 vs 目标路径，偏差 > 30% 时复盘调整
