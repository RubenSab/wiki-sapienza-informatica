---
updated_at: 2026-10-24T18:58:03.155+02:00
---
> I [[algebra di Boole|booleani]] di Church si basano sull'idea di non rappresentare il vero e il falso come elementi di un dominio, ma come *scelte*. Avendo due cose (due parametri passati a una [[funzione]]), il vero è la scelta della prima cosa e il falso è la scelta della seconda. Quindi vero e falso possono essere scritti come funzioni.

- $\text{True}(x, y) = x$
- $\text{False}(x, y) = y$

In [[Standard Meta Language (SML)]] ottenuta per [[curryficazione]]:

```
val True = fn x => fn y => x;
val False = fn x => fn y => y;
```

Esempio di applicazione:

``` sml
True "primo" "secondo"; (* valuta a "primo" *)
False "primo" "secondo"; (* valuta a "secondo" *)
```

# Operazioni

## Not

Se un booleano è una funzione che sceglie tra due cose, il not di un booleano è la funzione che sceglie la cosa opposta rispetto al booleano:

Intuizione:

$$
\text{not}(\text{boolean}(x, y)) = \text{boolean}(y, x)
$$

``` sml
val not = fn boolean => fn x => fn y => boolean y x;

not True "x" "y"; (* valuta a "y" *)
not False "x" "y"; (* valuta a "x" *)
```

## And

Intuizione: se x è falso, allora ritorna x; se x è vero allora il risultato dipende solo da y

``` sml
val b_and = fn x => fn y => x y x
```

## Or

Intuizione: se x è falso, allora il risultato dipende solo da y; se x è vero, allora ritorna x

``` sml
val b_and = fn x => fn y => x x y
```

## If then else

L'if then else di un booleano è la cosa che sceglie la stessa cosa che sceglie il booleano.

``` sml
fun ite = fn boolean => boolean;
(* equivalentemente *) fun ite boolean = boolean;

val condition = True;
ite condition "x" "y"; (* valuta a "x" *)
```

L'if then else è la funzione di identità dei booleani di Church. Quindi i booleani di Church *sono* l'if then else.

# Se applichiamo una funzione definita sui booleani di Church a un booleano di Church, la funzione ci da un booleano vero?

Si. #dadimostrare 
