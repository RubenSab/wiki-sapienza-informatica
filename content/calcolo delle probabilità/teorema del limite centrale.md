---
updated_at: 2025-12-17T15:30:09.500+01:00
---
Siano $X_{1}, X_{2}, \dots, X_{n}$ [[variabili aleatorie]] [[indipendenza di due variabili aleatorie continue|indipendenti]] e identicamente distribuite con [[valore atteso di una variabile aleatoria|media]] $\mu$ e [[varianza di una variabile aleatoria|varianza]] $\sigma^{2}$.

Allora

$$
\frac{\sum_{k=1}^{n}(X_{k}) - n \mu}{\sqrt{n \sigma^{2}}} \approx N(0, 1)
$$

([[legge Gaussiana standard]]) per un numero $n$ di variabili indipendenti sufficientemente grande.

> N.B.: Le medie e varianze sono uguali per tutte le variabili aleatorie perché sono identicamente distribuite, cioè hanno la stessa legge.

Questo teorema ci dice che ogni volta che abbiamo a che fare con somme di tante variabili aleatorie indipendenti e identicamente distribuite, possiamo usare l'approssimazione Gaussiana.

In particolare

$$
\forall x \in \mathbb{R} \quad \mathbb{P}\left(\frac{\sum_{k=1}^{n}(X_{k}) - n \mu}{\sqrt{n \sigma^{2}}} \leq x \right) \approx \phi(x) = \int_{-\infty}^{\infty}\frac{e^{-\frac{y^{2}}{2}}}{\sqrt{2 \pi}}\ dy
$$

# Esempio

Lancio 2 dadi 300 volte. Sia $X$ il numero di lanci che risultano nella coppia $(1, 1)$.

Notiamo che

$$
X = \sum_{k = 1}^{300} X_{k}\quad \text{dove} \quad X_{k} = \mathbb{1}((1, 1)\ \text{al lancio}\ k)
$$

Allora

$$
\mathbb{E}(X_{1}) = \mathbb{P}((1, 1)\ \text{al lancio}\ k) = \frac{1}{36} \quad \text{Var}(X_{1}) = \frac{1}{36} \cdot \frac{35}{36}
$$

Usando l'approssimazione Gaussiana otteniamo

$$
\mathbb{P}(X \geq 10) = \mathbb{P}\left(\sum_{k=1}^{300}X_{k} \geq 10 \right) = \mathbb{P}\left(\frac{\sum_{k=1}^{300} X_{k} - 300 \cdot \frac{1}{36}}{\sqrt{300 \cdot \frac{1}{36} \cdot \frac{35}{36}}} \geq \frac{10-300 \cdot \frac{1}{36}}{\sqrt{300 \cdot \frac{1}{36} \cdot \frac{35}{36}}}\right) \approx \mathbb{P}(N(0, 1) \geq 0.59)
$$

$$
= 27,76 \%
$$