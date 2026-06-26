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
          <p>当前包含 Part 1、Part 2 和 Part 3 学习笔记。</p>
        </div>
      </div>
      <div class="note-list">
        <a class="note-card" href="#part1">
          <h3>Part 1：Key Concepts in RL</h3>
          <div class="meta"><span>基础概念</span><span>·</span><span>基本掌握</span></div>
          <div class="meta"><span class="pill">RL</span><span class="pill">MDP</span><span class="pill">Policy</span><span class="pill">Value</span></div>
        </a>
        <a class="note-card" href="#part2">
          <h3>Part 2：Kinds of RL Algorithms</h3>
          <div class="meta"><span>算法分类</span><span>·</span><span>初步理解</span></div>
          <div class="meta"><span class="pill">PPO</span><span class="pill">DQN</span><span class="pill">SAC</span><span class="pill">Model-Based</span></div>
        </a>
        <a class="note-card" href="#part3">
          <h3>Part 3：Intro to Policy Optimization</h3>
          <div class="meta"><span>策略优化</span><span>·</span><span>初步理解</span></div>
          <div class="meta"><span class="pill">Policy Gradient</span><span class="pill">Advantage</span><span class="pill">Baseline</span></div>
        </a>
      </div>
    </aside>

    <main class="main card">
      <header class="hero">
        <div>
          <h2>入门强化学习</h2>
          <p>先把核心概念、算法分类和策略优化主线学清楚，再逐步进入具体算法。</p>
        </div>
      </header>

      <article id="part1" class="preview single-note">
        <h1>Part 1：Key Concepts in RL 学习笔记</h1>
        <p><span class="pill">基础概念</span> <span class="pill">RL</span> <span class="pill">MDP</span> <span class="pill">Policy</span> <span class="pill">Value</span> <span class="pill">Bellman</span></p>
        <h2>1. 强化学习的一句话理解</h2>
        <p><strong>强化学习 = 智能体通过试错学习决策策略。</strong></p>
        <h2>2. 强化学习的基本闭环</h2>
        <ul>
          <li>Agent 观察当前的 observation / state。</li>
          <li>Agent 根据 policy 选择 action。</li>
          <li>Environment 发生变化。</li>
          <li>Environment 返回 reward 和 next observation。</li>
          <li>Agent 更新 policy。</li>
          <li>目标是最大化 return。</li>
        </ul>
        <h2>3. 核心概念</h2>
        <table>
          <tr><th>概念</th><th>含义</th></tr>
          <tr><td><strong>State</strong></td><td>真实完整状态。</td></tr>
          <tr><td><strong>Observation</strong></td><td>智能体实际看到的信息。</td></tr>
          <tr><td><strong>Action</strong></td><td>智能体能采取的动作。</td></tr>
          <tr><td><strong>Action Space</strong></td><td>所有合法动作的集合。</td></tr>
          <tr><td><strong>Policy</strong></td><td>状态到动作的规则，相当于控制律。</td></tr>
          <tr><td><strong>Trajectory</strong></td><td>一整段状态—动作序列。</td></tr>
          <tr><td><strong>Reward</strong></td><td>一步奖励。</td></tr>
          <tr><td><strong>Return</strong></td><td>累计奖励。</td></tr>
        </table>
        <h2>4. 价值相关</h2>
        <table>
          <tr><th>概念</th><th>含义</th></tr>
          <tr><td><strong>V(s)</strong></td><td>状态 s 有多好。</td></tr>
          <tr><td><strong>Q(s,a)</strong></td><td>状态 s 下做动作 a 有多好。</td></tr>
          <tr><td><strong>Q*(s,a)</strong></td><td>最优情况下动作 a 有多好。</td></tr>
          <tr><td><strong>Bellman</strong></td><td>当前价值 = 当前奖励 + 折扣后的未来价值。</td></tr>
          <tr><td><strong>Advantage</strong></td><td>某动作比平均动作好多少。</td></tr>
        </table>
        <h2>5. MDP</h2>
        <p>用 <strong>S, A, R, P, ρ₀</strong> 描述强化学习环境。</p>
        <blockquote>核心思想：下一状态只和当前状态、当前动作有关。</blockquote>
      </article>

      <article id="part2" class="preview single-note">
        <h1>Part 2：Kinds of RL Algorithms 学习笔记</h1>
        <p><span class="pill">算法分类</span> <span class="pill">Model-Free</span> <span class="pill">Model-Based</span> <span class="pill">PPO</span> <span class="pill">DQN</span> <span class="pill">SAC</span></p>
        <h2>1. 强化学习算法分类主要看三个问题</h2>
        <ul>
          <li>有没有环境模型？</li>
          <li>Model-Free 里到底学什么？</li>
          <li>数据怎么用？</li>
        </ul>
        <h2>2. 有没有环境模型？</h2>
        <table>
          <tr><th>类别</th><th>核心思想</th></tr>
          <tr><td><strong>Model-Free</strong></td><td>不显式建模，直接通过交互学习策略或价值函数。</td></tr>
          <tr><td><strong>Model-Based</strong></td><td>使用或学习环境模型，然后基于模型规划或辅助学习。</td></tr>
        </table>
        <h2>3. Model-Free 里到底学什么？</h2>
        <table>
          <tr><th>路线</th><th>学什么</th><th>代表算法</th></tr>
          <tr><td><strong>Policy Optimization</strong></td><td>直接学习策略 π(a|s)</td><td>PPO</td></tr>
          <tr><td><strong>Q-Learning</strong></td><td>学习动作价值 Q(s,a)</td><td>DQN</td></tr>
          <tr><td><strong>混合路线</strong></td><td>同时学习策略和 Q 函数</td><td>DDPG、TD3、SAC</td></tr>
        </table>
        <h2>4. 数据怎么用？</h2>
        <table>
          <tr><th>类别</th><th>特点</th><th>常见算法</th></tr>
          <tr><td><strong>On-Policy</strong></td><td>用当前策略刚采集的数据更新，稳定但费数据。</td><td>PPO</td></tr>
          <tr><td><strong>Off-Policy</strong></td><td>旧数据也能反复使用，省数据但更容易不稳定。</td><td>DQN、DDPG、TD3、SAC</td></tr>
        </table>
        <h2>5. 一句话区分</h2>
        <ul>
          <li>PPO 像直接训练控制器。</li>
          <li>DQN 像训练动作评分器。</li>
          <li>SAC / TD3 像同时训练控制器和评分器。</li>
          <li>Model-Based RL 像先学系统模型，再用模型预测和规划。</li>
        </ul>
      </article>

      <article id="part3" class="preview single-note">
        <h1>Part 3：Intro to Policy Optimization 学习笔记</h1>
        <p><span class="pill">策略优化</span> <span class="pill">Policy Gradient</span> <span class="pill">Reward-to-go</span> <span class="pill">Baseline</span> <span class="pill">Advantage</span></p>
        <h2>1. Part 3 的目标</h2>
        <p>解释 <strong>Policy Optimization</strong> 如何直接优化策略。</p>
        <p>与 Q-Learning 先学动作评分器不同，Policy Optimization 更像是直接训练控制器本身。</p>

        <h2>2. 核心目标</h2>
        <p><strong>J(πθ)</strong> 表示：使用策略 <strong>πθ</strong> 采样轨迹时的期望回报。</p>
        <blockquote>训练目标是调整参数 θ，使 J(πθ) 变大。</blockquote>

        <h2>3. Policy Gradient</h2>
        <p>Policy Gradient 用梯度上升更新策略参数：</p>
        <blockquote>θ ← θ + α ∇θ J(πθ)</blockquote>
        <p>直观理解：不是让 loss 越小越好，而是让策略带来的长期回报越来越高。</p>

        <h2>4. 核心直觉</h2>
        <ul>
          <li>如果某个动作带来高回报，就提高以后在类似状态下选择它的概率。</li>
          <li>如果某个动作带来低回报，就降低以后在类似状态下选择它的概率。</li>
        </ul>

        <h2>5. 最简单形式的问题</h2>
        <p>最简单的 Policy Gradient 会用整条轨迹总回报 <strong>R(τ)</strong> 给轨迹中所有动作加权。</p>
        <blockquote>问题：一个动作不应该被它发生之前的奖励影响。</blockquote>

        <h2>6. Reward-to-go</h2>
        <p><strong>Reward-to-go</strong> 的思想是：第 t 步动作只用 t 之后的奖励总和评价。</p>
        <blockquote>直觉：一个动作只应该为它之后的结果负责。</blockquote>

        <h2>7. Baseline</h2>
        <p>可以减去一个只依赖状态的基准 <strong>b(s)</strong>，常用的是 <strong>Vπ(s)</strong>。</p>
        <table>
          <tr><th>作用</th><th>理解</th></tr>
          <tr><td>不改变期望梯度</td><td>减去 baseline 不会改变优化方向的期望。</td></tr>
          <tr><td>降低方差</td><td>让训练更稳定，不至于每次更新波动太大。</td></tr>
        </table>

        <h2>8. Advantage</h2>
        <p><strong>Aπ(s,a) = Qπ(s,a) - Vπ(s)</strong></p>
        <p>它表示：动作 a 比当前状态下平均动作好多少。</p>
        <table>
          <tr><th>Advantage</th><th>策略更新方向</th></tr>
          <tr><td><strong>A &gt; 0</strong></td><td>提高这个动作以后被选择的概率。</td></tr>
          <tr><td><strong>A &lt; 0</strong></td><td>降低这个动作以后被选择的概率。</td></tr>
        </table>

        <h2>9. 重要提醒</h2>
        <blockquote>Policy Gradient 里的 loss 不是监督学习 loss。</blockquote>
        <p>不能只看 loss 是否下降，真正要看的是 <strong>average return 是否上升</strong>。</p>
      </article>
    </main>
  </div>
</body>
</html>
