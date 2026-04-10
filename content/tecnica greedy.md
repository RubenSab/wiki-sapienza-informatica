---
updated_at: 2026-04-10T12:01:28.260+02:00
---
> La **tecnica greedy** è un approccio per progettare [[algoritmo|algoritmi]]: consiste nello sviluppare algoritmi *greedy* (avidi), i quali **assumono** che una serie di scelte **localmente ottimali** portino a una soluzione **globalmente ottimale**. Inoltre tutte le scelte locali che essi compiono passo passo sono **irrevocabili** e non considerano mai le conseguenze future anche immediate.

Dato che l'ottimalità locale non implica necessariamente quella globale, bisogna sempre dimostrare la correttezza dell'assunto.

> Una tecnica utile è l'**argomento di scambio**, dove si confronta l'algoritmo greedy con uno ottimale ipotetico (la cui esistenza è posta per assurdo) e si dimostra che si possono scambiare delle parti dell'algoritmo ottimale ipotetico per renderlo identico a quello greedy. Ciò porta a una contraddizione dell'assurdo, dimostrando che l'algoritmo greedy **è** quello ottimo.

# Esempi

- [[algoritmo di Dijkstra]] (scelta locale del vertice non ancora visitato con la distanza minima);
- [[algoritmo di Kruskal]] (scelta locale dell’arco con il peso minimo che non forma un ciclo).

## Algoritmo di *selezione* di attività

> Dato un [[insieme]] di attività con orario di inizio e fine, si deve selezionare il **[[sottoinsiemi|sottoinsieme]] massimo di attività** che non si sovrappongono.

Dei piccoli esempi dimostrano che scegliere le attività a ogni passo in base a:

- quella che dura di meno,
- quella che inizia prima,
- quella che crea meno conflitti con quelle non ancora scelte,

sono criteri incorretti, ma scegliere le attività in base a **quella che finisce prima** è il criterio greedy corretto.

``` python
def selezione_finisce_prima(attività: list[tuple[int, int]]):
    attività.sort(key = lambda x: x[1]) # O(n*logn)
    tempo = 0
    S = []
    for inizio, fine in attività:
        if tempo <= inizio:
            S.append((inizio, fine))
            tempo = fine
    return S
```

Ha [[complessità temporale]] $O(n\log{n})$ perché l'[[algoritmi di ordinamento|ordinamento]] è il passo più complesso.

Test:

``` python
attività = [(0, 1), (1, 3.5), (3, 5.5), (4.5, 8.5), (4.5, 6.5), (6, 9.5), (7, 10.5), (8, 10.5)]

print(selezione_finisce_prima(attività))

# output: [(0, 1), (1, 3.5), (4.5, 6.5), (7, 10.5)]
```

### Dimostrazione (per argomento di scambio)

#dadimostrare 

## Algoritmo di *assegnazione* delle attività

> Dato un insieme di attività con orario di inizio e fine, si devono assegnare al **minor numero di aule** in modo che in ogni aula nessuna attività si sovrapponga.

Il criterio greedy precedente dell'orario di fine è sbagliato: bisogna ordinare le attività per orario di inizio e assegnarle alla prima aula disponibile o crearne una nuova se non esiste.

``` python
class Aula:
    def __init__(self):
        self.orario_liberazione = 0
        self.attività = []

    def accoda(self, a: tuple(float, float)):
        self.attività.append(a)
        self.orario_liberazione = a[1]

    def __repr__(self):
        return str(self.attività)


def assegna_aule(attività: list[tuple[int, int]]):
    attività.sort(key = lambda x: x[0])
    tempo = 0
    aule = [Aula()]
    for inizio, fine in attività:
        attività_assegnata = False
        for aula in aule:
            if aula.orario_liberazione <= inizio:
                aula.accoda((inizio, fine))
                attività_assegnata = True
                break
        if not attività_assegnata:
            nuova_aula = Aula()
            nuova_aula.accoda((inizio, fine))
            aule.append(nuova_aula)
    return aule
```

Ha complessità temporale $O(n^{2})$, perché è un ciclo annidato (esaustivo nel caso peggiore) su attività e aule.

Test:

``` python
A = [(1, 4), (3, 6), (7.5, 10.5), (4, 5.5), (4.5, 8.5), (5.5, 9.5), (3, 6), (9, 11)]

print(*assegna_aule(A), sep='\n')

# output:
# [(1, 4), (4, 5.5), (5.5, 9.5)]
# [(3, 6), (7.5, 10.5)]
# [(3, 6), (9, 11)]
# [(4.5, 8.5)]
```

### Dimostrazione (diretta)

#dadimostrare

### Ottimizzazione

Questo algoritmo si può ottimizzare usando un [[heap|min-heap]] di aule ordinato sull'orario di liberazione. L'estrazione dell'"aula minima" (quella che si libera prima) ha complessità temporale $O(\log{n})$, quindi la complessità diventa dell'algoritmo è $O(n\log{n})$.