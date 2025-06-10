---
updated_at: 2025-06-10T16:53:56.483+02:00
---
> La cache è una memoria intermedia tra la [[CPU]] e la [[memoria (RAM)]]. È molto più veloce della RAM e serve per rendere disponibili i dati e le istruzioni utili alla CPU in modo più veloce.

In questo corso ci siamo concentrati sulla cache dati piuttosto che sulla cache istruzioni.

# Princìpi della cache

La cache copia i dati della RAM in base a due principi:
- il **principio di località temporale**: è più probabile che i dati acceduti recentemente dalla CPU saranno di nuovo acceduti in futuro, quindi la cache li memorizza.
- il **principio di località spaziale**: è più probabile che i dati fisicamente adiacenti alla posizione di un dato già acceduto saranno anch'essi accessi (si pensi agli indici di una lista), quindi la cache li memorizza.

> Se la CPU chiede alla memoria un dato in base al suo indirizzo e la cache lo ha già memorizzato, allora si parla di *cache hit*, se invece il dato non è presente nella cache ma sta solo nella memoria RAM, allora si parla di *cache miss*.

# Struttura della memoria cache

La cache divide l'informazione in *blocchi*, che sono le unità più piccole di memoria che può trasferire. Hanno una lunghezza fissa di 32, 64 o 138 byte, ma la maggior parte delle cache usa blocchi da 64 byte perché sono i più veloci.

### Campi del blocco

| Campo                       | Descrizione                                                                                                | Lunghezza                                                                      |
| --------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Valid bit**               | Indica se il blocco contiene dati validi                                                                   | 1 bit                                                                          |
| **Tag**                     | Rappresenta **i bit più significativi dell’indirizzo** che identificano univocamente il blocco nella cache | lunghezza indirizzo (32 o 64 bit) - lun. **set index** - lun. **block offset** |
| **Dati**                    | È il contenuto vero e proprio di dati.                                                                     | Dipende dalla dimensione del blocco (es. 32, 64 byte)                          |
| **(Facoltativo: Used bit)** | Indica se il dato in un blocco è stato già usato                                                           | 1 bit                                                                          |

La somma delle dimensioni di tutti questi campi da la lunghezza totale di un blocco.

|                  | Descrizione                  | Lunghezza                                    |
| ---------------- | ---------------------------- | -------------------------------------------- |
| **Set Index**    | Seleziona un set             | $\log_2(\text{set number})$ bit              |
| **Block Offset** | Seleziona un byte nel blocco | $\log_{2}(\text{block lenght in bytes})$ bit |

# Tipi di cache miss

- *Cold Start*: si verifica quando un blocco viene richiesto per la prima volta e non è mai stato caricato nella cache.
- *Capacity miss*: si verifica quando la cache non è abbastanza grande per contenere tutti i dati necessari, quindi un dato che era presente in precedenza è stato cancellato.
- *Conflict miss*: si verifica quando più blocchi di memoria competono nella stessa posizione nella cache, causando la rimozione prematura di dati ancora utili.

> N.B.: Anche se i **set index** e il **block offset** di due blocchi combaciano, bisogna controllare se tutti i tag visti finora sul set index siano gli stessi, in caso contrario non è una hit ma una **conflict miss**.

Esempio:

| block number  | 0          | 16         | 0                                                                      | 0   |
| ------------- | ---------- | ---------- | ---------------------------------------------------------------------- | --- |
| **index**     | 0          | 0          | 0                                                                      | 0   |
| **tag**       | 0          | 2          | 0                                                                      | 0   |
| **hit/miss**  | miss       | miss       | miss (non hit, perché<br>gli indici sono `0, 2, 0`<br>e non `0, 0, 0`) | hit |
| **miss type** | cold start | cold start | conflict                                                               |     |

# Inserimento di un dato nella cache in base all'indirizzo RAM

*Sia $B$ la grandezza del blocco in **byte***.

- **Numero di blocco** (Block#) = $\left\lfloor\frac{\text{indirizzo}}{B}\right\rfloor$ è il blocco a cui appartiene l'indirizzo.
- **Set index** = $\text{Block\#} \mod \text{numero di set}$
- **Tag del blocco** = $\left\lfloor\frac{\text{Block\#}}{\text{numero di set}}\right\rfloor$
- **Word offset** = $\left\lfloor\frac{\text{indirizzo}\mod B}{\text{word size}}\right\rfloor$ indica quale word (tra le word del blocco) è quella desiderata.

Altre formule utili:

- **Istruzioni svolte nel tempo medio** $T$ = $\frac{T}{\text{CPI}}\cdot \text{GHz}$
- per memoria  virtuale:
	- **Numero di pagina virtuale** = $\left\lfloor\frac{\text{indirizzo virtuale}}{\text{dimensione pagina in byte}}\right\rfloor$
	- **Page offset** = $\text{indirizzo virtuale} \mod \text{dimensione pagina in byte}$
	- **Indirizzo fisico** = $\text{pagina\#}\cdot \text{dimensione pagina in byte} + \text{page offset}$

# Tipi di cache

## Direct mapped

Ogni blocco della cache è contenuto in un set a sé stante, ha una struttura a "elenco".

## N-ways set associative cache

Per ridurre il numero di conflitti di memoria, lo spazio di memoria è diviso in *set*.
Ogni set è diviso in varie *linee* (o *ways*) che contengono ognuna un blocco della cache. Ha una struttura a "matrice".

> N.B.: Aumentare l'*associatività* vuol dire aumentare il numero di ways per set.

| Più associatività (es. 8-way)               | Meno associatività (es. 1-way) |
| ------------------------------------------- | ------------------------------ |
| ✅ Meno conflitti (cache conflict misses)    | ❌ Più conflitti                |
| ❌ *Numero di ways* confronti di tag per set | ✅ 1 confronto di tag per set   |
| ❌ Più consumo di energia e area             | ✅ Più efficiente in hardware   |

> N.B.: Non esiste il campo "way index" del blocco perché un blocco di memoria può essere solo in un set specifico, ma può trovarsi in una qualunque delle N vie di quel set. Quindi **non basta l'indirizzo per trovare esattamente il blocco**: bisogna **cercarlo (confrontare i tag) in tutte le N vie del set**.

## Fully associative cache

> È una [[cache]] con un solo set e N vie, è l'estremo della cache associativa. In questa cache i blocchi possono essere messi ovunque, come se fosse un insieme.