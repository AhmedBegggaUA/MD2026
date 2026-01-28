# Probability  
Pierre Simon (Marquis of Laplace) in [A Philoshopical Essay on Probabilities](https://www.informationphilosopher.com/solutions/scientists/laplace/probabilities.html) comments: 

*Present events are connected with preceding ones 
by a tie based upon the evident principle that a thing 
cannot occur without a cause which produces it.*

This leads us directly to "chance", i.e. we are talking about the "likelihood" of an event *in the future* based on the present knowledge (also quoting [The Feynmann Lectures on Physics](https://www.feynmanlectures.caltech.edu/I_06.html)). 

Actually, <span style="color:#469ff8">**probability can be described as** the quantification of chance</span>. In **discrete probability** we talk about a set $\Omega$ (the **sample set**) containing all the possible **atomic events**. Some examples: 

$
\begin{align}
\Omega_1 &= \{H,T\}\; & \text{Results of tossing a coin: Head (H), Tail (T)}\\
\Omega_2 &= \{1,2,\ldots,6\}\; & \text{Results of playing a dice of 6 faces}\\
\Omega_3 &= \{\omega_1,\ldots,\omega_{52!}\} & \text{Ways of shuffling a standard deck of 52 cards}\\
\Omega_4 &= \{\omega_1,\ldots,\omega_{N_{mn}}\} & \text{Number of paths in a grid}\\
\end{align}
$ 

Note that sometimes we can *explicitly name* the atomic events but some other times we can only *enumerate* how many of them do we have. Anyway, in discrete probability we are always **playing with countings**. 


<span style="color:#469ff8">Actually, the probability of a particular event is the ratio between two counts:</span>
- <span style="color:#469ff8">The number of **favorable** cases (to that event). </span>
- <span style="color:#469ff8">The number of **all cases**.</span>

For atomic events, their probability is simply $1/|\Omega|$. However, an event is any proposition that can be evaluated to true or false with a certain probability, such as: "playing a dice returns an even value with probability $3/6$". In this case, the event "even" is not atomic, but a subset $A\subseteq \Omega$, where $A=\{2,4,6\}$, i.e. the elements in $\Omega$ that satisfy the logical proposition "return an even value". We formalize this as follows: 

$$
p(A) = \frac{|A|}{|\Omega|}\;.
$$

**Axioms of Probability**. Given an atomic event $\omega\in\Omega$, its probability $p(\omega)$ is a function $p:\Omega\rightarrow [0,1]$ satisfying: 

$
0\le p(\omega)\le 1\; \text{and}\; \sum_{\omega\in\Omega}p(\omega) = 1\;.
$

In addition for **non-atomic events** $A$ we have: 

$
p(A) = \sum_{\omega\in A} p(\omega)= \sum_{\omega\in \Omega} p(\omega)[\omega\in A]\;,
$

where $p(\omega)[\omega\in A]$ reads: $p(\omega)$ if $\omega \in A$ and $0$ otherwise. 

Finally, for a countable sequence of **disjoint** events $A_1,A_2,\ldots$ we have the following axiom:

$
p\left(\bigcup_{i=1}^{\infty} A_i\right) = \sum_{i=1}^{\infty} p\left(A_i\right)\;.
$

which is a consequence of the PEI. Actually, if the events are not disjoint we have to consider the full definition of the PEI (excluding-including interesections).

**More properties**. As a result of the aforementioned axioms, we have: 

$
p(\emptyset) = 0\; \text{and}\; p(\Omega) = 1\;.
$

However, $\emptyset$ may be not the only event with probability zero. Actually: 

$
p(\bar{A}) = 1 - p(A)\; \text{(complement)}\; \text{and}\; A\subseteq B\Rightarrow p(A)\le p(B)\;\text{(monotonicity)}\;
$

Finally, we have the *binary* PEI: 

$
p(A\cup B) = p(A) + p(B) - p(A\cap B)\;.
$


## Independent Trials 
### Coins and dices
Events can be seen as the output of a given experiment. One of the most simplest experiments is *tossing a coin*. There are two possible outputs $\Omega=\{H,T\}$. If the coin is *fair*, each of these outputs is *equiprobable* or *equally likely to happen*: $p(H) = p(T) = 1/2$. 

Now assume that the coin experiment can be repeated $n$ times **under the same conditions**. Each of these repetitions is called a **trial**. So, a natural question to answer is <span style="color:#469ff8">"what is the probability of obtaining, say $k$ heads after $n$ trials?"</span>. We can use combinatory to answer to this question. Actually, the solution is: 

$$
P(n,k) = \frac{n\choose k}{2^n}\;.
$$

The number of *total cases* is $2^n$. If we assign $1$ to $H$ and $0$ to $T$, we have $2^n$ possible numbers of $n$ bits (permutations with repetition) and each of these numbers concatentates the results of $n$ trials. In addition, only ${n\choose k}$ cases are *favorable* since we have  ${n\choose k}$ groups of $k$ heads in $n$ trials. 

Actually, we can better understand the above rationale by reformulating $P(n,k)$ as:

$$
P(n,k) = {n\choose k}\left(\frac{1}{2}\right)^n\;.
$$

This means that the probability of any trial is $1/2$ and all the $n$ trials are **independent**. Intuitively, statistical independence means that a trial does not influence the following one (same experimental conditions for any trial). More formally, $n$ events $A_1, A_2,\ldots, A_n$ are independent if 

$$
P(A_1\cap A_2\cap\ldots \cap A_n) = p(A_1)p(A_2)\ldots p(A_n) = \prod_{i=1}^np(A_i)\;.
$$

Then, the probability of obtaining a given sequence say $HHHTT$ ($n=5$) is 

$$
p(HHHTT) = p(H)p(H)p(H)p(T)p(T)=\frac{1}{2}\cdot\frac{1}{2}\cdot\frac{1}{2}\cdot\frac{1}{2}\cdot\frac{1}{2} = \frac{1}{2^5}=\frac{1}{32}\;.
$$

Actually, all sequences with $n=5$ are equiprobable. However, what makes $HHHTT$ different from the others is the fact that *we have $3$ $H$s (and consequently $5-3=2$ heads)*. If we want to highlight this fact, we should *group* all sequences of $n=5$ trials having $3$ $H$s (or equivalently $2$ $T$s). Some hints:
- *Order matters*. Strictly speaking, sequences such as $HHHTT$ and $TTHHH$ should count twice. Since $H$ and $T$ can be repeated (three times and twice respectively). we have **permutations with repetition**:

$$
P_{\sigma}(n) = \frac{n!}{n_1!n_2!}\;\text{where}\; n=5, n_1 = k, n_2=n-k\; 
$$

- However, we know that 

$$
P_{\sigma}(n) = \frac{n!}{n_1!n_2!} = \frac{n!}{k!(n - k)!} = {n\choose k}
$$

This is where the combinations come from: we have $n=5$ positions and we need to fill $3$ of them (order does not matter) with heads. Then, we have ${5\choose 3}$ ways of doing it. It works because the strings $11100$ and $00111$ represent different subsets of $\{0,1\}^{5}$ and what combinations do is to encode subsets (members of the power set). 

Therefore, we have used the product rule to decompose the problem in two parts:
- Compute the probability of a configuration: $p(HHHTT)$. 
- Compute how many different configurations do you have: ${5\choose 3}$.

Then, the probability $p(\#H=3,5)$ of having $3$ heads in $5$ trials is: 

$$
p(\#H=3,5) = {5\choose 3}p(HHHTT) = {5\choose 3}\frac{1}{32} = \frac{10}{32}\;.
$$

In practice, use permutations with repetitions instead of combinations when the outcomes of a experiment are more than $2$. We illustrate this case in the following exercise. 

<span style="color:#347fc9">**Exercise**. Consider the problem of throwing a dice $n=6$ dices simultaneously. What is the probability of obtaining different results? And all equal? 
</span>

<span style="color:#347fc9"> This is equivalent to $n$ independent dice trials. Since $|\Omega|=6$, we have that $p(i)=1/6$ for $i=1,2,\ldots,6$. Therefore, the probability of a given sequence of $n$ trials is $(1/6)^n$. This is the first factor of the product rule (the probability of a given configuration). 
</span>

<span style="color:#347fc9"> The second factor (the number of possible configurations) comes from realizing that each of the $n$ positions can be filled by different values. Since order matters, we have to count the number of permutations *without repetition* or *permutations with individual repetition* (the elements must be different) of $n$ elements. This leads to $n!$ and 
</span>
<br></br>
<span style="color:#347fc9">
$
p(\text{All_diff.}) = n!\frac{1}{6^n} = \frac{n!}{1!1!1!1!1!1!} = \frac{6!}{6^6} =\frac{6}{6}\cdot\frac{5}{6}\cdot\frac{4}{6}\cdot\frac{3}{6}\cdot\frac{2}{6}\cdot\frac{1}{6} = 0.015\;.
$
</span>
<span style="color:#347fc9"> However, there are $n=6$ configurations where all the dices give the same result:
</span>
<span style="color:#347fc9">
$
p(\text{All_equal.}) = \frac{n}{6^n} = \frac{1}{6^5} = 0.0001\;. 
$
</span>

### The Binomial distribution 
#### Unimodality
As we have seen in the previous section, when performing $n$ independent trials, the odds of some events are higher that those of others. In particular, **extremal events** $E$ such as maximizing (or minimizing) the appearance of one of the elements of $\Omega$ have the smallest probability. However, since the probabilities of all events add $1$, the bulk of the *probability mass* should lie in non-extremal events.
  
In order to see that, we revisite coin tossing, where the two extremal events are $E=\{\text{All_}Ts, \text{All_}Hs\}$, both with probability $1/2^n$. Then, we have

$$
P(\text{All_}Ts) = {n\choose 0}\frac{1}{2^n} = {n\choose n}\frac{1}{2^n} = P(\text{All_}Hs) = \frac{1}{2^n}\;.
$$

As a result, the probability of non-extremal events becomes almost $1$ as $n$ grows since: 

$$
P(\bar{E}) = 1 - P(E) = 1 - \frac{2}{2^n} = \frac{2^n - 2}{2^n} = \frac{2(2^{n-1} - 1)}{2^n} = \frac{2^{n-1}-1}{2^{n-1}}\;.
$$

Being all the particular configurations equiprobable (i.e. $1/2^n$), the fact that $\lim_{n\rightarrow\infty}P(\bar{E}) = 1$ is due to the number that each particular configuration is repeated.  

A closer look to $2^n = {n\choose 0} + {n\choose 1} + {n\choose 2} + \ldots + {n\choose n}$ gives us the answer. The probability of having $k$ $H$s becomes:

$$
P(n,k) = \frac{{n\choose k}}{{n\choose 0} + {n\choose 1} + {n\choose 2} + \ldots + {n\choose n}}\;,
$$
 and due to the symmetry of ${n\choose k} = {n\choose n-k}$, this probability is going to grow from $k=0$ until a given $k=k_{max}$ and then decrease for $k=n$. Actually: 
 - If $n$ is even, $k_{max} = \frac{n}{2}$ and ${n\choose 0}<{n\choose 1}<\ldots <{n\choose \frac{n}{2}}>{n\choose \frac{n}{2}+1}>\ldots>{n\choose n}$.
 - If $n$ is odd, $k_{max} = \frac{n-1}{2}=\frac{n+1}{2}$ and ${n\choose 0}<{n\choose 1}<\ldots <{n\choose \frac{n-1}{2}}={n\choose \frac{n+1}{2}}>{n\choose \frac{n}{2}+1}>\ldots>{n\choose n}$.

 That is, for $n$ odd we have a double maximum of probability. Anyway the **distribution of probability** among the values $k=0,1,\ldots,n$ is **unimodal**. In addition, the increase of probability from $k-1$ to $k$ before the maximum is given by

 $$
 {n\choose k} = \frac{n!}{k!(n-k)!} = \frac{n-(k-1)}{k}\frac{n!}{(k-1)!\underbrace{(n-(k-1))(n-k)!}_{[n-(k-1)]!}} = \frac{n-(k-1)}{k}{n\choose k-1}
 $$

 i.e.

 $$
 \frac{{n\choose k}}{{n\choose k-1}} = \frac{n-(k-1)}{k}\;.
 $$
 
 These properties can be better understood by studying the Pascal's triangle. 


#### Pascal's Triangle
The [Pascal's Triangle](https://en.wikipedia.org/wiki/Pascal%27s_triangle) has had many names along the history of mathematics (e.g. Tartaglia Triangle). This construction gives the ${n\choose k}$ for all $n$. For instance, {numref}`HT`, each column denotes a value of $n$ and the coefficients in this column are the $n+1$ so called **binomial coefficients** for such $n$: ${n\choose 0},{n\choose 1},\ldots, {n\choose n}$.  


 ```{figure} ./images/Topic2/HT.png
---
name: HT
width: 600px
align: center
height: 500px
---
Binomial coefficients. 
```
The triangle is constructed as follows:
- Start by $n=0$ and make a trial. We have ${1\choose 0}=1$ ways of obtaining a $H$ and ${1\choose 1}=1$ ways of getting a $T$. Then set $n=1$.
- From $H$ we have again $1$ way of getting a H and one way of getting a $T$. However, this also happens from $T$. Therefore, after the second experiment we have $4$ possible outcomes: $HH, HT, TH, TT$. Two of these outcomes are extreme event and two of them collapse in the same representation $HT,TH$ (two ways of getting one $H$ and one $T$). This is way the central node has a value $2$. 
- Then, we set $n=2$ and continue... 

Some properties: 
- As noted above, even columns do have a unique maximual coefficients, whereas odd columns have two.
- If the normalize the $n-$th column by $2^n$ we have the **discrete probability distribution** asociated to having $k=0,1,2,\ldots,n$ heads $H$s.
- **Extreme events** are always placed (by symmetry) in the main diagonals. 
- **Non-extreme** or **regular** events begin to fill the distributions as $n$ increases. 
- The coefficients of any **regular event** can be obtained by adding those of their parents in the tree, since: 

$$
{n\choose k} = {n-1\choose k-1} + {n-1\choose k}\;.
$$

- The binomial coefficient in a node gives the **number of paths** that reach that node from the origin (equivalent to $\#\Gamma$ in a grid without obstacles). We will come back to this fact later on. 

- As $n$ increases, it becomes more and more clear that the **Binomial probability distribution** is centered on $n/2$, where the probability is maximal and then decreases to two tails corresponding to the extremal events. This allows us to intuitively understand the concept of **mean value**, as we will define later on. 

See for instance {numref}`Bern`, where we highlight the binomial coefficients after $n=8$ trials. Check that the highest coefficient at level $n=8$ is at position $n/2$ (starting by $0$).

 ```{figure} ./images/Topic2/Bernouilli.png
---
name: Bern
width: 600px
align: center
height: 600px
---
Binomial coefficients. 
```
Let us express all these things in probabilistic terms! 

#### Probable values and fluctuations
One of the magic elements behind the Pascal's triangle is that it provides the binomial coefficients, independently of whether we have a **fair coin** or not. 

The fair coin is a *particular case* where the **probability of success** in an independent trial (called **Bernouilli trial**) is $p=1/2$ (herein, we understand success as "landing on a head"). Consequently, the **probability of failure** ("landing on a tail") is $q = 1 - p = 1/2$. Then, the probability of $k$ successes after $n$ trials is more generally given by 

$$
P(n,k)  = {n\choose k}p^k(1-p)^{n-k} = {n\choose k}p^kq^{n-k}\;.
$$

Then, $P(n,k)$ is the **probability** of having $k$ successes out of $n$ trials. This is the solid line in {numref}`PD`, where we have performed $10,000$ games, each one with $n=1,000$ and $p=1/2$. In the $x$ axis we place $k=0,1,\ldots,n$ (the leaves in {numref}`Bern` for $n=1,000$). In the $y$ axis we plot (solid line) the **theoretical** $P(n,k)$ vales. But we also plot (idealy) a bar per $k$ value. <span style="color:#469ff8">The height of the bars is similar to $P(n,k)$ but it is not identical. Why?</span> Because we have performed $10,000$ games. The height of bar $k$ $\times$ $10,000$ is the number of games where we have obtained $k$ heads out of $n=1,000$ trials. This number (called the **observed number** of successes) is close to $10,000\cdot P(n,k)$ but it **fluctuates** around it(sometimes it is larger and sometimes it is lower). 

 ```{figure} ./images/Topic2/PD.png
---
name: PD
width: 700px
align: center
height: 600px
---
Theoretical probability vs fluctuations. 
```

Obviously, the **most likely** or most probable value of $k$ is $n/2=500$. However, it is not so obvious why the $k$s with smallest nonzero $P(n,k)$ are close to $440$ and $560$. Intuitively, this is related to the extremal events, but these values deserve a deeper mathematical interpretation. 

#### Expectation and variance 

**Random variables**. In the above example, each of the $10,000$ experiments consists of $n=1,000$ independent trials, each one resulting in landing either in $H$s or $T$s with probability $p$. Then the **sample space** $\Omega$ is $\{H,T\}^{n}$. Well, <span style="color:#469ff8">a *random variable* $X$ is a function $X:\Omega\rightarrow\mathbb{R}$: $X(\omega), \omega\in\Omega$</span> , such as the *number of $H$s*. This is indicated by $X(\omega)=k$, and $X\sim B(n,p)$ indicates that $X$ *follows* a Bernouilli or Binomial distribution.

**Expectation**. The expectation of a random variable $X$ is defined as follows: 

$$
E(X) = \sum_{\omega\in\Omega}X(\omega)\cdot p(w)= \sum_{x}x\cdot p(X=x)\;.
$$

For $X\sim B(n,p)$, we have: 

$$
\begin{align}
E(X) &= \sum_{k=0}^n k\cdot P(n,k)\\
     &= \sum_{k=0}^n k\cdot {n\choose k}p^{k}(1-p)^{n-k}\\
     &= \sum_{k=0}^n n{n-1\choose k-1}p^{k}(1-p)^{n-k}\;\text{since}\;k{n\choose k} = n{n-1\choose k-1}\\
     &= n\sum_{k=0}^n{n-1\choose k-1}p^{k}(1-p)^{n-k}\\
     &= np\sum_{k=1}^n{n-1\choose k-1}p^{k-1}(1-p)^{(n-1)-(k-1)}\\
     &= np\sum_{r=0}^{n-1}{n-1\choose r}p^{r}(1-p)^{(n-1)-r}\;\text{with}\; r=k-1\\
     &= np\;\text{due to the Binomial Theorem}\;.
\end{align}
$$

**The Binomial Theorem**. Newton's binomial theorem is behind the Pascal's triangle and the Binomial distribution. It basically states that the coefficients of expanding $(x+y)^n$, where $n$ is an integer, are the binomial coefficients ${n\choose k}$, as follows: 

$$
\begin{align}
(x+y)^n &= \sum_{j=0}^{n}{n\choose j}x^{n-j}y^{j}\\
        &= {n\choose 0}x^n + {n\choose 1}x^{n-1}y + {n\choose 2}x^{n-2}y^2 + \ldots + {n\choose n-1}xy^{n-1} + {n\choose n}y^{n}\;.
\end{align}
$$

Let us observe the theorem for $n=0,1,2,\ldots.$
- For $n=0$, we have $(x+y)^0 = {n\choose 0}x^{0-0}y^{0} = 1$.
- For $n=1$, we have $(x+y) = {n\choose 0}x + {n\choose n}y = 1\cdot x + 1\cdot y$. 
- For $n=2$, $(x+y)^2 = {n\choose 0}x^2 +  {n\choose 1}xy + {n\choose 1}xy + {n\choose n}y^2 = 1\cdot x^2 + 2\cdot xy + 1\cdot y^2$.
- For $n=3$, $(x+y)^3 = {n\choose 0}x^3 +  {n\choose 1}x^2y + {n\choose 2}xy^2 + {n\choose 1}xy^2 + {n\choose n}y^3 = 1\cdot x^3 + 3\cdot x^2y + 3\cdot xy^2 + 1\cdot x^3$.

If you observe the coefficients, they are given by the levels $n=0,1,2,3,\ldots$ of the Pascal's Triangle! In other words, herein the **extremal events** are the unit coefficients of $x^n$ and $y^n$ respectively. Then, the corresponding ${n\choose k}$ coefficient of $x^{n-k}y^k$ is just indicating the corresponding product, i.e. how many $x$s and how many $y$s do we takein each term. 

As a result, the way it is built the Pascal's triangle plays a fundamental role in the **inductive proof** of the theorem. Simply remind the expression $
{n\choose k} = {n-1\choose k-1} + {n-1\choose k}\;.$. 

Anyway, <span style="color:#469ff8">coming back to the expectation of $E(X) = np$, just apply the theorem expressing $p^{r}(1-p)^{(n-1)-r}$ as $p^{r}q^{(n-1)-r}$ for the binomial coefficient ${n-1\choose r}$</span>. All we are doing is computing $(x+y)^{n-1}$ where $x+y = p + q = 1$. As a result: 

$$
\sum_{r=0}^{n-1}{n-1\choose r}p^{r}q^{(n-1)-r} = (p + q)^{n-1} = 1^{n-1} = 1. 
$$

[//]: https://statproofbook.github.io/P/bern-var

**Variance**. The fact that when $X\sim B(n,p)$ we have $E(X)=np$ gives us directly the most likely number of successes (see {numref}`PD`). However, to explain the **amount of deviation from the expectation** we rely on the *variance* which is defined as follows: 

$$
Var(X) =  \sum_{x}(x - E(X))^2\cdot p(X=x)\;.
$$

In this way, <span style="color:#469ff8">$Var(X)$ is the expectation of the square deviations from $E(X)$</span>: 

$$
\begin{align}
Var(X) &= E([X-E(X)]^2)\\
       &= E(X^2 + E(X)^2 - 2XE(X))\\
       &= E(X^2) + E(E(X)^2)-2E(XE(X))\\
       &= E(X^2) + E(X)^2 - 2E(X)E(X))\\
       &= E(X^2) + E(X)^2 - 2E(X)^2\\
       &= E(X^2) - E(X)^2\;.
\end{align}
$$

One interesting (and simple) way to compute $Var(X)$ for Binomial variables $X$ is to realize that $X\sim B(n,p)$ means that $X = \sum_{i=1}^nY_n$ where $Y_i\sim Bern(p)$,i.e. **Bernouilli variables** where the outcomes can be $1$ (success) or $0$ (failure). 

In particular, if $Y\sim Bern(p)$ we have: 

$$
E(Y) = \sum_{y}y\cdot p(Y=y) = 1\cdot P(Y=1) + 0\cdot P(Y=0) = p\;.
$$

Since $X$ is the sum of $n$ $Y_i$s: $E(X) = E(Y_1)+ E(Y_2)+ \ldots + E(Y_n)$. As <span style="color:#469ff8">the expectation of a sum is the sum of expectations (indepedently of whether the variables are independent or not)</span>, we have: 

$$
E(X) = E\left(\sum_{i=1}^nY_i\right) = \sum_{i=1}^n E(Y_i) = np\;.
$$

Now, for computing $E(Y^2)$, $Y\sim Bern(p)$, we do: 

$$
E(Y^2) = \sum_{y}y^2\cdot p(Y=y) = 1^2\cdot P(Y=1) + 0^2\cdot P(Y=0) = p\;.  
$$

As a result 

$$
Var(Y) = E(Y^2) - E(Y)^2 = p - p^2 = p(1 - p) = pq\;.
$$

Now exploit the fact that <span style="color:#469ff8">the variance of the sum is the sum of variances **when the variables are independent**</span>. As this is the case for $Y_i\sim Bern(p)$. Then we can calculate

$$
Var(X) = Var(Y_1 + Y_2 + \ldots + Y_n) = \sum_{i=1}^nVar(Y_i) = npq; 
$$

It is obvious that $Var(X)$ increases linearly with $n$. This simply means that the shape of the distribution (see {numref}`PD`) becomes wider and wider as $n$ increases. 

#### Fundamental inequalities
Extremal events have small probabilities. In $X\sim B(n,p)$ the probability decays from its maximum value (for $k=\lfloor np\rfloor$) until close-to-zero at the extremal events. Such a decay is somewhat described by $Var(X)$. However, we have to go deeper in order to characterize the **probability of rare events**. 

Firstly, we should measure how the probability decays as we move away from the  expectation. For this task, we rely again on looking $X\sim B(n,p)$ as the sum of $n$ Bernoulli trials $Y_i\sim Bern(p)$.

For $X = Y_1 + Y_2 + \ldots Y_n$, we have

$$
p(\sum_{i=1}^nY_i - E(X)) = p(X - E(X))
$$

**Hoeffding's theorem** bounds $p(X - E(X)\ge t)$ for $t>0$ and $X$ being the sum of $n$ independent variables $Y_i$ satisfying $a_i\le  Y_i\le b_i$ *almost surely* or a.s. (i.e. with probability $1$), as follows: 

$$
\begin{align}
p(X - E(X)\ge t)&\le \exp\left(-\frac{2t^2}{\sum_{i=1}^n(b_i-a_i)^2}\right)\\
p(|X - E(X)|\ge t)&\le 2\exp\left(-\frac{2t^2}{\sum_{i=1}^n(b_i-a_i)^2}\right)\;.
\end{align}
$$

This theorem, simply means that deviating $t$ units from $E(X)$, results in an **exponential decay**. This justifies the exponetial shape of the Binomial distribution as we move from $E(X)$ towards the extremal events! In particular, for this distribution, where $0\le  Y_i\le 1$ a.s.,  the Hoeffding's bounds are:   

$$
p(X - np\ge t)\le \exp\left(-\frac{2t^2}{n}\right)\;\;\; \text{and}\;\;\; p(|X - np|\ge t)\le 2\exp\left(-\frac{2t^2}{n}\right)\;.
$$

Interestingly, the exponential decay is attenuated by $n$: the larger $n$ the slower the decay since the distribution becomes flatter and flatter as $n$ increases. 

**Cumulative distribution**. So far, we have been focused on describing random variables in terms of characterizing $p(X=x)$ (*point-mass function* or pmf). However, sometimes it is useful to quantify the **bulk of the probability**, for instance between two extremal values $a<b$. For $X\sim B(n,p)$, we now that this bulk is almost $1$ (but not *almost sure* unless $n\rightarrow 1$, since extremal events exist). However, <span style="color:#469ff8">for $k:a\le k\le b$, what is the probability that the number of heads is "less or equal than k"?</span>

The usual way to answer this question is to calculate $p(X\le k)$: 

$$
p(X\le k) = \sum_{x\le k}p(X=k)\;.
$$

We can use the **Hoeffding's bound** to give an idea of this probability, since 

$$
\begin{align}
p(X\le k) &= 1 - p(X>k)\\
          &= 1 - p(X\ge k+1)\\
          &= 1 - p(X-np\ge (k+1)-np)\\
          &\ge\exp\left(-\frac{((k+1)-np)^2}{n}\right)\;.\\
\end{align}
$$

Actually, $p(X\le k)$ is much larger that the neg-exp. Interestingly, when $k\approx np$ (close to the expected value), $p(X\le k)\ge \frac{1}{n}$, but actually it is $p(X\le np)=1/2$ due to the symmetry of the distribution. Therefore, the Hoeffding's bound is a very **conservative bound**. 

**The Chernoff bound** is one of the tighest bounds for quantifying the probability of rare events. It is formulated as follows. If we have $n$ independent variables $Y_1,Y_2,\ldots, Y_n$ with $p(Y_i=1)=p_i$ and $p(Y_i=0)=1-p_i$, $X = \sum_{i=1}^nY_i$ has expectation $E(X) = \sum_{i=1}^np_i$ and we have: 

$$
\begin{align}
\text{(Lower tail)}\;\;\;\;\;\;\;\;\;\; & p(X-E(X)\le -\lambda)\le \exp\left(-\frac{\lambda^2}{2E(X)}\right)\\
\text{(Upper tail)}\;\;\;\;\;\;\;\;\;\; & p(X-E(X)\ge \lambda)\le \exp\left(-\frac{\lambda^2}{2(E(X)+\lambda/3)}\right)\;.\\
\end{align}
$$

[//]: https://mathoverflow.net/questions/348234/tail-bound-regime-for-binomial-distribution-in-concentration-paper

The above formulation of the Chernoff bound was proposed in the [Survey paper dealing with concetration inequalities](https://mathweb.ucsd.edu/~fan/wp/concen.pdf). Actually, we have:
- The lower tail bound holds for all $\lambda\in [0, E(X)]$ and hence for all real $\lambda\ge 0$.
- The upper tail bound, too, holds for all real $\lambda\ge 0$.

Note that this version of <span style="color:#469ff8">the Chernoff bound decays more slowly than the Hoeffding's bound since the denominator is dominated by $E(X)$</span>.

Let us now compute the probabilities for the tails in {numref}`PD`: $440$ and $560$. Since $E(X) = np = 500$, we have that $440-500 = -60$ and $560 - 500 = 60$, we set $\lambda = 60$. Then
-  $p(X-E(X)\le -\lambda)\le \exp\left(-\frac{60^2}{1000}\right) = 0.0027$.
-  $p(X-E(X)\ge \lambda)\le \exp\left(-\frac{60^2}{2(500+60/3)}\right) = 0.0031$.

So far, we have characterized the Binomial distribution (concept, expectation, variance and rare events). The Binomial distribution plays a fundamental role in the analysis of AI algorithms for discovering the best solution (whenever possible). These algorithm explore a tree in an "intelligent way". Before giving an intution of this point, let us introduce an <span style="color:#469ff8">important concept also related with probability and "exploration": the **random walk**</span>. In particular, we will focus at random walks under the Binomial distribution. 

#### Random walks 
Let us start by defining the following game:
- Put a traveler at $x=0$. 
- Toss a coin. 
  - If the result is head move right: $x = x + 1$. 
  - Otherwise, move left: $x = x - 1$. 
- Continue until arriving to $n$ tosses. 

[//]: https://mathoverflow.net/questions/272544/the-mean-square-distance-of-a-random-walk-from-the-origin

<span style="color:#469ff8">The above procedure describes a **one-dimensional random walk** through the $\mathbb{Z}$</span>. One of the purposes of this game is to answer the question: "How far the traveler gets on average?" 

A bit formally, the problem consist of finding the expectation of $Z$, the sum of $n$ independent events $Y_i$ with output either $+1$ or $-1$. For a fair coin, $E(Y_i) = 1\cdot p + (-1)\cdot p = 0$ and this implies that $E(Z)=E(\sum_{i=1}^n Y_i)= \sum_{i=1}^nE(Y_i)=0$. 

Actually, under fairness, we can also answer the question: <span style="color:#469ff8">"What is the probability of landing at a give integer $z$ after $n$ steps?"</span>. This can be done by simply quering the Pascal Triangle!
In other words, this problem is equivalent to placing the $\mathbb{Z}$ line on top on the Pascal's triangle and aligning $x=0$ with the top vertex of the triangle. We do that in {numref}`PascalZ`, for clarifying that: 

```{figure} ./images/Topic2/PascalZ.png
---
name: PascalZ
width: 700px
align: center
height: 700px
---
One-dimensional (fair) Random Walk over Pascal's Triangle. 
```


- The random walker (RW) may progress towards the left (negative), the right (positive) or coming back home (zero). Landing at a given integer $z$ is just the probability $P(z,n)$ of $z$ successes (if $z>0$) or failures (if $z<0$). 
- In {numref}`PascalZ`, we link $z\in\mathbb{Z}$ with nodes of the respective *first levels* where we have $z$ successes (failures), but this line do extend to nodes below them if this property is satisfied: "if we do not have $z$ successes (failures) yet, maybe we may have them later". This is basically the gambler's conflict! 
- However, in the long run it is expected that the gambler lands on $z=0$ (no win - no lose) if its wealth is large enough. This is because $E(Z) = 0$ is equivalent to $E(X)=np$ for $X\sim B(n,p)$. 
- Of course, the hope (land on $z>0$) or risk (land on $z<0$) is measured by the probability of extremal events as we explained above. 
- Logically, if extremal events do happen much more frequently than when predicted by the theory, one may think that the coin is loaded (not fair).

 
[//]: https://math.stackexchange.com/questions/1945113/expected-value-of-squared-sum-vs-square-of-expected-sum

**Regardless of direction**. We have seen that $E(Z) = 0$ (going forward and backwards is equally likely). However, what happens if we reformulate the original question as follows: "How far the traveler gets on average, **regardless of direction**?". Answering this question implies computing 

$$
E(Z^2)=E[(\sum_{i=1}^nY_i]^2)\;.
$$ 

Using the identity (for any $Z$ given by the sum of **independent identically distributed** or i.i.d. variables):

$$
Var(Z) = E(Z^2) - E(Z)^2\;.
$$

Hence, we have $Var(Z) = nVar(Y)$ since the variables $Y_i$ are i.i.d., so we proceed to measure 

$$
\begin{align}
Var(Y) &= E(Y^2) - E(Y)^2\\
E(Y^2) &= (+1)^2\cdot p + (-1)^2\cdot q = p + q = 1\;.\\
E(Y)^2 &= [(+1)\cdot p + (-1)\cdot q ]^2 = [p - q]^2\;.\\
\end{align}
$$ 

Since $p = q$ for a fair coin, we have $Var(Y) = 1$ and, a result $Var(Z)=E(Z^2)=n$. For instance, in {numref}`RWrand` we plot $100$ fair RWs for $n=10,000$. The darkness of the blueness of each walk is proportional to $Var(Z)=E(Z^2)$ (we have inverted this brightness wrt previous figures for better visualizing extremal paths). Note that most of the paths have "deviations" upper bounded by $\pm 3\sqrt{Var(Z)} = \pm 3\sqrt{n} = \pm 300$. 

```{figure} ./images/Topic2/RWrand.png
---
name: RWrand
width: 800px
align: center
height: 400px
---
One-dimensional (fair) Random Walk: deviations. 
```


[//]: https://stats.stackexchange.com/questions/32405/how-is-poisson-distribution-different-to-normal-distribution

[//]: https://www2.stat.duke.edu/courses/Spring12/sta104.1/Lectures/Lec6.pdf

#### The Normal distribution 
When $n\rightarrow\infty$, the combinatorial nature of $B(n,p)$ and its links with random walks can be described in a simpler way. The $B(n,p)$ in the limit becomes another distribution: the well-known *Normal* or *Gaussian* distribution. 

In this regard, we exploit the Stirling's approximation rewriten as 

$$
n!\approx \sqrt{2\pi n}\cdot n^n e^{-n}\;.
$$

We plug in this formula in the probability of $k$ successes, in order to approximate *all the factorials*: 

$$
\begin{align}
p(X=k) & = {n\choose k}p^kq^{n-k}\\
       & = \frac{n!}{k!(n-k)!}p^kq^{n-k}\\
       & \approx \frac{\sqrt{2\pi n}\cdot n^n e^{-n}}{\sqrt{2\pi k}\cdot k^k e^{-k}\sqrt{2\pi (n-k)}\cdot (n-k)^{(n-k)} e^{-(n-k)}}p^kq^{n-k}\\
       & \approx \frac{\sqrt{2\pi n}\cdot n^n e^{-n}}{\sqrt{2\pi k}\sqrt{2\pi (n-k)}\cdot k^k \cdot (n-k)^{(n-k)} e^{-k}e^{-(n-k)}}p^kq^{n-k}\\
       & = \frac{\sqrt{2\pi n}\cdot n^n \cancel{e^{-n}}}{\sqrt{2\pi k}\sqrt{2\pi (n-k)}\cdot k^k \cdot (n-k)^{(n-k)} \cancel{e^{-n}}}p^kq^{n-k}\\
       & = \sqrt{\frac{n}{2\pi k(n-k)}}\cdot\frac{n^n}{k^k \cdot (n-k)^{n-k}} p^kq^{n-k}\\
       & = \sqrt{\frac{n}{2\pi k(n-k)}}\cdot\frac{n^k n^{n-k}}{k^k \cdot (n-k)^{n-k}} p^kq^{n-k}\\
       & = \sqrt{\frac{n}{2\pi k(n-k)}}\cdot\left(\frac{np}{k}\right)^k \cdot\left(\frac{nq}{n-k}\right)^{n-k}\;.\\
\end{align}
$$

 At this point, it is convenient to formulate the number of succeses $k$ in terms of deviations $k = np + z$ from the expectation $np$ as we did when defining random walks. As a result, 
 
 $$
 \begin{align}
 n-k &= n - (np + z) = n - (n(1-q) + z)\\
     &= n - (n - nq + z)\\
     &= nq - z\;.
 \end{align} 
 $$
 
 and we have

$$
\begin{align}
p(X=k) &= p(X = np + z)\\ 
       &\approx \sqrt{\frac{n}{2\pi k(n-k)}}\cdot \left(\frac{np}{np+z}\right)^{np + z} \cdot\left(\frac{nq}{nq-z}\right)^{nq - z}\\
       &= \sqrt{\frac{n}{2\pi (np + z)(nq - z)}}\cdot \left(\frac{np}{np + z}\right)^{np + z} \cdot\left(\frac{nq}{nq-z}\right)^{nq - z}\\
\end{align}
$$

Since 

$$
\begin{align}
\frac{n}{(np + z)(nq - z)} &= \frac{n}{n^2pq - npz + nqz - z^2}\\
                           &= \frac{1}{npq + \frac{-pz + qz - z^2}{n}}\\
                           &\approx \frac{1}{npq}\\
\end{align}
$$

we have

$$
\begin{align}
p(X=k) &= p(X = np + z)\\
       &\approx \frac{1}{\sqrt{2\pi\cdot npq}}\cdot \left(\frac{np}{np + z}\right)^{np + z} \cdot\left(\frac{nq}{nq-z}\right)^{nq - z}\\
       &= \frac{1}{\sqrt{2\pi\cdot npq}}\cdot \left(\frac{np + z}{np}\right)^{-(np + z)} \cdot\left(\frac{nq - z}{nq}\right)^{-(nq - z)}\\
       &= \frac{1}{\sqrt{2\pi\cdot npq}}\cdot \left(\frac{np}{np + z}\right)^{np + z} \cdot\left(\frac{nq}{nq - z}\right)^{nq - z}\\
       &= \frac{1}{\sqrt{2\pi\cdot npq}}\cdot \left(1 + \frac{z}{np}\right)^{-(np + z)} \cdot\left(1 - \frac{z}{nq}\right)^{-(nq - z)}\\
       &= \frac{1}{\sqrt{2\pi\cdot npq}}\cdot \left(1 + \frac{z}{np}\right)^{-(np + z)} \cdot\left(1 - \frac{z}{nq}\right)^{-(nq - z)}\;.
\end{align}
$$

Now, in order to highlight the exponential shape of $p(X = np + z)$ let us take logs at both sides 

$$
\begin{align}
\log p(X=k) &= \log p(X = np + z)\\
            &\approx \log\frac{1}{\sqrt{2\pi\cdot npq}} + \left(1 + \frac{z}{np}\right)^{-(np + z)} + \left(1 - \frac{z}{nq}\right)^{-(nq - z)}\\
            &= C + \log\left(1 + \frac{z}{np}\right)^{-(np + z)} + \log\left(1 - \frac{z}{nq}\right)^{-(nq - z)}\\
            &\approx C -(np + z)\log\left(1 + \frac{z}{np}\right) -(nq - z)\log\left(1 - \frac{z}{nq}\right)\\
            &= C - A - B\\
\end{align}
$$

Now, we exploit the Taylor expansions of $\log(1+x) = x - \frac{1}{2}x^2 + \frac{1}{3}x^3\ldots$ and $\log(1-x) = -x - \frac{1}{2}x^2 - \frac{1}{3}x^3\ldots$

Taking up to the quadratic terms, for A, B we have 

$$
A = (np + z)\left[\frac{z}{np} - \frac{1}{2}\left(\frac{z}{np}\right)^2\right]\;\;\text{and}\;\; B = (nq - z)\left[-\frac{z}{nq} - \frac{1}{2}\left(\frac{z}{nq}\right)^2\right]
$$

Then, we have 

$$
\begin{align}
A &= \left[np\frac{z}{np} - np\frac{1}{2}\left(\frac{z}{np}\right)^2\right] + 
\left[z\frac{z}{np} - z\frac{1}{2}\left(\frac{z}{np}\right)^2\right]\\
  &= z - \frac{1}{2}\frac{z^2}{np} + \frac{z^2}{np} - \frac{1}{2}\frac{z^3}{(np)^2}\\
  &= z + \frac{1}{2}\frac{z^2}{np} - \frac{1}{2}\frac{z^3}{(np)^2}\\
\end{align}
$$

and similarly 

$$
\begin{align}
B &= \left[-nq\frac{z}{nq} - nq\frac{1}{2}\left(\frac{z}{nq}\right)^2\right] - 
\left[-z\frac{z}{nq} - z\frac{1}{2}\left(\frac{z}{nq}\right)^2\right]\\
  &= -z - \frac{1}{2}\frac{z^2}{nq}  + \frac{z^2}{nq} + \frac{1}{2}\frac{z^3}{nq}\\
  &= -z + \frac{1}{2}\frac{z^2}{nq} +\frac{1}{2}\frac{z^3}{(nq)^2}
\end{align}
$$

Plugging $A$, $B$, $C$ in 

$$
\log p(X=k) &= \log p(X = np + z)\\
            &\approx C - A - B\\
            &= \log\frac{1}{\sqrt{2\pi\cdot npq}} - z - \frac{1}{2}\frac{z^2}{np} + \frac{1}{2}\frac{z^3}{(np)^2} + z - \frac{1}{2}\frac{z^2}{nq} -\frac{1}{2}\frac{z^3}{(nq)^2}\\
            &= \log\frac{1}{\sqrt{2\pi\cdot npq}} \cancel{- z} - \frac{1}{2}\frac{z^2}{np} + \frac{1}{2}\frac{z^3}{(np)^2} + \cancel{z} - \frac{1}{2}\frac{z^2}{nq} -\frac{1}{2}\frac{z^3}{(nq)^2}\\
            &= \log\frac{1}{\sqrt{2\pi\cdot npq}}  - \frac{1}{2}\frac{z^2}{np} - \frac{1}{2}\frac{z^2}{nq} + \left(\frac{1}{2}\frac{z^3}{(np)^2}-\frac{1}{2}\frac{z^3}{(nq)^2}\right)\\
            &\approx \log\frac{1}{\sqrt{2\pi\cdot npq}}  - \frac{1}{2}\frac{z^2}{np} - \frac{1}{2}\frac{z^2}{nq} \\
            &= \log\frac{1}{\sqrt{2\pi\cdot npq}}  + \frac{(-q - p)z^2}{2npq}\\ 
            &= \log\frac{1}{\sqrt{2\pi\cdot npq}}  + \frac{(-q - (1-q))z^2}{2npq} \\
            &= \log\frac{1}{\sqrt{2\pi\cdot npq}}  - \frac{z^2}{2npq} \\
$$

As a result, if we replace $z$ by $k - pq$ we have

$$
\log p(X=k) - \log\frac{1}{\sqrt{2\pi\cdot npq}} =  - \frac{z^2}{2npq}\;,
$$

i.e., the so called  <span style="color:#469ff8">**De Moivre - Laplace theorem** yields the usual expression for the Normal distribution as a limit of the Binomial one</span>: 

$$
p(X=k) =  \frac{1}{\sqrt{2\pi\cdot npq}}\exp\left(-\frac{1}{2}\frac{(k-np)^2}{npq}\right)\;,
$$

More generally, as $np$ is the "mean" of the Binomial, it is renamed as **mean** $\mu$ of the Normal. Similarly, as $npq = Var(X)$, it is renamed the **variance** $\sigma^2$ of the Normal, whose squere root is the **standard deviation** $\sqrt{\sigma^2}=\sigma$. 

Therefore, we can say that $X\sim N(\mu,\sigma^2)$ if its *pmf* is 

$$
p(X=x) =  \frac{1}{\sqrt{2\pi\cdot \sigma}}\exp\left(-\frac{1}{2}\frac{(x-\mu)^2}{\sigma^2}\right)\;.
$$

**The Standarized Normal**. Coming back to the fact that 

$$
k = np + z\;,
$$

we translate that to 

$$
x = \mu + z\;\;,\text{i.e. to}\;\; z = x - \mu\;.
$$

Then, the above definition becomes 

$$
p(X=z) =  \frac{1}{\sqrt{2\pi\cdot \sigma}}\exp\left(-\frac{1}{2}\frac{z^2}{\sigma^2}\right)\;.
$$

However, <span style="color:#469ff8">this expression is not yet a **probability mass function** but a **probability density function** *pdf* since</span>: 
- It does not yet describe the probability that the RW is at position $z$, but the probability thast a RW **with step-length $1$ on average** is **near** $z$. 
- As a result, $p(X=z)=0$ since we cannot undo precisely the run of the RW to land at an specific $z$ but **to land at an interval** $\Delta z$. The smaller the $\Delta z$ (it becomes a differential $dz\rightarrow 0$) the more precise is our result (see Feynman Lectures), and this happens when $n\rightarrow\infty$: 

$$
p(X\in [t,t+dt]) = \sum p(z)\Delta z = \int_{t}^{t+dt}p(z)dz\;.
$$

Then, the **cumulative distribution** becomes:

$$
p(X\le t) = \int_{z\le t}p(z)dz\;.
$$

In particular, let us define the (continuous) random variable $Z$ where, 

$$
Z = \left(\frac{x-\mu}{\sigma}\right) = \left(\frac{z}{\sigma}\right)\;.
$$

Then thr **unit** or **standarized Normal distribution** and its *pdf* is given by

$$
p(Z=z) =  \phi(z) = \frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}z^2}\;.
$$

Actually, the above integral, known as the **Gauss integral** satisfies the axioms of probability since 

$$
\int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}z^2}dz = 1\;,
$$

meaning that <span style="color:#469ff8">the **area under the Gauss function** defines a probability</span>. In particular, looking at {numref}`GaussU` we have: 

```{figure} ./images/Topic2/GaussU.png
---
name: GaussU
width: 800px
align: center
height: 250px
---
Cumulatives of the unit Gaussian: $a=-1, b=1$. 
```

- Probability of $Z\le a$ (lower tail): 

$$
p(Z\le a) =\frac{1}{\sqrt{2\pi}}\int_{-\infty}^a e^{-\frac{1}{2}z^2} = \phi(a)\;. 
$$

- Probability of $a\le Z\le b$ (between $a$ and $b$): 

$$
p(a\le Z\le b) =\frac{1}{\sqrt{2\pi}}\int_{a}^b e^{-\frac{1}{2}z^2} = \phi(b) - \phi(a)\;. 
$$

- Probability of $Z\ge a$ (upper tail):

$$
p(Z\ge a) = 1-\frac{1}{\sqrt{2\pi}}\int_{-\infty}^a e^{-\frac{1}{2}z^2} = 1 - \phi(a)\;. 
$$

Basically, once you standarize a variable $X$ (i.e. transform it into $Z$), you have all you need to compute Gaussian probabilities: 

$$
p(a\le X\le b) =  \frac{1}{\sqrt{2\pi\cdot \sigma}}\int_{a}^{b}\exp\left(-\frac{1}{2}\frac{(x-\mu)^2}{\sigma^2}\right)dx = \phi\left(\frac{b-\mu}{\sigma}\right)- \phi\left(\frac{a-\mu}{\sigma}\right)\;.
$$

If you want to query the lower tail values, please visit the [Standard Normal Cumulative Probability Table](https://www.math.arizona.edu/~jwatkins/normal-table.pdf)

**Link with fundamental bounds**. Once that we have discovered the exponential nature of the Gaussian, and once we realized that the Gaussian is the limit of the Binomial, we close the loop of understanding the exponential decays of both the **Hoeffding's and Chernoff bounds**. 

## Statistical dependence

### No replacement
 
Assuming that events are iid (independent and identically distributed) is somewhat far from modeling real events. <span style="color:#469ff8">The simplest way of understanding that is **change the conditions of the experiment** from one trial to another (**no replacement**)</span>. 

Take for instance a standard deck of $52$ cards: $4$ suits (clubs $\clubsuit$, diamonds $\diamondsuit$, spades $\spadesuit$ and hearts $\heartsuit$) and for each of them $2-10$ cards, plus Ace, $A$, Jack $J$, Queen $Q$ and King $K$: $13\times 4 = 52$ cards. In addition, 
- Diamonds and hearts are $\text{Red}$, whereas the other two suits are $\text{Black}$. 
- Jacks, Queens and Kings are $\text{Face}$ cards. 

Then, the probability of obtaining a spade is $p(\spadesuit)=\frac{13}{52}=1/4$. However: 
- If we obtain a $\spadesuit$, remove it from the deck and shuffle again, the probability changes: $p(\spadesuit'|\spadesuit)=\frac{12}{51}=0.235<1/4$.
- It also changes if we obtain a card of any other suit, say $\diamondsuit$, but in a different way: $p(\spadesuit'|\diamondsuit)=\frac{13}{51} = 0.254>1/4$. 

In both cases, the notation $p(A|B)$ denotes the probability of obtaining $A$ given $B$. In both cases, the conditioning modifies the probability of the original event $A$. Therefore, $A$ is **conditionally dependent on** $B$. In other words $A$ and $B$ are **independent** only if

$$
p(A|B) = p(A)
$$

In addition, condititional probability is computed by the **Bayes theorem**: 

$$
p(A|B) = \frac{p(A\cap B)}{P(A)}\;.
$$

Now, enforce not-independence or **conditioning** (dependence) by   drawing $k\ll 52$ cards **without replacement** and then asking for the probability of certain events related to these $k$ cards.

For instance, if we draw two cards *sequentially*, <span style="color:#469ff8">what is the probability of obtaining an ace of diamonds  $A\diamondsuit$ and a $\text{Black}$ card</span>. 

Since we draw the $k$ cards sequentially, the we have to consider the $k!$ possible orders of obtaing $k$ cards from $52$. In this case, we have $k=2$ and consequently two possible orders: 
- First $A\diamondsuit$, second $\text{Black}$. 
- First $\text{Black}$, second  $A\diamondsuit$.

We denote the events as follows: 

$
\begin{align}
A &=\{\text{First card is}\; A\diamondsuit\}\\
B &=\{\text{Second card is}\; A\diamondsuit\}\\
C &=\{\text{First card is}\; \text{Black}\}\\
D &=\{\text{Second card is}\; \text{Black}\}\\
\end{align}
$

Then, we explore the probability of each "order": 

$
\begin{align}
p(A\cap D) &= p(A)p(D|A) = \frac{1}{52}\cdot\frac{26}{51} = \frac{1}{102}\\
p(C\cap B) &= p(C)p(B|C) = \frac{26}{52}\cdot\frac{1}{51} = \frac{1}{102}\\
\end{align}
$ 

Therefore, since both orders are disjoint, the final result is given by

$
p(A\cap D) + p(C\cap B) = \frac{1}{102} + \frac{1}{102} = \frac{2}{102} = \frac{1}{51}\;. 
$

**Tree diagrams**. As we did with coins ($H$,$T$) and the Pascal's triangle (see {numref}`HT`), representing conditional-probability problems with trees facilitates the visualization of the problem and the interpretability of the solution. Probability trees are built as follows: 
- The root of the tree is the origin of the experiment. 
- All the edges are *directed* and they go from level $l$ to level $l+1$. The edges are labeled with probabilities. The edges leaving a given node $n$ *must add the unit*.
- The edges leaving the root (level $l=0$) are associated with *non-conditional probabilities of events*, e.g. $p(A)$.
- The edges in levels $l>0$ are associated with *probabilities conditioned* to the previous level e.g $p(B|A)$.
- The nodes describe events. 
- The leaves encode intersectional events e.g. $p(A\cap C)$.

Before using tree diagrams, it is interesting to note that **tree diagrams are not well suited** for solving problems like the above card-deck problem: <span style="color:#469ff8">what is the probability of obtaining an ace of diamonds  $A\diamondsuit$ and a $\text{Black}$ card taken sequentially (without replacement)</span>. Why? 
- Take an order, for instance $A,D$ (first card is $A\diamondsuit$, second is $\text{Black}$). As the probability of the branches must add $1$, we cannot put $A$ and $D$ as branches since $p(A) + p(D)\neq 1$.
- We actually need a tree for each order. 
  - In the first tree, we encode the order $A,D$ (first card is $A\diamondsuit$, second is $\text{Black}$) to calculate $p(A)$ and $p(D|A)$ leading to $p(A\cap D)$. 
  - In the second tree, we encode the order $C,B$ (first card is $\text{Black}$ and second is $A\diamondsuit$), to calculate $p(B)$ and $p(C|B)$ leading to $p(C\cap B)$.

In {numref}`Tree1`, we show the first of these two trees. Note that half of the nodes provided answers not required in this particular problem. However, the answer $p(A\cap D)$ added to that of $p(C\cap B)$ given by a second tree, solves the problem. 

```{figure} ./images/Topic2/Tree1.png
---
name: Tree1
width: 600px
align: center
height: 300px
---
Simple tree for $p(A\cap D)$. 
```

Despite the above example, tree diagrams are very useful in other **no-replacement problems** such as answering the following gambling question:  

<span style="color:#469ff8">What is the probability that after extracting two cards from the deck, without replacement,  I get **two cards with the same color?**</span>

We build the tree diagramm as follows: 
- Level $1$: we have two possibities $R = \{\text{1st card is}\; \text{Red}\}$ or $\bar{R} = \{\text{1st card is}\; \text{Black}\}$.
- Level $2$: we have, again two possibities $R' = \{\text{2nd card is}\; \text{Red}\}$ or $\bar{R'} = \{\text{2nd card is}\; \text{Black}\}$.

Then, the probabilities of the two branches at level $1$ are: 

$
\begin{align}
p(R) & = \frac{26}{52} = \frac{1}{2}\\
p(\bar{R}) & = 1 - p(R) = 1 - \frac{1}{2} = \frac{1}{2}\\
\end{align}
$

In level $2$ we have $4$ branches:

$
\begin{align}
p(R'|R) & = \frac{26-1}{52-1} = \frac{25}{51}\\
p(\bar{R'}|R) & = 1 - p(R'|R) = 1 - \frac{25}{51} = \frac{26}{51}\\
p(R'|\bar{R}) & = \frac{26}{52-1} = \frac{26}{51}\\
p(\bar{R'}|\bar{R}) & = 1 - p(R'|\bar{R}) = 1 - \frac{26}{51} = \frac{25}{51}\\
\end{align}
$ 

which lead to $4$ intersection probabilities:

$
\begin{align}
p(R)p(R'|R) & = \frac{1}{2}\cdot\frac{25}{51} = p(R\cap R')\\
p(R)p(\bar{R'}|R) & = \frac{1}{2}\cdot\frac{26}{51} = p(R\cap \bar{R'})\\
p(\bar{R})p(R'|\bar{R}) & = \frac{1}{2}\cdot\frac{26}{51} = p(\bar{R}\cap R')\\
p(\bar{R})p(\bar{R'}|\bar{R}) & = \frac{1}{2}\cdot\frac{25}{51} = p(\bar{R}\cap \bar{R'})\\
\end{align}
$

As a result, we are interested in events $R\cap R'$ and $\bar{R}\cap \bar{R'}$, i.e. the solution to the problem is 

$
p(R\cap R') + p(\bar{R}\cap \bar{R'}) = \frac{1}{2}\cdot\frac{25}{51} + \frac{1}{2}\cdot\frac{25}{51} = \frac{25}{51}\;.
$

Basically, when we extract a card of a given color, we **reduce the odds** of extracting a sample of the same color in the future and **increase** those of the opposite color. In other words, we are asking the probability of **imbalancing the odds**. The probability of balancing the odds is actually

$
p(R\cap \bar{R'}) + p(\bar{R}\cap R') = 1 - \left(p(R\cap R') + p(\bar{R}\cap \bar{R'})\right) = \frac{26}{51}\;,
$

i.e. slightly higher than that of imbalancing the odds. 

We show the tree diagram in {numref}`Tree2`. Note that at each level $l$ of the tree we have that the probability of all the leaves adds to one. 

```{figure} ./images/Topic2/Tree2.png
---
name: Tree2
width: 600px
align: center
height: 450px
---
Tree diagram for a card deck (no replacement). 
```

Note also that $p(R\cap \bar{R'}) = p(\bar{R}\cap R')$ and the second and third leaves can be fused in just one with probability $2\frac{1}{2}\cdot\frac{26}{51}=\frac{26}{51}$. Actually, both events represent the same outcome in different orders if consider obtaning a red card a "success" (either in the first or in the second round) and not obtaining it a "failure". 

Therefore, in some regard, this kind of tree remind us the Pascal's tree, but <span style="color:#469ff8">this time describing **conditional events or variables** instead of independent ones.</span> 

[//]: https://www.cl.cam.ac.uk/teaching/1920/Probablty/materials/Lecture5.pdf

### Conditional expectations

Before we dive deeper in "conditional trees", it is interesting to redefine expectations in terms of conditional probabilities. 

Consider for instance {numref}`Tree3` where we *generalize* the tree in {numref}`Tree2` as follows.
- The **nodes** are considered as the *states* of a random system with a tuple $(\text{cards},\text{deck})$, where $\text{cards}$ denote the number of red cards remaining in the deck, and $\text{deck}$ is the number of cards (both red and black) remaining in the deck. 
- The **edges** are labeled with the conditional probability of reaching the destination node from the original one. The probabilities emanating from the same node must add one. 

Now, we define the following **random** variables: 
- $X_0=\frac{a}{A}$ is the fraction of red cards in the original deck where: 
  - $A$ is the number cards in the original deck ($52$).
  - $a$ is the number of red cards in the deck ($26$).
- $X_1$ is the fraction of red cards remaining after the first draw with **no replacement**. 
- $X_2$ is the fraction of red cards remaining after the second draw with **no replacement**.  

```{figure} ./images/Topic2/Tree3.png
---
name: Tree3
width: 800px
align: center
height: 450px
---
General tree diagram for a card deck (no replacement). 
```

Then, we define the **conditional expectation** $E(X|Y=y)$ of $X$ wrt to setting $Y=y$ as follows: 

$$
E(X|Y=y) = \sum_{x}x\cdot p(X=x|Y=y) = \sum_{x}x\cdot \frac{p(X=x,Y=y)}{p(Y=y)}\;,
$$

where $p(X=x,Y=y)$ is the **joint probability** (intersection). 

Consider for instance, $X=X_1$ and $Y=X_0$. Since $X_1$ has two *states*, we commence by defining the conditional probabilities:  

$$
\begin{align}
p\left(X_1=\frac{a}{A-1}\bigg| X_0 =\frac{a}{A}\right) &= \frac{A-a}{A} = p\left(X_1=\frac{a}{A-1}\right)\\
p\left(X_1=\frac{a-1}{A-1}\bigg| X_0 =\frac{a}{A}\right) &= \frac{a}{A} = p\left(X_1=\frac{a-1}{A-1}\right)\\
\end{align}
$$

i.e. knowing $X_0 = \frac{a}{A}$ does not modifies the probability of $X_1$ ($X_0$ and $X_1$ are independent).

Since $X_0$ has a single value, we have

$$
\begin{align}
E(X_1|X_0) &= \sum_{x}x\cdot p\left(X_1=x\bigg|\frac{a}{A}\right)\\
           &= \frac{a}{A-1}\cdot\frac{A-a}{A} + \frac{a-1}{A-1}\cdot\frac{a}{A}\\
           &= \frac{a}{A}\left[\frac{(A-a) + (a-1)}{(A-1)}\right]\\
           & = \frac{a}{A}\left[\frac{A-1}{A-1}\right]\\
           &= \frac{a}{A}
\end{align}
$$

Since $X_0$ and $X_1$ are independent, we have that $E(X_1|X_0)=E(X_1)$. 

However $X_2$ depends clearly on $X_1$. Looking at level $l=2$ we have $3$ different values for $X_2$: $\frac{a}{A-2}$, $\frac{a-1}{A-2}$ and $\frac{a-2}{A-2}$. 

Let us compute the conditional probabilities for $X_2$ (actually the probability of each leaf in the tree). Herein, we apply the **chain rule** for conditional probabilities $p(X|Y,Z) = p(X|Y)p(Y|Z)$.  

$$
\begin{align}
p(X_2|X_1,X_0) &= p(X_2|X_1)p(X_1|X_0)\\
               &= p(X_2=x_2|X_1=x_1)p\left(X_1=x_1\bigg| X_0 = \frac{a}{A}\right)\\
\end{align}
$$

Then, looking at the tree we consider the paths leading to each different leaves: 

- $X_2 = 0\;\text{red cards extracted}$ (left branch):

$$
\begin{align}
p\left(X_2=\frac{a}{A-2}\bigg| X_1=\frac{a}{A-1}\right)\frac{A-a}{A} &= \frac{A-a-1}{A-1}\cdot\frac{A-a}{A}
\end{align}
$$

- $X_2 = 1\;\text{red card extracted}$ (middle branches):

$$
\begin{align}
 p\left(X_2=\frac{a-1}{A-2}\bigg| X_1=\frac{a}{A-1}\right)\frac{A-a}{A} &+ 
p\left(X_2=\frac{a-1}{A-2}\bigg| X_1=\frac{a-1}{A-1}\right)\frac{a}{A} = \\
 \frac{a}{A-1}\cdot\frac{A-a}{A} &+ \frac{A-a}{A-1}\cdot\frac{a}{A} = 2\frac{A-a}{A-1}\cdot\frac{a}{A}
\end{align}
$$

- $X_2 = 2\;\text{red cards extracted}$ (right branch):

$$
\begin{align}
p\left(X_2=\frac{a-2}{A-2}\bigg| X_1=\frac{a-1}{A-1}\right)\frac{a}{A} &= \frac{a-1}{A-1}\cdot\frac{a}{A}
\end{align}
$$

Then, we proceed to calculate $E(X_2|X_1,X_0)$ as follows: 

$$
\begin{align}
E(X_2|X_1,X_0) &= \sum_{x_2}x_2\cdot p(X_2=x_2|X_1,X_0)\\
               &= \frac{a}{A-2}\cdot\frac{A-a-1}{A-1}\cdot\frac{A-a}{A} + \frac{a-1}{A-2}\cdot 2\frac{A-a}{A-1}\cdot\frac{a}{A} + \frac{a-2}{A-2}\cdot\frac{a-1}{A-1}\cdot\frac{a}{A}\\
\end{align}
$$

<span style="color:#469ff8">Look **carefully** the pattern of the above expression</span>: 
- We move from $0$ successes (red card drawn) to $1$ and $2$ successes. 
- Each success is characterized by $a - k$, with $k=0,1,2$.
- Each failure is characterized by $A - a - l$, with $l=0,1$. 

Rearranging properly each term so that failures appear first, we have

$$
\begin{align}
E(X_2|X_1,X_0) &= \frac{A-a}{A-2}\cdot\frac{A-a-1}{A-1}\cdot\frac{a}{A} + 2\frac{A-a}{A-2}\cdot \frac{a-1}{A-1}\cdot\frac{a}{A} + \frac{a-2}{A-2}\cdot\frac{a-1}{A-1}\cdot\frac{a}{A}\\
& = \frac{a}{A}\left[\frac{A-a}{A-2}\cdot\frac{A-a-1}{A-1} + 2\frac{A-a}{A-2}\cdot \frac{a-1}{A-1} + \frac{a-2}{A-2}\cdot\frac{a-1}{A-1}\right]\\
&= \frac{a}{A}\left[\frac{A^2 - 3A + 2}{(A-1)(A-2)}\right]\\
&= \frac{a}{A}\left[\frac{(A-1)(A-2)}{(A-1)(A-2)}\right]\\
&= \frac{a}{A}
\end{align}
$$

Therefore, we have that $E(X_2|X_1,X_0) = E(X_1)$. This property is not satisfied, in general, by any conditional expectation, but when it happens, we say that we have a **martingale**. 

### Martingales

Given a sequence of random variables $X_0,X_1,\ldots,X_n,X_{n+1}$, it is a martingale if

$$
E(X_{n+1}|X_n,\ldots,X_1,X_0) = E(X_n)\;\;\text{for all}\;\;n\ge 0\;.
$$

In the previous example, $E(X_{n+1}|X_n,\ldots,X_1,X_0)=\frac{a}{A} = E(X_1)$, even if the variables are conditioned. 

<span style="color:#469ff8">Why Martingales are **useful** in Artificial Intelligence?</span>

Martingales are **random or stochastic processes** not so simpler than sums of i.i.d.s (coin tossing) but not too complex to study. Interestingly, **random walks** are particular cases of martingales. 

The idea behind martingales is that **expectation never changes** even when you add a new level in the tree (a new conditioned variable). On average, the value of the variable $X_{n+1}$ is that of $E(X_{n})$ which *does not mean* that $X_{n+1}$ is only conditioned to $X_{n}$ as it happens in Markov chains. Actually, $X_{n+1}$ is conditioned to $X_n,X_{n-1},\ldots,X_0$ but the conditional expectation is **invariant**. 

**Fair games**. The invariance of the conditional expectation explains the application of Martingales to model the expectations of gamblers in fair games:


Let us define a gambler betting $1$ coin  for the Casino drawing a red card from the deck. If we wins, he gets $1$ back. Doing so, the expected profit is **constant**. Why?.  
- $X_{n}$ models the gambler fortune at the end of the $n^{th}$ play. 
- If the game if fair, the **expected fortune** $E(X_{n+1})$ at the game $n+1$ is the same than that at game $n$ $E(X_{n})$, i.e. conditional information cannot predict the future.  

### Links with Pascal's Triangle

Looking carefully at the structure of $E(X_2|X_1,X_0)$ we have that it is equal to: 

$$
\begin{align}
\frac{a}{A-2}\cdot\underbrace{{2\choose 0}\frac{A-a-1}{A-1}\cdot\frac{A-a}{A}}_{p(R_2=0)} + \frac{a-1}{A-2}\cdot \underbrace{{2\choose 1}\frac{A-a}{A-1}\cdot\frac{a}{A}}_{p(R_2=1)} + \frac{a-2}{A-2}\cdot\underbrace{{2\choose 2}\frac{a-1}{A-1}\cdot\frac{a}{A}}_{p(R_2=2)}\\
\end{align}
$$

where $p(R_2=k)$ is the probability of drawing $k$ red cards at level $l=2$. 

In general we have: 

$$
p(R_n = k) = {n\choose k}\frac{P(A-a,n-k)\cdot P(a,n)}{P(A,n)} 
$$

where $P(n,r) = n(n-1)\ldots (n - r + 1)$ is an **r-permutation** of $n$ as defined in the topic of combinatorics. The above expression comes from observing the factorial patterns in both the numerator and the denominator. 

Compared with the i.i.d. case ({numref}`Bern`), i.e. with replacement,  where the probability of obtaining $k$ red cards should be Binomial

$$
p(R_n = k) = {n\choose k}p^k(1-p)^{n-k}
$$

with $p=1/2$, in {numref}`PascalMartin` we show, with colors, the probability distribution for the conditional case, i.e. for the martingale, where we kept $\frac{a}
{A} = p$ for being comparable to the independent case. 

```{figure} ./images/Topic2/PascalMartin.png
---
name: PascalMartin
width: 950px
align: center
height: 700px
---
Distribution for a martingale. 
```

Note that: 
- Extremal events (all failures/all success) tend to have a zero probability as $n$ grows. 
- The bulk of the distribution is close to $E(X_1)=\frac{a}{A}$ but as $n$ increases the pmf (point-mass function) is flattened. 
- Flattening with $n$ is due to the denominator $P(A,n)$ of $p(R_n = k)$. 
- Of course we may adapt the fundamental equalities defined for i.i.d. variables to conditional ones, but it is quite clear than rare envents will be less probable in conditional trees such as that in {numref}`PascalMartin` unless we change the ratio between $a$ and $A$. 


[//]: https://mpaldridge.github.io/math2750/S01-stochastic-processes.html

## Random walks on graphs

### Markov chains 

So far, we have studied both **independent random processes** and **conditional random processes**. In this regard, when we have independence, our random process is a *simple random walk* (see {numref}`RWrand`). However, when the variables in the random process are fully conditioned, the corresponding random process is more difficult to study unless we have a martingale. Fortunately, <span style="color:#469ff8">there is something in between the simplicity of independent random processes and the full conditioning of the martingale: we refer to **Markov chains**</span>.   

**Markov chain**. A *sequence* of random variables $X_0,X_1,\ldots$ is a Markov chain if for all possible *states* (values of the random variables) $x_{t+1},x_{t},\ldots,x_1$ we have: 

$$
\begin{align}
p(X_{t+1}=j|& X_t=i,\ldots,X_1=x_1,X_0=x_0) = p(X_{t+1}=j|X_t=i)=p_{ij}\\
&\text{with}\;\; p_{ij}\ge 0\;\forall i,j\;\;\text{and}\;\;\sum_{j}p_{ij}=1\;\forall i\;,
\end{align}
$$

i.e. the probability of a future event only depends on that of a present one. This is called the **Markov property** or the **memoryless property**.

A couple of interesting properties:
- **Irreducibility**. We say that a state $j$ in the Markov chain (MC) is **accesible** from another state $i$ if exists $t\ge 0$ so that 

$$
p(X_t=j|X_0=i) = p_{ij}(t)> 0\;\text{in}\;t\;\text{steps}\;,
$$

that is, we can get from a state $i$ to state $j$ in $t$ steps with probability $p_{ij}(t)$. Then, <span style="color:#469ff8">a MC is **irreducible** if each pair $(i,j)$ of states is mutually accessible.</span> 

[//]: https://galton.uchicago.edu/~lalley/Courses/312/MarkovChains.pdf

[//]: https://mpaldridge.github.io/math2750/S05-markov-chains.html

[//]: https://www.stat.berkeley.edu/users/aldous/RWG/book.pdf

[//]: https://web.pdx.edu/~gjay/teaching/mth271_2020/html/13_GamblersRuin.html

- **Periodicity**. A state $i$ has **period** $d_i$ if

$$
d_i = \text{gcd}(t\in\{1,2,\ldots\}: p_{ii}(t)>0)
$$

where $\text{gcd}$ denotes the greatest common divisor. Then, if $d_i>1$ the state $i$ is **periodic**; it $d_i=1$ it is **aperiodic**. Then <span style="color:#469ff8">a MC is **aperiodic** if all states have period $d_i=1$</span>. 

**Graphs**. A graph $G=(V,E)$ consists of a set of **nodes** or vertices $V={1,2,\ldots,n}$ where $|V|=n$, and a set of **edges** $E\subseteq V\times V$. 
- An edge $e=(i,j)$ is denoted by a pair of nodes $i$ and $j$, where $i$ is the origin and $j$ the target or destination. 
- If the graph is **undirected** both $(i,j)$ and $(j,i)$ do exist for all $e\in E$. Otherwise, the graph is **directed**. 
- If $e=(i,i)$ we have a **self-loop**. 

Graphs are very flexible mathematical tools. We commence by using them for describing a random process. The nodes $V$ provide the **states** and the edges $E$ provide the **transitions between states**. Actually we label the edges with the probability of a Markovian transition $p(j|i) = p_{ij}$. 

The following example is motivated by the essay [Random Walks and Electric Networks](https://math.dartmouth.edu/~doyle/docs/walks/walks.pdf) by Doyle and Snell. 

We want to build a graph for the **drunkard's walk**. A man walks along a $5-$blocks stretch in Madison Avenue. He starts at corner $x$ and, with probability $1/2$ walks one block to the right and, also with probability $1/2$ walks one block to the left. At the next corner, he again choses his direction randomly. He continues until he reaches corner $5$, which is home, or corner $0$, which is a bar. In both latter cases he stays there. 

Our graph for this walk has $n=6$ vertices or **states** $V=\{0,1,2,3,4,5\}$, where $5$ is $\text{Home}$ and $0$ is the $\text{Bar}$. See {numref}`Drunk` where the edges or **transitions** are in blue (bidirectional if we no depict the arrowheads) and the possible decision for node $x=3$ are depicted in black. 
 
```{figure} ./images/Topic2/Drunk.png
---
name: Drunk
width: 750px
align: center
height: 100px
---
A graph for the drunkard's walk. 
```

Actually, the edges of the above graph are $E=\{(0,0),(1,0),(1,2),(2,1)\ldots,(4,5),(5,5)\}$

<span style="color:#469ff8">Why our graph mimics the **drunkard's walk**, and why it is a **MC**?</span>

- We have two states, $0$ and $1$, with **self-loops** and no edges for returning to any other node. These states are called **absorbing states** in the MC terminology, since once the Markov-chain-random walk (MCRW) reaches them, it is trapped there. As a result the MC is **reducible**. 
- The graph is almost **bipartite**, i.e. we can parition $V$ in to subsets $V_1=\{0,2,4\}$ and $V_2=\{1,3,5\}$ so that nodes in $V_1$ can only go nodes of $V_2$ (except the absorbing nodes) and viceversa. As a result, the MC is almost **aperiodic**. Non-absorbing nodes have period $2$ and the absorbing ones have period $1$.  
- If we start our MCRW at a non-absorbing state, say $x\in\{2,3,4\}$ we walk left with probability $1/2$ and right also with probability $1/2$. 
- The **degree** $\text{deg}(i)$ of a node $i$ in the graph is the number of neighbors ${\cal N}_i$, i.e. the number of **outgoing edges** from $i$. In our graphs we have that all non-absorbing nodes have degree $2$ whereas the absorbing states have degree $1$ (actually their neighbors are themselves). 
- The degree $\text{deg}(i)$ of each node $i$ reveals that the (Markovian) probability of making a transition to a neighbor is

$$
p(j|i) = p_{ij} = \frac{a_{ij}}{\text{deg}(i)}\;\; \text{where}\;\; 
a_{ij}= 
\begin{cases}
     1\;\text{if}\; i\in {\cal N}_i  \\[2ex]
     0\; \text{otherwise}\;.
\end{cases}
$$

and $a_{ij}=1$ means that nodes $i$ and $j$ are **adjacent**. For absorbing states, we have $a_{ij}=0\;\forall j\neq i$. As a result, for these states $p_{ii}=1$ and $p_{ij}=0$ for $j\neq i$.

**Patterns of the drunkard's walk**. In order to have a rough idea of the behavior of this Markov process, we have generated $40,000$ random walks ($10,000$ starting at each non-absorbing states $x=1,2,3,4$). Each random walk has length $l=10$. Why? We will discover that shorly. What is important now is to note that some of the walks end up in one of the absorbing states ($x=0$), whereas many others end in the other one ($x=5$). The  probability of reaching each absorbing state is $1/2$.

We plot these walks in {numref}`Drunkard`. The darkest the blue line, the *slower* the walk reaches $x=5$. This means that if the walks reaches $x=5$ at the maximum length of the path $l=10$ it becomes the darkest one. 

 Some iteresting patterns: 
- As we start uniformly the same number of paths at each non-absorbing state, there is no clear difference between the paths ending in $x=0$ and those ending in $x=5$. 
- In addition, some paths tending to $x=0$ turn suddenly towards $x=5$ and vice versa.

Apparently, all the non-absorbing states reach $x=5$ *equally slowly*. **However this is misleading**. Actually, most of the paths reach $x=5$ very early. This suggests that the probability of reaching $x=5$ from any non-absorbing state *is not uniform*. This leads us to the answer the first question to solve about a random walk: what is the probability of ending $\text{Home}$.

Before addressing the **two fundamental questions** for a MCRW: (a) where does it converge to, and (b) how long does it take, it is important to note that the remainder of this section requires some practice with algebraic solvers of recurrent relations, namely **linear difference equations**. They are very practical tools that are explained in the excellent [Github of Mathew Aldridge](https://mpaldridge.github.io/math2750/) and even in the [Wikipedia](https://en.wikipedia.org/wiki/Linear_recurrence_with_constant_coefficients). The examples below have been adapted from the first source and solve some of the exercises in [Random Walks and Electric Networks](https://math.dartmouth.edu/~doyle/docs/walks/walks.pdf) by Doyle and Snell.


```{figure} ./images/Topic2/Drunkard.png
---
name: Drunkard
width: 800px
align: center
height: 400px
---
Patterns of generated drunkard's walks. 
```
<span style="color:#469ff8">**Q1.** What is the probability of ending at $\text{Home}$ if we start from the non-absorbing state $x$?</span>

In other words, what is the probability of **hitting** $x=5$ from $x$ before hitting $x=0$? 

1) We commence by **formulating the Markovianity** of the drunkward's path in a more generic way: 

$$
x_{n+1}= 
\begin{cases}
     x_{n} + 1 \;\text{with probability}\; p\; \text{if}\; 1\le n\le m-1 \\[2ex]
     x_{n} - 1 \;\text{with probability}\; q\; \text{if}\; 1\le n\le m-1 \\[2ex]
     0\; \text{if}\; n=0\\[2ex]
     m\; \text{if}\; n=m\;,
\end{cases}
$$

where: $x_{n}$ is the position of the walk at step $n$, $p = 1 - q = 1/2$ is the probability of a transition from a non-absorbing state and $m=5$ is the target node. 

2) We pose the above formula in probabilistic terms using the **condition on the first step**: 

$$
\begin{align}
p(\text{Home}) &= p(\text{1st step right})p(\text{Home}|\text{1st step right})\\ 
&+ p(\text{1st step left})p(\text{Home}|\text{1st step left})\\
& = p\cdot p(\text{Home}|\text{1st step right}) + q\cdot p(\text{Home}|\text{1st step left})\;.
\end{align}
$$

Herein, we use the **theorem of total probability** for the following events:

$$
\begin{align}
E &= \{\text{Home}\}\\
A &= \{\text{1st step right}\}\\ 
\bar{A} &= \{\text{1st step left}\} 
\end{align}
$$

Then, total probability means that the probability of an event given two (or more) exclusive events is

$$
p(E) = p(E\cap A) + p(E\cap \bar{A}) = p(A)p(E|A) + p(\bar{A})p(E|\bar{A})\;. 
$$

In our case: 

$$
P(E) = p\cdot p(E|A) + q\cdot p(E|\bar{A})\;,
$$

and we want to calculate both $p(E|A)$ and $p(E|\bar{A})$ to calculate $P(E)$. 

3) Formulate and solve a **recurrence relation**: 

Then, we have to solve the following recurence relation: 

$$
r_n = p\cdot r_{n+1} + q\cdot r_{n-1}\;\text{subject to}\; r_0=0, r_m = 1\;.
$$

where $r_0 = 0$ and $r_m=1$ are the **boundary conditions** that specify success if we reach $m$ ($\text{Home}$) and failure if we reach $0$ ($\text{Bar}$). 

We formulate the recurrence relation as a **linear difference equation**. In this case it is **homogeneous** (like an homogeneous linear system $\mathbf{A}\mathbf{x}=\mathbf{0}$) since: 

$$
p\cdot r_{n+1} + q\cdot r_{n-1} - r_n = 0\;.
$$

First of all, we apply the following change of variable: 

$$
r_n = \lambda^n\;,
$$

which leads to 

$$
p\lambda^{n+1} + q\lambda^{n-1} - \lambda^n = 0\;,
$$

and taking $\lambda^{n-1}$ as common factor yields

$$
\lambda^{n-1}(p\lambda^{2} + q - \lambda) = 0
$$

where $p\lambda^{2} + q - \lambda = 0$ is the **characteristic equation** of the recurrence. Then, reorganzing the coefficients we have  $p\lambda^{2} - \lambda + q = 0$. To solve this quadratic equation is convenient to use the remainder theorem (Ruffini). The dividers of the independent term ($q$) are $\pm 1$ and $\pm q$. If we try first $+1$, and apply $q = 1-p$, this leads to the equation $\lambda p - q = 0$ with yields $\lambda =\frac{q}{p}$ tha we call $\rho$. Then, the factorization we are looking for is 

$$
(p\lambda - q)(\lambda - 1)\; \text{and roots}\; \lambda_1=1, \lambda_2=\rho\;.
$$

Now, we have two cases:
- If $\rho \neq 1$, then we have two distinct roots. In this case, the general solution of an homogeneous equation has the shape: 

$$
r_n = A\lambda_1^n + B\lambda_2^n = A1^n + B\rho^n = A + B\rho^n\;.
$$

In order to determine $A$ and $B$ we exploit the two **boundary conditions** $r_0=0, r_m=1$: 

$$
\begin{align}
r_0 &=  A + B\rho^0 = A + B = 0\\
r_m &=  A + B\rho^m = 1\\
\end{align}
$$

From $A + B = 0$ we get $A = -B$ which leads to 

$$
\begin{align}
- B + B\rho^m &= 1 \Rightarrow (\rho^m - 1) B = 1 \Rightarrow B = \frac{1}{\rho^m - 1}\\
A = -B & = -\frac{1}{\rho^m - 1}\;.
\end{align}
$$

and, as a result 

$$
\begin{align}
r_n &= A\lambda_1^n + B\lambda_2^n\\
    &= -\frac{1}{\rho^m - 1} + \frac{\rho^n}{\rho^m - 1}\\
    &= \frac{\rho^n-1}{\rho^m - 1}
\end{align}
$$

- If $\rho=1$ we have $p=q$ and this means that we have two repeated solutions $\lambda_1=\lambda_2 = 1$. In this case, the general solution has the following shape: 

$$
r_n = (A + nB)\lambda_1^n\;,
$$
 
which leads to 

$$
\begin{align}
r_0 &=  (A + 0B)1^0 = A = 0\\
r_m &=  (A + mB)1^m = A + mB = 1\\
\end{align}
$$

whose solutions are $A = 0$ and $B = \frac{1}{m}$.

Finally

$$
\begin{align}
r_n &= (A + nB)\lambda_1^n\;\\
    &= (0 + n\frac{1}{m})\\
    &= \frac{n}{m}
\end{align}
$$

The generic result is: 

$$
r_n = 
\begin{cases}
  \frac{\rho^n-1}{\rho^m - 1} \;\text{if}\; p\neq q\\[2ex]
  \frac{n}{m} \;\text{if}\; p = q\\[2ex]
\end{cases}
\;\;\;\;i.e.\;\;\;\; 
r_n = 
\begin{cases}
  \frac{\left(\frac{q}{p}\right)^n-1}{\left(\frac{q}{p}\right)^m - 1} \;\text{if}\; p\neq q\\[2ex]
  \frac{n}{m} \;\text{if}\; p=q\\[2ex]
\end{cases}
$$

**Result for the ubiased walk**. If $p=q=1/2$ we have a random process according to the graph in {numref}`Drunk`. The probability of getting $\text{Home}$, i.e. of hitting $x=m=5$ before hitting $x=0$ is $p(x)=\frac{x}{m} = \frac{x}{5}$. The closer we are to $\text{Home}$ the more probable is that we get there. Note that if we invert the boundary conditions priming going to the $\text{Bar}$, the probability of getting there before arriving home is $p(x)=1-\frac{x}{5}$. 

However, as $m\rightarrow\infty$ the probability of getting $\text{Home}$ tends to zero, i.e. $p(x)\rightarrow 0$. 

The result for the unbiased (fair) walk is consistent with our observations in {numref}`Drunkard` and shows that the probability of reaching $\text{Home}$ is not **uniform**. This result also explain why most of the $40,000$ random walks lauched uniformly from any of the non-absorbing states reach $\text{Home}$ very soon. 

**Result for the biased walk**. Biased walks, however, are modeled in a different way. We label the edges with their probabilities. Then, instead of getting the transition probabilities from the degree, we simply set $p_{ij}=a_{ij}p$ or $p_{ij} = a_{ij}q$ as in {numref}`Drunkpq`

```{figure} ./images/Topic2/Drunkpq.png
---
name: Drunkpq
width: 800px
align: center
height: 100px
---
Graph for biased drunkard's walks. 
```

If $q\ll p$, then $p(x)\rightarrow 1$ since we are drifted to the right. Symmetrically, if $q\gg p$, then $p(x)\rightarrow 0$ since $m>n$. 

As $m\rightarrow\infty$, we have that $p(x)\rightarrow 0$, independently of the relationship between $p$ and $q$ since

$$
\lim_{m\rightarrow\infty} \frac{\rho^n-1}{\rho^m - 1} = \lim_{m\rightarrow\infty} \frac{\rho^n/\rho^m-1/\rho^m}{1 - 1/\rho^m} = \lim_{m\rightarrow\infty} \frac{0-0}{1 - 0} = 0\;.
$$

In {numref}`Drunkardpq` where $p=0.25, q=0.75$ we can see that few walks reach $x=5$, actually the proportion of "successful" paths is $p$. 


```{figure} ./images/Topic2/Drunkardpq.png
---
name: Drunkardpq
width: 800px
align: center
height: 400px
---
Patterns of generated biased drunkard's walks with $p=0.25$. 
```

<span style="color:#469ff8">**Q2.** What is the expected time or **hitting time** for arriving $\text{Home}$ if we start from the non-absorbing state $x$?</span>

We are interested in estimating the expected **hitting time** of $x=5$. 

As before, we rely on linear difference equations. 

1) We pose the above formula in probabilistic terms using the **condition on the first step**: 

$$
\begin{align}
E(\text{Duration}) &= p(\text{1st step right})p(\text{Duration}|\text{1st step right})\\ 
&+ p(\text{1st step left})p(\text{Duration}|\text{1st step left})\\
& = p\cdot p(\text{Duration}|\text{1st step right}) + q\cdot p(\text{Duration}|\text{1st step left})\;.
\end{align}
$$

Herein, we use the **conditional expectations** for the following random variables:

$$
\begin{align}
X &= \{\text{Duration}\}\\
Y &= \{\text{1st step}\}\\ 
\end{align}
$$

where $Y$ has values $y=\text{left}$ and $y=\text{right}$. 

Then, 

$$
E(X|Y=y) = \sum_{x}xP(X=x|Y=y)\;.
$$

However, we are interested in $E(X)$, which is defined by the **tower property** of conditional expectation: 

$$
E(X) = E(E(X|Y))=\sum_{y}p(Y=y)H(X|Y=y)\;.
$$

where $Y$ is the outcome of the first step. 

In this regard,

$$
\begin{align}
E(X|Y=\text{left})  &= 1 + d_{n-1}\\ 
E(X|Y=\text{right}) &= 1 + d_{n+1}\;. 
\end{align}
$$

Always count $1$ because we had made a step. 

This leads us to the following **inhomogeneous recurrence relation**: 

$$
d_n = p(1 + d_{n+1}) + q(1 + d_{n-1}) = 1 + pd_{n+1} + qd_{n-1}\;.
$$

and we have 

$$
pd_{n+1} -d_n + qd_{n-1} = -1\;\;\text{subject to}\;\; d_0=0, d_m=0\;.
$$

Whose left-hand-size lhs leads to the same homogeneous recurrence equation that we have studied before.  

- If $\rho\neq 1$ the general solution ($\lambda_1=1, \lambda_2=\rho$ are solutions of the homogeneous version) has the shape

$$
d_{n} = A + B\rho^n\;.
$$

Since we need a particular solution for the full equation and the lhs is a constant, we start trying to set $d_{n}=C$: 

$$
pC - C + qC = (p+q)C - C = C - C\neq -1\;
$$

Next, we try with $d_{n}=Cn$: 

$$
\begin{align}
pC(n+1) - Cn + qC(n-1) &= pCn + pC - Cn + qCn -qC\\ 
                       &= Cn - Cn + (p-q)C\\ 
                       &= (p-q)C = -1
\end{align}
$$

i.e. $C = \frac{-1}{p-q}$ and the particular solution becomes

$$
d_n = A + B\rho^n + Cn = A + B\rho^n - \frac{n}{p-q}\;.
$$

Then we apply the **boundary conditions** $d_0=0, d_m=0$ to find $A$ and $B$: 

$$
\begin{align}
d_0 &= A + B\rho^0 - \frac{0}{p-q} = A + B = 0\\
d_m &= A + B\rho^m - \frac{m}{p-q} = A + B\rho^m - \frac{m}{p-q}= 0\;,
\end{align}
$$

$A = - B$ and $-B + B\rho^m = \frac{m}{p-q}\Rightarrow (\rho^m -1)B = \frac{m}{p-q}\Rightarrow B = \frac{1}{\rho^m-1}\cdot\frac{m}{p-q}\;.$

Then

$$
\begin{align}
d_n &= A + B\rho^n - \frac{m}{p-q}\\
    &= -\frac{1}{\rho^m-1}\cdot\frac{m}{p-q} + \frac{\rho^n}{\rho^m-1}\cdot\frac{m}{p-q} - \frac{m}{p-q}\\
    &= \frac{1}{p-q}\left(m\frac{\rho^n}{\rho^m -1}-n\right)\; 
\end{align}
$$

- If $\rho = 1$, i.e $p=q=1/2$, the general solution ($\lambda_1=1, \lambda_2=1$ are solutions of the homogeneous version) has the shape

$$
d_{n} = A + nB\;.
$$

For getting a particular solution we find that both the eductated guesses (**antsazs**) $d_i=C$ and $d_i= nC$ do not work. We try $d_i=n^2C$: 

$$
\begin{align}
-1 &= pC(n^2 + 1 + 2n) - Cn^2 + qC(n-1)^2\\ 
   &= pCn^2 + pC + 2pCn) -Cn^2 + qC(n-1)^2\\ 
   &= p(Cn^2 + C + 2Cn) -Cn^2 + q(Cn^2 + C - 2Cn)\\
   &= p(Cn^2 + C + 2Cn) -Cn^2 + p(Cn^2 + C - 2Cn)\\
   &= \frac{1}{2}(Cn^2 + C + 2Cn) -Cn^2 +\frac{1}{2}(Cn^2 + C - 2Cn)\\
   &= C\;.
\end{align}
$$

and the resulting general solution is: 

$$
d_{n} = A + nB + Cn^2 = A + nB - n^2\;.
$$

Then, we exploit again the the **boundary conditions** $d_0=0, d_m=0$ to find $A$ and $B$:

$$
\begin{align}
d_0 &= A + 0B - n^2 = A = 0\\
d_m &= A + mB - n^2 = mB - m^2= 0\Rightarrow B = m\;,
\end{align}
$$

And for $A=0, B=m$ the general solution is 

$$
d_{n} = A + nB - n^2 = mn - n^2 = n(m - n)\;,
$$

which clearly tells us that the hitting time of $n$ is $O(n^2)$ por $p=q=1/2$ since we have equal probability of go back and forth. 

Summarizing 

$$
d_n = 
\begin{cases}
  \frac{1}{p-q}\left(m\frac{\rho^n}{\rho^m -1}-n\right) \;\text{if}\; p\neq q\\[2ex]
  n(m - n) \;\text{if}\; p = q\\[2ex]
\end{cases}
\;\;\;\;i.e.\;\;\;\; 
r_n = 
\begin{cases}
  \frac{1}{p-q}\left(m\frac{\left(\frac{q}{p}\right)^n-0}{\left(\frac{q}{p}\right)^m -1}-n\right) \;\text{if}\; p\neq q\\[2ex]
  n(m - n) \;\text{if}\; p=q\\[2ex]
\end{cases}
$$

**Result for the ubiased walk**. If $p=q=1/2$ the hitting time of $x=m$ from $n$ is $O(n^2)$ since we have equal probability of go back and forth. 

The behavior for $m\rightarrow\infty$ is obvious: 

$$
\lim_{m\rightarrow\infty}n(m - n) = \infty\;, 
$$

since $m$ becomes impossible to be reached from $n$. 

**Result for the biased walk**. If $p\neq q$ and $p\ll q$, the walk is drifted to the left and this means that $\rho\gg 1$, $m$ is amplified and the hitting time from $n$ increases notably. However, if $p\gg q$, $m$ is attenuated and this reduces the hitting time from $n$. 

Actually, the behavior for $m\rightarrow\infty$ is: 

$$
\begin{align}
\lim_{m\rightarrow\infty} \frac{1}{p-q}\left(m\frac{\rho^n}{\rho^m -1}-n\right) &= \lim_{m\rightarrow\infty}\frac{1}{p-q}\left(m\frac{\frac{\rho^n}{\rho^m}}{\frac{\rho^m}{\rho^m} -\frac{1}{\rho^m}}-n\right)\\
&=  \lim_{m\rightarrow\infty}\frac{1}{p-q}\left(m\frac{\frac{\rho^n}{\rho^m}}{1 -\frac{1}{\rho^m}}-n\right)\\
&=  \lim_{m\rightarrow\infty}\frac{1}{p-q}\left(m\frac{\rho^n}{\rho^m}-n\right)\\ 
\end{align}
$$

We have two cases: 
- If $q>p$, then $\rho^m\gg m$ and $\lim_{m\rightarrow\infty}\frac{1}{p-q}\left(m\frac{\rho^n}{\rho^m}-n\right)$ = $\frac{1}{p-q}(-n)= \frac{1}{q-p}(n)$. Then, the hitting time is a fraction of $n$. 

- If $p>q$, then $\rho^m\ll m$ and $m$ is amplified wrt $n$, increasing the hitting time. 

[//]: https://discrete.openmathbooks.org/dmoi3/sec_recurrence.html

[//]: https://www.youtube.com/watch?v=vEsUsaK1HBk

[//]: https://web.williams.edu/Mathematics/sjmiller/public_html/331Sp17/handouts/ProbLifesaver_Recurrences.pdf


<span style="color:#347fc9">**Exercise**. Solve questions Q1 and Q2 for the **path** graph $P_{m+1}$, where it has $m+1$ nodes from $0$ to $m=5$ but without asorbing states? 
</span>

The graph is in 



