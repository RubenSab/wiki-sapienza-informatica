---
updated_at: 2026-11-16T13:02:40.763+01:00
---
# Definizione

Il **Linguaggio While**:

$$
M, N ::= \underset{\text{costante}}{\underbrace{\mathcal{k}}} \mid \underset{\text{variabile}}{\underbrace{x}} \mid N+M \\
A, B ::= \text{true} \mid \text{false} \mid A \implies B \mid A < B \mid M = N \\
p, q ::= \text{skip} \mid p;q \mid x ::= M \mid \text{if}\ B\ \text{then}\ p\ \text{else}\ q \mid \text{while}\ B\ \text{do}\ p
$$

Abbinato alle **regole strutturali** ([[regola di inferenza|regole di inferenza]]):

$$
\{A\}\ p\ \{\text{true}\} \\
\{\text{false}\}\ p\ \{B\} \\
\frac{\{A\}\ p\ \{B\} \quad \ldots \quad \{A\}\ p\ \{B_{n}\}}{\{A\}\ p\ \{B_{0} \land B_{1} \land \ldots \land B_{n}\}}
$$

#todo regola or

Costituisce la **Logica di Hoore**, che permette di dedurre **Triple di Hoore**:

$$
\{A\}\ p\ \{B\}
$$

dove $A$ è un'espressione booleana ([[semantica|semanticamente]] sono le **precondizioni**), $p$ è un [[programma]] e $B$ è un'altra espressione booleana (semanticamente sono le **postcondizioni**).

> N.B.: La logica di Hoore non supporta nativamente le variabili locali.

## Esempio

$$
\{x>1\}\ x ::= x+47\ \{x>48\}
$$