# **Convergence Theorems**  

## **Fatou's lemma**  

## **Lebesgue Dominated Convergence**   

**Conditions:**  

- $f, f_n$ measurable  

- $f_n \to f$, $\mu-a.e.$  

- $g \in \mathcal{L}^1(\mu)$ integrable and nonnegative being a dominated function, $|f_n(x)|\leq g(x)$  

**Conclusion:**  

- $|\int_X f_n d\mu - \int_X f d\mu| \leq \int_X |f_n-f|d\mu \to 0$

## **Vitali's Convergence**  

**Assumptions:**  

- $\mu(X) < \infty$

- $f, f_n$ integrable

**Conditions**  

- $(f_n)_{n \geq 1}$ converges to $f$ in measure

- $\mathcal{F} = \{f_n: n\in \mathbb{N}\}$ has uniformly absolutely continuous integrals *i.e.*, can choose $\delta$ for any $\mu(A) < \delta$, such that for any $f$ in the family

$$
\int_{A} |f| d\mu < \epsilon
$$  

**Equivalent to**  

- $\int_X |f_n - f| d\mu \to 0$



## **Using Convergence to prove Riemann**   



# **$L^P$** **spaces**  


## **The $\mathcal{L}^P$ Norms**  



## **$\mathcal{L}^P$ produces Vector Space**  

- **Positive Definite**  

- **Homogeneity**  

- **Triangle Inequality**

&nbsp;



## **$L^P$ space is complete**  

- Aim to show $||f_n(x)-f(x)||_{L^P(\mu)} \to 0$  

- That is to show 
$$
\int |f-f_n|^p \ d\mu =0
$$

- Take subsequence $(f_{n_k})$ s.t. $||f_n-f_m||_{L^P(\mu)} < 2^{-k}$, $\forall n,m \geq n_k$


- Define  
$$
f(x) = f_{n_j}(x) + \sum_{k=j}^{\infty} (f_{n_k+1}(x)-f_{n_k}(x))
$$  
- which can be for any $j$  

- Using triangle inequality, we wish to bound $||f_n(x)-f(x)||_{L^P(\mu)}$ by  

$$
||f_n-f_{n_k}|| + ||f-f_{n_k}|| \leq \ 2^{-k} + ||f-f_{n_k}||
$$  

- To show the latter converges to zero, we use **Lebesgue Dominated Convergence Thm.**  

- Namely define a dominating function $g(x)$  

$$
g(x) = \lim_{l \to \infty} g_l(x)= \lim_{l \to \infty}\ \sum_{k=1}^{l} |f_{n_k+1}(x)-f_{n_k}(x)|
$$  

- We want $g$ to be in $L^P(\mu)$, which is true

