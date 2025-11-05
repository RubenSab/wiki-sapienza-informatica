---
updated_at: 2025-11-03T22:02:19.168+01:00
---
> Sia $\Omega$ uno [[spazio campionario]]. Diciamo che tre [[evento|eventi]] $A$, $B$ e $C$ su $\Omega$ sono indipendenti se

$$
\mathbb{P}(A \cap B \cap C) = \mathbb{P}(A)\cdot \mathbb{P}(B) \cdot \mathbb{P}(C)
$$

> N.B.: Se vale solo l'[[indipendenza di due eventi]] tra $A, B, C$, cioè $A \perp \!\!\! \perp B, A \perp \!\!\! \perp C, B \perp \!\!\! \perp B$, si dice che i tre eventi sono *indipendenti a coppie*.

> N.B.: L'indipendenza a coppie è una proprietà più debole dell'indipendenza.

$A, B, C\ \text{indipendenti} \implies A, B, C\ \text{indipendenti a coppie}$;

però $A, B, C\ \text{indipendenti a coppie}\ \;\not\!\!\!\!\implies A, B, C\ \text{indipendenti}$

# Esempio

Lancio due monete eque. Siano:

$$
A = \{\text{T al primo lancio}\}
$$

$$
B = \{\text{T al secondo lancio}\}
$$

$$
C = \{\text{esattamente una T}\}
$$

$\Omega = \{(T, T), (T, C), (C, T), (C, C)\}$

- $|A| = 2$
- $|C| = 2$
- $|C| = 2$

$\mathbb{P}(A) \cdot \mathbb{P}(B) = \mathbb{P}(A) \cdot \mathbb{P}(C) = \mathbb{P}(B) \cdot \mathbb{P}(C) = \frac{1}{4}$ cioè i tre eventi sono **indipendenti a coppie**.

Però $A \cap B \cap C = \emptyset \implies \mathbb{P}(A \cap B \cap C)=0 \quad \neq \quad \mathbb{P}(A)\cdot \mathbb{P}(B) \cdot \mathbb{P}(C)$, quindi i tre eventi **non sono indipendenti**.
