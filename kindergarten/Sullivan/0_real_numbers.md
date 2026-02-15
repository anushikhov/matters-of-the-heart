## Sets    
  
## Classification of Numbers    
  
Each time we expand a number system, such as from the whole numbers to the integers, we do so in order to be able to handle new, and usually more complicated, problems.    
  
Every irrational number may be represented by a decimal that neither repeats nor terminates.    
  
Irrational numbers occur naturally. Consider the isosceles right triangle whose legs are each of length 1. The length of the hypotenuse is root 2, an irrational number. Also, the number that equals the ratio of the circumference to the diameter of any circle, denoted by the symbol π is an irrational number.    
  
Together, the rational numbera and the irrational numbers form the set of **real numbers.**    
  
```     
Real Numbers    
     |         
     |         
--------------------------------------------     
|                                           |     
|                                           |     
Rational Numbers                            Irrational Numbers      
|                                               
|                                             
|                                             
-----------------------         
|                      |     
|                      |     
Integers               Fractions        
|                           
|                           
------------------------     
|                      |      
|                      |    
Whole Numbers          Whole Negative Numbers     
|                          
|                        
------------------------     
|                      |     
|                      |    
Counting Numbers       Zero        
```     
  
## Approximations    
  
Every decimal may be represented by a real number and every real number may be represented by a decimal.  
  
A **decimal** means a base-10 expansion like _±a₀.a₁a₂a₃..._ where _a₀_ is an integer and each _aₖ_Є{1,2,...,9}. It can be **finite** or **infinite**.    
  
**Every decimal represents a real number**     
  
Take a decimal _a₀.a₁a₂a₃..._ and interpret it as the infinite sum _x = a₀ + a₁/10 + a₂/10² + a₃/10³ + ... = a₀ + ∑ₖ᪲₌₁aₖ10⁻ᵏ_.       
  
This sum always converges, because it's bounded by a geometric series:     
```math    
0 \leqslant _sum_{k=1}^{\infty} a_k \, 10^{-k} \leqslant _sum_{k=1}^{\infty} 9 \cdot 10^{-k} = 1.    
```     
So the fractional tail is a well-defined real number, and adding the integer part _a₀_ (and possibly a minus sign) still gives a real number.     
  
Every (possibly infinite) deciaml expansion corresponds to a real number.     
  
**Every real number can be represented as a decimal**    
  
--------------------------------------------------------------------------------------------------------------------------------------------     
# Real numbers and decimal expansions (base 10)

We prove:

1. **Every (possibly infinite) decimal expansion represents a real number.**
2. **Every real number has a decimal expansion.**

We also explain the **non-uniqueness** phenomenon (e.g. `0.999… = 1.000…`) and what is **implicitly used** about limits and completeness.

Everything below is in base 10, but it generalizes to any base $b\ge 2$.

---

## 0) What we mean by a decimal expansion

A (base-10) decimal expansion is a symbol of the form

$$
\pm a_0.a_1a_2a_3\ldots
$$

where $a_0\in\mathbb Z$ and each $a_k\in\{0,1,\dots,9\}$.

Define the **$n$-th truncation** (a rational number) by

$$
x_n := \pm\left(a_0 + \sum_{k=1}^{n} a_k 10^{-k}\right).
$$

(If the sign is $+$, we omit it.)

The intended value of the infinite decimal is the limit (if it exists)

$$
x := \lim_{n\to\infty} x_n.
$$

So the analytic question is: **does $(x_n)$ always converge?**

---

## 1) Every decimal expansion represents a real number

### Theorem 1 (Decimal $\Rightarrow$ Real)

For any digits $a_0\in\mathbb Z$ and $a_k\in\{0,\dots,9\}$, the sequence

$$
x_n = a_0 + \sum_{k=1}^n a_k 10^{-k}
$$

converges in $\mathbb R$. Hence every infinite decimal expansion defines a real number

$$
a_0.a_1a_2a_3\ldots \;:=\; \lim_{n\to\infty} x_n \in \mathbb R.
$$

### Proof (Cauchy + completeness)

Consider only the fractional part

$$
s_n := \sum_{k=1}^n a_k 10^{-k}.
$$

For $m>n$,

$$
|s_m - s_n|
= \left|\sum_{k=n+1}^{m} a_k 10^{-k}\right|
\le \sum_{k=n+1}^{m} 9\cdot 10^{-k}
\le \sum_{k=n+1}^{\infty} 9\cdot 10^{-k}.
$$

Compute the tail bound (geometric tail):

$$
\sum_{k=n+1}^{\infty} 9\cdot 10^{-k}
= 9\cdot \frac{10^{-(n+1)}}{1-1/10}
= 9\cdot \frac{10^{-(n+1)}}{9/10}
= 10^{-n}.
$$

So for all $m>n$,

$$
|s_m - s_n|\le 10^{-n}.
$$

