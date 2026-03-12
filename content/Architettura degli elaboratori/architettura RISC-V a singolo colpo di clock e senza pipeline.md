---
updated_at: 2025-06-03T11:46:02.586+02:00
---
![[Pasted image 20250415132516.png]]

Questa CPU implementa le [[assembly RISC-V|istruzioni]] di Tipo R, `lw`, `sw` e `beq`.
# Come progettarla?

1. **Scegliere l'insieme di istruzioni da realizzare**,
2. **Definire come viene elaborata un'istruzione** (in quali fasi viene eseguita),
3. **Scegliere le unità funzionali necessarie** rendendosi conto che una singola unità può essere impostata per fare compiti diversi, quindi bisogna inserire delle linee di selezione adeguate,
4. **Collegare le unità funzionali tra loro** con i *datapath* (interconnessioni che definiscono il flusso di più bit per ognuna all'interno della [[CPU]]),
5. **Costruire la [[CU (Control Unit)]]** che ha come output tutte le linee di selezione per le unità funzionali,
6. Calcolare il tempo massimo di esecuzione delle istruzioni per ottenere il **periodo di clock**.

## 1. Istruzioni da realizzare

Decidiamo di implementare:
- `add` e`sub` che sono operazioni aritmetico-logiche,
- `beq`, salto condizionato,
- `sw` e `lw` che scrivono e leggono in memoria.

È necessario ricordarsi i [[formati delle istruzioni]] per progettare i datapath.

## 2. [[fasi dell'esecuzione di un'istruzione]]

## 3. Scegliere le unità funzionali necessarie

- Tutti i componenti della [[CPU]];
- gli [[elementi di stato (registri e RAM) dell'architettura RISC-V]];
- l'unità di [[estensione del segno in CA2]], che serve a trasformare un intero relativo da 12 a 32 bit: serve perché i campi immediati sono lunghi 12 bit, ma l'[[ALU]] e i [[registri]] lavorano su 32 bit. Dovrà necessariamente essere migliorata, diventando l'unità "Genera Costante": essa estende il segno, moltiplica il risultato ottenuto per 2 (in RISC-V le istruzioni vengono indicizzate alla half-word) e la somma al [[PC (Program Counter)]];
- L'*ALU Control Unit* (a 4 bit di input e 2 di selezione) prende in **selezione** il tipo di operazione *ALUOp* (che proviene dalla CU) e in **input** campi funzione (*funz7* e *funz3*) in base alle casistiche, produce *le linee di controllo ALU* e gliele passa come **linee di selezione**.

### Approfondimento sull'unità di controllo dell'ALU

La logica di controllo per l'ALU è implementata attraverso 2 livelli di decodifica:

- Selezione: L'ALU Control viene impostata da *ALUOp* che proviene dalla CU e agisce come una **linea di selezione** a 2 bit:

| tipo di istruzione                     | ALUOp |
| -------------------------------------- | ----- |
| lw, sw (operazioni di memoria)         | 00    |
| beq (operazioni di salto)              | 01    |
| tipo R (operazioni aritmetico-logiche) | 10    |

In base all'*ALUOp* si prendono i campi funzione adatti al tipo di istruzione e vengono **passati in input** all'ALU Control:

- Le operazioni di memoria e di salto prendono tutto il campo *funz7* dell'istruzione
- quelle R prendono un solo bit di *funz7* (il 30esimo bit dell'istruzione) + tutto il campo *funz3* (i bit da 14 e 12 inclusi dell'istruzione).

L'ALU control produce e **restituisce in output** la linea di selezione dell'ALU:

| Linee di controllo ALU | Funzione                                      |
| ---------------------- | --------------------------------------------- |
| 0000                   | AND                                           |
| 0001                   | OR                                            |
| 0010                   | ADD                                           |
| 0110                   | SUB                                           |
| ...                    | altre 14 possibili operazioni da implementare |

> N.B.: Se un'unità funzionale può ricevere dati da più sorgenti è necessario inserire un [[multiplexer (MUX)]] per selezionare la sorgente giusta.

## 5. Costruzione dell'unità di controllo

| Nome del segnale in output/linea di selezione per gli altri componenti | Effetto quando non assetito                                         | Effetto quando asserito                                                                                                            |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| ALUSrc (immediate)                                                     | Il secondo operando dell'ALU proviene da "Dato letto 2"             | Il secondo operando della ALU proviene dall'estensione del segno dei 12 bit del campo immediato dell'istruzione                    |
| MemToReg                                                               | Il dato inviato al register [[file]] per la scrittura proviene dall'ALU | Il dato inviato al register [[file]] per la scrittura proviene dalla Memoria Dati                                                      |
| RegWrite                                                               | Nullo                                                               | Il dato da scrivere viene memorizzato nel registro da scrivere                                                                     |
| MemRead                                                                | Nullo                                                               | Il dato della memoria nella posizione puntata dall'indirizzo viene inviato in uscita sulla linea "Dato Letto"                      |
| MemWrite                                                               | Nullo                                                               | Il contenuto della memoria nella posizione puntata dall'indirizzo viene sostituito con il dato presente sulla linea "Dato Scritto" |
| Branch (anche detto PCSrc)                                             | Il Program Counter si aggiorna normalmente (+4)                     | Il Program Counter esegue il salto                                                                                                 |
| ALUOp (2 bit)                                                          | Nullo (ad esempio nelle operazioni di memoria)                      | Passa come linea di selezione nell'unità di controllo dell'ALU, essa poi producerà l'*OpCode* dell'ALU                             |

| istruzione | ALUSrc | MemToReg | RegWrite | MemRead | MemWrite | Branch | AluOP |
| ---------- | ------ | -------- | -------- | ------- | -------- | ------ | ----- |
| Tipo R     | 0      | 0        | 1        | 0       | 0        | 0      | 10    |
| lw         | 1      | 1        | 1        | 1       | 0        | 0      | 00    |
| sw         | 1      | $\delta$ | 0        | 0       | 1        | 0      | 00    |
| beq        | 0      | $\delta$ | 0        | 0       | 0        | 1      | 01    |

## 6. Calcolare i tempi di esecuzione

È noto che:

| componente                              | tempo di esecuzione  |
| --------------------------------------- | -------------------- |
| memoria (accesso per dati o istruzioni) | 200 ps (Fetch e MEM) |
| ALU e [[adder]]                         | 200 ps (EX e PC)     |
| registri (lettura o scrittura)          | 100 ps (ID e WB)     |
| tutte le altre componenti               | 0 ps                 |

Da ciò si possono calcolare i tempi di esecuzioni delle istruzioni (in picosecondi)

| istruzione | Fetch dell'istruzione | lettura dei registri | ALU | accesso alla memoria | register write back | totale |
| ---------- | --------------------- | -------------------- | --- | -------------------- | ------------------- | ------ |
| `lw`       | 200                   | 100                  | 200 | 200                  | 100                 | 800    |
| `sw`       | 200                   | 100                  | 200 | 200                  |                     | 700    |
| Tipo R     | 200                   | 100                  | 200 |                      | 100                 | 600    |
| `beq`      | 200                   | 100                  | 200 |                      |                     | 500    |
