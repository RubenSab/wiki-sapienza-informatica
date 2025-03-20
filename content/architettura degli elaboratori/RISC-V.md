---
updated_at: 2025-03-20T10:17:45.008+01:00
---
> **Reduced Instruction Set Computers**: RISC-V è un'**A**rchitettura di **S**et di **I**struzioni (ISA) open-source, cioè un set minimo di istruzioni semplici che possiamo far eseguire al computer.

# In che contesto e come opera RISC-V?
## [[registri]]

L'architettura RISC-V ha:
- 32 [[registri generali dell'architettura RISC-V|registri generali]] per gli interi (x0, x1, ..., x31)
- 32 registri per i numeri in [[rappresentazione o codifica di numeri con la virgola (IEEE 754)|floating point]] (f0, f1, ..., f31)
- [[Program Counter]]
- Control Status Registers
- [[memoria RAM]] centrale

I registri hanno lunghezza fissa, sono chiamati x0, x1 ... x31, usati per memorizzare (ordini di grandezza più velocemente della memoria) sia dati temporanei che istruzioni. Ogni istruzione è codificata da una [[unità di misura del sistema binario|word]] immagazzinata in un singolo registro.

> N.B.: Il registro x0 contiene sempre il valore 0 (una sequenza di 32 zeri) e non può essere scritto (si può tentare a scriverci sopra ma non avrà alcun effetto).

## memoria

La [[memoria RAM]] consente di memorizzare vettori, altre strutture dati, il contenuto dei registri ***e il programma stesso (!!!)*** (**ogni riga è indicizzata in un indirizzo di memoria**): vi si accede dai registri solamente attraverso istruzioni di trasferimento dati dai registri (S-type).

Abbiamo a disposizione $2^{30}$ word (di 32 bit) a 32 bit di memoria, dalla posizione Memoria\[$0$\] a Memoria\[$2^{32}-4$\].

> N.B.: Nel RISC-V, la memoria è organizzata con **indirizzamento al byte**, ovvero ogni indirizzo di memoria identifica **un singolo byte**. Tuttavia, poiché una **word** in RISC-V a 32 bit è formata da **4 byte**, due word consecutive in memoria si trovano a **4 indirizzi di distanza**.

> N.B.: Il RISC-V non ha il vincolo di [[allineamento]]: le parole (DATI) non devono iniziare ad indirizzi multipli di 4 (ma per motivi di prestazione e atomicità delle istruzioni si preferisce allineare).

> N.B.: Gli indirizzi sono **little-endian** (byte meno significativo è memorizzato per primo, nella locazione di memoria con indirizzo minore).

## istruzioni

La codifica di un'istruzione deve indicare:

- L'**OpCode**: quale operazione far svolgere alla [[CPU]] (e se necessario quale sotto-operazione va svolta)
- Quali **argomenti** sono necessari
- Dove mettere il risultato

Più nel dettaglio, ogni istruzione ha una lunghezza totale fissa di 32 bit, e in linea di massima (ma ci sono diversi [[formati delle istruzioni]]) ha come campi:

- **OpCode** (**7 bit**)(operation code): l'"etichetta" che codifica il tipo di operazione da eseguire,
- **funct3** (**3 bit**): una parte aggiuntiva dell'OpCode nel caso esso non sia sufficiente a specificare l'operazione, non è adiacente all'OpCode,
- **funct7** (**3 bit**): un'altra parte aggiuntiva dell'OpCode, non è adiacente all'OpCode,
- **rs1** (**5 bit**): (first register source): l'indirizzo del registro in cui è memorizzato il primo argomento dell'istruzione,
- **rs2** (**5 bit**): (second register source): l'indirizzo del registro in cui è memorizzato il secondo argomento dell'istruzione,
- **rd** (**5 bit**): (register destination): l'indirizzo del registro in cui va scritto il risultato dell'operazione.
### formati delle istruzioni

Non tutte le istruzioni necessitano degli stessi campi, quindi si usano diversi **[[formati delle istruzioni|formati]]** per diverse categorie di istruzioni.

- [[elenco di operazioni RISC-V]]
### modi di indirizzamento

I [[modi di indirizzamento]] sono le tecniche utilizzate dai processori per determinare il dato memorizzato in un indirizzo (in memoria o in un registro), dato un indirizzo.

### etichette (label)

Gli indirizzi di salto sono noiosi da calcolare e possono indurre in facili errori, quindi esistono le **etichette** per semplificare il lavoro ai programmatori:

L’etichetta associa alla parola l’indirizzo dell’istruzione dove è scritta, potrà essere usata nel codice assembly al posto dell'indirizzo della [[memoria RAM]] che rappresenta (cioè alla riga del programma in esecuzione), come se fosse una costante numerica nei linguaggi ad alto livello.

- L’assemblatore converte le etichette in salti o in indirizzi
- Le pseudoistruzioni possono usare come argomenti le etichette

Esempio: etichetta per una funzione

```
sum:                # Etichetta "sum"
    add a0, a0, a1  # Somma a0 + a1 e salva in a0
    ret             # Ritorna (usa ra per tornare)
```

Esempio: etichetta per un [[cicli in RISC-V|ciclo]]

```
loop:           
    addi t0, t0, 1  # Incrementa t0 di 1
    blt t0, t1, loop # Se t0 < t1, salta a "loop"
```

Esempio: etichetta per dati in memoria

```
.data
message: 
    .asciz "Hello, RISC-V!\n"

.text
    la a0, message  # Carica l'indirizzo di "message" in a0
```

### pseudoistruzioni

Sono istruzioni non implementate in hardware, ma che possono essere tradotte in istruzioni macchina, un modo compatto ed intuitivo per specificare un insieme di istruzioni o istruzioni ricorrenti.

La traduzione in linguaggio macchina sono effettuate dall'assemblatore.

```
mv x10, x11 → addi x10, x11, 0
li, x9, 123. → addi x9, x0, 123
```

### fasi di esecuzione di un istruzione

- **Fetch/caricamento della istruzione** dalla posizione indicata dal Program Counter;
- **Decodifica/riconoscimento** della istruzione, la Control Unit attiva le parti funzionali necessarie;
- **Load/caricamento di eventuali argomenti** a seconda dei modi di indirizzamento (vedi dopo);
- **Esecuzione della istruzione**, in genere da parte dell’[[unità aritmetico logica (ALU)]]
- **Store/salvataggio del risultato** in memoria o in un registro
- **Aggiornamento del Program Counter** (contemporaneamente ad altre fasi)

## direttive per l'assemblatore

| nome    | sezione                      |
| ------- | ---------------------------- |
| .data   | definizione dei dati statici |
| .text   | definizione del programma    |
| .asciiz | stringa terminata da `\0`    |
| .byte   | sequenza di byte             |
| .double | sequenza di double           |
| .float  | sequenza di float            |
| .half   | sequenza di half words       |
| .word   | sequenza di words            |

# Implementazioni di costrutti ad alto livello in RISC-V Assembly

- [[vettori in RISC-V]]
- [[stringhe in RISC-V]]
- [[matrici in RISC-V]]
- [[cicli in RISC-V]]
- [[funzioni in RISC-V]]

# Esempi e altro

- [[esempio di codice RISC-V]]
- [[differenze tra CISC e RISC]]
- [[system calls]]