---
updated_at: 2025-06-04T17:31:18.381+02:00
---
> N.B. I "data hazard" che coinvolgono la scrittura o lettura del [[registri generali dell'architettura RISC-V|registro generale]] `x0` non sono veri data hazard perché `x0` è read-only e immutabile, il suo valore è sempre 0.

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