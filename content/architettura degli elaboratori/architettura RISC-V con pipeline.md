---
updated_at: 2025-05-14T12:21:22.157+02:00
---
> Si può ottimizzare l'[[architettura RISC-V a singolo colpo di clock e senza pipeline]] in quanto in ogni [[fasi dell'esecuzione di un'istruzione|fase dell'esecuzione delle istruzioni]] la [[CPU]] è inutilizzata per l'80%, perché le unità funzionali si attivano una alla volta. L'idea è di far eseguire contemporaneamente fasi diverse di più istruzioni (max 5) in modo che più unità funzionali possibili siano occupate in un determinato momento.

| istruzioni |     |     |     |     |     |     |     |     |     |
| ---------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1          | IF  | ID  | EXE | MEM | WB  |     |     |     |     |
| 2          |     | IF  | ID  | EXE | MEM | WB  |     |     |     |
| 3          |     |     | IF  | ID  | EXE | MEM | WB  |     |     |
| 4          |     |     |     | IF  | ID  | EXE | MEM | WB  |     |
| 5          |     |     |     |     | IF  | ID  | EXE | MEM | WB  |
La fase *Instruction Fetch* si può sovrapporre alla fase *Instruction Decode*, cioè possiamo calcolare il prossimo valore del PC (+=4) senza sapere di che tipo è la prossima istruzione, perché in **[[RISC-V]] tutte le istruzioni hanno la stessa lunghezza**.

> Questa sovrapposizione delle fasi può introdurre delle criticità, dette [[hazard]].

Il calcolo del periodo di clock cambia, non bisogna più vedere la durata totale dell'**istruzione** più lenta, ma quella della **singola fase** più lenta.

Senza pipeline: periodo di clock di **800 ps** in base alla durata totale dell'istruzione più lenta.

> Per valutare l'efficienza della pipeline bisogna introdurre il ***throughput***, cioè il numero di istruzioni per fase.

![[Pasted image 20250513185631.png]]


| istruzione | IF  | ID  | EXE | MEM | WB  | totale |
| ---------- | --- | --- | --- | --- | --- | ------ |
| `lw`       | 200 | 100 | 200 | 200 | 100 | 800    |
| `sw`       | 200 | 100 | 200 | 200 |     | 700    |
| Tipo R     | 200 | 100 | 200 |     | 100 | 600    |
| `beq`      | 200 | 100 | 200 |     |     | 500    |

Con pipeline: periodo di clock di **200 ps** in base alla durata della fase più lenta (IF e MEM).

Il periodo di clock è il 25% di quello dell'architettura non ottimizzata.

