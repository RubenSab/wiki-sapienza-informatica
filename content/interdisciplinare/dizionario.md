---
updated_at: 2025-05-23T12:02:54.508+02:00
---
> Il dizionario è una [[struttura dati]] dinamica che prevede tre operazioni: **inserimento** di una coppia key-value, **ricerca** di una value in base alla key e **cancellazione** di una coppia key-value.

- Implementato con le [[hash table]], il costo delle operazioni sarà $O(n)$, il caso migliore sarà $\Theta(1)$ e il caso medio è $O(1)$.
- Implementato con gli [[albero di ricerca|alberi di ricerca]], il costo delle operazioni sarà $O(\log{n})$, il caso migliore sarà $\Theta(1)$, **ma non è garantito che il caso medio sia $O(1)$**.
# Implementazione con [[albero di ricerca]]

Con gli alberi, si può fare in modo che i nodi siano al massimo a distanza $O(\log(n))$ dalla radice.
Inoltre le chiavi dei nodi dell'albero di ricerca sono univoche ed è facile navigarci, quindi la ricerca di una valore da una chiave si può fare in $O(h)=O(\log{n})$.

# Implementazione con [[hash table]]