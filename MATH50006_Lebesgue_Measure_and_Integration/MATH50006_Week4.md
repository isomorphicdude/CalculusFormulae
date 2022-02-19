---
title: "MATH50006 Week 3 and 4"
date: "18/02/2022"
output: 
  pdf_document:
    number_sections: true
---

## **The Lebesgue Measure**  
&nbsp;  

- Defined as the Hahn-Caratheodory extension of pre-measure $\tilde{\lambda}$ on $\mathcal{A}$ the **algebra** of collections of **elementray figures**  

- $(a,b)=\prod(a_k, b_k)$, with $a_k < b_k$ is the **interval**, whose finite disjoint union forms **elementary figures**  

- $\tilde{\lambda}([a,b])=b-a$ 
  
- $\tilde{\lambda}(\cup I)=\sum \tilde{\lambda}(I_i)$ for disjoint $I_j$, is a pre-measure  
   > - Only need to verify sigma additivity*
   > - $\tilde{\lambda}(I) \leq \sum^{\infty} I_i$ already by taking limits of finite additivity  
   > - The other direction is by compactness argument
   > - Case where $I$ is interval first
   > - Take $\bar{I}_L=\bar{I} \cap [-L,L]^N$ to ensure boundedness, hence compactness, and for taking $L$ to $\infty$
   > - Aim to find an open cover for $\bar{I}_L$
   > - Operate on the $I_i$'s, cover by $I_i^{\epsilon}$, then cover $I_i^{\epsilon}$ by open set $\tilde{I}_i^{\epsilon}$, where 
   > - $\tilde{\lambda}(\tilde{I}_i^{\epsilon}) \leq (1+\epsilon)^n \lambda(I_i) + \epsilon \ 2^{-i}$
   > - So can take finite subcover formed by $\tilde{I}_i^{\epsilon}$
   > - $\tilde{\lambda}(\bar{I}_L) \leq (1+\epsilon)^n \sum \lambda (I_i) +\epsilon$, taking first $\epsilon$ to $0$ then $L \rightarrow \infty$  
&nbsp;
- $\mathcal{B}(\mathbb{R}^n) \subset \Sigma$, where $\Sigma$ is defined from extension thm. 
  > - Note from extension thm., $\mathcal{A} \subset \Sigma$
  > - So suffice to show for open set $\mathcal{O} \in \mathcal{B}(\mathbb{R}^n)$, $\mathcal{O} \in \sigma(\mathcal{A})$ 
  > - Choose half open cubes $[\epsilon, \epsilon+2^{-m})$ at each step in $\mathcal{O}$ and disjoint with previous (finitely many each step)

- Above result finishes Lebesgue measure construction as original domain is $\Sigma$ and borel algebra
