---
updated_at: 2025-10-27T14:57:42.766+01:00
---
> La distribuzione di Poisson con parametro $\lambda \in \mathbb{R}_{+}$ è la misura di [[probabilità]] sullo [[spazio campionario]] $\Omega = \mathbb{N}$ definita dai pesetti 

$$
p_{k} = \frac{e^{-\lambda}\lambda^{k}}{k!},\ k \in \mathbb{N}
$$

Verifichiamo che $\forall k \in \mathbb{N}^{\star} (p_{k} \in [0, 1]) \land \sum_{k=1}^{+\infty}p_{k} = 1$:

1. La prima probabilità è [[misura di probabilità#^7cf400|verificata immediatamente]]
2. $\sum_{k=0}^{+\infty}p_{k} = \sum_{k=0}^{+\infty} \frac{e^{-\lambda}\lambda^{k}}{k!} = e^{-\lambda} \sum_{k=0}^{+\infty} \frac{\lambda^{k}}{k!} \underset{\text{Taylor}}{=}e^{-\lambda}e^{\lambda} = 1 \quad \checkmark$

# Intuizione

> Seguendo l'esempio dei lanci di monete truccate, la distribuzione di Poisson definisce *la proporzione di teste in infiniti lanci di monete con probabilità $p$*.

Con un numero finito di lanci avremo la probabilità di testa data da

$$
p=\frac{\lambda}{N}
$$

Intuitivamente mi aspetto $N\frac{\lambda}{N}=\lambda$ teste.

Sia $p_{k}\left(N, \frac{\lambda}{N}\right) := \text{probabilità di vedere k teste in N lanci, con}\ p=\frac{\lambda}{N} = \binom{N}{k}{\binom{\lambda}{N}}^{l} \cdot (1 - \frac{\lambda}{N})^{N-k}$

Abbiamo semplicemente usato la [[distribuzione binomiale]].

Ora basta verificare con un [[limite]] tendente a infinito che

$$
p_{k}\left(N, \frac{\lambda}{N}\right) \overset{N \to \infty}{\longrightarrow} \frac{e^{-\lambda} \lambda^{k}}{k!}
$$