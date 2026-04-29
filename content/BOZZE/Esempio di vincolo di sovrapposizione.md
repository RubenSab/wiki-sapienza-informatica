---
updated_at: 2026-04-20T15:45:20.853+02:00
---
```
[V.Veicolo.no_riparazioni_in_contemporanea]
// lo stesso veicolo non può essere oggetto di due riparazioni distinte che si sovrappongono nel tempo

Per ogni v: Veicolo, r1: Riparazione, r2: Ripatazione e r1 != r2, se esistono i link (v, r1): riguarda e (v, r2): riguarda
allora
non esiste t: DataOra tale che r1.accettazione <= t <= r1.riconsegna e r2.accettazione <= t <= r2.riconsegna
```

```
non_sovrapposti(i1: DataOra, f1: DataOra, i2: DataOra, f2: DataOra): Booleano

pre: i1 <= f1 AND i2 <= f2

post:
result = True se e solo se non esiste t: DataOra tale che i1 <= t <= f2 and i2 <= t <= f2
```

