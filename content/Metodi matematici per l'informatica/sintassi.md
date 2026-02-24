---
updated_at: 2025-05-17T18:55:02.462+02:00
---
> La sintassi è un'insieme di regole che definiscono un linguaggio.

> Un linguaggio è l'insieme di tutte le possibili espressioni che possiamo scrivere con i simboli disponibili.

Un'espressione è una sequenza di simboli. Essa è corretta:

- **sintatticamente** se rispetta le regole di sintassi imposte.
- **semanticamente** se assume un significato sensato.

Ogni numero è un'espressione aritmetica (atomica) valida, ciò implica che ognuna di queste combinazioni con operatori sia anch'essa un'espressione matematica valida.
$$E_{1}\in\text{Exp}\wedge E_{2}\in\text{Exp} \implies \begin{cases} (E_{1} + E_{2})\in \text{Exp} \\ (E_{1} - E_{2})\in \text{Exp} \\ (E_{1} \cdot E_{2})\in \text{Exp} \\ (E_{1} / E_{2})\in \text{Exp}\end{cases}$$

Esempio:

$$(3*7)-4/2\in\text{Exp}$$
Perché $(3*7)\in\text{Exp}$ e $(4/2)\in\text{Exp}$, perché $3\in\text{Exp}$ e $7\in\text{Exp}$ e $4 \in\text{Exp}$ e $2 \in\text{Exp}$.