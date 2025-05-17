---
updated_at: 2025-05-17T18:36:57.731+02:00
---
> Gli hazard sono delle criticità introdotte dalla sovrapposizione delle [[fasi dell'esecuzione di un'istruzione]] nell'[[architettura RISC-V con pipeline]].

# Tipi di hazard

- *Data hazard*: il dato necessario a cui si accede non è ancora stato calcolato.
- *Control hazard*: la presenza di un branch cambia il flusso di esecuzione delle istruzioni, l'istruzione successiva già caricata può dovere essere scartata.
- *Structural hazard*: dove le risorse hardware non sono sufficienti (esempio: se la memoria dati e la memoria istruzioni è la stessa si può verificare una *IF/MEM collision*, ma ciò è risolto in fase di design).

## Data hazard

Esempio:

```
add s0, t0, t1   IF  ID  EX   MM  [WB]
sub t2, s0, t3       IF [ID]  EX   MM  WB
```

Questa [[architettura RISC-V con pipeline|pipeline]] è impossibile (per ora) perché a ID di `sub` serve il dato scritto nei [[registri]] da WB di `add`, quindi bisogna "traslare" le fasi di esecuzione di `sub` di altri due cicli, non 3 perché **WB viene sempre eseguita nella prima metà del ciclo di clock, mentre ID (e anche IF) viene sempre eseguita nella seconda metà del ciclo di clock, quindi sono sovrapponibili**.

```
add s0, t0, t1   IF  ID  EX  MM  [WB]
sub t2, s0, t3       ->  ->  IF  [ID]  EX  MM  WB
```

Come si fa a "traslare" le fasi dell'esecuzione di un'istruzione? aggiungendo fasi di stallo.

```
add s0, t0, t1   IF   ID   EX   MM  [WB]
[stallo]              -    -    -    -    -
[stallo]                   -    -    -    -    -
sub t2, s0, t3                  IF  [ID]  EX   MM  WB
```

Questa è una possibile soluzione per risolvere il data hazard, ma una migliore usa il [[forwarding]]. Eventualmente si può anche usare il [[riordinamento delle istruzioni]].

## Control hazard

Quando si ha un salto condizionato, il meccanismo di pipeline assume che la prossima istruzione sia da prendere all'indirizzo [[PC (Program Counter)]]+4 quindi già la carica, ma se la condizione di branch si verifica allora si dovrà **scartarla** e prendere quella indicata dalla destinazione del salto.

> N.B.: l'implementazione di `beq` che studiamo in questo corso funziona così ed è detta soluzione HW (HardWare) perché serve modificare i componenti della pipeline per implementarla.

Oppure un'altra soluzione è caricare l'istruzione solo **dopo che il salto è stato già deciso**, inserendo degli stalli.

- Se il salto è deciso in EXE (salto condizionato, la cui condizione è determinata dalla [[ALU]]), allora sono necessari **2 stalli**.
- Se il salto è deciso in ID (salto incondizionato, la cui destinazione è presa direttamente dall'istruzione), allora è necessario **1 stallo**.

Esempio con salto condizionato (2 stalli):

```
Cicli:           1  2  3  4  5  6  7  8  9    
-------------------------------------------
add x4, x5, x6 | IF ID EX MM WB
beq x1, x0, 40 |    IF ID EX MM WB
[stallo]       |       -  -  -  -  -
[stallo]       |          -  -  -  -  -
or x7, x8, x9  |             IF ID EX MM WB

Avvenuta la fase EX di beq nel ciclo 4, nel ciclo 5 si potrà decidere se eseguire o meno or (in questo caso si assume che la condizione di salto non si verifica e or viene eseguita).
```

Esempio con salto incondizionato (1 stallo):

```
Cicli:           1  2  3  4  5  6  7  8  9    
-------------------------------------------
add x4, x5, x6 | IF ID EX MM WB
j 40           |    IF ID EX MM WB
[stallo]       |       -  -  -  -  -
or x7, x8, x9  |          IF ID EX MM WB

in questo caso si assume che or sia l'istruzione all'indice 40.
```

## Tutti i modi per mitigare i control hazard

- Caricando la prossima istruzione e eventualmente scartarla (soluzione HW):
	- Se il salto avviene ed è deciso dall'ALU nella fase EX bisognerà scartare 2 istruzioni già caricate.
	- Se il salto avviene ed è deciso dalla [[CU (Control Unit)]] nella fase ID bisognerà scartare un'istruzione

- Ritardando il fetch dell'istruzione dopo il salto inserendo degli stalli.
- Con la *Branch Prediction*, dove la CPU osserva la frequenza con cui un determinato salto avviene o meno e pre-carica l'istruzione eseguita più spesso (l'istruzione seguente o quella alla destinazione del salto). Se la predizione è sbagliata, la CPU lo scopre alcune fasi dopo, tipicamente nella fase EX, dove l’ALU calcola effettivamente l’indirizzo del salto o valuta la condizione: la CPU deve svuotare la pipeline (flush) per eliminare tutte le istruzioni sbagliate, poi riprendere l'esecuzione dall'indirizzo corretto del salto.  Ciò introduce un ritardo di tanti cicli quante sono le istruzioni sbagliate nella pipeline. 