### RL specialization offered by Univerisity of Albeta @Coursera

This repository is the record and note of this Coursera Course

This course followed the rl textbook by Sutton. 

-------------------
To begin with:

小小的吐槽🤫: 其实感觉这个课程的质量不高，两个老师讲的很快，推导也是一步带过。好几个video都是反复看了好几遍也没听懂，但是一看书就很清楚。
说实话我最烦的就是给数学公式跳步，bellman equation里面对哪个Random Variable求期望都没说清楚，直接给推导公式。刚开始看的时候一头雾水。😡
我在看这个课的同时也看了莫烦的rl课和王树森的深度强化学习课。王树森的推导相对更加详细，莫烦的例子很有意思。
我一般在吃饭的时候看王树森的课，一边吃一边记笔记想推导。吃完之后就直接看他的note，就发现好像都看懂了。反正看ua的rl课看不懂了就去看王树森🐶

--------------------

Certificate:

1. [Fundamentals of Reinforcement Learning](https://github.com/yoyostudy/rl_ua/blob/main/Certificates/UA_RL_1.pdf)
2. [Sample-based Learning Method](https://github.com/yoyostudy/rl_ua/blob/main/Certificates/UA_RL_2.pdf)
3. [Prediction and Control with Function Approximation](https://github.com/yoyostudy/rl_ua/blob/main/Certificates/UA_RL_3.pdf)
4. [A Complete Reinforcement Learning System](https://github.com/yoyostudy/rl_ua/blob/main/Certificates/UA_RL_4.pdf)

Assignments:

- Course-1-Assignment-1: [Bandit Exploration and Exploitation](https://github.com/yoyostudy/rl_ua/tree/main/code/C1_W1_A1_bandit_exploration_eploitation/Bandits)
- Course-1-Assignment-2: [Optimal Policies with Dynamic Programming](https://github.com/yoyostudy/rl_ua/blob/main/code/C1_W1_A2_GridworldCityParking_DP/DynamicProgramming/Assignment2.ipynb) 🔗 Sutton Chapter 4
      
      Key Words: Model-based, Policy Evaluation, Policy Iteration, Value Iteration
- Course-2-Assignments: 🔗 Sutton Chapter 6
  
  [Policy Evaluation in cliff Walking Environment](https://github.com/yoyostudy/rl_ua/tree/main/code/C2_A1_CliffWalking_PolicyEvaluation/Policy%20Evaluation%20with%20Temporal%20Difference%20Learning)
  
  [Q-learning and Expected SARSA in cliff Walking Environment](https://github.com/yoyostudy/rl_ua/tree/main/code/C2_A2_Qlearning_SARSA_CliffWalking/Q-Learning%20and%20Expected%20Sarsa)

      key Words: TD, Model-free, boostrapping, TD(0), policy-based
      
  
## Induction on Bellman Equation 

> Bellman equation for value function. It expresses a relationship between the value of a state and the values of its successor states

$$v_{\pi}(s) = \sum_{a} \pi(a|s) \sum_{s', r} p(s',r|s,a) (r + \gamma * v_{\pi}(s')) = E_{\pi} [R_t + \gamma* v_{\pi}(S_{t+1}) | S_t = s]$$

Proof:
- $v_{\pi}(s) := E_{\pi}(U_t|S_t = s) = E_{\pi}(R_t + \gamma * U_{t+1}) |S_t = s) = E_{\pi}(R_t|S_t = s) + \gamma * E_{\pi}(U_{t+1}|S_t = s)$
- $E_{\pi}(R_t|S_t = s)  = \sum_{r} r \cdot p(r|s) = \sum_r r \cdot \sum_a p(r,a|s) = \sum_r \sum_a r p(r|a,s) \pi(a|s) = \sum_a \pi(a|s) \sum_r \sum_{s'} r p(s',r|s,a) = \sum_a \pi(a|s) \sum_{r, s'} p(s',r|s,a) \cdot r$
- $E_{\pi}(U_{t+1}|S_t = s) = \sum_{u_{t+1}} u_{t+1} p(u_{t+1} |s) = \sum_{u_{t+1}} u_{t+1} \sum_a  p(u_{t+1}, a|s) =  \sum_{u_{t+1}} u_{t+1} \sum_a  p(u_{t+1}|s, a) \pi(a|s) = \sum_a \pi(a|s)  \sum_{u_{t+1}} u_{t+1} \cdot p(u_{t+1}|s, a)$
  $= \sum_a \pi(a|s) \sum_{u_{t+1}} u_{t+1} \sum_{s'} p(u_{t+1}, s'|s, a)$
  $= \sum_a \pi(a|s) \sum_{u_{t+1}} u_{t+1} \sum_{s'} p(u_{t+1}| s', s, a)p(s'|s,a) $
  $= \sum_a \pi(a|s) \sum_{u_{t+1}} u_{t+1} \sum_{s'} p(u_{t+1}| s') \sum_r p(s', r|s,a) $
  $= \sum_a \pi(a|s) \sum_{s'} \sum_r  p(s',r |s,a) \sum_{u_{t+1}}  p(u_{t+1}| s') \cdot u_{t+1} $
  $= \sum_a \pi(a|s) \sum_{s'} \sum_r  p(s',r |s,a) E[U_{t+1} | s']$
  $= \sum_a \pi(a|s) \sum_{s',r } p(s',r |s,a) v_{\pi}(s')$
- Write in the form of expectation, note that all the upper case letter are random variables where the expectations are performed.




$$q_{\pi}(s,a) = \sum_{s',r} p(r,s'|s,a) [r + \gamma * \sum_{a'} \pi(a'|s') q_{\pi}(s',a')]$$

> Connect $V_{\pi}(s)$ with $Q_{\pi}(s,a)$ 

$$v_{\pi}(s) = \sum_{a} \pi(a|s) q_{\pi}(a,s)$$

图片正在加载中....

> Connect $Q_{\pi}(s,a)$ with $V_{\pi}(s')$
  
  
  










