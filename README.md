# new_waypoint_collision_avoidance
collision avoidance via sequential convex programming

$$\begin{aligned}
  {\text{minimize}} \quad & \sum_{k=1}^K \sum_{t=0}^{T_k-1} \lvert {u_t^{(k)}} \rvert^2 + \sum_{k=1}^K \lambda_k \lvert w^{(k)} - \bar{w}^{(k)} \rvert^2 \\
  \text{subject to} \quad & v_{t+1}^{(k)} = v_{t}^{(k)} + \Delta t x_t^{(k)} + 0.5 \Delta t^2 u_t^{(k)} \\
                    \quad & x_{t+1}^{(k)} = x_{t}^{(k)} + \Delta t u_t^{(k)} \\
                    \quad & v_{T_k}^{(k)} = v_\text{des}^{(k)} \\
                    \quad & x_{T_k}^{(k)} = x_\text{des}^{(k)} \\
                    \quad & x_{t_k}^{(k)} = \bar{w}^{(k)}\\
                    \quad & 2\left( \tilde{x}_t^{(k)} - \tilde{x}_t^{(l)} \right)^T \left( {x}_t^{(k)} - {x}_t^{(l)} \right) \geq d_\text{safety}^2+\lvert \tilde{x}_t^{(k)} - \tilde{x}_t^{(l)} \rvert^2  \quad \text{for all } l \ne k 
\end{aligned}$$
