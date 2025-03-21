---
updated_at: 2025-03-21T11:17:00.213+01:00
---
> In informatica un [[algoritmo]] [[funzione|ricorsivo]] è un algoritmo che nella sua definizione fa riferimento a se stesso.

Esempio:

``` python
def fattoriale(n):
	if n==0:
		return 1
	return n * fattoriale(n-1)
```

Ogni problema che si può risolvere in modo ricorsivo può essere anche risolto in modo iterativo e nella maggioranza dei casi è anche meglio risolverlo iterativamente, anche per la leggibilità.

> N.B.: L'implementazione del fattoriale in modo ricorsivo è solo un esempio perché è estremamente inefficiente, anche dal punto di vista della [[complessità spaziale]], perché mentre l'implementazione iterativa occupa un numero costante di registri $\Theta(1)$, questa versione occupa un registro per ogni chiamata ricorsiva, quindi costa $\Theta(n)$.
# Quando usare la ricorsione?

Per quei casi in cui è più facile programmare una cosa in modo ricorsivo piuttosto che iterativo.

- [[equazioni di ricorrenza]]
