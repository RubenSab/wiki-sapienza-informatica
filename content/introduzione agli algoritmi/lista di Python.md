---
updated_at: 2025-05-10T17:07:41.830+02:00
---
> In Python le liste sono [[array]] *dinamiche* (di dimensioni variabili) e non *omogenee* (cioè possono contenere diversi [[tipi]], anche altre liste).

Sono implementate come [[array]] di [[puntatore|puntatori]] a [[oggetto|oggetti]], ciò vuol dire che l'accesso all'elemento a un indice $n$ (in $\Theta(1)$) avviene in due passaggi, prima l'accesso all'elemento dell'array di puntatori all'indice $n$, poi il recupero dell'oggetto (elemento richiesto) indicato dal puntatore.

| Metodi delle liste | [[complessità temporale]] |
| ------------------ | ------------------------- |
| `append(x)`        | $\Theta(1)$               |
| `insert(i, x)`     | $O(n)$                    |
| `pop()`            | $\Theta(1)$               |
| `pop(i)`           | $O(n)$                    |
| `extend(B)`        | $O(\text{len}(B))$        |
