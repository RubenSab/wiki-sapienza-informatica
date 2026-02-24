> è un tipo di flip-flop che cambia stato a ogni impulso di clock quando l'ingresso $T$ (toggle) è 1.

# Funzionamento

| $T$ | $y(t+1)$          |
| --- | ----------------- |
| 0   | $y(t)$            |
| 1   | $\overline{y(t)}$ |
## Tabella di verità

| $y$ | $T$ | $y(t+1)$ |
| --- | --- | -------- |
| 0   | 0   | 0        |
| 0   | 1   | 1        |
| 1   | 0   | 1        |
| 1   | 1   | 0        |

## Espressione booleana
$y(t+1) = T \oplus y(t)$

# realizzazione

È spesso realizzato modificando un [[flip-flop (JK)]] con $J = K = T$.  

```
      ____________
t ----| J      y |-->
   |  |>         |
   |__| k  not y |-->
      |__________|
```

Anche indicato come:

```
      ____________
t ----| T      y |-->
      |>         |
      |    not y |-->
      |__________|
```
# tabella inversa

| $t$ | $y(t+1)$          |
| --- | ----------------- |
| 0   | $y(t)$            |
| 1   | $\overline{y(t)}$ |
