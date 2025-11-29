# Dynamic-Pricing-Reinforcement-Learning
Dynamic pricing simulation using reinforcement learning. Models demand with a logistic curve and compares ε-Greedy, Thompson Sampling, Greedy, and tuned UCB1. Achieves 55–68% optimal-price selection with fast convergence, showing how bandit algorithms adapt to customer behavior.


1. Project Overview

This project builds a dynamic pricing system that tests multiple pricing strategies under uncertainty.
Demand is modeled using a logistic function, and algorithms learn which price maximizes expected revenue over repeated customer interactions.

The simulation evaluates:

Greedy

ε-Greedy

Thompson Sampling

UCB1 (tuned version)

📈 2. Market Environment

The customer purchase probability is defined by a logistic demand curve:

𝑃
(
purchase
)
=
𝑎
1
+
𝑒
𝑏
⋅
price
P(purchase)=
1+e
b⋅price
a
	​


Where:

a controls purchase scale

b controls price sensitivity

Each algorithm interacts with this environment and receives a binary reward (purchase = 1, no purchase = 0).

3. Algorithms Implemented
Greedy

Always selects the arm with the highest estimated reward.
Fails due to no exploration.

ε-Greedy

Explores with probability ε (small) and exploits otherwise.
Strong balance → good performance.

Thompson Sampling

Samples from Beta posterior distributions for each arm.
Highly effective and adaptive.

UCB1 (Improved Version)

Uses confidence bounds with:

reward normalization

tunable exploration constant C

After tuning (C ≈ 0.7), UCB1 becomes the best performer.

4. Simulation Setup
Parameter	Value
Price options	[20, 30, 40, 50, 60]
Steps per simulation	10,000
Repeated runs	1,000 epochs
Total interactions	~10 million

For each strategy, the simulation tracks:

Optimal price selection %

Reactivity (how quickly it converges)

Arm allocation distribution

5. Results Summary
1. Baseline Results

ε-Greedy and Thompson Sampling performed best initially

Both selected the optimal price in 55%+ of rounds

Both showed fast convergence (~1800–1900 steps)

2. After Tuning UCB1

Tuned UCB1 showed:

~68% optimal-price selection

More stable adaptation

Strongest performance across metrics

3. Final Ranking

Tuned UCB1 (C ≈ 0.7)

ε-Greedy

Thompson Sampling

Greedy (poor performance)

6. Metrics Used
🔹 Arm Allocation

Distribution of how often each algorithm selected each price.

🔹 Reactivity

The number of steps required to settle on the best price.

🔹 Reward Trend

How revenue or reward changed over time.

(Regret metric exists but not emphasized here.)

Key Takeaways

Demand curves + reinforcement learning = fast, adaptive pricing

ε-Greedy and Thompson Sampling are strong baselines

A tuned UCB1 model can outperform both by improving exploration behavior

Simulation-based RL is a powerful tool for real-world pricing strategy
