# Chapter 6: Quantum Search

This page collects the notes of chapter 6 of the book *Quantum Computation and Quantum Information* by Nielsen and Chuang.

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
    + To gain further speedup, we should make use of the structure of the oracle.
+ Black box algorithm limits
    + $Q_2(F)\geq\widetilde{deg}(F)/2$, where $Q_2$ is the bounded error quantum complexity (with success probability at least 2/3) and $\widetilde{deg}$ is the degree of the approximation polynomial such that $|p(X)-F(X)|<1/3$;
    + Without extra information about the structure of the black box oracle function $f$, no exponential speedup over classical algorithms is possible.
