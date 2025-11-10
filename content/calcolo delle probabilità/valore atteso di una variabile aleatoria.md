---
updated_at: 2025-11-10T14:54:39.151+01:00
---
> Il *valore atteso*, o [[media]] di una [[variabili aleatorie|variabile aleatoria]] $X$ è dato da

$$
\mathbb{E}(X) := \sum_{x \in S_{X}} x \cdot p_{x} \underset{p_{x} = \mathbb{P}(X = x)}{=} \sum_{x \in S_{X}}x \cdot \mathbb{P}(X=x)
$$

# Proprietà del valore atteso di una variabile aleatoria

1. Se $X \geq 0$ allora $\mathbb{E}(X) \geq 0$.
2. Se $\lambda \in \mathbb{R}$, allora $\mathbb{E}(\lambda X) = \lambda \cdot \mathbb{E}(X)$.
3. Se $\mathbb{E}(X+Y)= \mathbb{E}(X) + \mathbb{E}(Y)$.
4. *2* e *3* ci dicono che il valore atteso è **lineare**, ossia $\mathbb{E}(aX + bY) = a \mathbb{E}(X) + b \mathbb{E}(Y)\ \forall a, b \in \mathbb{R}$.
5. Valore atteso di un [[funzione]] di $X$:
   Se $X$ è una variabile aleatoria, e $g: S_{X} \to \mathbb{R}$ è una funzione, definiamo la variabile aleatoria $g(x)$, ponendo $g(x)(\omega) = g(X(\omega))$, allora vale che $\mathbb{E}(g(x))=\sum_{x \in S_{X}}g(x) \cdot p_{x}$.

# Esempi

## 1. [[distribuzione di Bernoulli]]

$$
X \sim \text{Bernoulli}(p),\ \text{allora}\ S_{X} = \{0, 1\}
$$

> Si legge $X$ *ha legge Bernoulli con parametro p*.

Quindi con $p_{1} = p$ e con $p_{0} = 1-p$.

Quindi $\mathbb{E}(X) = \sum_{x \in S_{X}} x \cdot p_{x}= 0 \cdot p_{n} + 1 \cdot p_{1} = p$.

> Osservazione: se tutti i valori assunti sono [[esiti equiprobabili|equiprobabili]], ossia $\forall x \in S_{x}(p_{x} = p)$, allora $\mathbb{E}(X)=p \cdot \sum_{x \in S_{X}} x$.

## 2. [[distribuzione binomiale]]

$$
X \sim \text{Binomiale}(N, p)
$$

Dove $N$ è il numero di lanci e $p$ è la probabilità di testa ad ogni lancio.

Qui $S_{X} = \{0, 1, 2, \ldots, N\}$ e $p_{k} = \binom{N}{k} p^{k}(1-p)^{N-k}$.

Il valore atteso da $X$ è dato da

$$
\mathbb{E}(X)= \sum_{x \in S_{X}}x \cdot p_{x} = \sum_{k=0}^{N}k \cdot p_{k} = \sum_{k=0}^{N}k \binom{N}{k}p^{k}(1-p)^{N-k} = \sum_{k=0}^{N}k \cdot \frac{N!}{k!(N-k)!} p^{k}(1-p)^{N-k}
$$

$$
 = 0 + \sum_{k=1}^{N}k \cdot \frac{N!}{k!(N-k)!}p^{k}(1-p)^{N-k}=\sum_{k=1}^{N}k \cdot \frac{N!}{k \cdot (k-1)! (N-k)!} p^{k}(1-p)^{N-k} = \sum_{k=1}^{N} \frac{N!}{(k-1)! (N-k)!} p^{k}(1-p)^{N-k} = 
$$

$$
= p \sum_{k=1}^{N}\frac{N!}{(k-1)((N-1)-(k-1))!}p^{k-1}(1-p)^{(N-1)-(k-1)}
$$

Cambio di variabile $k' = k-1$

$$
= p \sum_{k'=0}^{n-1}\frac{N(N-1)!}{k'!(N-1-k')!}p^{k} (1-p)^{N-1-k'} 
= N \cdot p \cdot \sum_{k'=0}^{n-1}\frac{(N-1)!}{k'!((N-1)-k')!}p^{k} (1-p)^{(N-1)-k'} = N_{p} 
$$

$$
N \cdot p \cdot \boxed{\sum_{k=0}^{N}k \cdot \frac{N!}{k!(N-k)!} p^{k}(1-p)^{N-k}} = N \cdot p
$$

Perché la somma di tutti i pesetti della distribuzione binomiale fa $1$.

## 3. [[distribuzione geometrica]]

$$
X \sim \text{Geometrica}(p)
$$

$$
S_{X} = \{1, 2, 3, \ldots\}\ \text{con}\ p_{k} = (1-p)^{k-1}p
$$

$$
\mathbb{E}(X) = \sum_{x \in S_{X}} x \cdot p_{x}= \sum_{k=1}^{+\infty}k\cdot p_{k} = \sum_{k=1}^{+\infty} k \cdot (1-p)^{k-1}p= p \cdot \sum_{k=1}^{+\infty}k \cdot (1-p)^{k-1} \underset{\text{sm genius ahh wizardry 🥀}}{=} -p \cdot \frac{d}{dp}\left(\sum_{k=1}^{+\infty}(1-p)^{k}\right)
$$

$$
= - p \cdot \frac{d}{dp}\left(\frac{1}{1-(1-p)}-1\right) = - p \cdot \frac{d}{dp}\left(\frac{1}{p}-1\right) = -p \cdot \left(\frac{-1}{p^{2}}\right) = \frac{1}{p}
$$

## 4. [[distribuzione di Poisson 🐟]]

$$
X \sim \text{Poisson}(\lambda),\ \lambda > 0,\ S_{x} = \{0, 1, 2, 3, \ldots\}
$$

$$
\mathbb{E}(X) = \sum_{x\in S_{X}} x \cdot p_{x} = \sum_{k=0}^{+\infty}k \cdot \frac{e^{-\lambda}\lambda^{k}}{k!} = e^{-\lambda} \cdot \sum_{k=1}^{+\infty}\frac{\lambda^{(k-1)+1}}{(k-1)!} = \lambda e^{-\lambda} \sum_{k=1}^{\infty}\frac{\lambda^{k-1}}{(k-1)!} \underset{k'=k-1}{=} \lambda e^{-\lambda} \sum_{k'=0}^{+\infty}\frac{\lambda^{k'}}{k'!}
$$

$$
= \lambda \cdot \boxed{\sum^{\infty}_{k=0}\frac{e^{-\lambda}\lambda^{k}}{k!}} = \lambda
$$

## 5. lancio un dado. Sia $X$ il valore ottenuto

$$
\mathbb{E}(X) = \sum_{x \in S_{X}}x \cdot p_{x} = \sum_{k=1}^{6}k \cdot \frac{1}{6} = \frac{1}{6} \left(\sum_{k=1}^{6}k\right) = \frac{21}{6} = 3.5
$$