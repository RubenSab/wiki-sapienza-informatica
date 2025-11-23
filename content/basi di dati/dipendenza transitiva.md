---
updated_at: 2025-11-23T12:08:47.312+01:00
---
Siano $R$ uno [[tabella|schema di relazione]] e $F$ un [[teoria degli insiemi|insieme]] di [[dipendenza funzionale|dipendenze funzionali]] su $R$.

Le dipendenze transitive sono casi specifici delle dipendenze funzionali, così definite:

> $X \to A \in F^{+},\ A \notin X$ è una *dipendenza parziale* su $R$ se $A$ non è primo e $X$ non è una superchiave (**per ogni** [[chiave]] $K$ di $R$ si ha che $X$ **non** è contenuto **[[sottoinsiemi|propriamente]]** in $K$ e $K-X \neq \emptyset$).

Praticamente $K$ e $X$ sono disgiunti **oppure** hanno un intersezione ma nessuno dei due è un sottoinsieme dell'altro.