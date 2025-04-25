---
updated_at: 2025-04-16T12:55:47.962+02:00
---
![[Pasted image 20250415132516.png]]

# Come progettarla?

1. **Definire come viene elaborata un'istruzione** (in quali fasi viene eseguita?);
2. **Scegliere l'insieme di istruzioni da realizzare** (nel nostro caso tutte quelle dell'[[assembly RISC-V]] o quasi),
3. **Scegliere le unità funzionali necessarie** rendendosi conto che una singola unità può essere impostata per fare compiti diversi, quindi bisogna inserire delle linee di selezione adeguate,
4. **Collegare le unità funzionali tra loro** con i *datapath* (interconnessioni che definiscono il flusso di più bit per ognuna all'interno della [[CPU]]),
5. **Costruire la [[CU (unità di controllo)]]** che ha come output tutte le linee di selezione per le unità funzionali,
6. Calcolare il tempo massimo di esecuzione delle istruzioni per ottenere il **periodo di clock**.

## 1. [[fasi dell'esecuzione di un'istruzione|Fasi di esecuzione]]

## 2. Istruzioni da realizzare

Le istruzioni principali da implementare potranno scrivere e leggere nella memoria (`sw` e `lw`), potranno essere salti incondizionati o condizionati (`beq`) e operazioni aritmetico-logiche (`add, sub, xor...`).

È necessario ricordarsi i [[formati delle istruzioni]] per progettare i datapath.

## 3. Scegliere le unità funzionali necessarie

- Tutti i componenti della [[CPU]];
- gli [[elementi di stato (registri e RAM)]];
- l'unità di [[estensione del segno in CA2]], che serve a trasformare un intero relativo da 12 a 32 bit: serve perché i campi immediati sono lunghi 12 bit, ma l'[[ALU]] e i [[registri]] lavorano su 32 bit. Dovrà necessariamente essere migliorata, diventando l'unità "Genera cost.": essa estende il segno, moltiplica il risultato ottenuto per 2 (in RISC-V le istruzioni vengono indicizzate alla half-word) e la somma al [[PC (Program Counter)]];
- l'unità di controllo dell'ALU (a 4 bit di input e 2 di selezione): prende in **selezione** il tipo di operazione *ALUOp* (che proviene dalla CU) e in **input** campi funzione (*funz7* e *funz3*) in base alle casistiche, produce *le linee di controllo ALU* e le passa come **linee di selezione** all'ALU.

### Approfondimento sull'unità di controllo dell'ALU

La logica di controllo per l'ALU è implementata attraverso multipli livelli di decodifica:

1. Prima l'ALU viene impostata dalla sezione *ALUOp* dell'istruzione, che agisce come una **linea di selezione** a 2 bit:

| tipo di istruzione                     | ALUOp |
| -------------------------------------- | ----- |
| lw, sw (operazioni di memoria)         | 00    |
| beq (operazioni di salto)              | 01    |
| tipo R (operazioni aritmetico-logiche) | 10    |
2. Poi vengono considerati i campi funzione adatti al tipo di istruzione e vengono **passati in input** all'ALU control

- Le operazioni di memoria e di salto prendono tutto il campo *funz7* dell'istruzione
- quelle R prendono un solo bit di *funz7* (il 30esimo bit dell'istruzione) + tutto il campo *funz3* (i bit da 14 e 12 inclusi dell'istruzione).

2. L'ALU control produce e **restituisce in output** l'ingresso di controllo alla ALU:

| Linee di controllo ALU | Funzione                                      |
| ---------------------- | --------------------------------------------- |
| 0000                   | AND                                           |
| 0001                   | OR                                            |
| 0010                   | ADD                                           |
| 0110                   | SUB                                           |
| ...                    | altre 14 possibili operazioni da implementare |

> N.B.: Se un'unità funzionale può ricevere dati da più sorgenti è necessario inserire un [[multiplexer (MUX)]] per selezionare la sorgente giusta.

## 5. Costruzione dell'unità di controllo