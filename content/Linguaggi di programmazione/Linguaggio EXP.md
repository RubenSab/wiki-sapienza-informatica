---
updated_at: 2026-10-26T12:38:06.633+01:00
---
#todo 

$$
M, N ::= \underset{\text{costante}}{\underbrace{\mathcal{k}}} \mid \underset{\text{variabile}}{\underbrace{x}} \mid N+M \mid \text{let}\ x = M\ \text{in}\ N
$$

$$
\begin{cases}
E \vdash k \to k \\
E \vdash x \to v\ (\text{se}\ E(x)=v) \\
\frac{E \vdash M \to v_{1}\quad E \vdash N \to v_{2}}{E \vdash M + N \to v}\ (\text{se}\ v_{1} + v_{2} = v) \\
\frac{E \vdash M \to v\quad E(x, v) \vdash N \to v'}{E \vdash \text{let} x = M\  \text{in}\ N \to v'}
\end{cases}
$$

## Eager

`let x = A in 3` valuto sempre $A$ anche se so che viene 3.

## Lazy

$$
\text{Env} \ni E:\ \text{Var} \overset{\text{fin}}{\to}\text{Val} \cup \text{Exp}
$$

Come cambia la definizione di ambiente in lazy o eager? in eager le variabili hanno un valore associato, mentre in lazy possono avere associate anche espressioni non ancora valutate.

### Lazy dinamico

```
   (x,5)(y,x)(x,9) ⊢ 9 → 9          (x,5)(y,x)(x,9) ⊢ x → 9
   ───────────────────────          ───────────────────────
   (x,5)(y,x)(x,9) ⊢ y → 5          (x,5)(y,x)(x,9) ⊢ 1 → 1
   ─────────────────────────────────────────────────────────
    (x,5)(y,x)(x,9) ⊢ y + 1 →
   ─────────────────────────────────────────────────────────
    (x,5)(y,x) ⊢ let x = 9 in y + 1 →
   ─────────────────────────────────────────────────────────
    (x,5) ⊢ let y = x in let x = 9 in y + 1 →
   ─────────────────────────────────────────────────────────
    ∅ ⊢ let x = 5 in let y = x in let y = x in let x = 9 in y + 1 →
```

### Lazy statico

Statico: risoluzione variabili tempo di compilazione
Dinamico: avviene a tempo di esecuzione

Portarsi un ambiente appresso corrisponde a far comportare uno scoping dinamico come statico.

$$
\frac{E(x, M) \vdash N \to v}{E \vdash \text{let}\ x = M\ \text{in}\ N \to v} \quad (\text{se}\ E(x) = M)
$$

```
E(x (M, E)) ⊢ N → v
──────────────────────
E ⊢ let x = M in N → V
```

Gli ambienti devono portare dentro altri ambienti.

```
   x 5 ∅ ⊢ x → 5
   ─────────────────────────────────────────────────────────
   E(x 9 E) ⊢ y →                           E(x 9 E) ⊢ 1 → 1
   ─────────────────────────────────────────────────────────
   
   E(x 9 E) ⊢ y + 1 →
   ─────────────────────────────────────────────────────────
           E
   (x 5 ∅)(y x (x 5 ∅)) ⊢ let x = 9 in y + 1 →
   ─────────────────────────────────────────────────────────
   (x 5 ∅) ⊢ let y = x in let y = x in let x = 9 in y + 1 →
   ─────────────────────────────────────────────────────────
   ∅ ⊢ let x = 5 in let y = x in let y = x in let x = 9 in y + 1 →
```

(fa 6)

lazy statico = eager (vale solo in Exp)

---


#todo impagina

```
let x = 3 in 2
let x = 2 in 3
let x = 3+1 in x+9
let y = 5 in let x= 3+y in x+y
```

- `let x = 3 in x+1` non è ambiguo perché il + è associativo.
- `let x = 3 in let x = 2 in x+x` è ambiguo, perchè non si sa se intendiamo `let x = 3 in (let x = 2 in x)+x` o `let x = 3 in let x = 2 in (x+x)`.
- `let x = (let x = x in x) in 3`
	- da errori se lo scoping è statico.
	- va bene nello scoping dinamico, ma va in loop infinito, quindi va bene, ma:
		- se la valutazione è lazy, da 3.
		- se la valutazione è eager, va in loop.

---

# Esercizio

Scoping statico e valutazione eager.

```
let x = (let y = M in N) in L
let y = M in (let x = N in L)
sono logicamente equivalenti?
```

L sta nello scope di y, quindi se nell'espressione di L c'è y o è associato a qualcosa nell'envirnment di x o porta due definizioni contraddittorie.

#todo aggiungi teorema Free

---

- eager
- lazy ingenua (la lazyness tirava fuori un comportamento dinamico)
- lazy statica (recuperiamo il comportamento operazionale della semantica eager)

è possibile dimostrare che lazy statica = eager (dimostrazione sulle note) nel caso in cui c'è un linguaggio semplice.


# Esempi di valutazione

- `let x = 3 in x+1` $\to$ Non è ambiguo poiché l'operatore $+$ è associativo e la struttura sintattica standard lega il `let` verso destra.
- `let x = 3 in let x = 2 in x+x` $\to$ **Ambiguo**, poiché la precedenza strutturale non specifica se debba essere inteso come:
- `let x = 3 in (let x = 2 in x) + x`
- `let x = 3 in (let x = 2 in (x + x))`
- `let x = (let x = x in x) in 3`
	- **Scoping Statico:** Genera un errore (la variabile $x$ interna non è definita o vi è unuso non valido).
	- **Scoping Dinamico:** Sintatticamente viene accettato, ma durante la valutazione va in **loop infinito** (cattura ricorsivamente se stessa).
    - Con valutazione **Lazy**: Restituisce `3`, perché l'espressione interna legata a $x$ non viene mai valutata (essendo il corpo del `let` principale semplicemente la costante `3`).
    - Con valutazione **Eager**: Tenta di valutare subito l'argomento del `let` esterno, entrando in un **loop infinito**.
    - Confronto tra `let x = (let y = M in N) in L` e `let y = M in (let x = N in L)`. **Sono logicamente equivalenti?** Non sempre in modo generale. $L$ si trova nello scope di $y$ nella seconda forma, mentre nella prima $y$ è confinato all'interno di $N$ e non è visibile in $L$ (a meno che $L$ non contenga a sua volta legami o conflitti). Se $L$ utilizza la variabile $y$, la prima forma fallisce o fa riferimento a un $y$ esterno (libero), mentre la seconda lega correttamente $y$ tramite il `let` più esterno. Dunque, i due termini non sono equivalenti a meno che $L$ non contenga variabili libere $y$ dipendenti da quel legame.