---
updated_at: 2026-03-30T15:33:23.176+02:00
---
# Ogni crociera viene effettuata utilizzando una nave

## *utilizza* come simbolo di predicato

```
P = {
	Crociera/1 // Crociera(x) <-> "x è una crociera"
	Nave/1 // Nave(x) <-> "X è una nave"
	utilizza/2 // utilizza(x, y) <-> "x utilizza y"
}
```

$$
\forall x \ \text{Crociera}(x) \implies \ldots
$$

$$
\ldots (\exists y\ (\text{Nave}(y) \land \text{utilizza}(\text{x}, \text{y})) \land (\forall y, z\ \text{Nave}(y) \land \text{Nave}(z) \land \text{utilizza}(x, y) \land \text{utilizza}(x, z) \implies y = z))
$$

A parole, se $x$ è una crociera allora se $y$ è una nave e $x$ utilizza $y$ allora due navi utilizzate da $x$ sono la stessa nave (iniettività, $x$ usa una sola nave).

### Interpretazione modello della formula

```
D = {c1, c2, n1, n2, n3}
I(Crociera) = {c1, c2}
I(Nave) = {n1, n2}
I(Utilizza) = {(c1, n2), (c2, n2)}
```

## *utilizza* come simbolo di funzione

```
P = {
	Crociera/1 // Crociera(x) <-> "x è una crociera"
	Nave/1 // Nave(x) <-> "X è una nave"
}

F = {
	utilizza/1 // utilizza(x) <-> "restituisce la nave utilizzata da x"
}
```

$$
\forall x\ \text{Crociera}(x) \implies \text{Nave}(\text{utilizza}(x))
$$

# Ogni crociera segue un itinerario

# Gli itinerari hanno un nome univoco

```
P = {
	Crociera/1      // Crociera(x) <-> "x è una crociera"
	Nave/1          // Nave(x) <-> "X è una nave"
	utilizza/2      // utilizza(x, y) <-> "x utilizza y"
	Itinerario/1    // ...
	nome/1          // nome(x) <-> "x è un nome"
	ha_nome/2       // nome(x, y) <-> "x ha il nome y"
}
```

```
NOT EXISTS i
	Itinerario(i) AND NOT EXISTS n ha_nome(i, n)
AND
NOT EXISTS i, n1, n2
	n1 != n2 AND ha_nome(i, n1) AND ha_nome(i, n2)
AND
not EXISTS i1, i2, n
	i1 != i2 AND Itinerario(i1) AND Itinerario(i2) AND nome(n)
	AND ha_nome(i1, n) AND ha_nome(i2, n) 
```

# Ogni crociera tocca un certo insieme non vuoto di destinazioni

#todo

# Le crociere si dividono in crociere di luna di miele e crociere per famiglia.

#todo