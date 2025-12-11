---
updated_at: 2025-12-10T14:50:51.534+01:00
---
*Vedere prima [[valore atteso di una variabile aleatoria]]*.

> La *funzione generatrice dei momenti* di una [[variabili aleatorie|variabile aleatoria]] $X$ a valori in $S_{X} \subseteq \mathbb{N}$ è definita come la [[funzione]]:

$$
G_{X}(t) := \mathbb{E}(t^{X})\ \text{per}\ t \in (0,1] = \sum_{x \in S_{X}} t^{x} \mathbb{P}(X = x)
$$


> Il nome funzione generatrice dei momenti deriva dal fatto che da $G_{X}(t)$ possiamo ricavare, derivando, $\mathbb{E}(X^{k}), \forall k \geq 1$,  cioè gli momenti $k$-esimi di $X$*.

Osservazioni:

- per $t=1, \quad G_{X}(1) = \mathbb{E}(1^{X}) = 1$
- per $t < 1$, la somma che definisce $G_{X}(t)$ è convergente.

Nel *[[probabilità continua|continuo]]*, abbiamo

$$
M_{X}(\theta) := \mathbb{E}(e^{\vartheta X}) = \int_{-\infty}^{+\infty} e^{\vartheta x} f(x)\ dx
$$

La funzione generatrice dei momenti specifica univocamente la legge di $X$.

Inoltre $M_{X}(0) = 1,\ M'_{X}(0) = \mathbb{E}(X),\ M''_{X}(0) = \mathbb{E}(X^{2})$

# Applicazione utili di $G_{X}(1)$

## 1. Calcolo del valore atteso

> La funzione generatrice dei momenti ci permette di calcolare il [[valore atteso di una variabile aleatoria]] velocemente, basta calcolare la sua [[derivate|derivata]] in $t=1$.

$$
G_{X}(t) = \mathbb{E}(t^{X})
$$

$$
G'_{X}(t) = \mathbb{E}(X t^{X-1})
$$

$$
G'_{X}(1) = \mathbb{E}(X \cdot 1^{X-1}) = \mathbb{E}(X)
$$

### Esempio con la [[distribuzione di Poisson 🐟]]:

Se $X \sim \text{Poisson}(X)$, la sua funzione generatrice dei momenti è data da

$$
G_{X}(t) = \mathbb{E}(t^{X}) = \sum_{k=0}^{+\infty} t^{k} \cdot \mathbb{P}(X = k) = \sum_{k = 0}^{+\infty}\frac{t^{k} \cdot e^{-\lambda} \lambda^{k}}{k!} = e^{-\lambda} \sum_{k=0}^{+\infty}\frac{(\lambda t)^{k}}{k!} = e^{-\lambda} \cdot e^{\lambda t} = e^{\lambda t - \lambda}
$$

## 2. Calcolo dei momenti $k$-esimi di $X$

$$
G_{X}(t) = \mathbb{E}(t^{X}) \to G'_{X}(1) = \mathbb{E}(X)
$$

$$
G'_{X}(t) = \mathbb{E}(X \cdot t^{X-1}) \to G''_{X}(1) = \mathbb{E}(X^{2}) - \mathbb{E}(X)
$$

$$
G''_{X}(t) = \mathbb{E}(X \cdot (X-1) \cdot t^{X-2}) \to G''_{X}(1) = \mathbb{E}(X^{2}) - \mathbb{E}(X)
$$

$$
G'''_{X(t)}= \mathbb{E}(X \cdot (X-1) \cdot (X-2) \cdot t^{x-3}) \to G'''_{X}(1) = \mathbb{E}(X^{3}) - 3\mathbb{E}(X^{2}) + 2\mathbb{E}(X)
$$

## 3. Teorema dell'univocità delle [[misura di probabilità|leggi]] delle variabili aleatorie corrispondenti

> La legge generatrice dei momenti determina univocamente la legge della variabile aleatoria corrispondente.

Esempio: Se $G_{X}(t) = tp + 1 - p$, allora $X \sim \text{Bernoulli}(p)$. *([[distribuzione di Bernoulli]])*

## 4. Somme di variabili **indipendenti**

Siano X e Y due variabili aleatorie con legge di Poisson, di parametri $\lambda_{X}$ e $\lambda_{Y}$, [[indipendenza di due eventi|indipendenti]] tra loro.

Voglio capire che legge ha la variabile $Z = X + Y$.

$$
G_{X}(t) = \mathbb{E}(t^{X}) = \sum_{k = 0}^{\infty} t^{k} \frac{e^{-\lambda_{X}}\lambda_{X}^{k}}{k!} = e^{t \lambda_{X} - \lambda X}
$$

$$
G_{Y}(t) = e^{t\lambda_{Y} - \lambda_{Y}}
$$

$$
G_{Z}(t) = \mathbb{E}(t^{Z}) = \mathbb{E}(t^{X+Y}) = G_{X}(t) \cdot G_{Y}(t)
$$

> In generale, se $X$ e $Y$ sono due variabili indipendenti

$$
G_{X + Y}(t) = \mathbb{E}(t^{X + Y}) = G_{X}(t) \cdot G_{Y}(t)
$$

Ciò vale anche con un numero maggiore di variabili indipendenti.