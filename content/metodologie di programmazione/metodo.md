---
updated_at: 2025-03-20T18:45:44.101+01:00
---
> Un metodo è una [[funzione]] associata in modo esclusivo a una [[classe]], può essere richiamato sia da un'[[oggetto]] che una classe stessa. Ha degli argomenti in input e spesso restituisce un output con `return`.

- I metodi sono tipicamente [[modificatori di visibilità|pubblici]].
- Per convenzione il nome dei metodi è in *camelCase*.

I metodi permettono di modularizzare un programma separandone i compiti in unità autocontenute.

> N.B.: Nella [[programmazione orientata agli oggetti]] **ogni funzione** è un metodo di quale classe.

> N.B.: Da Java 5, un metodo può avere un numero variabile di parametri (senza dover passare un'[[array]]).

# definizione di un metodo

``` java
public tipo_di_dati nomeDelMetodo(tipo_di_dati_del nomeParam1, ..., tipo_di_dati_del nomeParamN)
{
	istruzione 1;
	...
	...
	...
	istruzione m;
}
```

# metodi statici

> Sono **metodi di classe** che NON hanno accesso a [[campi]] di istanza/oggetto, ma hanno accesso solo ai campi di classe.

Esempio:

![[Pasted image 20250311105109.png]]

# metodi astratti

> Sono metodi che non possono essere implementati e non fanno nulla, infatti non hanno nemmeno le parentesi graffe del corpo di istruzioni. Servono solo ad essere [[ereditarietà|ereditati]], facendo da prototipi.