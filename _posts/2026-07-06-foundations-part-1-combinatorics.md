---
layout: post
title:  "Foundations, Part I: Counting and Combinatorics"
date:   2026-07-06 10:30:00 +0000
categories: [foundations, mathematics]
tags: [combinatorics, counting, probability]
---

# Combinatorics
Combinatorics is the study of how to count *things* i.e. the various combinations, pemutations, subgroups that can be formed from a given set of objects/people etc.

- How many different ways we can sort three objects $[\square, \enspace \triangle, \enspace \star]$?

- How many times we can pick pair of balls from an urn that contains three different coloured balls; red, green, blue? etc.

- How many different outcomes are possible if you flip a coin four times?

- How many different full-house hands are there in poker? (Full house = three of one rank + two of another rank. For instance, e.g. `AAA KK` or `222 55` etc.)

- How many different committees of three people can be chosen from five people?
    - What if we additonally designate one person as the committee's president?

$\rhd$ Knowing how to count these type of things is critical for an understanding of probability, because when calculating the probability of a given event, we often need ti count the number of ways that event can happen. Note that throughout this book we will use that we are using the frequentist approach.

**Frequentist vs Bayesian approaches:** Note that we assuming frequentist approach throughout this book meaning that after the experiments/trials based on our initial assumption (i.e. probability of heads occuring is 0.5) is not going to be updated by using the data, which is the Bayesian approach. Here, in order to understand basics of the probability we are assuming we are using frequentist approach.

# Factorials
Before getting into the discussion of actual combinatorics and related concepts we first need to look at a certain quantity that comes up very frequently. This quantity is called the <u>factorial</u>.

Throughout this book when dealing with a situation that involves an intger value $N$, we often need to consider the product of the first $N$ integers:

$$
\begin{equation}
N! = N\times (N-1) \times (N-2) \cdots 1
\end{equation}
$$

For the few integers we have:

$$
\begin{align}
\begin{split}
0! &= 1 \\
1! &= 1 \\
2! &= 1 \times 2 = 2 \\
3! &= 1 \times 2 \times 3 = 6 \\
4! &= 1 \times 2 \times 3 \times 4 = 24 \\
5! &= 1 \times 2 \times 3 \times 4 \times 5 = 120 \\
6! &= 1 \times 2 \times 3 \times 4 \times 5 \times 6 = 720
\end{split}
\end{align}
$$

From above expression we can see some pattern, however, there are also some elements doesn't make as much sense. For instance,

$$
\begin{align}
\begin{split}
0! &= 1 \\
1! &= 1 \\
\end{split}
\end{align}
$$

why both $0!$ and $1!$ are equal to 1? 

<div class="callout callout-warn" markdown="1">
**Why the common proof for the 0!=1 is not valid?**

Generally, in some sources the $0! = 1$ is proven by using the following logic:

$$
\begin{align}
\begin{split}
&\text{The expression}\enspace 0! = 1 \enspace\text{because,}\enspace n! = n\cdot (n-1)! \\
&\text{If we take}\enspace n = 1,\enspace \text{then,}\enspace 1! = 1\cdot 0!\\
&\text{Thus,}\enspace 0! = 1
\end{split}
\end{align}
$$
However, above expression is invalid [3]. Why?
In order for $0! = 1$ expression to be meaningful both sides of this equality must be meaningful.
$$
\begin{align}
\begin{split}
&\text{If we take}\enspace n = 1,\enspace \text{then,}\enspace 1! = 1\cdot 0!\\
&\text{Here, the right hand side of the equality is undefined since,} \\
& 0! = \text{undefined}
\end{split}
\end{align}
$$
Consequently, we can infer that the equality $0!=1$ is not valid for the $n=1$ case.

</div>

Let's take an alternative approach. From [2], we can see the following pattern,

$\rhd$ For $5!$, we need to multiply 5 integers,

$$
\begin{align*}
5! &= \underbrace{1 \times 2 \times 3 \times 4 \times 5}_{\text{multiply 5 consecutive integers}}
\end{align*}
$$

$\rhd$ For $4!$, we need to multiply 4 integers,

$$
\begin{align*}
4! &= \underbrace{1 \times 2 \times 3 \times 4}_{\text{multiply 4 consecutive integers}}
\end{align*}
$$

$\rhd$ For $3!$, we need to multiply 3 integers,

