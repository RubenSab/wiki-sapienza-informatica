---
updated_at: 2025-10-26T19:05:21.401+01:00
---
> Ogni numero naturale maggiore di 1 o è un numero [[primalità|primo]] oppure si può esprimere come un prodotto **unico** di numeri naturali.

> $\forall a \in \mathbb{N}^{\star}$, l'insieme $I_{a} = \{p \in \mathbb{N} : p\ \text{è primo con}\ p \mid a\}$ (cioè la scomposizione in primi di $a$) è un insieme finito e inoltre

$$
a = \prod_{p\ \text{primo}} p^{v_{p}(a)}
$$

dove l'[[applicazione]] $p \in \mathbb{P} \mapsto v_{p}(a) \in \mathbb{N}$, con $a$ fissato, è l'applicazione che conta quante volte $p$ divide $a$.

Essa **quasi ovunque nulla** perché $\{p \in \mathbb{P}: v_{p}(a) > 0\}$ (insieme dei fattori primi di $a$) è finito.

Esempio: $a = 12$

$a = 18 = 3^{2} \cdot 2^{1}$

- $v_{2}(12) = 1$
- $v_{3}(12) = 2$
- $v_{5}(12) = 0$
- $v_{7}(12) = 0$
- $v_{11}(12) = 0$
- $\ldots$

$$
18 = \prod_{p\ \text{primo}} p^{v_{p}(18)} = 2^{1} \cdot 3^{2} \cdot 5^{0} \cdot 7^{0} \cdot 11^{0} \cdot \ldots
$$

Come può un prodotto essere ben definito se ha infiniti fattori? perché l'insieme $\{p \in \mathbb{P}: v_{p}(a) > 0\}$

> N.B.: È **impossibile** trovare una formula semplice per calcolare $v_{p}(a+b)$ in funzione di $v_{p}(a)$ e $v_{p}(b)$.

> Un *test di primalità* è un [[algoritmo]] (è impossibile trovare una formula chiusa) che riceve in input un numero naturale e determina se esso è primo o meno. Il test di primalità più comune è il [[crivello di Eratostene]].


# Calcolare MCD e mcm con le fattorizzazioni

- $a = \prod_{p}^{v_{p}(a)}$
- $b = \prod_{p}^{v_{p}(b)}$

$MCD(a, b) = \prod_{p}p^{\min(v_{p}(a),\ v_{p}(b))}$

Esiste un unico $m \in \mathbb{N}^{\star} :$

1. $a \mid m \land b \mid m$
2. se $m' \in \mathbb{Z} : a \mid m' \land b \mid m' \to m \mid m'$

Lemma: $a b \in \mathbb{Z} \neq 0$. Si scrive $mcm(a, b) = m$. Si chiama minimo comune multiplo


#todo

