---
updated_at: 2025-11-26T14:23:24.112+01:00
---
# Legge congiunta

> Siano $X$ e $Y$ due [[variabili aleatorie]] sullo [[spazio campionario]] $\Omega$ a valori in $S_{X}$ e $S_{Y}$ rispettivamente. La *legge congiunta* di $X$ e $Y$ è la [[misura di probabilità|misura di probabilità]] su $S_{X} \times S_{Y} = \{(x, y): x \in S_{X}, y \in S_{Y}\}$ data dai pesetti $p_{x,y} = \mathbb{P}\underset{\{X = x\} \cap \{Y=y\}}{(X = x, Y = y)}\ \forall (x, y) \in S_{X} \times S_{Y}$.

> N.B.: Questa è una legge di probabilità, quindi necessariamente

$$
\begin{cases}
p_{x,y} \in [0, 1]\quad \forall (x, y) \in S_{X} \times S_{Y}
\\
\sum_{(x, y) \in S_{X} \times S_{Y}}\ p_{xy} = 1
\end{cases}
$$

> N.B.: Date due variabili aleatorie $X$ e $Y$ a valori in $S_{X} \times S_{Y}$ rispettivamente, se

$$
f: S_{X} \times S_{Y} \to R
$$

definiamo la media pesata ([[valore atteso di una variabile aleatoria|valore atteso]]) dei valori di $f$ rispetto alla legge congiunta

$$
\mathbb{E}(f(X, Y)) = \sum_{(x, y) \in S_{X} \times S_{Y}} f(x, y) \cdot \mathbb{P}(X = x, Y = y)
$$

In particolare, per $f(x, y) = x \cdot y$

$$
\mathbb{E}(X \cdot Y) = \sum_{x \in S_{X}} \sum_{y \in S_{Y}} xy\ \mathbb{P}(X = x, Y = y)
$$

Se $X$ e $Y$ sono indipendenti

$$
\sum_{x \in S_{X}} x \cdot \mathbb{P}(X = x) \cdot \sum_{y \in S_{Y}} y \cdot \mathbb{P}(Y = y) = \mathbb{E}(X) \cdot \mathbb{E}(Y)
$$

## Esempio: lanciamo due dadi

Sia $X$ il risultato del primo lancio, contenuto in $S_{X} = \{1, 2, 3, 4, 5, 6\}$ e sia $Y$ il massimo dei due lanci, contenuto in $S_{Y} = S_{X}$.

Scriviamo la legge congiunta di $X$ e $Y$, che è una misura di probabilità su $\{1, 2, 3, 4, 5, 6\}^{2}$.

Per ogni $(i, j) \in \{1, 2, 3, 4, 5, 6\}^{2}$ calcoliamo $p_{i, j} = \mathbb{P}(X=i, Y=j)$

- $p_{1,1} = \mathbb{P}(X=1, Y=1) = \mathbb{P}((1,1)) = \frac{1}{36}$
- $p_{1,2} = \mathbb{P}(X=1, Y=2) = \mathbb{P}((1,2)) = \frac{1}{36} = p_{1, 3} = p_{1, 4} = p_{1, 5} = p_{1, 6}$
- $p_{2,1} = \mathbb{P}(X = 2, Y = 1) = 0 = P_{3,1} = P_{4,1} = P_{5,1} = P_{6,1}$
- $p_{3, 2} = \mathbb{P}(X = 3, Y = 2) = 0$

| $Y/X$ | 1        | 2        | 3        | 4        | 5        | 6        |
| ----- | -------- | -------- | -------- | -------- | -------- | -------- |
| **1** | $$1/36$$ | $$0$$    | $$0$$    | $$0$$    | $$0$$    | $$0$$    |
| **2** | $$1/36$$ | $$2/36$$ | $$0$$    | $$0$$    | $$0$$    | $$0$$    |
| **3** | $$1/36$$ | $$1/36$$ | $$3/36$$ | $$0$$    | $$0$$    | $$0$$    |
| **4** | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$4/36$$ | $$0$$    | $$0$$    |
| **5** | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$5/36$$ | $$0$$    |
| **6** | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$1/36$$ | $$6/36$$ |

Notiamo che $p_{x, y} > 0 \iff Y \geq X$

È evidente che la somma dei pesetti fa 1.

# Leggi marginali

Dalla legge congiunta di $X$ e $Y$ si possono ricavare le *leggi marginali* delle variabili $X$ e $Y$, tramite le seguenti identità.

$$
\mathbb{P}(X=1) \underset{\{X = 1\} \cap \Omega = \{x = 1\} \cap \left( \bigcup_{y \in S_{Y}} \{Y = y\} \right) = \bigcup_{y \in S_{Y}} \{X = x\} \cap \{Y = y\}}{=} \sum_{y=1}^{6} \mathbb{P}(X = 1, Y = y)
$$

