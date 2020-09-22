# Limit behaviour of solutions of linear ODEs

## General theory (reminder)

Consider $\dot x=Ax$.

* If $Av=λv$, then $x(t)=e^{λt}v$ is a solution of $\dot x=Ax$.
* If $A$ is diagonalizable, then *any* solution is a linear combination of $e^{λ_kt}v_k$: $x(t)=\sum_{k=1}^nc_ke^{λ_kt}v_k$.

## Limit behaviour

What happens to a *generic* solution $x(t)$ of $\dot x=Ax$ as $t→∞$? Here “generic” means that we can ignore finitely many lines on the plane (or hyperplanes in the space).

### Diagonalizable systems

If $A$ is diagonalizable, then $x(t)=c₁e^{λ₁t}v₁+c₂e^{λ₂t}v₂$. The limit behaviour depends on the order of $λ₁$, $λ₂$, and $0$ on the real line.
We assume $λ₁≤λ₂$, otherwise we swap the indices $1$ and $2$. We also exclude the cases corresponding to degenerate matrices (i.e., we assume that $λ₁λ₂≠0$).

| Name                     | Inequalities | Limit behaviour of a generic orbit | Genericity assumption | Otherwise                            |
| :--- | :---: | :--- | :---: | :---: |
| Saddle point             | $λ₁<0<λ₂$    | $x(t)≈c₂e^{λ₂t}v₂→∞$               | $c₂≠0$                | $x(t)=c_1e^{λ_1t}v_1→0$                 |
| Stable node              | $λ₁<λ₂<0$    | $x(t)≈c₂e^{λ₂t}v₂→0$               | $c₂≠0$                | $x(t)=c_1e^{λ_1t}v_1→0$                 |
| Unstable node            | $0<λ₁<λ₂$    | $x(t)≈c₂e^{λ₂t}v₂→∞$               | $c₂≠0$                | $x(t)=c_1e^{λ_1t}v_1→∞$ unless $x(t)=0$ |
| Stable dicritical node   | $λ₁=λ₂<0$    | $x(t)=e^{λ₁t}x(0)→0$               | -                     | -                                    |
| Unstable dicritical node | $0<λ₁=λ₂$    | $x(t)=e^{λ₁t}x(0)→∞$               | $x(0)≠0$              | $x(t)=0$                             |

### Complex eigenvalues

If $A$ has complex eigenvalues $λ=a+bi$ and $\bar λ=a-bi$, then the solutions are given by $x(t)=e^{at}\left[(c₁\cos(bt)+c₂\sin(bt))v+(c₂\cos(bt)-c₁\sin(bt))w\right]$, where $v+iw$ is an eigenvector corresponding to $λ=a+bi$. The limit behaviour of a generic orbit depends on the sign of $a$.

| Name           | (In)equalities | Limit behaviour of a generic orbit | Genericity assumption | Otherwise |
|----------------|----------------|------------------------------------|-----------------------|-----------|
| Stable focus   | $a<0$          | $x(t)→0$, $C_1e^{at}\le\|x(t)\|\le C_2e^{at}$       | -                     | -         |
| Unstable focus | $a>0$          | $x(t)→∞$, $C_1e^{at}\le\|x(t)\|\le C_2e^{at}$       | $x(0)≠0$              | $x(t)=0$  |
| Center         | $a=0$          | $x(t)$ is periodic                 | -                     | -         |