Thus $(s_n)$ is a **Cauchy sequence**. Since $\mathbb R$ is **complete** (every Cauchy sequence converges in $\mathbb R$), $(s_n)$ converges to some real $s$. Then $x_n = a_0 + s_n$ converges to $a_0+s$. $\square$

### What was implicit here?

The step “Cauchy $\Rightarrow$ convergent” is exactly **completeness of $\mathbb R$**. In an incomplete number system (like $\mathbb Q$), a Cauchy sequence might fail to converge *within that system*.

---

## 2) Every real number has a decimal expansion

### Theorem 2 (Real $\Rightarrow$ Decimal)

For each real number $x$, there exist digits $a_0\in\mathbb Z$ and $a_k\in\{0,\dots,9\}$ such that

$$
x = a_0 + \sum_{k=1}^{\infty} a_k 10^{-k},
$$

i.e. $x$ has a base-10 decimal expansion.

### Construction (digit-by-digit algorithm)

Let

$$
a_0 := \lfloor x \rfloor,\qquad r_0 := x-a_0 \in [0,1).
$$

For $n\ge 1$, define recursively

$$
a_n := \lfloor 10 r_{n-1}\rfloor \in \{0,1,\dots,9\},\qquad
r_n := 10r_{n-1}-a_n \in [0,1).
$$

Define truncations

$$
x_n := a_0 + \sum_{k=1}^n a_k 10^{-k}.
$$

### Key identity

For every $n\ge 0$,

$$
x = x_n + 10^{-n}r_n.
$$

#### Proof of the identity (induction)

For $n=0$, $x=x_0+r_0$ and $10^{0}r_0=r_0$, so $x=x_0+10^{-0}r_0$.

Assume $x=x_n+10^{-n}r_n$. Then

$$
x_{n+1}
= x_n + a_{n+1}10^{-(n+1)}.
$$

Also $r_{n+1}=10r_n-a_{n+1}$, hence

$$
10^{-(n+1)}r_{n+1}
=10^{-(n+1)}(10r_n-a_{n+1})
=10^{-n}r_n - a_{n+1}10^{-(n+1)}.
$$

Add this to $x_{n+1}$:

$$
x_{n+1}+10^{-(n+1)}r_{n+1}
= x_n + a_{n+1}10^{-(n+1)} + 10^{-n}r_n - a_{n+1}10^{-(n+1)}
= x_n + 10^{-n}r_n
= x.
$$

So the identity holds for all $n$. $\square$

### Convergence conclusion

Since $r_n\in[0,1)$,

$$
0 \le 10^{-n}r_n < 10^{-n} \to 0.
$$

From $x = x_n + 10^{-n}r_n$, this implies $x_n\to x$. Therefore the digits $(a_n)$ define a decimal expansion

$$
x = a_0.a_1a_2a_3\ldots
$$

in the sense that the truncations converge to $x$. $\square$

---

## 3) Non-uniqueness: why `0.999… = 1.000…`

Decimal expansions are **not always unique**. A number can have **two** base-10 expansions exactly when it has a terminating one.

Example:

$$
1.0000\ldots = 0.9999\ldots,\qquad
2.5000\ldots = 2.4999\ldots.
$$

Intuitively: “carrying” the final $1$ in a terminating decimal can be traded for an infinite tail of $9$’s.

---

## 4) Proofs that $0.999\ldots = 1$

Below are three proofs. They all rely on interpreting an infinite decimal as a **limit of truncations**.

### Proof A (via geometric series and partial sums)

Let

$$
x_n := 0.\underbrace{99\ldots 9}_{n\text{ digits}}.
$$

Then

$$
x_n = \sum_{k=1}^{n} 9\cdot 10^{-k}
= 9\sum_{k=1}^{n} 10^{-k}.
$$

Compute the finite geometric sum:

$$
\sum_{k=1}^{n} 10^{-k}
= \frac{\frac{1}{10}\left(1-\left(\frac{1}{10}\right)^{n}\right)}{1-\frac{1}{10}}
= \frac{1-10^{-n}}{9}.
$$

Hence

$$
x_n = 9\cdot \frac{1-10^{-n}}{9} = 1 - 10^{-n}.
$$

Taking limits:

$$
0.999\ldots
:= \lim_{n\to\infty} x_n
= \lim_{n\to\infty} (1-10^{-n})
= 1.
$$

$\square$

---

### Proof B (the “gap” goes to zero)

From above, $x_n = 1-10^{-n}$. So the difference from $1$ is

$$
1-x_n = 10^{-n}\to 0.
$$

Therefore $\lim x_n = 1$, i.e. $0.999\ldots = 1$. $\square$

---

### Proof C (“algebra with dots”, justified by limits)

Let $x := 0.999\ldots := \lim x_n$ where $x_n=0.\underbrace{99\ldots 9}_{n}$.

Then

$$
10x = \lim_{n\to\infty} 10x_n.
$$