$$
\mathbb{P}(Y = 1) = \frac{1}{36}
$$

$$\mathbb{P}(Y = 2) = \mathbb{P}(Y = 2, X = 1) + \mathbb{P}(Y = 2, X = 1) = \frac{3}{36}$$

$$
\mathbb{P}(Y = 3) = \frac{5}{36}, \quad \mathbb{P}(Y = 4) = \frac{7}{36}, \quad \mathbb{P}(Y = 5) = \frac{9}{36}, \quad \mathbb{P}(Y = 6) = \frac{11}{36} 
$$

> In generale, se $X$ e $Y$ hanno legge congiunta data dai pesetti $(P_{x, y})_{(x, y) \in S_{X} \times S_{Y}}$, allora le *leggi marginali* di $X$ e $Y$ sono date da:

$$
p_{x}  =\mathbb{P}(X = x) = \sum_{y \in S_{Y}} \mathbb{P}(X = \underset{\text{fissata}}{x}, Y = y) \quad \forall x \in S_{X}
$$

$$
p_{y}  =\mathbb{P}(Y = y) = \sum_{y \in S_{Y}} \mathbb{P}(X = x, Y = \underset{\text{fissata}}{y}) \quad \forall y \in S_{Y}
$$
In generale, dalla legge congiunta di $X$ e $Y$ possiamo ricavare le marginali; ma dalle  marginali non si può, senza informazioni aggiuntive, scrivere la legge congiunta.

> N.B.: Se $X$ e $Y$ sono [[indipendenza di due eventi|indipendenti]], la loro legge congiunta è il "prodotto" delle leggi marginali, ossia

$$
\forall (x, y) \in S_{X} \times S_{Y} \quad \mathbb{P}(X = x, Y = y) = \mathbb{P}(X=x) \cdot \mathbb{P}(Y = y)
$$

> N.B.: $X$ e $Y$ sono indipendenti, a valori in $S_{X}$ e $S_{Y}$ rispettivamente, allora

$$
\forall (x, y) \in S_{X} \times S_{Y} \quad p_{xy} = \mathbb{P}(X = x, Y=y) > 0
$$

## Esempio

Siano $X$ e $Y$ due variabili aleatorie con legge congiunta data dai pesetti


| $S_{Y}/S_{X}$ | 1    | 2    | 3    |
| ------------- | ---- | ---- | ---- |
| **1**         | 0    | 1/12 | 1/12 |
| **2**         | 2/12 | 3/12 | 0    |
| **3**         | 0    | 1/12 | 0    |
| **4**         | 1/12 | 1/12 | 2/12 |

su

$S_{X} = \{1, 2, 3\}$
$S_{Y} = \{1, 2, 3, 4\}$

Leggi marginali:

- $\mathbb{P}(X)$:
	- $\mathbb{P}(X = 1) = p_{1,1} + p_{1,2} + p_{1,3} + p_{1,4} = \frac{3}{12}$
	- $\mathbb{P}(X = 2) = p_{2,1} + p_{2,2} + p_{2,3} + p_{2,4} = \frac{6}{12}$
	- $\mathbb{P}(X = 3) = p_{3,1} + p_{3,2} + p_{3,3} + p_{3,4} = \frac{3}{12}$

- $\mathbb{P}(Y)$:
	- $\mathbb{P}(Y = 1) = p_{1,1} + p_{2,1} + p_{3, 1} = \frac{2}{12}$
	- $\mathbb{P}(Y = 2) = p_{1,2} + p_{2,2} + p_{3, 2} = \frac{5}{12}$
	- $\mathbb{P}(Y = 3) = p_{1,3} + p_{2,3} + p_{3, 3} = \frac{1}{12}$
	- $\mathbb{P}(Y = 4) = p_{1,4} + p_{2,4} + p_{3, 4} = \frac{4}{12}$

Esempi di [[evento|eventi]] di natura "geometrica" calcolati nel "piano discreto" della la legge congiunta dei pesetti:

- $\mathbb{P}(X+Y=4) = \mathbb{P}(\{(x, y): x+y\}) = \mathbb{P}(\{(1, 3), (2, 2), (3, 1)\}) = 0 + \frac{3}{12} + \frac{1}{12} = \frac{1}{3}$ (retta)
- $\mathbb{P}((X-2)^{2}+(Y-1)^{2} \leq 1) = p_{1, 1} + p_{2,1} + p_{3,1} + p_{2,2} = \frac{5}{12}$ (cerchio)
