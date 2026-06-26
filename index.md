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
          <p>当前包含 Part 1 和 Part 2 学习笔记。</p>
        </div>
      </div>
      <div class="note-list">
        <a class="note-card" href="#part1">
          <h3>Part 1：Key Concepts in RL 学习笔记</h3>
          <div class="meta"><span>Part 1 Key Concepts</span><span>·</span><span>基本掌握</span></div>
          <div class="meta"><span class="pill">RL</span><span class="pill">MDP</span><span class="pill">Policy</span><span class="pill">Value</span><span class="pill">Bellman</span></div>
        </a>
        <a class="note-card" href="#part2">
          <h3>Part 2：Kinds of RL Algorithms 学习笔记</h3>
          <div class="meta"><span>Part 2 Algorithms</span><span>·</span><span>初步理解</span></div>
          <div class="meta"><span class="pill">Model-Free</span><span class="pill">PPO</span><span class="pill">DQN</span><span class="pill">SAC</span><span class="pill">TD3</span></div>
        </a>
      </div>
    </aside>

    <main class="main card">
      <header class="hero">
        <div>
          <h2>入门强化学习</h2>
          <p>先把核心概念和算法分类学清楚：Part 1 建立强化学习语言体系，Part 2 理解不同算法路线。</p>
        </div>
      </header>

      <article id="part1" class="preview single-note">
        <h1>Part 1：Key Concepts in RL 学习笔记</h1>
        <p><span class="pill">Part 1 Key Concepts</span> <span class="pill">基本掌握</span> <span class="pill">RL</span> <span class="pill">MDP</span> <span class="pill">Policy</span> <span class="pill">Value</span> <span class="pill">Bellman</span></p>

        <h2>1. 强化学习的一句话理解</h2>
        <p><strong>强化学习 = 智能体通过试错学习决策策略。</strong></p>
        <p>它关注的不是“给定输入直接预测答案”，而是：智能体在环境中不断尝试动作，根据奖励反馈逐步学会更好的决策方式。</p>

        <h2>2. 强化学习的基本闭环</h2>
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

        <h2>5. MDP</h2>
        <p>MDP 可以用 <strong>S, A, R, P, ρ₀</strong> 描述强化学习环境。</p>
        <blockquote>下一状态只和当前状态、当前动作有关，而不需要依赖更早之前的完整历史。</blockquote>
        <p>这就是所谓的<strong>马尔可夫性</strong>。</p>
      </article>

      <article id="part2" class="preview single-note">
        <h1>Part 2：Kinds of RL Algorithms 学习笔记</h1>
        <p><span class="pill">Part 2 Algorithms</span> <span class="pill">初步理解</span> <span class="pill">Model-Free</span> <span class="pill">Model-Based</span> <span class="pill">PPO</span> <span class="pill">DQN</span> <span class="pill">SAC</span></p>

        <h2>1. 强化学习算法分类主要看三个问题</h2>
        <p>理解强化学习算法分类时，不要一上来死记算法名字，而是先看三个问题：</p>
        <ul>
          <li>有没有环境模型？</li>
          <li>Model-Free 里到底学什么？</li>
          <li>数据怎么用？</li>
        </ul>

        <h2>2. 有没有环境模型？</h2>
        <table>
          <tr><th>类别</th><th>核心思想</th></tr>
          <tr><td><strong>Model-Free</strong></td><td>不显式建模环境，直接通过交互学习策略或价值函数。</td></tr>
          <tr><td><strong>Model-Based</strong></td><td>使用或学习环境模型，然后基于模型进行规划，或者用模型辅助学习。</td></tr>
        </table>
        <p>直观理解：Model-Free 更像是“直接练”；Model-Based 更像是“先学会环境怎么变化，再利用模型预测和规划”。</p>

        <h2>3. Model-Free 里到底学什么？</h2>
        <table>
          <tr><th>路线</th><th>学什么</th><th>代表算法</th></tr>
          <tr><td><strong>Policy Optimization</strong></td><td>直接学习策略 π(a|s)</td><td>PPO</td></tr>
          <tr><td><strong>Q-Learning</strong></td><td>学习动作价值 Q(s,a)</td><td>DQN</td></tr>
          <tr><td><strong>混合路线</strong></td><td>同时学习策略和 Q 函数</td><td>DDPG、TD3、SAC</td></tr>
        </table>

        <h2>4. 数据怎么用？</h2>
        <table>
          <tr><th>类别</th><th>核心特点</th><th>常见算法</th></tr>
          <tr><td><strong>On-Policy</strong></td><td>用当前策略刚采集的数据更新，训练更稳定，但比较费数据。</td><td>PPO</td></tr>
          <tr><td><strong>Off-Policy</strong></td><td>旧数据也能反复使用，更省数据，但训练更容易不稳定。</td><td>DQN、DDPG、TD3、SAC</td></tr>
        </table>

        <h2>5. 一句话区分常见算法</h2>
        <ul>
          <li><strong>PPO</strong> 像直接训练控制器。</li>
          <li><strong>DQN</strong> 像训练动作评分器。</li>
          <li><strong>SAC / TD3</strong> 像同时训练控制器和评分器。</li>
          <li><strong>Model-Based RL</strong> 像先学系统模型，再用模型预测和规划。</li>
        </ul>

        <h2>6. 我目前的理解</h2>
        <p>Part 2 的重点是先建立“算法地图”：看到一个强化学习算法时，先判断它有没有模型、学的是策略还是价值函数、用的是当前数据还是历史数据。这样后续学习 PPO、DQN、DDPG、TD3、SAC 时就不会混在一起。</p>
      </article>
    </main>
  </div>
</body>
</html>
