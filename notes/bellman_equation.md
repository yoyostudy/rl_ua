  
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

------------------------------------------------------------------------------------------------------------------------------------------
![image](https://user-images.githubusercontent.com/115062425/236090808-af477106-0250-4eb5-9142-902e84157276.png)

> Connect $V_{\pi}(s)$ with $Q_{\pi}(s,a)$ 

$$v_{\pi}(s) = \sum_{a} \pi(a|s) q_{\pi}(a,s)$$

图片正在加载中....

> Connect $Q_{\pi}(s,a)$ with $V_{\pi}(s')$

$$q_{\pi}(s,a) = \sum_{s',r} p(s',r|s,a) (r + \gamma * v_{\pi}(s'))$$

图片正在加载中....

![think](https://user-images.githubusercontent.com/115062425/236089921-6041f5bb-54b1-48a0-b103-99860552fe08.jpg)


  
