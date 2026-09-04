---
updated_at: 2026-09-04T14:38:26.386+02:00
---
> È un miglioramento della [[tecnica divide et impera]] nel caso in cui i sotto-problemi si sovrappongono (non sono indipendenti). Consiste nel risolvere ogni sotto-problema una sola volta, memorizzandone il risultato per riutilizzarlo.

Ci sono due modi per implementare gli algoritmi con questo principio:

- **Memoizzazione**: è l'approccio top-down con la **ricorsione**, aiutata da una **cache**, a partire dal problema principale verso i casi base.
- **Tabulazione**: è l'approccio bottom-up con l'**iterazione** a partire dai casi base verso il problema principale.

#todo

---

# Tecnica mia (top-down)

1. Obiettivo (capire la consegna)
2. Scrivere la regola come [[induzione]] da uno stato in $t$ a uno stato in $t-1$.
3. Codificare la geometria del problema ([[array]], matrice, matrice 3D).
4. Scrivere i casi base dentro l'array/matrice/etc.
5. Formalizzare la regola secondo la geometria del problema (scrivere la condizione $T[i][j][\dots][t] = T[\dots][\dots][\dots][t-n]\ \dots$).
6. Test a mano almeno sull'esempio della consegna.
7. Scrivere il codice.

## Struttura di una funzione scritta con la PD

1. Definizione
2. Early returns
3. Inizializzazione struttura dati e casi base
4. Loop
5. Regola iterativa
6. Return del risultato

# Consigli

- Pensa "lo stato $t$ da quale tipo di stati $t-1$ può essere stato prodotto?". Ad esempio: "Una sequenza di interi con somma pari può essere stata prodotta da una sequenza interi con somma parti + un intero pari, oppure da una sequenza di interi con somma dispari + un intero dispari".
- Spesso quando la funzione prende come argomento una struttura dati e non un numero, non servono gli early return.
- Il loop inizia dopo l'indice dell'ultimo caso base.
- Le parentesi intorno all' `... if ... else ...` one-liner sono necessarie, anche se si trova alla fine della riga.
- L'istante passato è $t-1$, non $t$.
- Meglio fare condizioni positive e negarle. Combinare le negazioni è prono a errori.
- Più che pensare a come sono fatti gli stati, bisogna sempre pensare al loro numero.