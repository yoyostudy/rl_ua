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

[UA_RL_1.pdf](https://github.com/yoyostudy/rl_ua/files/11346475/UA_RL_1.pdf)

[UA_RL_4.pdf](https://github.com/yoyostudy/rl_ua/files/11346478/UA_RL_4.pdf)

Assignments:

- Course-1-Assignment-1: [Bandit Exploration and Exploitation](https://github.com/yoyostudy/rl_ua/tree/main/code/C1_W1_A1_bandit_exploration_eploitation/Bandits)
- Course-1-Assignment-2: [Optimal Policies with Dynamic Programming](https://github.com/yoyostudy/rl_ua/blob/main/code/C1_W1_A2_GridworldCityParking_DP/DynamicProgramming/Assignment2.ipynb) 🔗 Sutton Chapter 4
      
      Key Words: Model-based, Policy Evaluation, Policy Iteration, Value Iteration
- Course-2-Assignments: 🔗 Sutton Chapter 6

      key Words: TD, Model-free, boostrapping, TD(0), policy-based
      
       - [Policy Evaluation in cliff Walking Environment](https://github.com/yoyostudy/rl_ua/tree/main/code/C2_A1_CliffWalking_PolicyEvaluation/Policy%20Evaluation%20with%20Temporal%20Difference%20Learning)

## Course 1. 

### Bellman Equation

### Dynamic Programming

Refer to _Sutton Chapter4_

- DP + Perfect Model of finite MDP env --> compute optimal policy

**1. (Prediction Problem) Policy Evaluation**

$$v_{\pi}(s) = \mathbb{E_{\pi}}$$






## Course 2. Sample-based Learning Method

🔗 Refer to _Sutton_ **Chapter5** - **Chapter8**

### Module1 

🔗 **Chapter5.0-5.5**

1. Introduction to Monte-Carlo Methods
      - 🎯 Learn state value function for a fixed policy 
        $$\large{v_{\pi}(s) = \mathit{E_{\pi}} \[G_t | S_t = s \]}$$
      - Model-free : 😖❓ no idea of the environment (state transaction function) 💪 learn from simulated experience
        > learn from the agent's own interaction with the world, rather than a model of the world
      - Episodic-by-episode Update: learn value use averaging sample returns 回合更新

        > Learn the __state-value function__ $v_{\pi}(s)$ considering Monte-Carlo method

        ```pseudocode
        Estimate the state value based on reward average on each episode

        Args:
          policy pi ## policy to be evaluated
          V(s)      ## state-value function given the policy pi
          S(s)      ## a list of total reward for each episode
          N(s)      ## number of episode

        Repeat for each episode:
          N(s) += 1
          For each state s until episode terminate:
            Generate an episode following policy pi: S0(s), A0, R1, S1, A1,....
            G(s) <- return given initial state S0=s
            S(s) <- S(s).append(G(s))
            V(s) <- average(S(s))
        ```
        Law of Large Numbers gives: $$N(s) \rightarrow \infty, V(s) \rightarrow v_{\pi}(s)$$

2. Monte-carlo for Control

      - 🎯 Learn action value function for a given policy
      $$q_{\pi}(s,a) = \mathit{E_{\pi}} \[G_t | S_t = s, A_t = a \]$$
      
      - 🎯 Build a generalized policy iteration algorithm (GPI)
        
        policy improvement + policy evaluation
        
        ```
        Args:
          policy pi # p(a|s)
          Q(s,a) 
          S(s,a)
          N(s)      # number of episode
          
        Repeat for each episode:
          N(s) += 1
          Choose (S0,A0)
          Generate a episode starting from (S0,A0), following policy pi
          For each pair (s,a) in the episode:
            G <- Return given initial state s, action a
            S(s,a) <- S(s,a).append(G)
            Q(s,a) <- average(S(s,a))
          For each s in the episode:
            pi(s) = argmax_a Q(s,a)  
        ```
        ![Screen Shot 2023-04-24 at 1 16 06 PM](https://user-images.githubusercontent.com/115062425/234106405-2aa48b2c-0cb3-43db-aaa7-0e2a5acf6df6.png)
      
3. Exploration Methods for Monte-Carlo
    

4. Off-policy learning for prediction


### Model 2. Temporal difference (TD) learning
🔗 **Chapter 6.3**


## Course3 Prediction and Control with Function Approximation

- learn parametrized function <-- store all values for all states in a table
- neural network to approximate the value

- refer: **Ch.9.1-9.4**









