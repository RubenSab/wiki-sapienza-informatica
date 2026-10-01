---
updated_at: 2026-10-01T11:06:01.817+02:00
---
# Definizioni
## Omomorfismo di algebre

![[Pasted image 20261001101718.png]]

> N.B.: $f$ è una [[funzione]] unaria e $b$ è binaria.

> $h$ si dice **[[omomorfismo]] di algebre** è un mapping che "rispetta le operazioni", cioè (seguendo questo esempio) succede che $h(f_{A}(x)) = f_{B}(h(x))$, o equivalentemente $h(g_{A}(x, y)) = g_{B}(h(x), h(y))$.

## Isomorfismo di algebre

![[Pasted image 20261001101235.png]]

> Un [[isomorfismo]] di algebre è un omomorfismo bidirezionale.

# Teoremi

**Teorema**: $A$ è induttiva e $B$ hanno la stessa segnatura di $A$ $\implies \exists !\ f: A \to B$.

**Lemma** (è più importante del suo teorema sopra): $A, B$ sono induttive e hanno la stessa segnatura $\implies A, B$ sono isomorfe.

Il lemma di Lamback si può usare per dimostrare che due algebre sono isomorfe in modo elegante:

- Assumiamo che le algebre induttive $A$ e $B$ hanno un omomorfismo $h_{1}:\ A \to B$ e $h_{2}:\ B \to A$.
- La funzione di identità $\text{Id}(X)$ sull'algebra $X$ crea banalmente un isomorfismo $X \leftrightarrow X$.
- Si può combinare tutto in una sola funzione, la quale è un omomorfismo (si capisce seguendo le linee del disegno). Inoltre, dato che l'identità è l'unico omomorfismo tra un'algebra a se stessa, allora questa combinazione di funzioni è unica, quindi l'omomorfismo trovato è unico.

![[Pasted image 20261001105356.png]]

---

Non riguarda strettamente i morfismi tra algebre, ma questi diagrammi sono utili per dimostrare proposizioni come:

![[Pasted image 20261001110530.png]]

dove $(L, +_{\text{append}})$ è l'algebra delle liste.