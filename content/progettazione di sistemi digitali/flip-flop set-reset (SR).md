> è un [[AND gate con funzione di controllo|gated]] [[latch set-reset (SR)]] che ha come ingressi S, R e un clock (un segnale che oscilla tra 0 e 1 a intervalli costanti) che rende abilita le porte NOR.

![[flip-flop SR.svg]]
# tavola di verità

| $s$ | $r$ | $Y$ (stato futuro)                    |
| --- | --- | ------------------------------------- |
| 0   | 0   | $y$ (stato corrente) (memorizzazione) |
| 0   | 1   | 0 (reset)                             |
| 1   | 0   | 1 (set)                               |
| 1   | 1   | configurazione proibita               
Astrazione a *blackbox* del flip-flop SR:

```
      ________________
s ->  | s       y    | -> y
      |              |
CK -> |>             |
	  |              |
r ->  | r   not y (z)| -> z
      |______________|
```

# tabella inversa

| $y, Y$ | $s, r$                                                                |
| ------ | --------------------------------------------------------------------- |
| 00     | 0 $\delta$ (se si passa da 0 a 0 o si memorizza 0 o si resetta)       |
| 01     | 10 (funzione di set)                                                  |
| 10     | 01 (funzione di reset)                                                |
| 11     | $\delta$ 0 (se si passa da 1 a 1 o si memorizza 1 o non si fa niente) |
