---
updated_at: 2026-10-24T20:15:05.453+02:00
---
I numerali di Church si basano sull'idea di non rappresentare il numero naturale $n$ come elemento di un dominio, ma come *la ripetizione di un qualcosa $n$ volte*.

> Cioè ogni numerale di Church che rappresenta $n$ è la [[funzione]] che data $f$ e una $x$, restituisce la composizione $n$-esima di $f$ applicata a $x$.

- $0 = \text{zero}(f, x)\ \text{tale che}\ \text{zero}(f, x) \rightsquigarrow x$
- $1 \equiv \text{uno}(f, x)\ \text{tale che}\ \text{uno}(f, x) \rightsquigarrow f(x)$
- $2 \equiv \text{due}(f, x)\ \text{tale che}\ \text{due}(f, x) \rightsquigarrow f(f(x))$
- $3 \equiv \text{tre}(f, x)\ \text{tale che}\ \text{tre}(f, x) \rightsquigarrow f(f(f(x)))$
- $\ldots$
- $n \equiv \text{enne}(f, x) \rightsquigarrow f^{\circ n}(x)$

In [[Standard Meta Language (SML)]]:

``` sml
val zero = fn f => fn x => x
val uno = fn f => fn x => f x
val due = fn f => fn x => f (f x)
val tre = fn f => fn x => f (f (f x))
...
```

Ad esempio, se definiamo la funzione incremento

``` sml
val incremento = fn x => x + 1;
```

allora la funzione successore applicata tre volte (`tre incremento`) a 0 farà 3.

``` sml
tre incremento 0; (* valuta a 3*)
```

# Funzioni e operazioni

## Funzione successore

Se $n$ è definito come il ripetere qualcosa ($f$) $n$ volte, allora la funzione successore di $n$ è il ripetere $n$ un'altra volta.

``` sml
val succ = fn numerale => (fn f => fn x => f (numerale f x));
```

Avendo lo zero e alla funzione successore possiamo costruire tutti i numeri naturali:

``` sml
val uno = succ zero;
val due = succ (succ zero);
val tre = succ (succ (succ zero));
...
```

## Funzione eval

La funzione eval (valutazione) prende in input un numerale di Church e restituisce il vero numero naturale corrispondente.

Dato che la funzione successore per i numerali di Church è equivalente alla funzione incremento per i veri numeri naturali, 

Per valutare un numerale di Church possiamo dargli la funzione incremento come $f$, cioè l'azione da ripetere, e dargli $0$ come $x$, cioè la cosa su cui ripetere l'azione. 

``` sml
val eval = fn numerale => numerale incremento 0;
eval zero; (* valuta a 0 *)
eval uno; (* valuta a 1 *)
eval due; (* valuta a 2 *)
```

## Funzione somma

La funzione $\text{piu}(n_{1}, n_{2})$ ripete applica $n_{1}$ volte la funzione successore a $n_{2}$, restituendo $n_{1}+n_{2}$.

``` sml
val piu = fn n1 => fn n2 => n1 succ n2;
val test = eval (piu uno due); (* valuta a 3 *)
```