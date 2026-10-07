---
updated_at: 2026-10-07T09:29:25.765+02:00
---
> Un *Generic Non deterministic Finite state [[automa|Automaton]]* è una tupla $N = (Q, \Sigma, \delta, q_{\text{start}}, q_{\text{accept}})$, dove $\delta:\ Q\ \setminus \{q_{\text{accept}}\} \times Q \setminus \{q_{\text{start}}\} \to \text{re}(\Sigma) = \mathcal{R}$.

> Accettazione: un GNFA accetta $w \in \Sigma^{\star}$ se $w = w_{1}, \ldots, w_{k} \quad (w_{i} \in \Sigma)$ ed:

$\exists q_{0}, \ldots, q_{k}\ \text{t.c.}$:

- $\ q_{0} = q_{\text{start}} \land q_{k} = q_{\text{accept}}$
- $\forall i = 1 \ldots k \quad w_{i} \in L(R_{i}) \land R_{i} \in \text{re}(\Sigma) \land R_{i} = \delta(q_{i-1}, q_{i})$

# Conversione NFA $\to$ GNFA

Dato un qualsiasi [[automa non deterministico a stati finiti (NFA)]] è facile ottenere un GNFA equivalente.

Ad esempio questo NFA

![[Pasted image 20261007083119.png]]

Può essere convertito in questo GNFA

![[Pasted image 20261007090521.png]]

## [[algoritmo|Algoritmo]] $\text{Convert}(G)$

Sia $k$ il numero di stati di $G$.

- Se $k = 2$, ci sono solo $q_{\text{start}}$ e $q_{\text{accept}}$ e l'arco $\delta(q_{\text{start}}, q_{\text{accept}}) = R \in \text{re}(\Sigma)$.
  Output: $R$.
- Se $k > 2$, scelgo $q_{\text{rappresentante}} \in Q \setminus \{q_{\text{start}}, q_{\text{accept}}\}\ \forall q_{i} \in Q'$.
	- Creo un GNFA $G' = (Q \setminus \{q_{\text{rappresentante}}\}, \Sigma, \delta', q_{\text{start}}, q_{\text{accept}})$
	- $\forall q_{i} \in Q' \setminus \{q_{\text{accept}}\},\ q_{j} \in Q' \setminus \{q_{\text{start}}\} \quad \delta'(q_{i}, q_{j})$ (si costruisce $\delta'$ progressivamente, seguendo la [[forma canonica degli NFA]])

$\delta'(q_{i}, q_{j}) = (R_{1})(R_{2})^{\star}(R_{3}) \cup R_{4}$

![[Pasted image 20261007091758.png]]

> Affermazione: $\forall \text{GNFA} G,\ G' = \text{Convert}(G)$ è equivalente a $G$. Cioè l'etichetta finale $R$ tale che $R = \delta(q_\text{start}, q_\text{accept})$ è l'[[espressioni regolari (regex)|espressione regolare]] equivalente al GNFA $G$ di partenza.

Dimostrazione:

- $k = 2$ è banale.
- caso [[induzione|induttivo]]: suppongo vera l'affermazione per GNFA con $k$ stati, è vero pure per $k+1$ stati.

Dimostriamolo per $k$ stati.

Ma in effetti:

- se $G$ accetta $w$, ci sarà ramo di computazione che attraversa $q_{\text{start}}, \ldots, q_{\text{accept}}$. Due casi:
	- $q_{\text{rappresentante}}$ non è uno degli stati intermedi allora non è cambiato nulla ($R_{4}$ è compreso nell'unione).
	- $q_{\text{rappresentante}}$ è uno degli stati intermedi: è ok per lo stesso motivo ma relativo a $R_{1}(R_{2})^{\star}R_{3}$ ovvero tutti i modi per andare da $q_{i}$ a $q_{j}$ passando per $q_{\text{rappresentante}}$.

$\square$

# Esercizi

## 1. Trasformare $(ab \cup a)^{\star}$ in NFA.

## 2. Trovare l'espressione regolare equivalente al seguente NFA

![[Pasted image 20261007092632.png]]

$$
\Sigma = \{0, 1, 2\}
$$