---
updated_at: 2026-05-13T19:51:15.046+02:00
---
> Il **backtracking** può risolvere problemi di **enumerazione, ricerca e ottimizzazione**. Consiste nella visita esaustiva dello spazio delle soluzioni, le quali vengono esplorate seguendo un itinerario ad [[albero]] (le cui **foglie** sono le **soluzioni**) da un [[algoritmo]] che trova una soluzione, poi procede, torna indietro e cambia strada se non ci sono più soluzioni valide nel ramo corrente (cioè quando si raggiunge una "foglia").

# Pruning o potatura

> Si può ottimizzare il backtracking decidendo di non esplorare rami che la **funzione di potatura** ritiene non promettenti.

La [[complessità temporale]] di un algoritmo che implementa il backtracking con potatura è:

$$
O\left(\underset{\text{n. di soluzioni}}{\underbrace{S(n)}} \cdot \underset{\text{costo operazioni su foglie}}{\underbrace{g(n)}} + \underset{\text{altezzza albero}}{\underbrace{h}} \cdot \underset{\text{n. di soluzioni}}{\underbrace{S(n)}}\cdot \underset{\text{costo operazioni su nodi non foglie}}{\underbrace{f(n)}}\right)
$$
# Esempi

## Stampare e stringhe binarie lunghe $n$ che hanno al massimo $k$ uno consecutivi

Possiamo usare due approcci:

- aggiungere 0 e 1 senza controllare la correttezza della stringa formata, poi controllare una volta raggiunta una foglia dell'albero (approccio senza potatura),
- aggiungere 0 e 1 **solo se** si produce una stringa corretta (approccio migliore con funzione di potatura).

``` python
def es(n, k, numero_di_1_consecutivi = 0, sol = []):
	if len(sol) == n: # caso foglia
		print("".join(sol))
		return
	# casi non foglia
	# si può sempre aggiungere uno 0
	sol.append('0')
	es(n, k, numero_di_1_consecutivi, sol)
	sol.pop()
	# per aggiungere 1 bisogna fare un controllo (funzione di potatura)
	if numero_di_1_consecutivi < k:
		sol.append('1')
		es(n, k, numero_di_1_consecutivi+1, sol)
		sol.pop()
```

## Generare tutte le matrici binarie quadrate con righe crescenti

*Per righe crescenti si intende che ogni riga va intesa come un numero binario e questi numeri sono disposti in ordine crescente dall'alto verso il basso nella matrice*.

Si dimostra che le matrici binarie quadrate di lato $n$ senza vincolo sono $2^{n^{2}}$, quelle con il vincolo sono $n^{n}$.

*(Soluzione mia che sfrutta l'[[omomorfismo]] tra una lista di interi e le righe di una [[spazio vettoriale di matrici|matrice]] binaria)*

``` python
def test(n, sol=[]):
	# caso foglia:
	# stampa la matrice se tutte le sue righe sono state calcolate
    if len(sol) == n:
        print(*map_to_matrix(sol, n), sep='\n', end='\n\n')
        return
    # caso non foglia:
    for i in range(2**n):
	    # solo se la matrice è vuota o l'ultima riga è minore di quella nuova proposta (funzione di potatura), aggiungi la nuova riga (rappresentazione binaria di i) alla matrice
        if not sol or i >= sol[-1]:
            sol.append(i)
            test(n, sol)
            sol.pop()

# converte una lista di numeri in una matrice binaria le cui righe sono le rappresentazioni binarie di ogni numero corrispondente
def map_to_matrix(int_list, n):
    matrix = []
    for i in int_list:
        row = list(bin(i)[2:])
        padding = ['0'] * (n - len(row))
        matrix.append(padding + row)
    return matrix

test(4)

```

output:

```
...

['0', '1', '0']
['0', '1', '1']
['1', '1', '1']

['0', '1', '0']
['1', '0', '0']
['1', '0', '0']

...
```