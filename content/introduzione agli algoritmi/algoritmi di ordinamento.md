---
updated_at: 2025-04-04T11:43:28.949+02:00
---
# Lista dei principali algoritmi

| algoritmo          | complessità temporale         | complessità spaziale |
| ------------------ | ----------------------------- | -------------------- |
| [[selection sort]] | $\Theta(n^{2})$ (è naive)     |                      |
| [[insertion sort]] | $O(n^{2})$ (è naive)          |                      |
| [[bubble sort]]    | $O(n^{2})$ (è naive)          |                      |
| [[counting sort]]  | $O(n+k)$ (ordina solo interi) |                      |
| [[bucket sort]]    |                               |                      |
| [[mergesort]]      |                               |                      |
| [[quicksort]]      |                               |                      |
| [[heapsort]]       |                               |                      |
# *Lower bound* dell'ordinamento

Si può dimostrare che il *lower bound* della [[complessità temporale]] degli [[algoritmo|algoritmi]] di ordinamento (caso pessimo al di sotto del quale nessun algoritmo di ordinamento basato su confronti fra coppie di elementi possa andare) è $\Theta(n \cdot \log{n})$.

Si dimostra considerando un albero di decisione con tutte le strade possibili che termina con le "foglie" cioè i possibili output.

1. Assumendo che i numeri da ordinare sono distinti, si può verificare solo che un numero è maggiore o minore di un altro, cioè ogni nodo genera altri due nodi; quindi ogni livello ha $2^k$ nodi.
2. I possibili ordinamenti (permutazioni) di $n$ numeri sono $n!$, quindi l'albero deve avere $n!$ foglie.
3. Dato che ogni livello ha $2^{k}$ nodi, allora per arrivare ad avere un livello di $n!$ nodi servirà scendere di $\log_{2}{(n!)}$ nodi, cioè l'altezza dell'albero sarà $\log_{2}{(n!)}$.
4. Si dimostra matematicamente che asintoticamente $\log{(n!)} = n\log{n}$.
5. Ogni ramo/strada che va dal primo elemento fino a una foglia (ordinamento completato), sarà lungo tanto quanto è alto l'albero, quindi per $n$ numeri bisogna prendere $n \log{n}$ decisioni, cioè fare $n \log{n}$ confronti.