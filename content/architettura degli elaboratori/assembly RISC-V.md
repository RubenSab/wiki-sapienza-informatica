---
updated_at: 2025-04-15T12:34:10.027+02:00
---
# Implementazioni di costrutti ad alto livello in Assembly RISC-V

- [[array]]
- [[stringhe in RISC-V]]
- [[matrici in RISC-V]]
- [[cicli in RISC-V]]
- [[funzioni in RISC-V]]
# Istruzioni

- [[elenco di operazioni RISC-V]]

## Fasi di esecuzione di un istruzione

- **Fetch/caricamento della istruzione** dalla posizione indicata dal Program Counter;
- **Decodifica/riconoscimento** della istruzione, la Control Unit attiva le parti funzionali necessarie;
- **Load/caricamento di eventuali argomenti** a seconda dei modi di indirizzamento (vedi dopo);
- **Esecuzione della istruzione**, in genere da parte dell’[[ALU]]
- **Store/salvataggio del risultato** in memoria o in un registro
- **Aggiornamento del Program Counter** (contemporaneamente ad altre fasi)

## Com'è fatta un'istruzione?

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
### Formati delle istruzioni

Non tutte le istruzioni necessitano degli stessi campi, quindi si usano diversi [[formati delle istruzioni|formati]] per diverse categorie di istruzioni.

### Pseudoistruzioni

Sono istruzioni non implementate in hardware, ma che possono essere tradotte in istruzioni macchina, un modo compatto ed intuitivo per specificare un insieme di istruzioni o istruzioni ricorrenti.

La traduzione in linguaggio macchina sono effettuate dall'assemblatore.

```
mv x10, x11 → addi x10, x11, 0
li, x9, 123. → addi x9, x0, 123
```

### Modi di indirizzamento delle istruzioni

I [[modi di indirizzamento]] sono le tecniche utilizzate dai processori per determinare il dato memorizzato in un indirizzo (in memoria o in un registro), dato un indirizzo e spesso anche un'offset (spiazzamento).

## Etichette (label)

Gli indirizzi di salto sono noiosi da calcolare e possono indurre in facili errori, quindi esistono le **etichette** per semplificare il lavoro ai programmatori:

L’etichetta associa alla parola l’indirizzo dell’istruzione dove è scritta, potrà essere usata nel codice assembly al posto dell'indirizzo della [[memoria (RAM)]] che rappresenta (cioè alla riga del programma in esecuzione), come se fosse una costante numerica nei linguaggi ad alto livello.

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

## Direttive per l'assemblatore

Indicano lo scopo delle varie sezioni del programma (quindi della parte della RAM che contiene le istruzioni del programma da eseguire).

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

## System Calls

#todo