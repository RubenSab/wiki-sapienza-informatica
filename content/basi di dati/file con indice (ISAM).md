---
updated_at: 2026-01-30T13:03:19.438+01:00
---
# Cosa risolve l'ISAM

Quando le chiavi dei dati memorizzati in un [[database]] hanno un ordinamento naturale (come interi e stringhe), è conveniente tenerne conto nell'[[organizzazione fisica di un database relazionale|organizzazione fisica del database]]. Per più campi si può ordinare sul primo, poi il secondo e via dicendo.

Ciò è utile perché avendo una [[struttura dati]] ordinata, l'operazione di ricerca può fare uso della **[[ricerca binaria]]**, che ha [[complessità temporale]] [[notazione O-grande|logaritmica]].

# Cos'è l'ISAM

> Il file ***ISAM*** *(Indexed Sequential Access Method)* è un file i cui record sono ordinati in base alla ***chiave di ricerca***. In genere viene lasciato dello spazio libero in ogni blocco.

Questa struttura dati si divide in due parti:

- il **file indice**: è un file ordinato i cui record sono composti dalla **chiave di ricerca** e dal **[[puntatore]]** al primo record (quello con la chiave dal valore minore) di un blocco del **file principale**.
  Potrebbe comunque essere così grande da non entrare nella [[memoria]] principale, quindi potrebbe necessitare di essere caricato a pezzi dalla memoria secondaria.
- il **file principale**: è il file ordinato di record che contiene il database.

# Operazioni

## Ricerca

### Ricerca binaria

La ricerca binaria avviene sul file indice.

Cercando una chiave $k$ su $m$ blocchi [[algoritmo]] è:

- Si legge il blocco $\frac{m}{2}+1$ e si confronta $k$ con $k_{1}$ (la prima chiave del blocco):
	- Se $k=k_{1}$ ritorna $\frac{m}{2}+1$. 
	- Se $k < k_{1}$ si ripete l'algoritmo da $1$ a $\frac{m}{2}$.
	- Se $k > k_{1}$ si ripete l'algoritmo da $\frac{m}{2}+1$ a $m$.

Ci si ferma quando lo **spazio di ricerca** è ridotto ad un unico blocco. Dato che esso si dimezza a ogni iterazione, in media abbiamo $\left\lceil \log_{2} m\right\rceil$ accessi.

### Ricerca per interpolazione

La ricerca per interpolazione è una miglioria di quella binaria: al posto di dividere a metà lo spazio di ricerca ogni volta, applica una [[funzione]] basata su un'approssimazione della distribuzione delle chiavi **conosciuta a priori**, che prende come argomenti tre chiavi e restituisce la **frazione** dello spazio di ricerca tra la prima e la terza chiave in cui si deve trovare la seconda chiave.

Richiede solo $\approx 1+\log_{2}(\log_{2}(m))$ accessi, ma spesso conoscere $f$ o è troppo difficile o è praticamente impossibile.

## Inserimento

L'inserimento costa al minimo come la ricerca, a cui si aggiunge:

- +1 accesso per scrivere il nuovo record nel blocco modificato se nel blocco c'è dello spazio libero;
- la richiesta di un nuovo blocco al file system, ripartire i record tra vecchio e nuovo blocco e riscrivere tutti i blocchi modificati.

## Cancellazione

La cancellazione costa al minimo come la ricerca, a cui si aggiunge:

- +1 accesso per scrivere il blocco modificato se **non** si sta cancellando il primo record del blocco;
- +2 accessi se si sta cancellando **il primo record del blocco**, perché bisogna spostare il prossimo record alla prima posizione e azzerare il record che lo conteneva;
- la modifica del file indice e la restituzione del blocco al sistema se si sta cancellando l'unica chiave del blocco.

## Modifica

- Se **non** coinvolge la chiave costa ricerca+1 per riscrivere il blocco modificato;
- se **coinvolge** la chiave corrisponde a **cancellazione** + **inserimento**.

# ISAM con record puntati

> L'ISAM visto fin'ora è quello classico, detto *sparso*. Esiste anche un altro tipo di ISAM detto *con record puntati*, dove al posto del singolo blocco ci sono delle [[linked list]] di blocchi, come nel [[file hash]].

Qui i record non possono essere spostati, perché deve essere mantenuto l'ordinamento. Se non c'è abbastanza spazio per inserire un nuovo record nel blocco B, bisogna richiedere al sistema un nuovo blocco collegato a B tramite un puntatore.