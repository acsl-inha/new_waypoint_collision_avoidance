# 다개체 최적 충돌회피 궤적 설계

본 과제에서는 기존의 경로점 접근 및 충돌 회피 문제를 최적 경로점 추천 및 충돌 회피 문제로 변형하였다.

$$\begin{aligned}
  {\text{minimize}} \quad & \sum_{k=1}^K \sum_{t=0}^{T_k-1} \|\| {u_t^{(k)}} \|\|^2 + \sum_{k=1}^K \lambda_k \|\| w^{(k)} - \bar{w}^{(k)} \|\|^2 \\
  \text{subject to} \quad & v_{t+1}^{(k)} = v_{t}^{(k)} + \Delta t x_t^{(k)} + 0.5 \Delta t^2 u_t^{(k)} \\
                    \quad & x_{t+1}^{(k)} = x_{t}^{(k)} + \Delta t u_t^{(k)} \\
                    \quad & v_{T_k}^{(k)} = v_\text{des}^{(k)} \\
                    \quad & x_{T_k}^{(k)} = x_\text{des}^{(k)} \\
                    \quad & x_{t_k}^{(k)} = \bar{w}^{(k)}\\
                    \quad & 2\left( \tilde{x}_t^{(k)} - \tilde{x}_t^{(l)} \right)^T \left( {x}_t^{(k)} - {x}_t^{(l)} \right) \geq d^2+\|\| \tilde{x}_t^{(k)} - \tilde{x}_t^{(l)} \|\|^2  \quad \text{for all } l \ne k 
\end{aligned}$$

목적함수의 첫 번째 항은 모든 player의 전 horizon에 대한 기동 에너지 최소화, 두 번째 항은 기존 경로점( $w^{(k)}$ )과 새롭게 추천된 경로점( $\bar{w}^{(k)}$ ) 사이 거리의 최소화를 의미한다.

각 구속조건은 순서대로

1. 동역학

2. 동역학

3. 종말 시점의 속도 조건

4. 종말 시점의 위치 조건

5. Affine approximation한 충돌 회피 조건 ( $\|\| x_t^{(k)} - x_t^{(l)} \|_2 \geq d$ )

6. 시점 $t_k$ 의 경로점 통과

를 의미한다.

충돌 회피 조건이 concave한 형태이므로 문제 해결을 위해 convex-concave procedure를 적용하였으며, 6개의 충돌 시나리오를 이용하여 알고리듬의 성능을 검증하였다.
