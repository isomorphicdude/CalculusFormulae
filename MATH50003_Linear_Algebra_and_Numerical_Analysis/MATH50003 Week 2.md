## Finite Difference
### Goal
Approximate $\frac{f(x+h)-f(x)}{h}$

Recall Taylor's series with remainder term up to 2 (including 2 remainder)
the $\frac{f''(t)h^2}{2! \ h}$ is the absolute error

### Difficulty
Numerical instability in floating point arithmetic  

examples: f=1+x+x^2 works well but going above significant bits yields 0
g=1+x/3+x^2
choose small h as above being 2^-5 good for first one  
Both converges at first but start exploding   

(computations for the f above)

**case1** n between 1 and S/2, (S no of mantissa), exact computation but with error
**case2** $\frac{S}{2}<n\leq S$  last term of high power gets dropped so exact in this case with no error
**case3** $n>S$ all powers get dropped only 1 left so error is 1

### Solution

Would like to find optimal point  
Error of  a function at a point 
use Taylor to evaluate and bound
**Heuristic** to balance error choose Mh =4c/h \epsilon
h is approx. sqrt(\epsilon)

## Differentiation with Dual Numbers
Take $a+b\epsilon$, where $\epsilon ^2=0$.  

For any polynomial 
$$p(a+b\epsilon)=p(a)+bp'(a)\epsilon$$

Thus for any other functions, express them using Taylor and differentiate term by term

### Dual Extension
If 
$$f(a+b\epsilon)=f(a)+bf'(a)\epsilon$$  then such functions are called dual extensions at $a$.

**Product and Chain rule still holds** for dual extensions, so can differentiate all common functions. 