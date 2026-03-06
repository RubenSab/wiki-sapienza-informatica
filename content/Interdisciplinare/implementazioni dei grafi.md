---
updated_at: 2026-03-03T17:34:26.410+01:00
---
# Matrice di appartenenza

Si usa una matrice di booleane di dimensione $n \times n$ per indicare le connessioni.

Ad esempio la matrice del grafo orientato $\{(0, 1), (0, 2), (1, 2)\}$ è

|     | 0   | 1   | 2   |
| --- | --- | --- | --- |
| 0   | 0   | 1   | 1   |
| 1   | 0   | 0   | 1   |
| 2   | 0   | 0   | 0   |

> Osservazione: un [[grafo]] non orientato è una [[proprietà, tipi di relazioni e ordini#^260c8b|relazione simmetrica]], quindi anche la matrice è simmetrica ($G[u][v] = G[v][u]$).

## Vantaggi

- Il principale vantaggio di questo metodo è che non servono [[puntatore|puntatori]], ma in linguaggi moderni come python questo vantaggio è superfluo, perché l'uso dei puntatori è così facile da essere implicito.
- La verifica di un arco costa $O(1)$.

## Svantaggi

- [[complessità spaziale]] $\Theta(n^{2})$, inefficiente per grafi sparsi.
- Inoltre calcolare il grado di un nodo costa $O(n)$, perché bisogna scansionare la sua riga contando gli uno.

# Liste di adiacenza

È una [[lista di Python|lista]] di liste, dove ogni lista rappresenta un nodo, i cui elementi sono gli indici dei nodi collegati.

La complessità spaziale è $\Theta(n+m)$.

## Vantaggi

- È spazialmente efficiente: $\Theta(n+m)$
- Iterare sui vicini costa $O(\text{grado}(u))$

## Svantaggi

- La verifica di un arco costa $O(\text{grado}(u))$, nel caso peggiore $O(n)$.
- L'implementazione usa i puntatori

# Dizionario

Similmente alla lista di adiacenza si usa un [[dizionario]] di insiemi, dove ogni insieme rappresenta un nodo, i cui elementi sono i **nomi** dei nodi collegati. Ha la stessa complessità spaziale delle liste di adiacenza.

## Vantaggi

- È spazialmente efficiente: $\Theta(n+m)$.
- La verifica di un arco costa $O(1)$ **in media**.
- I nodi possono avere nomi non numerici.

## Svantaggi

- Overhead di memoria leggermente superiore.
- Nel **caso peggiore** la ricerca può degenerare a $O(n)$ in caso di collisioni [[hash table#^575716|hash]].