  
## Induction on Bellman Equation 

> Bellman equation for value function. It expresses a relationship between the value of a state and the values of its successor states

$$v_{\pi}(s) = \sum_{a} \pi(a|s) \sum_{s', r} p(s',r|s,a) (r + \gamma * v_{\pi}(s')) = E_{\pi} [R_t + \gamma* v_{\pi}(S_{t+1}) | S_t = s]$$
Proof:
- $v_{\pi}(s) := E_{\pi}(U_t|S_t = s) = E_{\pi}(R_t + \gamma * U_{t+1}) |S_t = s) = E_{\pi}(R_t|S_t = s) + \gamma * E_{\pi}(U_{t+1}|S_t = s)$
- $E_{\pi}(R_t|S_t = s)  = \sum_{r} r \cdot p(r|s) = \sum_r r \cdot \sum_a p(r,a|s) $
  
  $= \sum_r \sum_a r p(r|a,s) \pi(a|s) = \sum_a \pi(a|s) \sum_r \sum_{s'} r p(s',r|s,a) = \sum_a \pi(a|s) \sum_{r, s'} p(s',r|s,a) \cdot r$
- $E_{\pi}(U_{t+1}|S_t = s) = \sum_{u_{t+1}} u_{t+1} p(u_{t+1} |s) = \sum_{u_{t+1}} u_{t+1} \sum_a  p(u_{t+1}, a|s) $

  $=  \sum_{u_{t+1}} u_{t+1} \sum_a  p(u_{t+1}|s, a) \pi(a|s) = \sum_a \pi(a|s)  \sum_{u_{t+1}} u_{t+1} \cdot p(u_{t+1}|s, a)$
  
  $= \sum_a \pi(a|s) \sum_{u_{t+1}} u_{t+1} \sum_{s'} p(u_{t+1}, s'|s, a)$
  
  $= \sum_a \pi(a|s) \sum_{u_{t+1}} u_{t+1} \sum_{s'} p(u_{t+1}| s', s, a)p(s'|s,a) $
  
  $= \sum_a \pi(a|s) \sum_{u_{t+1}} u_{t+1} \sum_{s'} p(u_{t+1}| s') \sum_r p(s', r|s,a) $
  
  $= \sum_a \pi(a|s) \sum_{s'} \sum_r  p(s',r |s,a) \sum_{u_{t+1}}  p(u_{t+1}| s') \cdot u_{t+1} $
  
  $= \sum_a \pi(a|s) \sum_{s'} \sum_r  p(s',r |s,a) E[U_{t+1} | s']$
  
  $= \sum_a \pi(a|s) \sum_{s',r } p(s',r |s,a) v_{\pi}(s')$
- Write in the form of expectation, note that all the upper case letter are random variables where the expectations are performed.

> Bellman equation for action value function. It expresses a relationship between the value of a action and the values of its successor actions

$$q_{\pi}(s,a) = \sum_{s',r} p(r,s'|s,a) [r + \gamma * \sum_{a'} \pi(a'|s') q_{\pi}(s',a')]$$
Proof:
- $q_{\pi}(s,a) = E(U_t | S_t = s, A_t = a) = E(R_t + \gamma * U_{t+1} | S_t = s, A_t = a) = E(R_t| S_t = s, A_t = a) + \gamma * E(U_{t+1} | S_t = s, A_t = a)  $
- $E(R_t| S_t = s, A_t = a) = \sum_r r \cdot p(r|s,a) = \sum_{r} \sum_{s'} r \cdot p(r,s'|s,a) = \sum_{r,s'} p(r,s'|s,a) r$
- $E(U_{t+1} | S_t = s, A_t = a)  = \sum_{u_{t+1}} u_{t+1} p(u_{t+1}|s,a) = \sum_{u_{t+1}} u_{t+1} \sum_{s'}  p(u_{t+1}, s'|s,a)$
  
  $= \sum_{u_{t+1}} u_{t+1} \sum_{s'}  p(u_{t+1}| s') p(s'|s,a) = \sum_{u_{t+1}}  u_{t+1} \sum_{s'} p(u_{t+1}| s') \sum_r p(s',r |s,a)$
  
  $= \sum_{u_{t+1}} u_{t+1} \sum_{s'} \sum_{a'}  p(u_{t+1}, a'| s') \sum_r p(s',r |s,a)$
  
  $=  \sum_{u_{t+1}} u_{t+1} \sum_{s'} \sum_{a'}  p(u_{t+1}| a',s') \pi(a'|s') \sum_r p(s',r |s,a) $
  
  $= \sum_{s'} \sum_r p(s',r |s,a)  \sum_{a'} \pi(a'|s')    \sum_{u_{t+1}} u_{t+1}  p(u_{t+1}| a',s') $
  
  $= \sum_{s',r} p(s',r|s,a)  \sum_{a'} \pi(a'|s')   E_{\pi}(U_{t+1}|s',a') = \sum_{s',r} p(s',r|s,a)  \sum_{a'} \pi(a'|s')   q_{\pi}(s',a') $
------------------------------------------------------------------------------------------------------------------------------------------
![image](https://user-images.githubusercontent.com/115062425/236090808-af477106-0250-4eb5-9142-902e84157276.png)

> Connect $V_{\pi}(s)$ with $Q_{\pi}(s,a)$ 

<img width="300" alt="image" src="https://user-images.githubusercontent.com/115062425/236315038-1605790b-8d89-4dda-9726-5f7355db96c7.png">

$$v_{\pi}(s) = \sum_{a} \pi(a|s) q_{\pi}(a,s)$$

> Connect $Q_{\pi}(s,a)$ with $V_{\pi}(s')$

<img width="500" alt="image" src="https://user-images.githubusercontent.com/115062425/236315521-20527812-2786-42c7-9195-feed4baa5672.png">

$$q_{\pi}(s,a) = \sum_{s',r} p(s',r|s,a) (r + \gamma * v_{\pi}(s'))$$


------------------------------------------------------------------------------------------------------------------------------------------
![think](https://user-images.githubusercontent.com/115062425/236089921-6041f5bb-54b1-48a0-b103-99860552fe08.jpg)


https://stepneverstop.github.io/%E4%BB%B7%E5%80%BC%E4%B8%8E%E8%B4%9D%E5%B0%94%E6%9B%BC%E6%96%B9%E7%A8%8B.html


  
