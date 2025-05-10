---
updated_at: 2025-05-10T12:58:21.748+02:00
---
> Un array, o vettore, è una [[struttura dati]] statica che memorizza un insieme ordinato di elementi dello stesso [[tipi|tipo]] (per questo si dice che le array sono *omogenee*).

# Vantaggi e svantaggi

| Pros                                                                               | Cons                                     |
| ---------------------------------------------------------------------------------- | ---------------------------------------- |
| Si può accedere all'i-esimo elemento direttamente.                                 | Ha lunghezza immutabile.                 |
| Nel raro caso in cui non siano built-in, sono estremamente facili da implementare. | Rimuovere un elemento costa $\Theta(1)$. |
|                                                                                    | Sono omogenee.                           |
# [[complessità temporale|Costo]] delle operazioni

| operazione                                        | array disordinato | array ordinato |
| ------------------------------------------------- | ----------------- | -------------- |
| ricerca in base al valore                         | $O(n)$            | $O(\log n)$    |
| minimo e massimo                                  | $\Theta(n)$       | $\Theta(1)$    |
| inserimento\* a posizione $n\neq$ lunghezza array | $\Theta(n)$       | $O(n)$         |
| rimozione\* in base al valore                     | $\Theta(n)$       | $O(n)$         |
\*prevedono anche lo scorrimento per mantenere l'ordine tra gli elementi e coprire i buchi.
# In Java

> N.B.: le [[variabile|variabili]] di array contengono il riferimento all’array.

> Gli elementi di un array possono essere tipi primitivi (interi, double, ecc.) oppure riferimenti a oggetti (inclusi altri array!).

``` java
/* array di n (specificato in-line) elementi inizializzati al valore di default */
int[] numeri = new int[10];

/* array di n (variabile costante) elementi */
final int n = 10;
int[] numeri = new int[n];

/* array di n (variabile) elementi */
int numeroCifre = new Scanner(System.in).nextInt();
int[] numeri  new int[numeroCifre]

/* array specificando esplicitamente i valori */
int[] numeri = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
```

## Array a due dimensioni (matrice)

``` java
String[] righe = new String[100]
String[] colonne = new String[100]
String[][] matrice = new String[righe][colonne]
```

Implementiamo un'array come una lista ordinata di elementi contenuti nella [[memoria (RAM)]] a determinati indirizzi, con una distanza costante tra indirizzi di 4 byte (per l'architettura con word a 32 bit).

# In Assembly [[RISC-V]]

**Esempio con \[5, 10, 20\]**:

Innanzitutto riserviamo/allochiamo 3 slot di memoria RAM e inizializziamoli con 5, 10 e 20.

```
.data
	arr: .word 5, 10, 20

```

Ogni volta che scriveremo `arr`, l'assembler lo intenderà in automatico come l'indirizzo del primo elemento del vettore (0x10010000).

| Indirizzo di memoria | Valore |
| -------------------- | ------ |
| 0x10010000           | 5      |
| 0x10010004           | 10     |
| 0x10010008           | 20     |

Poi carichiamo i valori della lista dalla memoria a dei [[registri]]:

```
.text

	.globl _start

_start:

    la t1, arr        # carica l'indirizzo base di arr in t1

    # carica i valori dell'array in memoria

    lw t2, 0(t1)      # carica il valore all'indirizzo t1 + 0 in t2
    lw t3, 4(t1)      # carica il valore all'indirizzo t1 + 4 in t3
    lw t4, 8(t1)      # carica il valore all'indirizzo t1 + 8 in t4
```
