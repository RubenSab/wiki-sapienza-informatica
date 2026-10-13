---
updated_at: 2026-10-12T12:57:50.227+02:00
---
> Un [[linguaggio]] di programmazione è l'[[insieme]] dei suoi programmi scrivibili in esso, detti suoi **termini**.

> Chiamare un programma *noto* $N$, ad esempio, rende $N$ una **variabile**.

> Chiamare un programma *qualsiasi* $N$, ad esempio, rende $N$ una **meta-variabile**.

# Esempio

Consideriamo i programmi $M, N ::= 5 \mid 7 \mid \ldots \mid M+N \mid N \ast M$ dell'algebra $\text{Exp}$ ($N, M \in \text{Exp}$) che è una grammatica generativa. Ciò vuol dire che ad esempio $5$ è un programma e anche $5 + 7$ e $5 + 7 \ast 5$ lo sono.

![[Pasted image 20261005124809.png]]

Il problema della definizione di $\text{eval}$ è che sto applicando una definizione per clausole, che è una definizione [[induzione|induttiva]] su un'[[algebra eterogenea|algebra]] che non è induttiva, perché i *costruttori* $+$ e $\ast$ non hanno *immagini disgiunte*.

> La grammatica così ottenuta si dice **ambigua**.

> Però basta dichiarare che quella sintassi è la **sintassi astratta** di $\text{Exp}$. Nel concreto, se al posto di scrivere $5 \ast 7 + 9$, che è ambiguo, si scrive $\ast(5,\ +(7, 9))$ o $+(*(5, 7),\ 9)$ e si dichiarano come diversi (***la diversità sta nel programma, non nel risultato***), allora le immagini di $+$ e $\ast$ si disgiungono e si è risolve l'ambiguità.

# Altro esempio, il linguaggio "EXP"

$$
M, N ::= \underset{\text{costante}}{\underbrace{\mathcal{k}}} \mid \underset{\text{variabile}}{\underbrace{x}} \mid N+M \mid \text{let}\ x = M\ \text{in}\ N
$$

$$
\begin{cases}
E \vdash k \to k \\
E \vdash x \to v\ (\text{se}\ E(x)=v) \\
\frac{E \vdash M \to v_{1}\quad E \to N \to v_{2}}{E \vdash M + N \to v}\ (\text{se}\ v_{1} + v_{2} = v) \\
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