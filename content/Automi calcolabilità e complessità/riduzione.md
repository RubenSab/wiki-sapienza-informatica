---
updated_at: 2026-11-18T09:28:18.618+01:00
---
È un modo per dimostrare che alcuni linguaggi non sono [[macchina di Turing (TM)|Turing riconoscibili/decidibili]].

> Consideriamo le $TM$ che calcolano [[funzione|funzioni]] (input  $\langle f, w \rangle$ su nastro, calcolo della funzione nell'esecuzione, output $f(w)$ su un nastro qualsiasi).

> $f:\ \Sigma^{\star} \to \Sigma^{\star}$ è [[calcolabilità|calcolabile]] se $\exists\ \text{TM}\ \text{t.c.}\ \forall w \in \Sigma^{\star}\ M$ si ferma con $f(w)$ sul nastro.

> Un [[linguaggio]] $A$ è riducibile mediante una funzione al linguaggio $B$ (si denota con $A \leq_{m} B$, $m$ sta per [[applicazione|mapping]]) se $\exists f:\ \Sigma^{\star} \to \Sigma^{\star}\ \text{t.c.}\ \forall w \in A \iff f(w) \in B$. Le [[cardinalità]] degli [[insieme|insiemi]] $A$ e $B$ possono differire perchè la mappa non è [[applicazione biiettiva o biiezione|biunivoca]].
