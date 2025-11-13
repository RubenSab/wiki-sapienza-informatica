---
updated_at: 2025-11-12T14:35:29.200+01:00
---
> Il *valore atteso*, o media di una [[variabili aleatorie|variabile aleatoria]] $X$ è dato da

$$
\mathbb{E}(X) := \sum_{x \in S_{X}} x \cdot p_{x} \underset{p_{x} = \mathbb{P}(X = x)}{=} \sum_{x \in S_{X}}x \cdot \mathbb{P}(X=x)
$$

> N.B.: Se la domma che definisce $\mathbb{E}(x)$ è data da un numero infinito di termini (quindi non è un somma, è una [[serie]]), ci vuole un po' di cautela bisogna controllare che la somma sia ben definita.

Esempio:

$$
\sum_{k=1}^{\infty}(-1)^{k} = -1+1-1-1+1-1+1+\ldots
$$

Questa somma, a seconda dell'ordine in cui sommiamo gli addendi, può assumere risultati diversi, quindi non è ben definita.

Questo problema potrebbe sorgere nel calcolare il valore atteso di una variabile aleatoria a valori in $\mathbb{Z}$ (o per [[sottoinsiemi]] infiniti di $\mathbb{Z}$).

Esempio: Sia $X$ una variabile aleatoria a valori in $\mathbb{Z}$ con legge data dai pesetti $(p_{k})_{k \in \mathbb{Z}}$ con

$$
\begin{cases} p_{k} = \frac{3}{\pi} \cdot \frac{1}{k^{2}},\ k \neq 0 \\ p_{0} = 0\end{cases}
$$

$$
\sum_{k \in \mathbb{Z}}^{\infty} p_{k} = \sum_{k \in \mathbb{Z}}^\infty \frac{3}{\pi} \cdot \frac{1}{k^{2}} = \frac{6}{\pi^{2}} \cdot \sum_{k=1}^{\infty} \frac{1}{k^{2}} = \frac{6}{\pi^{2}}\cdot \frac{\pi^{2}}{6}= 1
$$

Nota, questa variabile aleatoria ha una legge simmetrica, ossia $\forall k \neq 0\ (\mathbb{P}(X=k)= \mathbb{P}(X = -k) = \frac{3}{\pi} \cdot \frac{1}{k^{2}})$

# Proprietà del valore atteso di una variabile aleatoria

$S_{x} \subseteq [0, \infty)$

 > N.B.: $\forall \lambda \in \mathbb{R}\ (\mathbb{E}(\lambda) = \lambda)$
 
1. Se $X \geq 0$ allora $\mathbb{E}(X) \geq 0$.
2. Se $\lambda \in \mathbb{R}$, allora $\mathbb{E}(\lambda X) = \lambda \cdot \mathbb{E}(X)$.
3. Se $\mathbb{E}(X+Y)= \mathbb{E}(X) + \mathbb{E}(Y)$.
4. *2* e *3* ci dicono che il valore atteso è **lineare**, ossia $\mathbb{E}(aX + bY) = a \mathbb{E}(X) + b \mathbb{E}(Y)\ \forall a, b \in \mathbb{R}$.
5. Valore atteso di un [[funzione]] di $X$:
   Se $X$ è una variabile aleatoria a valori in $S_{x}$, e $g: S_{X} \to \mathbb{R}$ è una funzione, allora vale che $\mathbb{E}(g(x))=\sum_{x \in S_{X}}g(x) \cdot \mathbb{P}(X = x)$.

## Perché la proprietà 4 è utile?

Esempio: Lancio 2 dadi. Siano $X$ e $Y$ le variabili aleatorie che registrano i risultati del primo e del secondo lancio rispettivamente.

Ovviamente $X$ e $Y$ sono uniformemente distribuite perché i numeri sui dadi sono [[esiti equiprobabili]].

Voglio calcolare, in media, il valore della somma dei due lanci.

Sia $S = X + Y$ la variabile aleatoria che registra la somma dei due lanci.

$$
\mathbb{E}(S) = \mathbb{E}(X) + \mathbb{E}(Y) = 2 \mathbb{E}(X) = \frac{42}{6} = 7
$$

$$
\mathbb{E}(X) = \sum_{k=1}^{6} k \cdot \frac{1}{6} = \frac{21}{6}
$$

Senza usare la linearità, avremmo dovuto calcolare $\mathbb{P}(S=k) \forall k = 2, \ldots, 12$ e quindi

$$
\mathbb{E}(X) = \sum_{k=2}^{12}k \cdot \mathbb{P}(S = k)
$$
Che è un calcolo mostruoso.

Generalizziamo. Lanciando $N$ dadi e siano $X_{1}, X_{2}, \ldots, X_{N}$ Le variabili aleatorie che registrano il risultato dei lanci $1, 2, \ldots, N$.

Allora:

$$
\mathbb{E}\left(\sum_{k=1}^{N}X_{k}\right) = \sum_{k=1}^{N}\mathbb{E}(X_{k}) = N \cdot \mathbb{E}(X_{1}) = \frac{21}{6} N
$$

## Cosa succede se facciamo il prodotto di variabili aleatorie?

Esempio: lancio due dadi, e siano $X$ e $Y$ due variabili aleatorie che registrano il risultato dei due lanci. Voglio calcolare il prodotto atteso dei risultati.

Osserviamo che $X$ e $Y$ sono variabili aleatorie indipendenti, poiché

$$
\forall i, j \in \{1, 2, 3, 4, 5, 6\}\ (\ \mathbb{P}(X = i,\ Y = j) = \mathbb{P}(X=1) \cdot \mathbb{P}(Y = j)\ )
$$

Quindi $\mathbb{E}(X \cdot Y) = \mathbb{E}(X) \cdot \mathbb{E}(Y) = \left(\frac{21}{6}\right)^{2}$

Generalizzando con $N$ dadi si ottiene che $\mathbb{E}\left(\prod_{k=1}^{N}X_{k}\right)=\left(\frac{21}{6}\right)^{N}$.

## Esempio della proprietà 5

Lancio un dado, sia $X$ la variabile aleatoria che registra il risultato. Allora $\mathbb{E}(X^{2}) = \mathbb{E}(g(x)) = \sum_{x \in S_{x}}x^{2} \cdot \mathbb{P}(X=x) = \sum_{k=1}^{6} k^{2} \cdot \frac{1}{6} = \frac{1}{6} \cdot 91 = \frac{91}{6}$

# Esempi di variabili aleatorie

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