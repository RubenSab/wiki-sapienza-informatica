---
updated_at: 2026-02-26T15:57:06.117+01:00
---
> È una coppia $G = (V, E)$, dove $V$ è un [[insieme|insieme]] di *vertici* e $E$ è un insieme di *archi* $E$.

# Definizioni e glossario

> In un grafo **non orientato** (o semplicemente *grafo*), un **arco** è un insieme $\{v_{1}, v_{2}\}, v_{1} \in V, v_{2} \in V$ che rappresenta il collegamento tra due vertici.

> In un grafo **orientato**, un **arco** è una coppia ordinata $(v_{1}, v_{2}), v_{1} \in V, v_{2} \in V$ che rappresenta il collegamento (orientato) tra due vertici.

> Il **grado** di un nodo è il numero di archi collegati ad esso. In un grafo orientato esiste il **grado uscente**, cioè il numero di archi che **partono** dal nodo, e il **grado entrante**, cioè il numero di archi che **entrano** nel nodo.

> Un grafo si dice **connesso** se da ogni nodo si può arrivare a qualsiasi altro nodo.

> Un grado si dice **aciclico** se partendo da un qualsiasi nodo non possiamo tornare ad esso ripercorrendo gli archi del grafo.

> Un grafo si dice **planare** se può essere disegnato sul piano senza che gli archi si intersechino.

> In un grafo orientato, un **pozzo** è un nodo senza archi uscenti.

> In un grafo orientato, un **pozzo universale** è un pozzo che riceve un arco da ogni altro nodo.

> In un grafo orientato, una **sorgente** è un nodo senza archi entranti.

# Notazione standard e proprietà [[notazione asintotica|asintotiche]]

> $n$ è definito nella notazione standard come il numero di vertici, mentre $m$ è il numero di archi.

Per ogni grafo vale $m = O(n^{2})$, in particolare:

- per un **grafo sparso** $m = O(n)$ ([[notazione O-grande]])
- per un **grafo denso** $m = \Omega(n^{2})$ ([[notazione Omega]])

È utile notare che un [[albero]] è un grafo connesso e aciclico.

- Per un albero vale $m = n-1$.
- Per un grado planare con $n>2$ vale il *teorema di Eulero*, cioè $m \leq 3n-6$.

# Rappresentazione interna dei grafi

### Matrice di appartenenza

Si usa una matrice di booleane di dimensione $n \times n$ per indicare le connessioni.

Ad esempio la matrice del grafo orientato $\{(0, 1), (0, 2), (1, 2)\}$ è

|     | 0   | 1   | 2   |
| --- | --- | --- | --- |
| 0   | 0   | 1   | 1   |
| 1   | 0   | 0   | 1   |
| 2   | 0   | 0   | 0   |

### Vantaggi

- Il principale vantaggio di questo metodo è che non servono [[puntatore|puntatori]], ma in linguaggi moderni come python questo vantaggio è superfluo, perché l'uso dei puntatori è così facile da essere implicito.
- La verifica di un arco costa $O(1)$.

### Svantaggi

- [[complessità spaziale]] $\Theta(n^{2})$, inefficiente per grafi sparsi.
- Inoltre calcolare il grado di un nodo costa $O(n)$, perché bisogna scansionare la sua riga contando gli uno.

# Liste di adiacenza

È una [[lista di Python|lista]] di liste, dove ogni lista rappresenta un nodo, i cui elementi sono gli indici dei nodi collegati.

La complessità spaziale è $\Theta(n+m)$.

### Vantaggi

- È spazialmente efficiente: $\Theta(n+m)$
- Iterare sui vicini costa $O(\text{grado}(u))$

### Svantaggi

- La verifica di un arco costa $O(\text{grado}(u))$, nel caso peggiore $O(n)$.
- L'implementazione usa i puntatori

# Dizionario

Similmente alla lista di adiacenza si usa un [[dizionario]] di insiemi, dove ogni insieme rappresenta un nodo, i cui elementi sono i **nomi** dei nodi collegati. Ha la stessa complessità spaziale delle liste di adiacenza.

### Vantaggi

- È spazialmente efficiente: $\Theta(n+m)$.
- La verifica di un arco costa $O(1)$ **in media**.
- I nodi possono avere nomi non numerici.

### Svantaggi

- Overhead di memoria leggermente superiore.
- Nel **caso peggiore** la ricerca può degenerare a $O(n)$ in caso di collisioni [[hash table#^575716|hash]].