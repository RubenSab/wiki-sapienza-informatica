---
updated_at: 2026-04-30T10:37:39.969+02:00
---
> Un [[algoritmo]] che usa questa tecnica **divide** il problema principale in sotto-problemi più piccoli, li risolve (**impera**) e **combina** le loro soluzioni per ottenere la soluzione finale.

È ideale per problemi che possono essere **scomposti** in modo efficiente in **sotto-problemi indipendenti**.

È il principio dietro a [[merge sort]], [[ricerca binaria]] e [[quick sort]].

# Esempio 1: il problema della selezione

> Dato un [[insieme]] di interi distinti e un intero $k, 0 \leq k \leq n-1$ vogliamo determinare quale elemento di troverebbe alla $k$-esima posizione se l'insieme venisse [[algoritmi di ordinamento|ordinato]] in modo crescente.

Si potrebbe ordinare l'insieme e restituire l'elemento in posizione $k$ con una [[complessità temporale]] di $O(n\log{n})$, però ci sono almeno due algoritmi che lo fanno in $O(n)$ in media senza dover ordinare.

## Algoritmo Quickselect

- **Divide**:  in $O(1)$ sceglie un pivot **casualmente** (per evitare di far degenerare la complessità a $O(n^{2})$ se il pivot scelto è sempre l'elemento minimo);
- **Impera**: l'[[array]] viene diviso due array, "minori del pivot" e "maggiori del pivot" in $O(n)$;
- **Combina**: si cerca ricorsivamente solo sull'array corretto, scelto confrontando $k$ con la lunghezza dell'array dei minori del pivot.

``` python
import random

def quick_select(insieme, posizione_k):
	# divide
	pivot = random.choice(insieme)
	# impera
	minori, maggiori = [], []
	for elemento in insieme:
		if elemento < pivot:
			minori.append(elemento)
		elif elemento > pivot:
			maggiori.append(elemento)
	# combina
	if posizione_k < len(minori): # l'elemento è nei minori
		return quick_select(minori, posizione_k)
	elif posizione_k == len(minori): # l'elemento è il pivot
		return pivot
	else: # l'elemento è nei maggiori
		return quick_select(maggiori, posizione_k-len(minori)-1)
```

#dadimostrare PL13 pag. 10 a 12

## Algoritmo della mediana delle mediane

Funziona esattamente come il quick select, tranne che per la scelta del pivot.

Ad ogni iterazione, al posto di sceglierlo casualmente, lo sceglie in modo che sia abbastanza lontano dagli estremi per poter **scartare una frazione costante di elementi a ogni passo**.

Divide l'array in gruppi da 5, calcola la mediana di ogni gruppo in $O(1)$ e chiama se stesso per trovare la mediana delle mediane, la quale sarà il pivot.

``` python
def selezione(insieme, posizione_k):
	# se è un array piccolo:
	if n < 10:
		insieme.sort()
		return insieme[posizione_k]
	
	mediane = []
	for i in range(0, n, 5):
		gruppo_da_5 = sorted(insieme[i: i+5]) # O(1)
		mediana_gruppo = gruppo[len(gruppo)//2]
		mediane.append(mediana_gruppo)
	# chiamata ricorsiva sulle 5 mediane (T(n/5))
	pivot = selezione(mediane, len(mediane)//2)
	
	# ... passaggi "impera" e "combina" del quick select
	# ... chiamata ricorsiva sul caso peggiore con 7n/10 elementi (T(7n/10))
```

## Di quanto si riduce l'array a ogni iterazione?

Per definizione di mediana, **almeno la metà** delle mediane dei gruppi da 5 è **minore del pivot** (mediana delle mediane) che troveremo.

In tutto ci sono $\lceil \frac{n}{5} \rceil$ gruppi, quindi $\lceil \frac{n}{10} \rceil$ mediane sicuramente minori del pivot.

In ognuno di questi gruppi dalla mediana minore del pivot, sicuramente ci sono anche altri 2 elementi inferiori al pivot; perché il **requisito minimo** per avere una mediana minore del pivot è avere **3 elementi minori del pivot** e 2 maggiori (tutti i gruppi sono da 5).

In totale, $3\frac{n}{10}$ elementi sono **sicuramente inferiori al pivot**.

D'altra parte si può dire anche che **almeno la metà** delle mediane dei gruppi da 5 è **maggiore del pivot**; quindi applicando il ragionamento in modo analogo abbiamo $3 \frac{n}{10}$ elementi **sicuramente maggiori del pivot**.

Segue che in entrambi i casi, durante lo smistamento degli elementi nelle 2 array, i casi più sbilanciati possibili prevedono $n-3 \frac{n}{10} = \frac{7}{10}n$ elementi in un'array e $\frac{3}{10}n$ elementi nell'altra.

Nei casi peggiori in assoluto, dove la sotto-array corretta è sempre quella più grande ($\frac{7}{10}n$), la dimensione della nuova sotto-array da smistare è $\frac{7}{10}$ di quella precedente.

Sommando il costo delle due chiamate ricorsive abbiamo

$$
T(n) \leq O(n) + T\left(\left\lceil\frac{n}{5} \right\rceil\right)+ T\left(\frac{7n}{10}\right)
$$

risolvendo con il [[metodo di sostituzione]] si ottiene $O(n)$ **nel caso peggiore**.

## Note

> N.B.: Nonostante il caso peggiore $O(n^{2})$ di quick select, esso è preferito rispetto alla mediana delle mediane per la sua facilità di implementazione, il **fattore costante inferiore** (**velocità maggiore** nella pratica) e la rarità estrema del caso $O(n^{2})$.
> Tuttavia la mediana delle mediane da una **garanzia matematica** maggiore (caso medio = caso peggiore).

# Esempio 2: Coppia di punti a distanza minima

#todo PL14 pag. 3 a 10

# Esempio 3: Conteggio delle inversioni

> Dato un array di interi, contare le inversioni, cioè tutte le coppie di interi in cui quello con l'indice più grande è minore di quello con l'indice più piccolo.

Esaustivamente, si potrebbe confrontare ogni coppia possibile in $\Theta(n^{2})$; però esiste un'alternativa migliore basata sul divide et impera.

Si modifica il [[merge sort]] per contare e ritornare anche il numero delle inversioni in $O(n\log{n})$.

Se, durante l'esecuzione della funzione `merge`, l'elemento corrente dell'array di **sinistra** è **maggiore** dell'elemento corrente dell'array a **destra**, allora tutti gli elementi ancora da processare dell'array a **sinistra** sono sicuramente più grandi di esso; quindi si formano tante inversioni quanti sono questi elementi rimanenti a sinistra (lunghezza dell'array a sinistra **meno** il puntatore dell'elemento corrente a sinistra).

La funzione `mergesort` deve essere modificata per sommare e ritornare le inversioni trovate con `merge` più quelle trovate prima nelle array destra e sinistra.

``` python
def merge(left, right):

    sorted_array = []
    i = j = 0
    inversions = 0

    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sorted_array.append(left[i])
            i += 1
        else:
            sorted_array.append(right[j])
            j += 1
            inversions += len(left) - i # elementi rimanenti a sinistra

    sorted_array.extend(left[i:])
    sorted_array.extend(right[j:])

    return sorted_array, inversions


def mergesort(array):
    if len(array) == 1:
        return array, 0 # numero di inversioni
    elif len(array) == 2:
        if array[0] > array[1]:
            return [array[1], array[0]], 1 # numero di inversioni
        else:
            return array, 0 # numero di inversioni
    else:
        mid = len(array) // 2
        left_sorted_arr, left_inversions = mergesort(array[:mid])
        right_sorted_arr, right_inversions = mergesort(array[mid:])
        merged_arr, merge_inversions = merge(left_sorted_arr, right_sorted_arr)
        return merged_arr, merge_inversions + left_inversions + right_inversions


def count_inversions(array):
    return mergesort(array)[1]
```