---
updated_at: 2025-11-18T22:13:46.618+01:00
---
> La *covarianza* di due [[variabili aleatorie]] $X$ e $Y$ è un valore numerico che fornisce una misura di quanto due variano assieme: è il **[[valore atteso di una variabile aleatoria|valore atteso]] del prodotto delle loro distanze dalla media** ([[varianza di una variabile aleatoria|varianze]]):

$$
\text{Cov}(X, Y) = E(\text{Var}(X) \cdot \text{Var}(Y)) = E[(X-E(X))\cdot (Y-E(Y))]
$$

ma può anche essere espressa così

$$
\text{Cov}(X, Y) = E(XY) - E(X) \cdot E(Y)
$$

applicando la proprietà di **linearità** del valore atteso.

*^ da [Wikipedia](https://it.wikipedia.org/wiki/Covarianza_(probabilit%C3%A0))*

Esplicitando l'ultima formula si ottiene

$$
\sum_{x \in S_{X}} \sum_{y \in S_{Y}} \left( X Y \cdot \mathbb{P}(X = x, Y = y) - \sum_{x \in S_{X}} x \mathbb{P}(x) \cdot \sum_{y \in S_{Y}} y \mathbb{P}(y) \right)
$$

> $\mathbb{P}(X = x, Y = y)$ è la *[[probabilità|legge congiunta di X e Y]]*.

# Proprietà

1. $\text{Cov}(X, X) = \text{Var}(X)$
2. $\text{Cov}(X, c) = E(cX) - E(c) E(X) = 0$
3. $E(X) = 0 \lor E(Y) = 0 \implies \text{Cov}(X, Y) = E(XY)$
4. $\text{Cov}(aX, Y) = a \cdot \text{Cov}(X, Y)$
5. $\text{Cov}(aX, bY) = ab \cdot \text{Cov}(X, Y)$
6. $\text{Cov}(X, Y) = \text{Cov}(Y, X)$, cioè la covarianza è [[proprietà, tipi di relazioni e ordini|simmetrica]]
7. $\text{Cov}(X, Y+Z) = \text{Cov}(X, Y) + \text{Cov}(X, Z)$
8. $\text{Cov}(X, Y+c) = \text{Cov}(X, Y) + \text{Cov}(X, c) = \text{Cov}(X, Y)$
9. $X, Y$ [[indipendenza di due eventi|indipendenti]] $\implies \text{Cov}(X, Y) = 0$.

> Da queste proprietà deriva che la covarianza è ***bilineare***, cioè $\text{Cov}(aX+bY, Z) = a \text{Cov}(X, Z) + b \text{Cov}(Y, Z)$.