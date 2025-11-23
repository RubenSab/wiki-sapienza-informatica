---
updated_at: 2025-11-23T17:14:31.628+01:00
---
# Lista degli algoritmi principali

## Algoritmi naive

> Nonostante siano più i semplici, sia concettualmente sia per l'implementazione, sono anche i più inefficienti su grandi [[struttura dati|struttura dati]].

| [[Algoritmo]] naive | Caso migliore           | Caso medio | Caso peggiore | Lista già ordinata      | [[Complessità spaziale]] |
| ------------------- | ----------------------- | ---------- | ------------- | ----------------------- | ------------------------ |
| [[bubble sort]]     | $O(n)$ (se ottimizzato) | $O(n^2)$   | $O(n^2)$      | $O(n)$ (se ottimizzato) | $O(1)$                   |
| [[selection sort]]  | $O(n^2)$                | $O(n^2)$   | $O(n^2)$      | $O(n^2)$                | $O(1)$                   |
| [[insertion sort]]  | $O(n)$                  | $O(n^2)$   | $O(n^2)$      | $O(n)$                  | $O(1)$                   |

## Algoritmi non naive

> Essendo più complessi sono meno intuitivi, ma anche molto più veloci.

| Algoritmo         | Caso Migliore | Caso Medio    | Caso Peggiore | Lista Ordinata | Complessità Spaziale |
| ----------------- | ------------- | ------------- | ------------- | -------------- | -------------------- |
| [[merge sort]]    | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$  | $O(n)$               |
| [[quick sort]]    | $O(n \log n)$ | $O(n \log n)$ | $O(n^2)$      | $O(n \log n)$  | $O(\log n)$          |
| [[heap sort]]     | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$  | $O(n)$               |
| [[bucket sort]]   | \*            | \*            | \*            | \*             | $O(n + k)$           |
| [[counting sort]] | $O(n + k)$    | $O(n + k)$    | $O(n + k)$    | $O(n + k)$     | $O(k)$               |
\* la [[complessità temporale]] del Bucket sort è sempre la somma delle complessità degli ordinamenti dei singoli bucket.
# *Lower bound* dell'ordinamento

Si può dimostrare che il *lower bound* della [[complessità temporale]] degli [[algoritmo|algoritmi]] di ordinamento (caso pessimo al di sotto del quale nessun algoritmo di ordinamento basato su confronti fra coppie di elementi possa andare) è $\Theta(n \cdot \log{n})$.

Si dimostra considerando un albero di decisione con tutte le strade possibili che termina con le "foglie" cioè i possibili output.

1. Assumendo che i numeri da ordinare sono distinti, si può verificare solo che un numero è maggiore o minore di un altro, cioè ogni nodo genera altri due nodi; quindi ogni livello ha $2^k$ nodi.
2. I possibili ordinamenti (permutazioni) di $n$ numeri sono $n!$, quindi l'albero deve avere $n!$ foglie.
3. Dato che ogni livello ha $2^{k}$ nodi, allora per arrivare ad avere un livello di $n!$ nodi servirà scendere di $\log_{2}{(n!)}$ nodi, cioè l'altezza dell'albero sarà $\log_{2}{(n!)}$.
4. Si dimostra matematicamente che asintoticamente $\log{(n!)} = n\log{n}$.
5. Ogni ramo/strada che va dal primo elemento fino a una foglia (ordinamento completato), sarà lungo tanto quanto è alto l'albero, quindi per $n$ numeri bisogna prendere $n \log{n}$ decisioni, cioè fare $n \log{n}$ confronti.