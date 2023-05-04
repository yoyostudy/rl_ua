# Automate Lunar Lander with Reinforcement Leanring

- 🏷️ A capstone project for the reinforcement learning specialization by the University of Albeta
- 🎯 Teach a RL agent to land the lunar without crashing. 
  - 🔧 Use a neural network as a function approximator to the action-values 
  - 🎲 Select actions according to the __softmax policy__
  - 🏃‍♀️ Train SARSA agent with __Adam optimizer__
  - 💪 Improve sample efficiency use __experience relay__
  
 ## Libraries:
 - rl_glue.py : a library glue together experiment, agent and environment
 - environment.py : an abstract class BaseEnvironment for RLGlue
 - lunar_lander.py : LunarLanderEnvironment Class inherent from BaseEnvironment
 - agent.py : an abstract class BaseAgent for RLGlue
 - plot_script: helper library to plot the result
 
 ## Classes:

- ActionValueNetwork
  > Implement a neurral network based function approximator to approximate the action-value function
  - __init__():
    - call function self.init_saxe for weight
  - get_action_value(self, state) -> q_vals: a list of q_value for each action
  - get_TD_update(self, s, delta_mat)
  - init_saxe(self, rows, cols): weight initialization borrowed idea from Saxe

- Adam Optimizer  
  > It is a more advanced variant of stochastic gradient descent(SGD) 随机梯度下降 
  >
  > The Adam algorithm improves the SGD update with two concept
  > 
  > 1. adoptive vector stepsizes
  >
  > 2. momentum

- ReplayBuffer
  > Experience replay is a simple method that can get some of the advantages of Dyna by saving a buffer of experience and using the data stored in the buffer as a model

## Functions

- softmax
  $$Pr(A_t=a|S_t=s) = \frac{e^{Q(s,a)/ \tau - max_c Q(s,c)/\tau }}{\sum_{b \in A} e^{Q(s,b)/\tau - max_c Q(s,c)/\tau}}$$
  
  - $\tau$ is the temperature parameter controls how much the agent focuses on the highest value actions.
  - The smaller the temperature parameter $\tau$, the more the agent selects the greedy action.
  - To prevent the exponential explosion, we subtract the maximum preferences across the action

- get_td_error
  $$Q_{t+1}^{i+1}(s,a) \leftarrow Q_{t+1}^i(s,a) + \alpha \cdot \[ r + \gamma (\sum_b \pi(b\|s') Q_t(s',b) ) - Q_{t+1}^i(s,a) \]$$
  1. Compute the action-values for the next states using the action-value network $Q_t$:  $$Q_t(s',b) \quad  \forall \  b \in \mathit{A}$$
  2. Compute the policy $\pi(b\|s')$ induced by the action-values $Q_t$, using the _softmax()_
  3. Compute the Expected sarsa targets $r + \gamma \cdot \large{\(} \sum_b \pi(b\|s') Q_t(s',b) \large{\)}$




 
 
 
 
  
 


