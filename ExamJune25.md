## Assignment 06/25  



### The multi-Choose Sum
<span style="color:#347fc9">**Exercise**. We have $3$ natural numbers, including $0$ (whatever they are, this is actually the question). Then: </span> 

 <span style="color:#347fc9">**a)** How may **ways do we have of summing three numbers** so that the result is exacltly $10$?</span> 
 <br></br>
 <span style="color:#347fc9">**b)** How may **ways do we have of summing three numbers** so that the result is exacltly $10$ **but** no-one can be $0$?</span>
<br></br>
<span style="color:#347fc9">First of all, **we can repeat** the numbers (they are not necessarily different) and the **order does not matter** (the sum is invariant to order). This is a **really good candidate to a multi-choose problem or combinations-with-repetitions**. 
</span>
<br></br>
<span style="color:#347fc9">Then, we identify the elements of the problem: three variables $x_1$, $x_2$ and $x_3$, each one for the numbers we want to sum. Then, in **a)**  we must solve these variables for   
</span>
<br></br>
<span style="color:#347fc9">
 $
 x_1 + x_2 + x_3= 10\;.
 $
</span>
<br></br>
<span style="color:#347fc9">The **general solution** (without constraints) is 
</span>
<br></br>
<span style="color:#347fc9">
$
C_{\sigma}(m=3,k=10) = \left(\!\!{m\choose k}\!\!\right) = {k + m - 1\choose k} = \left(\!\!{3\choose 10}\!\!\right) = {3 + 10 - 1\choose 10} = {12\choose 10}= 12\cdot 11\cdot 10!/(2!\cdot 10!) = 66 \;.
$
</span>
<br></br>

<span style="color:#347fc9">**b)** We have a minimal value for the numbers: $x_i\ge 1\;$. Then, we "take" these values by making $y_i = x_i - 1$ and solve the problem. 
</span> 
<br></br>
<span style="color:#347fc9">
 $
 y_1 + y_2 + y_3= 10-3 = 7\;.
 $
</span>
<br></br>
<span style="color:#347fc9">The **solutions** is 
 $
C_{\sigma}(m=3,k=7) = \left(\!\!{m\choose k}\!\!\right) = {k + m - 1\choose k} = \left(\!\!{3\choose 7}\!\!\right) = {3 + 7 - 1\choose 7} = {9\choose 7}= 9\cdot 8\cdot 7!/(2!\cdot 7!) = 36 \;.
$ 
</span>
<br></br>
<span style="color:#347fc9">Some of the **solutions** and their transformations after **undoing** $y_i = x_i - 1$, so that $x_1 + x_2 + x_3 = 10$, are
</span>
<span style="color:#347fc9">
$
\begin{align}
& (0\;0\;7)\rightarrow (1\;1\;8)\\
& (1\;0\;6)\rightarrow (2\;1\;7)\\
& (2\;1\;4)\rightarrow (3\;2\;5)\\
& (3\;2\;2)\rightarrow (4\;3\;3)\\
& (4\;1\;2)\rightarrow (5\;2\;3)\\
\end{align}
$
</span>
<br></br>
<span style="color:#347fc9">**Additional explanation to the problem**. In other words, from the $66$ solutions for the general unconstrained problem, removing the posibilities of any of the $x_i=0$ reduces the solution space to only $36$, i.e. $66-36=30$ solutions are lost. This is not difficult  to prove since we have to discard, in addition to $(10\;0\;0)$,$(0\;10\;0)$ and $(0\;0\;10)$, solutions where they have a **unique** zero and the remaining slots sum $10$. For instance: $(1\;9\;0),(2\;8\;0),(3\;7\;0),(4\;6\;0),(5\;5\;0),(6\;4\;0),(7\;3\;0),(8\;2\;0)$ and $(9\;1\;0)$ [a block of $9$ solutions]. Since we can do this in $3$ different slots we have $9\cdot 3 + 3 = 27 + 3 = 30$ solutions to remove!
</span> 
<br></br>

