> Memorizza un bit di informazione sincronizzato con un segnale di clock.
> Quando il clock è basso, lo stato rimane invariato. Quando arriva un fronte attivo, lo stato assume il valore di D.
 
Risolve il problema degli stati proibiti del [[flip-flop set-reset (SR)]] impedendo che $S$ e $R$ siano uguali a 1 contemporaneamente.

## **Tabella di verità**

| $D$ | $Y$ |
| --- | --- |
| 0   | 0   |
| 1   | 1   |

# tabella inversa
| $y, Y$ | $d$ |
| ------ | --- |
| 00     | 0   |
| 01     | 1   |
| 10     | 0   |
| 11     | 1   |
# realizzazione

È spesso realizzato modificando un flip-flop SR con $D = S;\ R = \overline{S}$.

```
         ____________
d -------| s      y |-->
   |     |>         |
   |-not-| r  not y |-->
         |__________|
```

Anche indicato come:

```
      ____________
d ----| d      y |-->
      |          |
      |>  not y  |-->
      |__________|
```

# tabella inversa

| $D$ | $Y$ |
| --- | --- |
| 0   | 0   |
| 1   | 1   |
