---
updated_at: 2026-03-07T17:31:34.125+01:00
---
Nella Java Virtual Machine, esistono due (+1) tipi di memoria:

- lo **[[stack]]** dove vengono caricate le **[[variabile|variabili]] locali**, i **riferimenti** agli [[oggetto|oggetti]];
- lo **heap**, dove vanno le aree di [[memoria]] allocate per la **creazione dinamica**;
- la zona speciale di memoria **nativa** (gestita dal sistema operativo stesso in automatico) detta **metaspace**, che memorizza i [[campi]] static.

## Cosa succede alla creazione di un [[oggetto]]?

1. **Dichiarazione**
    Viene dichiarata una variabile di riferimento all'oggetto. In questa fase viene allocata una porzione di [[memoria]] nello **stack**, che contiene un valore inizialmente indefinito (o `null` se viene assegnato esplicitamente).
    
2. **Creazione (allocazione)**
    L’oggetto vero e proprio viene creato tramite l’istruzione `new`. Questo comporta:
    
    - Allocazione di memoria nello **heap**, dove viene creata un'istanza della [[classe]].
    - Inizializzazione implicita dei campi con valori di default: `0` per i numeri, `false` per i booleani, `null` per i riferimenti, ecc.
        
3. **Assegnazione del riferimento**
    L'indirizzo di memoria dell'oggetto nello heap viene memorizzato nella variabile nello **stack**, creando un riferimento dallo stack all'heap.

## Cosa succede alla creazione di una [[variabile]] locale?

1. **Dichiarazione**  
    Viene dichiarata all'interno di un [[metodo]] o di un blocco. Viene allocata nello **stack**.
    
2. **Inizializzazione**  
    Viene assegnato un valore esplicito alla variabile. La memoria nello **stack** contiene direttamente il valore (non un riferimento, se è un tipo primitivo).
	- Per i **tipi primitivi**, lo stack contiene direttamente il valore.  
    - Per i **tipi riferimento**, lo stack contiene l'indirizzo dell'oggetto nello heap (se è stato creato con `new`).

## Cosa succede alla creazione di un [[campi|campo]] static?

1. I campi `static` vengono allocati **una sola volta per classe**, indipendentemente dal numero di oggetti creati.
2. Vengono allocati in una **sezione speciale della memoria chiamata Metaspace** (nelle JVM recenti, a partire da Java 8).
3. Vengono inizializzati all’avvio della classe (di solito al primo accesso a un membro statico o alla classe stessa), **prima** di qualsiasi istanza della classe.