### Gaussians and Binomials
<span style="color:#347fc9">**Exercise**. It is well known that the Binomial distribution $B(n,p)$ converges to the Gaussian distribution for large values of $n$. 
<br></br>
Given $X\sim B(n,p)$ **compute the following probability** $P(E(X)-2 \le X \le E(X)+2)$ under 2 conditions: **a)** $n=100, p=q$ and **b)** $n=100, p=1/4$. **c)** How are both **results related** and why if so?
</span>
<br></br>
<span style="color:#347fc9">
The expectation of $X$ is $E(X)=np$. Therefore we need to find $P(np-2 \le X \le np+2)$. Then: 
</span>
<br></br>
<span style="color:#347fc9">
$
P(np-2 \le X \le np+2) = P(X \le np+2)-P(X \le np-2)
$
</span>
<br></br>
<span style="color:#347fc9">
$
\begin{align}
P(X \le np+2) &= \phi\left(\frac{np+2 - np}{\sqrt{npq}}\right) =  \phi\left(\frac{2}{\sqrt{npq}}\right)\\
P(X \le np-2) &= \phi\left(\frac{np-2 - np}{\sqrt{npq}}\right) = \phi\left(\frac{-2}{\sqrt{npq}}\right)
\end{align}
$
</span>
<br></br>
<span style="color:#347fc9">
**a)** For $n=100, p=q=1/2$ we have $\mathbf{E(X)=np=50}$ and
</span>
<br></br>
<span style="color:#347fc9">
$
\begin{align}
\phi\left(\frac{2}{\sqrt{npq}}\right)  &= \phi\left(\frac{2}{\sqrt{100\frac{1}{2}\frac{1}{2}}}\right) = 
\phi\left(\frac{2}{10\cdot \frac{1}{2}}\right) = \phi\left(\frac{2}{5}\right)=\phi\left(0.4\right)=0.6554\\
\phi\left(\frac{-2}{\sqrt{npq}}\right)  &= \phi\left(\frac{-2}{\sqrt{100\frac{1}{2}\frac{1}{2}}}\right) = 
\phi\left(\frac{-2}{10\cdot \frac{1}{2}}\right) = \phi\left(-\frac{2}{5}\right)=\phi\left(-0.4\right)=0.3446\\
\\
& \mathbf{P(X \le 52) - P(X \le 48) = \phi\left(0.4\right) - \phi\left(-0.4\right) = 0.6554 - 0.3446 = 0.3108}\;. 
\end{align}
$
</span>
<br></br>
<span style="color:#347fc9">
**b)** For $n=100, p=1/4$ we have $\mathbf{E(X)=np=25}$ and
</span>
<br></br>
<span style="color:#347fc9">
$
\begin{align}
\phi\left(\frac{2}{\sqrt{npq}}\right)  &= \phi\left(\frac{2}{\sqrt{100\frac{1}{4}\frac{3}{4}}}\right) = 
\phi\left(\frac{2}{10\cdot \frac{\sqrt{3}}{4}}\right) = \phi\left(\frac{2}{4.3}\right)=\phi\left(0.46\right)=0.6772\\
\phi\left(\frac{-2}{\sqrt{npq}}\right)  &= \phi\left(\frac{-2}{\sqrt{100\frac{1}{4}\frac{3}{4}}}\right) = 
\phi\left(\frac{-2}{10\cdot \frac{\sqrt{3}}{4}}\right) = \phi\left(-\frac{2}{4.3}\right)=\phi\left(-0.46\right)=0.3228\\
\\
& \mathbf{P(X \le 27) - P(X \le 23) = \phi\left(0.46\right) - \phi\left(-0.46\right) = 0.6772 - 0.3228= 0.3544}\;. 
\end{align}
$
</span>
<br></br>
<span style="color:#347fc9">
**c)** There are small differences in both results but the highest probability is given in **b)**. Basically, what happens is that in this latter case the standard deviation is $4.3$ whereas in the first case is $5$. Smaller normalization in the standarized variables lead to higher values of $\phi(.)$ when fixing the numerators to $2$ and $-2$. 
</span>
<br></br>

###  The Barbell graph
<span style="color:#347fc9">The **Barbell graph** $B_{m}$ results from joining two **complete graphs** $K_m$ (without loops) with a single edge (known as the "bottleneck"). For $m=4$ we have $n=2m=8$ nodes. 
<br></br>
In {numref}`Barbell` we show the non-trivial eigevector on the Laplacian, the spectrum $\tilde{\lambda}_i$ of the normalized Laplacian $\tilde{\triangle}$ and eigenvectors $\phi_i$ of the normalized Laplacian $\tilde{\triangle}$. 
</span>.

