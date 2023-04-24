### RL specialization offered by Univerisity of Albeta @Coursera

This course followed the rl textbook by Sutton. 

## Course 2. Sample-based Learning Method

🔗 Refer to _Sutton_ **Chapter5** - **Chapter8**

### Module1 

🔗 **Chapter5.0-5.5**

1. Introduction to Monte-Carlo Methods
  - Model-free : 😖❓ no idea of the environment (state transaction function) 💪 learn from simulated experience
  - only for Episodic tasks: learn value use averaging sample returns
    
    > Learn the __state-value function__ $v_{\pi}(s)$ considering Monte-Carlo method

    ```pseudocode
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
    Recall that  $$\large{v_{\pi}(s) = \mathit{E_{\pi}} \[G_t | S_t = s \]}$$
    
    Law of Large Numbers gives: $$N(s) \rightarrow \infty, V(s) \rightarrow v_{\pi}(s)$$

3. Monte-carlo for Control
4. Exploration Methods for Monte-Carlo
5. Off-policy learning for prediction




