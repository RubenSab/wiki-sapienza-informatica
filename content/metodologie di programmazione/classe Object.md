---
updated_at: 2025-04-01T10:53:15.174+02:00
---
> È la [[classe]] da cui [[ereditarietà|ereditano]] **tutte le [[classe|classi]]**, direttamente o indirettamente.

Scrivere

``` java
public class Classe {
	...
}
```

equivale a

``` java
public class Classe extends Object {
	...
}
```

# Metodi principali della classe Object

| Metodo                                |              | Descrizione                                                                                   |
| ------------------------------------- | ------------ | --------------------------------------------------------------------------------------------- |
| `Object clone()`                      | [[clone]]    | Restituisce una copia dell'[[oggetto]].                                                       |
| `Class <? extends Object> getClass()` | [[getClass]] | Restituisce un oggetto di tipo Class che contiene informazioni sul tipo dell'oggetto.         |
| `int hashCode()`                      | [[hashcode]] | Restituisce un intero associato all'oggetto ([[hashcode]]).                                   |
| `boolean equals(Object o)`            | [[equals]]   | Confronta l'oggetto con quello in input.                                                      |
| `String toString()`                   | [[toString]] | Restituisce una rappresentazione di tipo String dell'oggetto (per default: tipo@codice_hash). |
