# Part 1：Key Concepts in RL 学习笔记

## 强化学习的一句话理解

**强化学习 = 智能体通过试错学习决策策略。**

## 基本闭环

- Agent 观察 observation / state。
- 根据 policy 选择 action。
- Environment 发生变化。
- 返回 reward 和 next observation。
- Agent 更新 policy。
- 目标是最大化 return。

## 核心概念

| 概念 | 含义 |
| --- | --- |
| State | 真实完整状态 |
| Observation | 智能体实际看到的信息 |
| Action | 智能体能采取的动作 |
| Action Space | 所有合法动作的集合 |
| Policy | 状态到动作的规则，相当于控制律 |
| Trajectory | 一整段状态-动作序列 |
| Reward | 一步奖励 |
| Return | 累计奖励 |

## 价值相关

| 概念 | 含义 |
| --- | --- |
| V(s) | 状态 s 有多好 |
| Q(s,a) | 状态 s 下做动作 a 有多好 |
| Q*(s,a) | 最优情况下动作 a 有多好 |
| 最优动作 | 选择 Q* 最大的动作 |
| Bellman | 当前价值 = 当前奖励 + 折扣后的未来价值 |
| Advantage | 某动作比平均动作好多少 |

## MDP

用 S, A, R, P, ρ0 描述强化学习环境。

核心思想：下一状态只和当前状态、当前动作有关。