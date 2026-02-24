---
updated_at: 2025-04-01T10:29:22.137+02:00
---
> Spesso è utile definire dei [[tipi]] (detti enumerazioni) i cui valori possono essere scelti tra un insieme predefinito e immutabile di **costanti**, dette *costanti enumerative*, che sono **implicitamente** `static`.

Ciò si realizza con le [[classe astratta|classi astratte]]:

``` java
public enum NomeEnumerazione
{
	COSTANTE1, COSTANTE2, ..., COSTANTEN
}
```

> N.B.: Non è possibile creare un [[oggetto]] del tipo enumerazione, però ogni costante enumerativa è un'istanza public e final; non se ne possono creare altre.

> N.B.: Il costruttore deve essere definito **necessariamente** senza [[modificatori di visibilità]] come de fosse default (anche se non è veramente default ma implicitamente private). 

Le classi enumerative estendono la classe Enum, da cui ereditano i metodi [[toString]] e [[clone]].

Come ogni classe, la dichiarazione di un'enumerazione può contenere:

- costruttori,
- [[campi]],
- [[metodo|metodi]]

Esempio: implementazione di una classe Mese

- con uno switch case

![[Pasted image 20250318112236.png]]

- con le enumerazioni

![[Pasted image 20250318112302.png]]

# Metodi statici values() e valueOf()

> Per ogni enumerazione, il compilatore genera il metodo statico **values()** che restituisce un [[array]] delle costanti enumerative.

> Viene generato anche un metodo **valueOf()** che restituisce la costante enumerativa associata alla stringa fornita in input.

# Enumerazioni e switch

> L'enumerazioni possono essere utilizzate all'interno di un costrutto [[flussi di controllo|switch]].

Esempio:

![[Pasted image 20250318114106.png]]

![[Pasted image 20250318114121.png]]