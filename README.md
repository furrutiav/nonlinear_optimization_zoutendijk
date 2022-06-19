# MA5701 Optimización no lineal: Tarea 3

**Fecha de entrega:** 4 de Julio a las 23:59 hrs.

**Autor:** Felipe Urrutia Vargas

# Método de direcciones admisibles (Zoutendijk)

## Pseudo-algoritmo

(0) Sean $\epsilon>0$, $k = 0$, $x_0 \in \mathbb{R}^n$ tal que $Ax_0 \leq  b$, $Ex_0=e$ 

(1) Sea la descomposición $A = [A_1,A_2]^T, b =(b_1, b_2)^T$ tal que $A_1x_k = b_1, A_2x_k < b_2$.

(2) Resolver el problema lineal

$$ (D_k) \quad \begin{cases} \min & \nabla f (x_k)^T d\\
s.a. &A_1d \leq 0 \\
&Ed = 0\\
&−1 \leq d_j \leq 1, \quad j = 1, . . . , n
\end{cases} $$
y sea $d_k$ solución de $(D_k)$.

Si $|| \nabla f (x_k)^T d_k || < \epsilon$, entonces parar.

Si no, ir a (3).

(3) Determinar el paso, resolviendo aproximadamente el problema de minimización unidimensional

$$(L) \quad \begin{cases} \min &f (x_k + \lambda d_k)\\
s.a. &\lambda \in [0, \bar{\lambda_k}]
\end{cases}$$

mediante el método de Armijo.

Se usa 

$$ \bar{\lambda_k} = \min \left\lbrace \frac{(b_2 − A_2 x_k)_i}{(A_2 d_k)_i} : (A_2 d_k)_i > 0 \right\rbrace$$
y se considera $\bar{\lambda_k} = +\infty$ cuando $(A_2 d_k)_i \leq 0 \forall i$.

Sea $\lambda_k$ la solución del subproblema $(L)$. Hacer:

$$x_k+1 = x_k + \lambda_k d_k,$$
$$k ← k + 1,$$
$$\text{e ir a $(1)$.}$$

