---
permalink: /
---
<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>入门强化学习</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <div class="app">
    <aside class="sidebar card">
      <div class="brand">
        <div class="logo">RL</div>
        <div>
          <h1>强化学习入门笔记</h1>
          <p>当前只保留 Part 1 学习笔记。</p>
        </div>
      </div>
      <div class="note-list">
        <button class="note-card">
          <h3>Part 1：Key Concepts in RL 学习笔记</h3>
          <div class="meta"><span>Part 1 Key Concepts</span><span>·</span><span>基本掌握</span></div>
          <div class="meta"><span class="pill">RL</span><span class="pill">MDP</span><span class="pill">Policy</span><span class="pill">Value</span><span class="pill">Bellman</span></div>
        </button>
      </div>
    </aside>

    <main class="main card">
      <header class="hero">
        <div>
          <h2>入门强化学习</h2>
          <p>先把 Agent、Environment、Policy、Reward、Return、Value Function、Bellman 和 MDP 这条主线学清楚。</p>
        </div>
      </header>

      <article class="preview single-note">
        <h1>Part 1：Key Concepts in RL 学习笔记</h1>
        <p><span class="pill">Part 1 Key Concepts</span> <span class="pill">基本掌握</span> <span class="pill">RL</span> <span class="pill">MDP</span> <span class="pill">Policy</span> <span class="pill">Value</span> <span class="pill">Bellman</span></p>

        <h2>1. 强化学习的一句话理解</h2>
        <p><strong>强化学习 = 智能体通过试错学习决策策略。</strong></p>
        <p>它关注的不是“给定输入直接预测答案”，而是：智能体在环境中不断尝试动作，根据奖励反馈逐步学会更好的决策方式。</p>

        <h2>2. 强化学习的基本闭环</h2>
        <p>强化学习可以理解成一个不断循环的过程：</p>
        <ul>
          <li><strong>Agent</strong> 观察当前的 <strong>observation / state</strong>。</li>
          <li>Agent 根据当前 <strong>policy</strong> 选择一个 <strong>action</strong>。</li>
          <li><strong>Environment</strong> 接收动作后发生变化。</li>
          <li>Environment 返回 <strong>reward</strong> 和 <strong>next observation</strong>。</li>
          <li>Agent 根据反馈更新自己的 <strong>policy</strong>。</li>
          <li>最终目标是最大化长期累计奖励，也就是 <strong>return</strong>。</li>
        </ul>
        <blockquote>Agent 观察环境 → 做动作 → 环境反馈奖励和新状态 → Agent 调整策略 → 尽可能获得更高的长期回报。</blockquote>

        <h2>3. 核心概念整理</h2>
        <table>
          <tr><th>概念</th><th>我的理解</th></tr>
          <tr><td><strong>State</strong></td><td>环境的真实完整状态，包含决策所需的全部信息。</td></tr>
          <tr><td><strong>Observation</strong></td><td>智能体实际看到的信息，可能只是 State 的一部分。</td></tr>
          <tr><td><strong>Action</strong></td><td>智能体能够采取的具体动作。</td></tr>
          <tr><td><strong>Action Space</strong></td><td>所有合法动作组成的集合。</td></tr>
          <tr><td><strong>Policy</strong></td><td>从状态到动作的规则，相当于控制系统里的“控制律”。</td></tr>
          <tr><td><strong>Trajectory</strong></td><td>一整段状态—动作—奖励序列，可以理解为一次完整经历。</td></tr>
          <tr><td><strong>Reward</strong></td><td>当前一步动作带来的即时奖励。</td></tr>
          <tr><td><strong>Return</strong></td><td>从当前开始往后累计得到的总奖励。</td></tr>
        </table>

        <h2>4. 价值函数相关概念</h2>
        <table>
          <tr><th>概念</th><th>我的理解</th></tr>
          <tr><td><strong>V(s)</strong></td><td>状态 s 有多好：从这个状态出发，未来大概能拿到多少回报。</td></tr>
          <tr><td><strong>Q(s, a)</strong></td><td>在状态 s 下做动作 a 有多好。</td></tr>
          <tr><td><strong>Q*(s, a)</strong></td><td>最优情况下，在状态 s 下做动作 a 有多好。</td></tr>
          <tr><td><strong>最优动作</strong></td><td>选择让 Q*(s, a) 最大的动作。</td></tr>
          <tr><td><strong>Bellman 方程</strong></td><td>当前价值 = 当前奖励 + 折扣后的未来价值。</td></tr>
          <tr><td><strong>Advantage</strong></td><td>某个动作比该状态下的平均动作好多少。</td></tr>
        </table>

        <h2>5. Bellman 思想的直观理解</h2>
        <p>Bellman 的核心不是复杂公式，而是一种“拆问题”的思想：</p>
        <blockquote>一个状态现在有多好，取决于当前这一步能拿多少奖励，以及走到下一个状态后未来还能有多好。</blockquote>
        <p>也就是：<strong>当前价值 = 当前奖励 + 未来价值</strong>。</p>
        <p>其中未来价值通常会乘上折扣因子 <strong>γ</strong>，表示越远的奖励影响越小。</p>

        <h2>6. MDP：强化学习环境的数学描述</h2>
        <p>MDP 可以用下面几个部分描述强化学习环境：</p>
        <table>
          <tr><th>符号</th><th>含义</th></tr>
          <tr><td><strong>S</strong></td><td>状态集合</td></tr>
          <tr><td><strong>A</strong></td><td>动作集合</td></tr>
          <tr><td><strong>R</strong></td><td>奖励函数</td></tr>
          <tr><td><strong>P</strong></td><td>状态转移概率</td></tr>
          <tr><td><strong>ρ₀</strong></td><td>初始状态分布</td></tr>
        </table>
        <blockquote>下一状态只和当前状态、当前动作有关，而不需要依赖更早之前的完整历史。</blockquote>
        <p>这就是所谓的<strong>马尔可夫性</strong>。</p>

        <h2>7. 我目前的阶段性理解</h2>
        <ul>
          <li>强化学习的目标是最大化长期累计奖励。</li>
          <li>Policy 决定 Agent 如何选择动作。</li>
          <li>Value / Q-value 用来评价状态或动作的好坏。</li>
          <li>Bellman 方程把“长期价值”拆成“当前奖励 + 未来价值”。</li>
          <li>MDP 是描述强化学习问题的标准数学框架。</li>
        </ul>

        <h2>8. 后续需要继续搞懂的问题</h2>
        <ul>
          <li>State 和 Observation 在实际机器人任务中怎么区分？</li>
          <li>Policy 和传统控制里的控制律有哪些相似和不同？</li>
          <li>V(s)、Q(s,a)、Advantage 在不同算法里分别怎么用？</li>
          <li>Bellman 方程为什么能支撑价值迭代和 Q-learning？</li>
          <li>MDP 假设在真实复杂环境中是否总是成立？</li>
        </ul>
      </article>
    </main>
  </div>
</body>
</html>
