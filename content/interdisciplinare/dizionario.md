---
updated_at: 2025-05-12T10:05:41.377+02:00
---
> Il dizionario è una [[struttura dati]] dinamica che prevede tre operazioni: **inserimento** di una coppia key-value, **ricerca** di una value in base alla key e **cancellazione** di una coppia key-value.

Indipendentemente dall'implementazione, inevitabilmente il caso pessimo di tutte e tre le operazioni sarà $O(n)$ e il caso migliore sarà $\Theta(1)$; quindi una buona implementazione deve ottimizzare il caso medio.
# Implementazione con [[albero di ricerca]]

Con gli alberi, si può fare in modo che i nodi siano al massimo a distanza $O(\log(n))$ dalla radice.
Inoltre le chiavi dei nodi dell'albero di ricerca sono univoche ed è facile navigarci, quindi la ricerca di una valore da una chiave si può fare in $O(h)=O(\log{n})$.