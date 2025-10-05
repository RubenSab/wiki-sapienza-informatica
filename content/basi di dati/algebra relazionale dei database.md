---
updated_at: 2025-10-05T17:22:37.808+02:00
---
> Si fonda sul concetto di [[relazione]] matematica ed è la base dei [[database relazionali]].

> Il numero di domini di cui si fa il prodotto cartesiano è il suo **grado**.

> Il numero di tuple di una relazione è la sua **[[cardinalità]]**.

- In [[SQL]] il concetto di dominio si traduce concretamente nel **tipo** degli attributi.
- Le tuple di una relazione sono tutte distinte.

# Dipendenze funzionali

> Una dipendenza funzionale stabilisce un particolare legame semantico tra due insiemi non vuoti di attributi $X$ e $Y$ appartenenti ad uno schema $R$.

Tale vincolo si scrive $X \to Y$ e si legge $X$ e $Y$.

- $X$ si dice *determinante*,
- $Y$ si dice *determinato*.

> In modo astratto, si può considerare la dipendenza funzionale come la coppia ordinata di [[sottoinsiemi]] di $R$, cioè $(X, Y)$.

Ad esempio il modello di macchina "Punto" **determina** la marca "Fiat". L'importante è che non possa assegnare "Punto" a due marche diverse.