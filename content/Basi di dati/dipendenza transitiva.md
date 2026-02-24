---
updated_at: 2026-01-23T14:04:54.267+01:00
---
Siano $R$ uno [[tabella|schema di relazione]] e $F$ un [[insieme|insieme]] di [[dipendenza funzionale|dipendenze funzionali]] su $R$.

Le dipendenze transitive sono casi specifici delle dipendenze funzionali, così definite:

> $X \to A \in F^{+},\ A \notin X$ è una *dipendenza transitiva* su $R$ se $A$ non è primo e $X$ non è una superchiave (**per ogni** [[chiave]] $K$ di $R$ si ha che $X$ **non** è contenuto **[[sottoinsiemi|propriamente]]** in $K$ e $K-X \neq \emptyset$).

Praticamente **ogni chiave** e $X$ sono insiemi disgiunti **oppure** hanno un intersezione ma nessuno dei due è un sottoinsieme dell'altro.