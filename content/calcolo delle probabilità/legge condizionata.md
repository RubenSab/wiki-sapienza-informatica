---
updated_at: 2025-11-26T14:53:59.971+01:00
---
Siano $X$ e $Y$ due [[variabili aleatorie]] a valori in $S_{X}$ e $S_{Y}$ rispettivamente. Sia $y \in S_{Y}$ tale che $\mathbb{P}(Y-y)=p_{y}^{Y} > 0$.

> La *legge di $X$ [[probabilità condizionata|condizionata]] all'[[evento]]* $\{Y = y\}$ è la [[misura di probabilità]] su $S_{X}$ data dai pesetti

$$
\forall x \in S_{X} \quad p_{x \mid y} = \mathbb{P}(\{X = x \mid Y = y\}) = \frac{\mathbb{P}(X = x, Y = y)}{\mathbb{P}(Y = y)}
$$
# Dimostrazione della validità della misura di probabilità

$$
\sum_{x \in S_{X}} \mathbb{P}(X = x \mid Y = y) = \sum_{x \in S_{X}} \frac{\mathbb{P}(X = x, Y = y)}{\mathbb{P}(Y = y)} = \frac{1}{\mathbb{P}(Y = y)} \cdot \mathbb{P}(Y = y) = 1
$$

$$
 \implies \sum_{x \in S_{X}} \mathbb{P}(X = x \mid Y = y) = 1
$$

> N.B.: Se $X$ e $Y$ sono [[indipendenza di due eventi|indipendenti]], la legge di $X$ condizionata a $\{Y = y\}$ è uguale alla legge non condizionata di $X$, poiché

$$
\mathbb{P}(X = x \mid Y = y) = \frac{\mathbb{P}(X = x, Y = y)}{\mathbb{P}(Y = y)} = \frac{\mathbb{P}(X = x) \cdot \mathbb{P}(Y = y)}{\mathbb{P}(Y = y)} = \mathbb{P}(X)
$$

# Valore atteso di $X$ condizionato a $\{Y = y\}$

> Il [[valore atteso di una variabile aleatoria|valore atteso]] di $X$ condizionato all'evento $\{Y = y\}$ è dato da:

$$
\mathbb{E}(X \mid Y = y) = \sum_{x \in S_{X}} x \cdot \mathbb{P}(X = x \mid Y = y)
$$

# Esempio: lancio due dadi

- Sia $X$ la variabile aleatoria che registra il risultato del primo lancio.
- Sia $Y$ la variabile aleatoria che registra il minimo dei due valori ottenuti.

| $Y/X$ | 1        | 2        | 3        | 4        | 5        | 6        |
| ----- | -------- | -------- | -------- | -------- | -------- | -------- |
| **1** | $$1/36$$ | $$0$$    | $$0$$    | $$0$$    | $$0$$    | $$0$$    |
| **2** | $$1/36$$ | $$2/36$$ | $$0$$    | $$0$$    | $$0$$    | $$0$$    |
| **3** | $$1/36$$ | $$1/36$$ | $$3/36$$ | $$0$$    | $$0$$    | $$0$$    |
| **4** | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$4/36$$ | $$0$$    | $$0$$    |
| **5** | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$5/36$$ | $$0$$    |
| **6** | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$6/36$$ |

Calcolare la legge di $X$ condizionata all'evento $\{Y=4\}$.

Questa è una legge di probabilità su $S_{X} = \{1, 2, 3, 4, 5, 6\}$ con pesetti:

- $\mathbb{P}(X = 1 \mid Y = 4) = \frac{\mathbb{P}(X = 1, Y = 4)}{\mathbb{P}(Y = 4)} = \frac{\mathbb{P}((1, 4))}{7/36}=1/7$
- $\mathbb{P}(X = 2 \mid Y = 4) = \frac{\mathbb{P}(X = 2, Y = 4)}{\mathbb{P}(Y = 4)} = \frac{\mathbb{P}((2, 4))}{7/36}=1/7$
- $\mathbb{P}(X = 3 \mid Y = 4) = \frac{\mathbb{P}(X = 3, Y = 4)}{\mathbb{P}(Y = 4)} = \frac{\mathbb{P}((3, 4))}{7/36}=1/7$
- $\mathbb{P}(X = 4 \mid Y = 4) = \frac{\mathbb{P}(X = 4, Y = 4)}{\mathbb{P}(Y = 4)} = \frac{\mathbb{P}((4, 4))}{7/36}=4/7$
- $\mathbb{P}(X = 5 \mid Y = 4) = 0$
- $\mathbb{P}(X = 6 \mid Y = 4) = 0$

> N.B.: Gli eventi $\{X = 5\}$ e $\{X = 6\}$ sono incompatibili con l'evento $\{Y = 4\}$.

Valore atteso: $\mathbb{E}(X \mid Y = y) = \sum_{X = 1}^{6} x \cdot \mathbb{P}(X = x \mid Y = 4) = 1 \cdot \frac{1}{7} + 2 \cdot \frac{1}{7} + 3 \cdot 4 \cdot \frac{4}{7} + 0 + 0 = \frac{22}{7}$
