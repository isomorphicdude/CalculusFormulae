---
title: "MATH50003 Problem Sheets and Solutions"
date: "25/02/2022"
output: 
  pdf_document:
    latex_engine: xelatex
---
# Week 1  

## 1. Binary representation


**Problem 1.1** What is the binary representation of $1/5$?   

**SOLUTION**  
Hence we  show that
$$
\begin{aligned}
(0.00110011001100…)_2 &= (2^{-3} + 2^{-4})(1.00010001000…)_2 =  (2^{-3} + 2^{-4}) \sum_{k=0}^{\infty} {1 \over 16^k} \\
&= {2^{-3} + 2^{-4} \over 1 - {1\over 2^4}} = \frac{1}{5}
\end{aligned}
$$

&nbsp;

## 2. Integers  

**Problem 2.1** With 8-bit signed integers, find the bits for the following: $10, 120, -10$.  

**SOLUTION**  

We can find the binary digits by repeatedly subtracting the largest power of 2 less than a number
until we reach 0, e.g. $10 - 2^3 - 2 = 0$
implies $10 = (1010)_2$.
Thus the bits are: $00001010$.  

For negative numbers we perform the same trick but adding $2^p$ to make it positive, e.g.,
$$
-10 = 2^8 - 10 ({\rm mod 2^8}) = 246 = 2^7 + 2^6 + 2^5 + 2^4 + 2^2 + 2 = (11110110)_2
$$  

Thus the bits are $11110110$  

&nbsp;

## 3. Floating point numbers  

&nbsp;

**Problem 3.1** What are the single precision $F_{32}$ (`Float32`) floating point representations for the following:  
$$
2, 31, 32, 23/4, (23/4)\times 2^{100}
$$  

&nbsp;

**SOLUTION**  

Recall that we have $\sigma,Q,S = 127,8,23$. Thus we write
$$
2 = 2^{128-127} * (1.00000000000000000000000)_2
$$
The exponent bits are those of
$$
128 = 2^7 = (10000000)_2
$$  

We write
$$
31 = (11111)_2 = 2^{131-127} * (1.1111)_2
$$
And note that $131 = (10000011)_2$ Hence we have: $01000001111110000000000000000000$  

On the other hand,
$$
32 = (100000)_2 = 2^{132-127}
$$
and $132 = (10000100)_2$ hence: $01000010000000000000000000000000$  

Note that
$$
23/4 = 2^{-2} * (10111)_2 = 2^{129-127} * (1.0111)_2
$$  

and $129 = (10000001)_2$ hence we get: $01000000101110000000000000000000$    

Finally,
$$
23/4 * 2^{100} = 2^{229-127} * (1.0111)_2
$$
and $229 = (11100101)_2$ giving us: $\color{red}{0}\color{green}{11100101}\color{blue}{0111000000000000000000}$  

&nbsp;

**Problem 3.2** Let $m(y) = \min\{x \in F_{32} : x > y \}$ be the smallest single precision number
greater than $y$. What is $m(2) - 2$ and $m(1024) - 1024$?  

&nbsp;

**SOLUTION**  

The next float after $2$ is $2 * (1 + 2^{-23})$ hence we get $m(2) - 2 = 2^{-22}$, similarly, for $1024 = 2^{10}$ we find that the difference $m(1024) - 1024$ is $2^{10-23} = 2^{-13}$  

&nbsp;

## 4. Arithmetic  


&nbsp;  

**Problem 4.1** Suppose $x = 1.25$ and consider 16-bit floating point arithmetic (`Float16`). 
What is the error in approximating $x$ by the nearest float point number ${\rm fl}(x)$?
What is the error in approximating $2x$, $x/2$, $x + 2$ and $x - 2$ by $2 \otimes x$, $x \oslash 2$, $x \oplus 2$ and $x \ominus 2$?  

&nbsp;  

**SOLUTION**  

None of these computations have errors since they are all exactly representable as floating point numbers.  

&nbsp;  

**Problem 4.2** For what floating point numbers is $x \oslash 2 \neq x/2$ and $x \oplus 2 \neq x + 2$?  

&nbsp;  

**SOLUTION**  


Consider a normal $x = 2^{q-\sigma} (1.b_1\ldots b_S)_2$.
Provided $q > 1$  we have
$$
x \oslash 2 = x/2 = 2^{q-\sigma-1} (1.b_1\ldots b_S)_2
$$
However, if $q = 1$ we lose a bit as we shift:
$$
x \oslash 2 = 2^{1-\sigma} (0.b_1\ldots b_{S-1})_2
$$
and the property will be satisfy if $b_S = 1$.  

Similarly, if we are sub-normal, $x = 2^{1-\sigma} (0.b_1\ldots b_S)_2$ and
we have
$$
x \oslash 2 = 2^{1-\sigma} (0.0b_1\ldots b_{S-1})_2
$$
and the property will be satisfy if $b_S = 1$.
(Or `NaN`.)  

&nbsp;  

**Problem 4.3** Explain why for `x = 10.0^100`, we have $x=x+1$. What is the largest floating point number $y$ such that $y + 1 \neq y$?  

&nbsp;  

**SOLUTION**  

&nbsp;  

Writing $10 = 2^3 (1.01)_2$ we have
$$
\rm{fl}(10^{100}) = \rm{fl}(2^{300} (1 + 2^{-4})^{100}) = 2^{300} (1.b_1 \ldots b_{52})_2
$$
where the bits $b_k$ are not relevant. We then have:
$$
\rm{fl}(10^{100}) \oplus 1 = \rm{fl}(2^{300} [(1.b_1 \ldots b_{52})_2 + 2^{-300}]) = \rm{fl}(10^{100})
$$
since $2^{-300}$ is below the necessary precision.

The largest floating point number satisfying the condition is $y = 2^{53} - 1$  

&nbsp;  

**Problem 4.4** What are the exact bits for $1/5$, $1/5 + 1$ computed
using  half-precision arithmetic (`Float16`) (using default rounding)?  

&nbsp;  

**SOLUTION**

We saw above that
$$
1/5 = 2^{-3} * (1.10011001100…)_2 \approx 2^{-3} * (1.1001100110)_2
$$
where the $\approx$ is rounded to the nearest 10 bits (in this case rounded down).
We write $-3 = 12 - 15$
hence we have $q = 12 = (01100)_2$.  

Adding `1` we get:
$$
1 + 2^{-3} * (1.1001100110)_2 = (1.001100110011)_2 \approx (1.0011001101)_2 
$$
Here we write the exponent as $0 = 15 - 15$ where $q = 15 = (01111)_2$. 
Thus we get: $0011110011001101010$.  

&nbsp;  

**Problem 4.5** Explain why $F_{16}(0.1)/(F_{16}(1.1)-1)$ does not return 1. Can you compute the bits explicitly?  

&nbsp;  