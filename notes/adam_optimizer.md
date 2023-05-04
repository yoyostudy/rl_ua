# Adam Optimizer

> Adam Optimizer is a more advanced variant of Stochastic Gradient Descent (SGD)

  - $m_t = \beta_m * m_{t-1} + (1-\beta_m) g_t$
  - $v_t = \beta_v * v_{t-1} + (1-\beta_v) g_t^2$
  - To get unbiased estimates of mean and second moment:
    - $\large \hat{m_t} = \frac{m_t}{1-\beta_m^t}$
    - $\large \hat{v_t} = \frac{v_t}{1-\beta_v^t}$
  - The weights are then updated as:
    - $\large w_t = w_{t-1} + \frac{\alpha}{\sqrt{\hat{v_t}} +\epsilon } \hat{m_t}$