```{figure} ./images/Topic5/Barbellcuts.png
---
name: Barbell
width: 820px
align: center
height: 480px
---
$B_4$. Normalized Laplacian's spectrum and partitions inferred from the non-trivial eigenvectors.  
```  
<br></br>
<span style="color:#347fc9"> **a) Compute the ratio-cut losses of the partitions** induced by eigenvectors $\phi_2$, $\phi_3$ and $\phi_8$. Do the results agree with Spectral Theory?
</span>
<br></br>
<span style="color:#347fc9"> **Eigenvector** $\phi_2$ induces the partition $A_2=\{0,1,2,3\}$, $B_2=\{4,5,6,7\}$ has $\text{cut}(A_2,B_2)=1$ and 
</span>
<br></br>
<span style="color:#347fc9">
$
\text{Rcut}(A_2,B_2) = \frac{\text{cut}(A_2,B_2)}{|A_2|} + \frac{\text{cut}(A_2,B_2)}{|B_2|} = \frac{1}{4} + \frac{1}{4} = \frac{1}{2} = 0.83\;.
$
</span>
<br></br>
<span style="color:#347fc9"> **Eigenvector** $\phi_3$ induces the partition $A_3=\{0,1,2,5,6,7\}$, $B_3=\{3,4\}$ has $\text{cut}(A_3,B_3)=6$ and 
</span>
<br></br>
<span style="color:#347fc9">
$
\text{Rcut}(A_3,B_3) = \frac{\text{cut}(A_3,B_3)}{|A_3|} + \frac{\text{cut}(A_3,B_3)}{|B_3|} = \frac{6}{6} + \frac{6}{2} = 1 + 3 = 4\;.
$
</span>
<br></br>
<span style="color:#347fc9"> **Eigenvector** $\phi_8$ induces the partition $A_4=\{0,1,2,4\}$, $B_4=\{3,5,6,7\}$ has $\text{cut}(A_4,B_4)=6+1=7$ and 
</span>
<br></br>
<span style="color:#347fc9">
$
\text{Rcut}(A_4,B_4) = \frac{\text{cut}(A_4,B_4)}{|A_4|} + \frac{\text{cut}(A_4,B_4)}{|B_4|} = \frac{7}{4} + \frac{7}{4} = \frac{7}{2} = 3.5\;.
$
</span>
<br></br>
<span style="color:#347fc9">
**On SGT**. The above partitions result from the eigenvectors. When evaluating the Rcuts we see that the Fiedler vector $\phi_2$ provides the minimal Rcut ($0.83$). This is actally very consistent with Spectral Graph Theory (SGT). When we examine the Rcut of $\phi_2$'s partition, where there is a kind of sub-division of the Fiedler's partition, the Rcut suddenly climbs to $4$. There is then an agreement between SGT and discrete solutions (Rcut). However, the theoretically worst partition $\phi_8$ has  slighly smaller Rcut than $\phi_3$ which is not so consistent. 
</span>
<br></br>
<span style="color:#347fc9">
**b) Compare $\tilde{\lambda_2}$ (spectral gap) with those of other graphs (complete, star, path, cycle)  and justify why it is significantly smaller than the corresponding gaps**. The **spectral gap** of the Barbell graph ($0.11$) is significanly smaller than those of the path graph ($0.29$) and cycle ($0.6$), and off course those of the star ($1.0$) and the complete graph ($8/7=1.14)$. Actually, the Barbell graph is formed by a partition with minimal cut and maximal elements per cluster, where the **Cheeger constant** is better bounded!
</span>
<br></br>
<span style="color:#347fc9">
**c1)What is the commute time** between two nodes in a graph? The commute time $C(u,v)$ between nodes $u$ and $v$, is the expected time taken by a random walk to go from $u$ to $v$ and then return to $u$.
</span>
<span style="color:#347fc9">
**c2)Approximate the commute times** between nodes $0$ and $1$ and between $0$ and $7$.  Use only the Fiedler value and vector (use 2 decimals). NOT NECESSARY TO USE THE VOLUME. Justify the results. Why are they different if so?
</span>
<br></br>
<span style="color:#347fc9">
$
\text{vol}(G) = 2*(3 + 3 + 3) + 2*4 = 26\;.
$
</span>
<br></br>
<span style="color:#347fc9">
$
CT(0,1)=\text{vol}(G)\frac{1}{\lambda_2}[\phi_2(0)-\phi_2(1)]^2 = 26\cdot\frac{1}{0.11}[0.37-0.37]^2 = 0\;.
$
</span>
<br></br>
<span style="color:#347fc9">
$
CT(0,7)=\text{vol}(G)\frac{1}{\lambda_2}[\phi_2(0)-\phi_2(7)]^2 = 26\cdot\frac{1}{0.35}[0.37-(-0.37)]^2 = 26\cdot 4.97 = 129.43\;.
$
</span>
<br></br>
<span style="color:#347fc9">
**Comment**. The CT between $0$ and $7$ is really larger than between $0$ and $2$ since these latter ones belong to the same community and $0$ and $7$ belong to different communities. Technically, as $\tilde{\lambda_2}\rightarrow 0$, random walks starting in one community resonate inside it before crossing the "bottleneck". Statistically, the "leakage" of info between two communities becomes less and less for smaller $\tilde{\lambda_2}$. 
</span>

