# Automate Lunar Lander with  Reinforcement Leanring

- 🏷️ A capstone project for the reinforcement learning specialization by the University of Albeta
- 🎯 Teach a __Expected Sarsa__ rl agent to land the lunar without crashing. 
  - 🔧 Use a neural network as a function approximator to the action value function $q_{\pi}(s,a)$
  - 🏃‍♀️ Train deep neural network with __Adam optimizer__
  - 🎲 Select actions $a \leftarrow \pi(\cdot|s)$ according to the __softmax policy__
  - 💪 Improve sample efficiency use __experience relay__
  
 ## Libraries:
 - rl_glue.py : a library glue together experiment, agent and environment
 - environment.py : an abstract class BaseEnvironment for RLGlue
 - lunar_lander.py : LunarLanderEnvironment Class inherent from BaseEnvironment
 - agent.py : an abstract class BaseAgent for RLGlue
 - plot_script: helper library to plot the result
 
 ## Classes and Functions:

- ActionValueNetwork Class
  > A neural network based function approximator to approximate the action-value function 
  $q(s,a;w) \rightarrow q_{\pi}(s,a)$
  
  - __init__():
    - set hyperparameters and parameters
  - get_action_value(self, state) -> q_vals: a list of q_value for each action
  - get_TD_update(self, s, delta_mat)
  - init_saxe(self, rows, cols): weight initialization borrowed idea from Saxe

- Adam Class [🔗](https://github.com/yoyostudy/rl_ua/blob/main/notes/adam_optimizer.md)

- ReplayBuffer Class [🔗](https://github.com/yoyostudy/rl_ua/blob/main/notes/experience_replay.md)

- softmax Function
  $$Pr(A_t=a|S_t=s) = \frac{e^{Q(s,a)/ \tau - max_c Q(s,c)/\tau }}{\sum_{b \in A} e^{Q(s,b)/\tau - max_c Q(s,c)/\tau}}$$
  
  - $\tau$ is the temperature parameter controls how much the agent focuses on the highest value actions.
  - The smaller the temperature parameter $\tau$, the more the agent selects the greedy action.
  - To prevent the exponential explosion, we subtract the maximum preferences across the action

- get_td_error Function
  $$Q_{t+1}^{i+1}(s,a) \leftarrow Q_{t+1}^i(s,a) + \alpha \cdot \[ r + \gamma (\sum_b \pi(b\|s') Q_t(s',b) ) - Q_{t+1}^i(s,a) \]$$
  1. Compute the action-values for the next states using the action-value network $Q_t$:  $$Q_t(s',b) \quad  \forall \  b \in \mathit{A}$$
  2. Compute the policy $\pi(b\|s')$ induced by the action-values $Q_t$, using the _softmax()_
  3. Compute the Expected sarsa targets $r + \gamma \cdot \large{\(} \sum_b \pi(b\|s') Q_t(s',b) \large{\)}$




 
 
 
 
  
 


