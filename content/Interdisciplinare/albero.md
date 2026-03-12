---
updated_at: 2026-03-12T13:29:46.373+01:00
---
> Un albero radicato è una [[struttura dati]] composta da nodi organizzati gerarchicamente. Ha un nodo radice che non ha genitori. Ogni altro nodo dell'albero ha esattamente un genitore e può avere $n$ figli. I nodi che non hanno figli sono chiamati foglie.

- [[grafo#^f4e592|Gli alberi sonno grafi particolari]]

> In un albero tutti gli archi sono ponti.

- [[nomenclatura degli alberi]]
- [[implementazioni degli alberi binari]]
- [[albero di ricerca]]

Tutte queste funzioni sono realizzate con [[implementazioni degli alberi binari|l'implementazione degli alberi con i puntatori]].
## Stampa

``` python
def stampa(p, livello=0):
	if p:
		print('| '*livello, p.key)
		stampa(p.left, h+1)
		stampa(p.right, h+1)
```

## Crea un albero con $n$ nodi e un numero casuale di figli

``` python
def crea_albero(n):

    if n == 0:
        return None

    nodo = Nodo(random.randint(0, 9))
    # stabilire il numero di figli dei sottoalberi
    n_left = random.randint(0, n - 1)
    n_right = n - 1 - n_left
    # creare i sottoalberi
    nodo.left = crea_albero(n_left)
    nodo.right = crea_albero(n_right)

    return nodo
```

# Visita dell'albero

> La visita dell'albero è l'accesso progressivo a tutti i suoi nodi con un determinato criterio di ordine.

## Visite per profondità

Per gli alberi binari esistono tre possibili visite *in profondità*, ovviamente dallo stesso [[complessità temporale|costo computazionale]]:

- In **preordine**: il nodo è visitato prima di proseguire la visita nei suoi sottoalberi.

``` python
def preorder(nodo):
	if nodo is None:
		return
	print(nodo.value, end=' ')
	preorder(nodo.left)
	preorder(nodo.right)
```

- In **ordine**: il nodo è visitato dopo la visita del sottoalbero sinistro e prima di quella del sottoalbero destro.

``` python
def inorder(nodo):
	if nodo is None:
		return
	inorder(nodo.left)
	print(nodo.value, end=' ')
	inorder(nodo.right)
```

- In **postordine**: il nodo è visitato dopo entrambe le visite dei sottoalberi.

``` python
def postorder(nodo):
	if nodo is 
        preordine(nodo.right)
        print(nodo.key, end = ' ')None:
		return
	postorder(nodo.left)
	postorder(nodo.right)
	print(nodo.key, end=' ')
```

## Visita per ampiezza/livello (BFS)

^34c59b

Esiste anche un altro tipo di visita, cioè la visita **in ampiezza** "Breadth-First Search" (per livello, da sinistra a destra).

L'idea è di sfruttare una [[queue]]  (importata da `collections`) per memorizzare i nodi in ogni livello e man mano estrarre i nodi visitati (da stampare o da inserire in un generatore) in $\Theta(1)$.

``` python
from collections import deque

def visita_per_livello(nodo) -> List:

    if nodo is not None:
        coda = deque([nodo])

        while coda: # aggiungiamo i figli destro e sinistro, rimuoviamo l'ultimo nodo dalla coda poi ripetiamo finché la coda si è svuotata
            nodo = coda.popleft()
            yield nodo.key # anche print(nodo.key, end=' ') andava bene
            if nodo.left:
                coda.append(nodo.left)
            if nodo.right:
                coda.append(nodo.right)

print(list(visita_per_livello(nodo)))
```

## Costo computazionale

Chiamiamo $k$ il numero di nodi del sottoalbero destro, l'[[equazioni di ricorrenza|equazione di ricorrenza]] è:

$$T(n) = \begin{cases} \Theta(1) & \text{se } n=0 \\ T(k) + T(n-1-k) + \Theta(1) & \text{se } n>0 \end{cases}$$

Se l'albero è completo, la suddivisione delle due chiamate ricorsive è la più equa possibile:

$$k\approx \frac{n}{2} \longrightarrow T(n)=2T\left(\frac{n}{2}\right)+\Theta(1)$$
$$T(n)=\Theta(n^{\log_{2}{2}})=\Theta(n)$$
Se l'albero è massimamente sbilanciato, quindi quando $k=0$ o $n-1-k=0$, si ottiene
$$T(n)=T(n-1)+\Theta(1)=\Theta(n)$$

Indipendentemente dall'albero, la complessità della visita è **sempre** $\Theta(n)$.

## Funzioni utili che sfruttano la visita dell'albero

``` python
def conta_nodi_albero(nodo):
	if nodo == None:
		return 0
	return conta_nodi_albero(nodo.left) + conta_nodi_albero(nodo.right) + 1
```

``` python
def cerca_nodo(nodo, query):
	if nodo == None:
		return False
	return nodo.key==query or cerca_nodo(nodo.left, query) or cerca_nodo(nodo.right, query)
```

``` python
def altezza(nodo):
	if nodo == None:
		return -1 # albero vuoto
	return max(altezza(nodo.left), altezza(nodo.right)) + 1
```

``` python
def conta_nodi_al_livello(nodo, livello): # O(2^livello)
	if nodo == None:
		return 0 # albero vuoto
	if k==0: # si è raggiunto il livello
		return 1
	return conta_nodi_al_livello(nodo.left, k-1) + conta_nodi_al_livello(nodo.right, k-1)
```

``` python
def lvl_min_foglie(nodo): # O(n)

    if not nodo:
        return -1

    if not nodo.left and not nodo.right:
        return 0

    elif nodo.left and nodo.right:
        return min(lvl_min_foglie(nodo.left), lvl_min_foglie(nodo.right)) + 1

    elif nodo.left:
        return lvl_min_foglie(nodo.left) + 1

    elif nodo.right:
        return lvl_min_foglie(nodo.right) + 1
```

``` python
def helper(nodo):

    if not nodo:
        return 0, 0

    figli_left, sb_left = helper(nodo.left)
    figli_right, sb_right = helper(nodo.right)

    sb = abs(figli_right-figli_left)
    
    return figli_right + figli_left + 1, max(sb, sb_right, sb_left)

def sbilanciamento(nodo):
    return helper(nodo)[1]
```