# Chapter 6: Quantum Search

$$
\def\dyad#1#2{\left|#1\middle>\middle<#2\right|}
\def\inner#1#2{\left<#1\middle|#2\right>}
$$

## Takeaways

+ Grover's search & Quantum counting
    + Well-known, *verdad*?
+ Quantum search as a quantum simulation
    + The Hamiltonian must be a sum of terms like $\dyad{x}{x}$, $\dyad{\psi}{\psi}$, $\dyad{x}{\psi}$, $\dyad{\psi}{x}$, where $\ket{\psi}$ is the initial state and $\ket{x}$ is the target state;
    + Suppose the simulation step is performed to an accuracy $O(\Delta t^r)$, then the total error is $O(N^{r/2(r-1)})$;
    + But if $\Delta t = \pi$, then it's equivalent to the Grover's search algorithm.
+ Optimality of the search algorithm
    + Suppose the unstrutured search problem has $M$ solutions out of $N$, then $O(\sqrt{N/M})$ oracle calls are required to find a solution;
    + 
+ Black box algorithm limits
    + $Q_2(F)\geq\widetilde{deg}(F)/2$, where $Q_2$ is the bounded error quantum complexity (with success probability at least 2/3) and $\widetilde{deg}$ is the degree of the approximation polynomial such that $|p(X)-F(X)|<1/3$;
    + Without extra information about the structure of the black box oracle function $f$, no exponential speedup over classical algorithms is possible.

## Exercises

### Ex. 6.11

Let $\ket{x}$ be the uniform superposition of all solution states, then $H=\dyad{\psi}{\psi} + \dyad{x}{x}$.

### Ex. 6.12

(1) With the same basis we have

$$H = \begin{pmatrix}
    2\alpha & \beta \\
    \beta & 0
\end{pmatrix} = \alpha(I+Z) + \beta X,$$

thus

$$\exp(-iHt) = \exp(-i\alpha t)[\cos t\cdot I-i\sin t\cdot(\alpha Z+\beta X)].$$

Ignoring the global phase factor $\exp(-i\alpha t)$ we have

$$\ket\psi \xrightarrow{\text{after time }t} \cos t\ket\psi - i\sin t\ket{x}.$$

Choosing $t=\frac{\pi}{2}$ yields the result $\ket{x}$.

(2) *Ref: https://quantumcomputing.stackexchange.com/questions/9243*

### Ex. 6.17 (TODO)

### Problem 6.1

The algorithm is as follow:

+ First randomly choose $1\le j\le N$.
+ Then loop the following procedures:
    + Construct an oracle to implement the Boolean function $$f_j(i) = \begin{cases} 1,& x_i < x_j \\ 0,& \text{otherwise} \end{cases}.$$
    + Apply Grover's Search to $f_j$.
    + If a solution $i_0$ is found, set $j=i_0$. In contrast, if no solution can be found, break.
+ Return $j$.

Let $a_m$ be the expected number of loops to go when the current $x_j$ is the $m$-th least number in the database.
The next loop will evenly randomly return the $i$-th least number where $1\le i<m$, hence

$$a_m=1+\frac{1}{m-1}\sum_{i=1}^{m-1}a_i.$$

By substiting $m+1$ to $m$ we have

$$a_{m+1}=1+\frac{1}{m}\sum_{i=1}^{m}a_i.$$

Combining the two equations we can derive that

$$a_{m+1}=a_m+\frac{1}{m}.$$

Therefore,

$$a_{m+1}=a_1+\sum_{i=1}^m\frac{1}{i}\sim\log(m+1).$$

Since each Grover's Search requires $O(\sqrt{N})$ oracle calls, the whole algorithm requires $O(\sqrt{N}\log(N))$ oracle calls.

### Problem 6.2

(1) $U_{\ket\psi} = U(I-2\dyad{0}{0})U^\dagger$, where $I-2\dyad{0}{0}$ can be implemented like Groove's search.

(2) Apply the oracle to the Bell state $(\ket{00} + \ket{11})/\sqrt{2}$.

$$\begin{gathered}
    \frac{
        \ket{00} + \ket{11}
    }{
        \sqrt{2}
    } \overset{
        U_{\ket{\psi_1}}
    }{
        \longrightarrow
    } \frac{
        \ket{00} - \ket{11}
    }{
        \sqrt{2}
    },
    \\
    \frac{
        \ket{00} + \ket{11}
    }{
        \sqrt{2}
    } \overset{
        U_{\ket{\psi_2}}
    }{
        \longrightarrow
    } \frac{
        \ket{01} + \ket{01}
    }{
        \sqrt{2}
    },
    \\
    \frac{
        \ket{00} + \ket{11}
    }{
        \sqrt{2}
    } \overset{
        U_{\ket{\psi_3}}
    }{
        \longrightarrow
    } i\frac{
        \ket{01} - \ket{10}
    }{
        \sqrt{2}
    }.
\end{gathered}$$

Measure the result in the Bell basis and we can identify the oracle.

(3) TODO

### Problem 6.3 (TODO)

### Problem 6.4 (TODO)
