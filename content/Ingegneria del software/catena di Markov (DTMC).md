---
updated_at: 2026-10-05T15:14:45.400+02:00
---
> N.B.: Una catena di Markov ha uno stato corrente che cambia a ogni iterazione, attraversandola. L'input è ricevuto tutto insieme all'inizio, **inizializzando la catena** stessa; invece l'output è la **catena stessa di stati attraversati**, prodotta a ogni transizione.

> Una **catena di Markov a tempo discreto (DTMC)** è una tupla $(U, X, Y, p, g)$ tale che:

- $U$ è un [[insieme]] vuoto, finito o infinito che contiene i valori dell'**input** che può essere ricevuto all'inizio.
- $X$ è un insieme non vuoto, finito o infinito che contiene gli **stati**.
- $Y$ è un insieme non vuoto, finito o infinito che contiene i **valori di output** prodotti appena si arriva nei vari stati, cioè gli stati stessi.
- La [[funzione]] $p:\ X \times X \times U \to [0, 1]$ definisce la [[probabilità]] di transizione da uno stato $x \in X$ a uno stato $x' \in X$ dato un input $u \in U$.
  Essa è pari a $p(x' \mid x, u)$, cioè la [[probabilità condizionata]] di passare allo stato $X'$ se la DTMC ha come stato corrente $X$.
  La somma delle probabilità di tutti gli stati successivi di un determinato stato è 1. Nel continuo, vale che $\int_{X'} p (x' \mid x, u)\ dx^{'} = 1$
- La funzione $g:\ X \to Y$ è la funzione di output, che definisce l'output prodotto dalla DTMC a un determinato passo.

> La probabilità di un cammino su una catena di Markov è il prodotto delle probabilità di ogni transizione del cammino.

> Una rete di catene di Markov è essa stessa una catena di Markov.

# Notazione

> Avendo una catena $M$, $M(U)$ è il suo input, $M(X)$ il suo stato corrente e $M(Y)$ il suo output.

# Esempio di catena di Markov

![[Pasted image 20260929125921.png]]

- Per calcolare la probabilità che il processo termina in **esattamente** $n$ mesi, bisogna trovare a mano tutti i cammini che durano $n$ mesi, calcolarne le probabilità (prodotto delle probabilità di ogni transizione del cammino) e sommarle.
- Si può anche fare l'inverso, cioè calcolare la probilità incognita di una singola transizione fra due stati in modo che il processo termina in **esattamente** $m$ mesi è **almeno** $p_{\text{tot}}$ così:
	1. si trova il cammino che dura $m$ mesi,
	2. si risolve $p_{1} \cdot p_{2} \cdot \ldots \cdot x \cdot \ldots p_{n} \geq p_\text{tot}$.
   Questo può servire a capire quando "deve essere bravo" il team che si occupa di un determinato stato del design del progetto.

## Implementazione mia in Python

``` python
import random

def traverse(graph, start, end):
    output = []
    current = start
    i = 0
    while current != end:
        i += 1
        print(f'{i}. {current}')
        output.append(graph[current]['months'])
        current = random.choices(
            population=[next for next, p in graph[current]['next']],
            weights=[p for next, p in graph[current]['next']],
            k=1
        )[0]
    return output


graph = {
    'Requirements definition': {
        'months': 2,
        'next': [
            ('System development', 0.7),
            ('Requirements definition', 0.3),
        ]
    },
    'System development': {
        'months': 4,
        'next': [
            ('System development', 0.2),
            ('Requirements definition', 0.2),
            ('System testing', 0.6)
        ]
    },
    'System testing': {
        'months': 2,
        'next': [
            ('System development', 0.2),
            ('Requirements definition', 0.1),
            ('System testing', 0.1),
            ('END', 0.6)
        ]
    }
}

output = traverse(graph, 'Requirements definition', 'END')
print(f'\nmonths: {output}')
print(f'sum: {sum(output)}')
```

Output che mi è capitato:

```
1. Requirements definition
2. Requirements definition
3. System development
4. System development
5. System testing
6. System testing
7. System development
8. System testing
9. System development
10. System testing

months: [2, 2, 4, 4, 2, 2, 4, 2, 4, 2]
sum: 28
```

### Istogramma dei risultati di un milione di catene

``` python
import matplotlib.pyplot as plt

n = 1_000_000
samples = [
    sum(traverse(graph, 'Requirements definition', 'END'))
    for _ in range(n)
]

plt.hist(samples, bins=50, color='skyblue', edgecolor='black')
plt.xlabel('Months')
plt.ylabel('Frequency')
plt.show()

```

![[hist.png]]

Media = ~18.09 mesi per un progetto completo.

# Tempo di soggiorno nella catena di Markov

## A stati numerabili

Consideriamo un modello **semplificato** della catena di Markov, cioé una tupla $(X, P)$ dove $X$ è un'insieme [[cardinalità|numerabile]] non vuoto di stati e $P:\ X \times X \to [0, 1]$ è la probabilità di transizione della catena di Markov, che soddisfa la condizione $\sum_{x'\in X}P(x, x') = 1$.

Ad esempio, possiamo definire una catena di Markov

$$
(\mathbb{N}, P),\quad P(x, x') = \begin{cases} \frac{2}{3}\ \text{se}\ x' = x+2 \\ \frac{1}{3}\ \text{se}\ x' = x+1 \\ 0 \ \text{altrimenti} \end{cases}
$$

> N.B.: $\forall x \in \mathbb{N} \quad \sum_{x' \in \mathbb{N}} = 1$

## A stati finiti

> Nella catena $(X, P)$, se $X$ ha cardinalità finita, $P$ può essere rappresentata come una [[spazio vettoriale di matrici|matrice]] $n \times n$ che chiamiamo la **matrice di transizione** $Q$, indicizzata da $i$ sulle colonne e $j$ sulle righe, definita come $Q(i, j) = P(i,j)$, ovvero la probabilità che dallo stato $i$ si transiti nello stato $j$. La colonna $i$ rappresenta lo stato da cui si parte e la riga $j$ rappresenta lo stato prossimo a cui si arriva.

Segue che:

$$
\sum_{j=1}^{n} Q(i, j) = \sum_{j=1}^{n} P(i, j) = 1
$$

La rappresentazione della transizione come una matrice ci permette di calcolare la distribuzione di probabilità $z'$ dalla distribuzione $z$ in un singolo passaggio usando un prodotto [[spazio vettoriale|vettore]]-matrice:

$$
z' = z\ Q
$$

Per modellare un processo stocastico temporale, possiamo usare:

$$
P(X(t+1) = x' \mid X(t) = x) = P(x, x')
$$

Dove $t$ è l'istante corrente, $t+1$ il prossimo, $x$ lo stato all'istante $t$ e $x'$ lo stato all'istante $t+1$.

---

> Un **self-loop** è una transizione da uno stato a se stesso. La sua probabilità $P(x, x)$ è denotata $S(x)$.

> La distribuzione della **probabilità di salto** da $x$, denotata $J(x, k)$ è la probabilità che si facciano $k$ self-loop da $x$ in $x$ prima di prendere una transizione da $x$ a $k$.

Quindi:

- $J(x, 0) = 1 - S(x)$
- $J(x, 1) = S(x)(1 - S(x))$
- $\ldots$
- $K(x, k) = S(x)^{k}(1-S(X))$

> N.B.: $S(X) = 1 \implies J(x, k) = 0$.

$$
|z| < 1 \implies \sum_{k=0}^{+\infty}z^{k} = \frac{1}{1-z}
$$

## Tempo di soggiorno

> Il **tempo atteso di soggiorno** nello stato $x$, denotato $SJ(x)$ è il [[valore atteso di una variabile aleatoria|valore atteso]] del numero di self-loop fatti prima di lasciare $x$:

$$
SJ(x) = \sum_{k=0}^{+\infty}kJ(x, k) = \ldots = (1-S(x))\sum_{k=1}^{+\infty}kS(x)^{k}
$$
#todo