$$
\begin{align*}
3! &= \underbrace{1 \times 2 \times 3}_{\text{multiply 3 consecutive integers}}
\end{align*}
$$

$\rhd$ For $2!$, we need to multiply 2 integers,

$$
\begin{align*}
2! &= \underbrace{1 \times 2}_{\text{multiply 2 consecutive integers}}
\end{align*}
$$

$\rhd$ For $1!$, we need to multiply 1 integer,

$$
\begin{align*}
1! &= \underbrace{1}_{\text{ multiply 1 consecutive integers}}
\end{align*}
$$

$\rhd$ For $0!$, we need to multiply 0 integer,

$$
\begin{align*}
0! &= \underbrace{\phantom{1 \times 2 \times 3}}_{\text{multiply 0 consecutive integers}}
\end{align*}
$$

How are we meant to multiple 0 integer?

Let's look at other operations such as exponentiation

$$
\begin{align}
\begin{split}
3^5 &= \underbrace{3 \times 3 \times 3 \times 3 \times 3}_{\text{5 times}} = 243 \\
3^4 &= \underbrace{3 \times 3 \times 3 \times 3}_{\text{4 times}} = 81 \\
3^3 &= \underbrace{3 \times 3 \times 3}_{\text{3 times}} = 27 \\
3^2 &= \underbrace{3 \times 3}_{\text{2 times}} = 9 \\
3^1 &= \underbrace{3}_{\text{1 times}} = 3 \\
3^0 &= \underbrace{\phantom{3 \times 3}}_{\text{0 times}} = (?) \\
\end{split}
\end{align}
$$

How about if we look at the multiplication operation?

$$
\begin{align}
\begin{split}
3\times 5 &= \underbrace{3 + 3 + 3 + 3 + 3}_{\text{5 times}} = 15 \\
3\times 4 &= \underbrace{3 + 3 + 3 + 3}_{\text{4 times}} = 12 \\
3\times 3 &= \underbrace{3 + 3 + 3}_{\text{3 times}} = 9 \\
3\times 2 &= \underbrace{3 + 3}_{\text{2 times}} = 6 \\
3\times 1 &= \underbrace{3}_{\text{1 times}} = 3 \\
3\times 0 &= \underbrace{\phantom{3 + 3}}_{\text{0 times}} = (?) \\
\end{split}
\end{align}
$$

<div class="callout callout-warn" markdown="1">
**Important**

Because of the agreed definition/convention summing an integer 0 times has been defined as 0 [2].

$$\boxed{3 \times 0 = \underbrace{\vphantom{3 + 3}}_{\text{sum 3 zero times}} = 0}$$

Similarly, because of an agreed definition/convention for multplying an integer 0 times has been defined as 1.

$$\boxed{3^0 = \underbrace{\vphantom{3 \times 3}}_{\text{multiply 3 zero times}} = 1}$$

As a direct consequence of the above expression, the identity/natural element of the exponentiation operation becomes,

$$\boxed{0! = \underbrace{\;}_{\text{multiply zero consecutive integers}} = 1}$$

More generally, if an operation has an <u>identity element</u><sup>⋆</sup>, operating that specific operation on 0 integers is accepted **by convention** to yield that identity element.

<sup>⋆</sup> Identity/Natural element is an element that leaves unchanged every element when the operation is applied.
</div>

It is also important to note that as $N$ increases $N!$ gets large very fast

```matlab
N = 0:20;
factorialVec = zeros(size(N));
dFactorialVec = NaN(size(N));

% Factorial values
for i = 1:length(N)
    n = N(i);
    factorialVec(i) = factorial(n);
end

% Finite difference values
for j = 2:length(N)-1
    % Forward difference: (f[x+1] - f[x]) / ((x+1) - x) =  f[x+1] - f[x]
    dFactorialVec(j) = factorialVec(j+1) - factorialVec(j);
end

figure;
semilogy(N,factorialVec,'o','MarkerSize',6)
hold on
semilogy(N,dFactorialVec,'*','MarkerSize',7)
hold off
grid on
xlabel('$N$',"Interpreter","latex")
legend({'$N!$','$\Delta(N!)$'},"Interpreter","latex","Location","northwest")
```
{% include code-output.html src="/assets/images/2026-07-06-foundations-part-1-combinatorics/factorial_growth.png" alt="N! growth with the Δ(N!)" %}

