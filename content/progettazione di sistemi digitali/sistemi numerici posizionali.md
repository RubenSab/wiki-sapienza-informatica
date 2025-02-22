---
updated_at: 2025-02-22T12:11:46.964+01:00
---
> I sistemi numerici posizionali hanno una base $b$, un alfabeto di [[rappresentazione o codifica dei numeri naturali|codifica]] $\Sigma = \{ 0, 1, ..., b - 1 \}$ con $n$ simboli con cui formare $b^n$ numeri diverse in un intervallo $[0, b^n-1]$.

- [[sistemi numerici del calcolatore]]

Una possibile notazione compatta per esprimere la base di un numero è $numero (base)$

# come de/codificare i numeri da una base n a una base m
Dividendolo per m e appuntandosi il resto in una colonna a ogni divisione finché si raggiunge l'uno
>**ESEMPIO**: 26(10) = 11010(2)

```
26|0
13|1 (26/base = 13 -> 26/13 non ha resto, scrivo zero)
 6|0 (13/6 ha il resto di 1, scrivo 1)
 3|1
 1|1
```
Leggendo dal basso verso l'alto si legge 11010(b2), cioè 26(b10) in base 2.
Il procedimento è molto più semplice per convertire in una base minore di quella di partenza.

> Osservazione: non si può decodificare un numero non sapendone la base: 312 sarà al minimo di base 4, perché troviamo il simbolo 3, cioè $4-1$ (base-1). Ad esempio supponendo che sia in base 4: $3\cdot4^2 + 1\cdot4^1 +2\cdot4^0 = 54$ (base 10)