But $10x_n = 9.\underbrace{99\ldots 9}_{n}$, so for every $n$,

$$
10x_n - x_n = 9.
$$

Take limits:

$$
\lim_{n\to\infty}(10x_n - x_n) = 9.
$$

Using limit laws (linearity),

$$
\lim_{n\to\infty}(10x_n - x_n)
= 10\lim_{n\to\infty}x_n - \lim_{n\to\infty}x_n
= 9x.
$$

So $9x=9$, hence $x=1$. $\square$

#### What’s implicit here?

We used:

- The definition $0.999\ldots := \lim x_n$.
- Limit laws:
  $$
  \lim (A_n\pm B_n)=\lim A_n \pm \lim B_n,\qquad
  \lim (cA_n)=c\lim A_n
  $$
  provided the limits exist.

That is why the familiar “subtract the repeating tails” argument is legitimate.

---

## 5) Summary of the logical structure

- A decimal expansion corresponds to truncations
  $$
  x_n = a_0 + \sum_{k=1}^n a_k 10^{-k}\in\mathbb Q.
  $$
- The infinite decimal is **defined** as $\lim x_n$.
- Theorem 1 proves $\lim x_n$ exists in $\mathbb R$ (Cauchy + completeness).
- Theorem 2 constructs digits for any $x\in\mathbb R$ so that $x_n\to x$.
- Uniqueness fails only in the trailing $000\ldots$ vs trailing $999\ldots$ cases.

---

## 6) Optional one-line formulation

There is a surjective map from digit sequences to real numbers, and if you identify the two representations ending in $000\ldots$ and $999\ldots$, it becomes a bijection.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------    
In practice, decimals are generally represented by approximations.  

In approximating decimals, we either round off or truncate to a given number of decimal places.  The number of places establishes the location of the final digit in the decimal approximation.  

**Truncation:** Drop all the digits that follow the specified final digit in the decimal.  
**Rounding:**  Identify the specified final digit in the decimal. If the next digit is 5 or more, add 1 to the final digit; if the next digit is 4 or less, leave the final digit as it is. Truncate following the final digit.   

## Calculators   

## Operators   

## Order of operations  

## Properties of Real Numbers  

1. The **reflexive property** states that a number always equals itself, that is _a = a_.  
2. The **symmetric property** states that if _a = b_ then _b = a_.  
3. The **transitive property** states that if _a = b_ and _b = c_ then _a = c_.  
4. The **principle of substitution** states that if _a = b_ then we may substitute _b_ for _a_ in any expression containing _a_.  
5. **Commutative property:** _a + b = b + a_, _a * b = b * a_  
6. **Associative properties:** _a + (b + c) = (a + b) + c = a + b + c_, _a * (b * c) = (a * b) * c = a * b * c_   
7. **Distributive property:** _a * (b + c) = a * b + a * c_, _(a + b) * c = a * c + b * c_  
8. **Identity properties:** _0 + a = a + 0 = a_, _a * 1 = 1 * a = a_  
9. **Additive inverse property:** _a + (-a) = -a + a = 0_  
10. **Multiplicative inverse property:** _a * 1/a = 1/a * a = 1   if a ≠ 0_   
   
The multiplicative inverse _1/a_ of a nonzero real number _a_ is also referenced as the **reciprocal** of _a_.  

The **difference** _a - b_, is defined as _a - b = a + (-b)_   

If _b_ is a nonzero real number, the **quotient** _a/b_, is defined as _a/b = a * 1/b   if b ≠ 0._   

Multiplication by Zero:  _a * 0 = 0_   

**Division by zero is not defined.**  

Division properties: _0/a = 0, a/a = 1 if a ≠ 0_  

Rules of signs: _a(-b) = -(ab), (-a)b = -(ab), (-a)(-b) = ab, -(-a) = a, a/(-b) = (-a)/b = -(a/b), (-a)/(-b) = a/b_   

Cancellation properties: ac = bc implies a = b if c ≠ 0, ac/bc = a/b if b ≠ 0, c ≠ 0  

**Zero-product property**  
If _ab = 0_, then _a = 0_ or _b = 0_, or both.  

Arithmetic of quotients:  
_a/b + c/d = ad/bd + bc/bd = (ad + bc)/bc if b ≠ 0, d ≠ 0_  
_a/b * c/d = ac/bd  if b ≠ 0, d ≠ 0_   
_(a/b)/(c/d) = (a/b) * (d/c) = ad/bc  if b ≠ 0, c ≠ 0, d ≠ 0_   

Sometimes it is easier to add two fractions using  _least common multiples_ (LCM).   
**The LCM of two numbers is the smallest number that each has as a common multiple.**    

The LCM of 15 and 12: to find the LCM of 15 and 12, we look at multiples of 15 and 12.   
15: 15, 30, 45, **60**, 75, 90, 105, 120, ...  
12: 12, 24, 36, 48, **60**, 72, 84, 96, 108, 120, ...  




