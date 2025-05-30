---
updated_at: 2025-05-30T09:53:28.471+02:00
---
> A volte, l'informazione necessaria per una fase di esecuzione di un'[[assembly RISC-V|istruzione]] è già presente nella [[architettura RISC-V con pipeline|pipeline]] prima del Write Back. In questi casi si usa il *forwarding* (detto anche *propagazione* o *bypassing*), cioè l'inserimento di **scorciatoie** nel datapath, ovvero dei cavi che danno il dato all'unità funzionale che ne ha bisogno senza aspettare la fase di Write Back.

Esempio:

```
add s0, t0, t1   IF  ID  EX  MEM  [WB]
[stallo]             -   -   -    -     -
[stallo]                 -   -    -     -   -
sub t2, s0, t3               IF   [ID]  EX  MEM  WB
```

Al posto di risolvere così il data [[hazard]], aspettando 2 colpi di clock, possiamo usare le unità di forwarding per portare il risultato di EX di `add` come uno dei due input di EX di `sub`, saltando ID per quel dato (visto che non è ancora stato scritto in memoria con il WB).

```
add s0, t0, t1   IF >| ID >| EX >| MEM >| WB >|
                                 |
                                 v
sub t2, s0, t3         IF >| ID >| EX  >| MEM>| WB >|
```

> Non è sempre possibile risolvere un data hazard **direttamente** con il forwarding, ma a volte è necessario inserire uno **stallo** (detto anche attesa o *bubble*).

Esempio:

```
lw x1, 0(x2)   IF >| ID >| EX >| MEM>| WB >|
                                     |
[stallo]             -     -     -   v -      -    
sub x4, x1, x5             IF >| ID >| EX  >| MEM>| WB >|
```

#todo aggiungere cose aggiuntive del pdf. 15