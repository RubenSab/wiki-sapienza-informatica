---
updated_at: 2026-10-30T17:39:30.833+01:00
---
Sono un modo di descrivere [[linguaggio|linguaggi]]. Permettono di descrivere caratteristiche ricorsive delle stringhe riconosciute. Per questo sono utili per descrivere linguaggi umani e [[Linguaggi di programmazione|linguaggi di programmazione]].

> Il **linguaggio di una grammatica acontestuale**, cioè l'[[insieme]] di tutte le stringhe che possono essere generate dalla suddetta grammatica, è detto *context free language*.

> Una grammatica acontestuale consiste in un insieme di **regole di sostituzione**, anche chiamate **produzioni**, scritte nel formato $\text{variabile} \to \text{stringa}$.
> Le **variabili** (indicate con lettere maiuscole) sono simboli da sostituire, mentre le **stringhe** sono sequenze di variabili e **terminali**, altri simboli dell'alfabeto.
> Una delle variabili è la **variabile iniziale**, scritta a sinistra nella prima regola.

> Esempio di **derivazione** (sequenza di simboli per ottenere una stringa) di "00#11" nella seguente grammatica:

$$
A \to 0A1 \\ A \to B \\ B \to \#
$$

$$
A \to 0A1 \to 00A11 \to 00B11 \to 00\#11
$$

> Si dice che $A$ **genera** $00\#11$; scritto come: $A \overset{\star}{\implies} 00\#11$.

> N.B.: Più regole $X \to Y$ e $X \to Z$ possono essere abbreviate in $X \to Y \mid Z$.

# Definizioni formali

> Una **grammatica acontestuale** è una quadrupla $(V, \Sigma, R, S)$ dove:

- $V$ sono le **variabili**. Esse **non** sono simboli dell'alfabeto,
- $\Sigma$ è l'alfabeto,
- $R$ solo le **regole**,
- $S \in V$ è la **variabile iniziale**.

> Il **linguaggio di una grammatica acontestuale** è $\{w \in \Sigma^{\star} \mid S \overset{\star}{\implies} w\}$.

> La derivazione di una stringa di una grammatica $G$ si dice derivazione **leftmost** se a ogni step la variabile più a sinistra della stringa viene rimpiazzata.

> Una stringa si dice **derivata ambiguamente** in una grammatica acontestuale $G$ se ha una o più dericazioni leftmost.

> Una grammatica si dice **ambigua** se genera ambiguamente almeno una stringa.


- [[forma normale di Chomsky]]

# Esercizi: formalizzare le descrizioni dei seguenti linguaggi in CFG

## 1. $L_{1} = \{w \in {\{0, 1\}}^{\star}:\ {\#}_{1}(w) \geq 3\}$

$$
S \to A1A1A1A \\
A \to 0A \mid 1A \mid \varepsilon
$$
Stringhe binarie con almeno 3 uno

![[Pasted image 20261020224259.png]]


## 2. $L_{2} = \{w \in {\{0, 1\}}^{\star}:\ w = w^{R},\ | w | = 2n\ n \in \mathbb{N}\}$

> $w = w^{R}$ vuol dire palindroma.

$$
S \to A \\
A \to 0A0 \mid 1A1 \mid 00 \mid 11
$$

## 3. $L_{3} = \{a^{i}b^{i}c^{k}:\ i+1 = k\quad i, k \geq 0\}$

?

# Implementazione mia su python

``` python
def derive_from(string, grammar, iterations, i=0, path=None):
    if path is None:
        path = []
    if i > iterations:
        return
    if not any([var in string for var in grammar.keys()]):
        print(*path, string, sep=' -> ')
    for variable, substitutions in grammar.items():
        if variable in string:
            for substitution in substitutions:
                path.append(string)
                derive_from(
                    string.replace(variable, substitution, 1),
                    grammar,
                    iterations,
                    i+1,
                    path
                )
                path.pop()

G = {
    'A': ['0A1', 'B'],
    'B': ['#']
}

derive_from('A', G, 5)
```

output:

```
A -> 0A1 -> 00A11 -> 000A111 -> 000B111 -> 000#111
A -> 0A1 -> 00A11 -> 00B11 -> 00#11
A -> 0A1 -> 0B1 -> 0#1
A -> B -> #
```

Altro esempio

``` python
G = {
    'START': ['Hi! SENTENCE'],
    'SENTENCE': ['I am PERSON', 'I know a PERSON', 'have a nice TIME in PLACE!', 'I really like ACTIVITY in PLACE', 'I really like ACTIVITY in PLACE in the TIME'],
    'PLACE': ['Rome', 'Paris'],
    'TIME': ['morning', 'evening'],
    'PERSON': ['a GENDER who PREFERENCE ACTIVITY in the TIME', 'a GENDER from PLACE who PREFERENCE ACTIVITY in the TIME'],
    'PREFERENCE': ['likes', 'hates', 'would like'],
    'GENDER': ['boy', 'girl'],
    'ACTIVITY': ['running', 'skating', 'singing']
}

derive_from('START', G, 8)

# Esempi output:
# Hi! have a nice time in Paris!
# Hi! I know a girl from Rome who likes singing in the morning
# Hi! I really like skating in Rome
```