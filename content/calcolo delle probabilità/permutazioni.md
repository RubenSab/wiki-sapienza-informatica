---
updated_at: 2025-11-03T20:18:53.255+01:00
---
Dati $n$ elementi distinti, in quanti modi possiamo ordinarli?

$$
n \cdot(n-1) \cdot(n-2) \cdot \ldots \cdot 2 \cdot 1 = n!
$$

> N.B.: Per definizione, $0!=1$

Esempio: quante parole di lunghezza 8 posso formare con i caratteri V E R O N I C A? $8!$

Osservazione: e se invece se avessimo caratteri ripetuti come in M O N D O? Qui avremmo $\frac{5!}{2!}$ parole diverse di lunghezza 5, perché abbiamo contato ogni parola 2 volte distinguendo erroneamente le O, quindi dobbiamo eliminare tutti i modi diversi di ordinare le due O, cioè $2!$ (2). Questo è un esempio di [[disposizioni senza ripetizioni|disposizione senza ripetizione]].