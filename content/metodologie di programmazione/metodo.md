---
updated_at: 2025-03-11T10:51:51.079+01:00
---
> Un metodo è una [[funzione]] associata in modo esclusivo a una [[classe]], può essere richiamato sia da un'[[oggetto]] che una classe stessa.

- I metodi sono tipicamente [[modificatori di accesso|pubblici]].
- Per convenzione il nome dei metodi è in *camelCase*.

> N.B.: Nella [[programmazione orientata agli oggetti]] **ogni funzione** è un metodo di quale classe.

# definizione di un metodo
``` java
public tipo_di_dati nomeDelMetodo(tipo_di_dati_del nomeParam1, ..., tipo_di_dati_del nomeParamn)
{
	istruzione 1;
	...
	...
	...
	istruzione m;
}
```

# metodi statici

> Sono **metodi di classe** che NON hanno accesso a [[campi]] di istanza, ma hanno accesso solo ai campi di classe.

Esempio:

![[Pasted image 20250311105109.png]]