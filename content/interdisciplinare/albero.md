---
updated_at: 2025-05-11T23:14:07.994+02:00
---
> Un albero radicato è una [[struttura dati]] composta da nodi organizzati gerarchicamente. Ha un nodo radice che non ha genitori. Ogni altro nodo dell'albero ha esattamente un genitore e può avere $n$ figli. I nodi che non hanno figli sono chiamati foglie.

- [[nomenclatura degli alberi]]
- [[rappresentazione degli alberi binari]]

# Implementazione con puntatori

``` python
class Nodo
	def __init__(self, key=None, left=None, right=None):
		self.key = key
		self.left = left
		self.right = right

# esempio di creazione
radice = Nodo(6)
radice.left = Nodo(9)
radice.right = Nodo(4)
radice.left.right = Nodo(1)
```

## Stampa

``` python
def stampa(p, h=0):
	if p:
		print('| '*h, p.key)
		stampa(p.left, h+1)
		stampa(p.right, h+1)
```

## Crea un albero con $n$ nodi e un numero casuale di figli

``` python
import random

def crea_albero(n, min_val, max_val):
	
	if n == 0:
		return None
	
	nuovo = Nodo(random.randint(min_val, max_val))
	
	s = random.randint(0, n-1)
	
	nuovo.left = crea_albero(s, min_val, max_val)
	nuovo.right = crea_albero(n-1-s, min_val, max_val)
	
	return p
```

# Visita dell'albero

> La visita dell'albero è l'accesso progressivo a tutti i suoi nodi con un determinato criterio di ordine.

Per gli alberi binari esistono tre possibili visite, ovviamente dallo stesso [[complessità temporale|costo computazionale]]:

- In **preordine**: il nodo è visitato prima di proseguire la visita nei suoi sottoalbero.

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
	if nodo is None:
		return
	postorder(nodo.left)
	postorder(nodo.right)
	print(nodo.key, end=' ')
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
def conta_nodi(nodo):
	if nodo == None:
		return 0
	return conta_nodi(nodo.left) + conta_nodi(nodo.right) + 1
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