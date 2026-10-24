---
updated_at: 2026-10-24T18:51:31.143+02:00
---
> SML è un linguaggio funzionale con [[scoping statico]] e [[valutazione eager]].

# Binding di variabili a valori nelle [[espressione|espressioni]]

`val variabile = valore` crea il binding variabile $\to$ valore nello [[scoping|scope]] locale.

Lo scope può essere quello di un'espressione. In tal caso si usa:

- `let` per definire lo scope,
	- in esso seguono uno o più `val`,
- poi `in` (per "collegare" l'espressione all'ambiente),
- l'espressione,
- e infine `end`.

Le variabili $x$ e $y$ non sono visibili fuori dall'espressione e dai bindings.

Ad esempio:

``` sml
let
  val x = 1
  val y = 2
in
  x + y
end;
(* valuta a 3 (int) *)
```

> N.B.: la funzione ha valutato a un'intero perché il + è [[overloading|overloaded]] e ha un comportamento definito sia se `x` e `y` sono interi, sia se sono reali.

``` sml
let
  val x = 1.0
  val y = 2.0
in
  x + y
end;
(* valuta a 3.0 (real) *)
```

Però con int e real o viceversa non funziona:

``` sml
let
  val x = 1.0
  val y = 2
in
  x + y
end;

(*
Elaboration failed: Type clash. Functions of type "int * int → int" cannot take an argument of type "real * int": Cannot merge "real" and "int".
*)
```

Altro esempio:

``` sml
let
  val a = 2
  val b = a * a
in
  b + 1
end;
(* valuta a 5 (int) *)
```

# Funzioni

## Dichiarazione di [[funzione|funzioni]]

Abbiamo visto solo quelle unarie dichiarate con `fun`, ma le funzioni n-arie si possono ricavare per [[curryficazione]].

``` sml
fun square x = x * x;
```

*Questa espressione vale `fn: int -> int`, cioè la funzione il cui dominio sono gli interi e il codominio anche*.

> N.B.: La funzione `square` è è definita per tutti i tipi per cui è definito `*`.

## Funzioni lambda

`fn` crea una funzione senza chiamarla.

``` sml
val succ = fn x => x + 1;
```

`fun nome x = ...`  quindi è solo zucchero sintattico per `val nome = fn x => ...`.

# [[polimorfismo dei tipi|Polimorfismo dei tipi]]

>  La funzione `fun id x = x` o equivalentemente la lambda `fn x => x` sono definite per tutti i tipi. Valutano a `∀ 'a . 'a → 'a`.

# Unit

#todo