As we can see from the above figure that the $N!$ increases almost exponentially with $N$, where $5!=120$, $10!=3,628,800$, and $20!=2.4329e+18$, if we superimpose $10^N$ and $e^N$ exponential functions on the current figure we will have:
```matlab
N = 0:20;
factorialVec = zeros(size(N));
dFactorialVec = NaN(size(N));

% Factorial values
for i = 1:length(N)
    n = N(i);
    factorialVec(i) = factorial(n);
end

% Finite difference values
for j = 2:length(N)-1
    % Forward difference: (f[x+1] - f[x]) / ((x+1) - x) =  f[x+1] - f[x]
    dFactorialVec(j) = factorialVec(j+1) - factorialVec(j);
end

% Various functions for comparison
expFunction = @(x,k) x.^k;

figure;
semilogy(N,factorialVec,'o','MarkerSize',6)
hold on
semilogy(N,dFactorialVec,'*','MarkerSize',7)
semilogy(N,expFunction(exp(1),N),'-')
semilogy(N,expFunction(10,N),'-')
hold off
grid on
xlabel('$N$',"Interpreter","latex")
legend({'$N!$','$\Delta(N!)$','$e^N$','$10^N$'},"Interpreter","latex","Location","northwest")
```
{% include code-output.html src="/assets/images/2026-07-06-foundations-part-1-combinatorics/factorial_growth_2.png" alt="N! and Δ(N!) compared to e^N and 10^N" %}

As we can see from the above figure that the permutation is increasing very rapidly, in fact $N!$ grows faster than much faster than $e^N$ also even faster than $10^N$.

# Permutations
Now we have a very basic understanding of how counting and numbers are working, we can focus on calculating number of ways things are happenning. More specifically, a <u>permutation</u> of a set of objects is a way of ordering them.

For example, if we have three people; Alice (A),  Bob (B), and Carol (C), then some permutations are $(\mathrm{A}-\mathrm{B}-\mathrm{C})$, $(\mathrm{A}-\mathrm{C}-\mathrm{B})$, $(\mathrm{C}-\mathrm{A}-\mathrm{B})$ etc.

It turns out that there are six permutations in total:

$$
\begin{split}
&(\mathrm{A}-\mathrm{B}-\mathrm{C}),~(\mathrm{A}-\mathrm{C}-\mathrm{B}) \\
&(\mathrm{B}-\mathrm{A}-\mathrm{C}),~(\mathrm{B}-\mathrm{C}-\mathrm{A}) \\
&(\mathrm{C}-\mathrm{A}-\mathrm{B}),~(\mathrm{C}-\mathrm{B}-\mathrm{A})
\end{split}
$$

Let's now investigate how can we order different number of objects to get some insights about how many total possibilities appear, and how to generalize the calculation to count them.

## One Object

For a single object, there is only one way to arrange it, $P_1=1$.

$$
(A)
$$

{% include figure.html src="/assets/images/2026-07-06-foundations-part-1-combinatorics/one_object.svg" alt="Ordering one object." caption="Fig. 1 Number of permutations for one object." %}

## Two Objects
When we have two object $A$ and $B$ we can order them in 2 different ways,$P_2=2$:

$$
(A,B)
(B,A)
$$

{% include figure.html src="/assets/images/2026-07-06-foundations-part-1-combinatorics/two_objects.svg" alt="Ordering two objects." caption="Fig. 1 Number of permutations for two objects." %}

## Three Objects
## Four Objects

# Combinations

# References
[1] Morin, David J. Probability: For the Enthusiastic Beginner. CreateSpace Independent Publishing Platform, 2016.

[2] Ali Nesin, 0! (Sıfır Faktöriyel) Neden 1'e Eşittir? (Why zero factorial 0! equals to zero?) URL: [https://youtu.be/i5gxEhNDYls?si=DQIWMxDdY2-MzJK8](https://youtu.be/i5gxEhNDYls?si=DQIWMxDdY2-MzJK8) (Accessed: 08-07-2026)

[3] Ali Nesin, 0!=1'in Önerilen Kanıtları Neden Yanlış  (Why is the proposed solutions for 0!=1 are wrong?)[https://youtu.be/T97dGFB7dww?si=u9IYBCfF-vtZEz-v] (Accessed: 15-07-2026)
