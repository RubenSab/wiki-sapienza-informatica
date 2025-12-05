---
updated_at: 2025-12-05T14:28:08.415+01:00
---
> Volendo parlare di [[probabilità]] continua, non si possono generalizzare le proprietà viste finora su [[spazio campionario|spazi campionari]] discreti. Ad esempio, sull'intervallo continuo $[0, 1]$, non si può definire una [[misura di probabilità]] uniforme, perché ci sarebbero infiniti pesetti.

Per ottenere una *misura di probabilità continua*, invece di definire i pesetti dei singoli punti, dobbiamo definire la **probabilità degli intervalli**.

# Funzione di densità

Una [[funzione]] $f: \mathbb{R} \to \mathbb{R}$ è detta *funzione di densità* o *funzione di densità di probabilità* se:

- $\forall x \in \mathbb{R} \quad f(x) \geq 0$
- $\int_{-\infty}^{+\infty}f(x)\ dx = 1$

# Misura di probabilità continua

> Data una funzione di densità $f: \mathbb{R} \to \mathbb{R}$, la misura di probabilità associata a un [[sottoinsiemi|sottoinsieme]] $A$ di $\mathbb{R}$ è data dall'integrale:

$$
\mathbb{P}(\underset{A \subseteq \mathbb{R}}{A}) = \underset{A}{\int} f(x)\ dx
$$

> La probabilità di un sottoinsieme di $\mathbb{R}$ si dice la sua *lunghezza*.

Osservazioni:

- $\mathbb{P}((-\infty, + \infty)) = 1$
- $\mathbb{P}(\emptyset) = 0$
- Se $A, B$ sono disgiunti, $\mathbb{P}(A \cup B)$

## Esempi

1. $f(x) = \begin{cases} 1 \quad \forall x \in [0,1] \\ 0 \quad \text{altrimenti} \end{cases}$ è una funzione di densità, perché ha tutti valori positivi e integra a $1$. Quindi $\mathbb{P}(A) = \underset{A}{\int} f(x)\ dx = \underset{A}{\int} \mathbb{1}_{[0,1]}(x)\ dx = |A \cap [0,1]|$, perché in questo caso $f(x)$ è la [[variabile aleatoria indicatrice]].

> In generale, per $a, b \in \mathbb{R},\ a<b$ possiamo definire:

$$
f(x) = \frac{\mathbb{1}_{[a,b]}(x)}{b-a} = f(x) = \begin{cases} \frac{1}{b-a} \quad \forall x \in [0,1] \\ 0 \quad \text{altrimenti} \end{cases}
$$

Questa è una funzione di densità? Sì, perché è sempre positiva e integra sempre a $1$. Abbiamo modificato la funzione dell'esempio 1. per fare in modo che integrasse sempre a $1$. Nell'esempio ciò non serviva perché $b-a = 1-0 = 1$.

2. La funzione $f(x) = \frac{e^{-|x|}}{2}$ è una funzione di densità, perché ha tutti valori positivi e integra a $1$. Curiosità: per questa distribuzione di probabilità si ha la stessa probabilità che scegliendo un numero a caso da $R$, si prenda un numero negativo o uno positivo, perché $f(x)$ è **pari**, quindi l'area sottesa a $f(x),\ x \geq 0$ è la stessa sottesa a $f(x),\ x < 0$.