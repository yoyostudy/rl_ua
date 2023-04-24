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
      S(s)      ## 
    
    Repeat forever:
      For each state s appearing in the episode:
        G(s) <- return given initial state s
        S(s) <- S(s).append(G(s))
        V(s) <- average(S(s))
    ```



3. Monte-carlo for Control
4. Exploration Methods for Monte-Carlo
5. Off-policy learning for prediction




