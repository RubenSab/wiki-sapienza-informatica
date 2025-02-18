> è il tipo di latch più semplice, costruito a partire da due porte NOR.

![[latch.svg]]

Lo stato del [[flip-flop]] è determinato dall'uscita superiore (y).
Il flip-flop si può pensare come un meccanismo bi-stabile che può trovarsi solo negli stati 0 e 1.  

# tavola di verità

| $s$ | $r$ | $Y$ (stato futuro)                    |
| --- | --- | ------------------------------------- |
| 0   | 0   | $y$ (stato corrente) (memorizzazione) |
| 0   | 1   | 0 (reset)                             |
| 1   | 0   | 1 (set)                               |
| 1   | 1   | configurazione proibita               |

Astrazione a *blackbox* del latch:

```
     ________________
s -> | s       y    | -> y
     |              |
r -> | r   not y (z)| -> z
     |______________|
```

$$y_{\text{ nuova}}=\overline{r+z}=\overline{r+\overline{s+y_{\text{ vecchia}}}}=\overline{r}\bullet(s+y_{\text{ vecchia}})$$

>N.B.: Il tempo $\Delta t$ tra la $y$ nuova e quella vecchia non è indifferente: dipende dal tempo di attraversamento del segnale fra porte NOR.

- [[analisi del latch]]