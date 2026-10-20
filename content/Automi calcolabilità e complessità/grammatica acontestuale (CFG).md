---
updated_at: 2026-10-20T23:17:28.126+02:00
---
#todo 

- [[forma normale di Chomsky]]
# Esercizi: formalizzare le descrizioni dei seguenti linguaggi in CFG

## 1. $L_{1} = \{w \in {\{0, 1\}}^{\star}:\ {\#}_{1}(w) \geq 3\}$

$$
S \to A1A1A1A \\
A \to 0A \mid 1A \mid \varepsilon
$$
Stringhe binarie con almeno 3 uno

![[Pasted image 20261020224259.png]]


## 2. $L_{2} = \{w \in {\{0, 1\}}^{\star}:\ w = w^{R},\ | w | = 2n\ n \in \mathbb{N}\}$

> $w = w^{R}$ vuol dire palindroma.

$$
S \to A \\
A \to 0A0 \mid 1A1 \mid 00 \mid 11
$$

## 3. $L_{3} = \{a^{i}b^{i}c^{k}:\ i+1 = k\quad i, k \geq 0\}$

$$
S \to Xc \\
X \to YXc \\
Y \to aYb \mid \varepsilon
$$

xc
yxc
aybyxcc
aaybbyxcc -> no
?