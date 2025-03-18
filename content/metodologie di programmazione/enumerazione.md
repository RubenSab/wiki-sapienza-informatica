---
updated_at: 2025-03-18T11:41:07.239+01:00
---
> Spesso è utile definire dei [[tipi]]/[[classe|classi]] (detti enumerazioni) i cui valori possono essere scelti tra un insieme predefinito di identificatori univoci **costanti**, dette *costanti enumerative*, che sono **implicitemente** `static`. Un tipo enumerazione viene dichiarato mediante la sintassi.

> N.B.: Non è possibile creare un [[oggetto]] del tipo enumerato.

``` java
public enum NomeEnumerazione
{
	COSTANTE1, COSTANTE2, ..., COSTANTEN
}
```

Come ogni classe, la dichiarazione di un'enumerazione può contenere altre componenti tradizionali:
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