---
updated_at: 2025-05-30T09:55:34.239+02:00
---
Quando si ha un salto condizionato, il meccanismo di pipeline assume che la prossima istruzione sia da prendere all'indirizzo [[PC (Program Counter)]]+4 quindi già la carica, ma se la condizione di branch si verifica allora si dovrà **scartarla** e prendere quella indicata dalla destinazione del salto.

> N.B.: l'implementazione di `beq` che studiamo in questo corso funziona così ed è detta soluzione HW (HardWare) perché serve modificare i componenti della pipeline per implementarla.

Oppure un'altra soluzione è caricare l'istruzione solo **dopo che il salto è stato già deciso**, inserendo degli stalli.

- Se il salto è deciso in **EXE**, cioè determinato dalla [[ALU]], allora sono necessari **2 stalli**.
- Se il salto è deciso in **ID**, cioè preso direttamente dall'istruzione o da un'*unità di comparazione* aggiuntiva (fatta apposta solo per questo lavoro) che si attiva durante la fase ID, allora è necessario **1 stallo**.

Esempio con salto determinato in EXE dalla ALU (2 stalli):

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

Esempio con salto determinato in ID (1 stallo):

```
Cicli:           1  2  3  4  5  6  7  8  9    
-------------------------------------------
add x4, x5, x6 | IF ID EX MM WB
beq x1, x0, 40 |    IF ID EX MM WB
[stallo]       |       -  -  -  -  -
or x7, x8, x9  |          IF ID EX MM WB

Avvenuta la fase ID di beq nel ciclo 3, nel ciclo 4 si potrà decidere se eseguire o meno or (in questo caso si assume che la condizione di salto non si verifica e or viene eseguita).
```

## Tutti i modi per mitigare i control hazard

- Caricando la prossima istruzione e eventualmente **scartarla** (soluzione HW):
	- Se il salto avviene ed è deciso dall'ALU nella fase EX bisognerà scartare 2 istruzioni già caricate.
	- Se il salto avviene ed è deciso dalla [[CU (Control Unit)]] nella fase ID bisognerà scartare un'istruzione.

- **Ritardando** il fetch dell'istruzione dopo il salto inserendo degli stalli.
- Con la ***Branch Prediction***, dove la CPU osserva la frequenza con cui un determinato salto avviene o meno e pre-carica l'istruzione eseguita più spesso (l'istruzione seguente o quella alla destinazione del salto). Se la predizione è sbagliata, la CPU lo scopre alcune fasi dopo, tipicamente nella fase EX, dove l’ALU calcola effettivamente l’indirizzo del salto o valuta la condizione: la CPU deve svuotare la pipeline (**flush**) per eliminare tutte le istruzioni sbagliate, poi riprendere l'esecuzione dall'indirizzo corretto del salto.  Ciò introduce un **ritardo di tanti cicli quante sono le istruzioni sbagliate nella pipeline**.

#todo cose del pdf 17.