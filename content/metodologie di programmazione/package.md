---
updated_at: 2025-03-31T18:32:05.527+02:00
---
> Sono collezioni (rappresentate fisicamente da **cartelle**) di [[classe|classi]] con funzionalità correlate e sotto-package.

> N.B.: quando si usa una classe, è necessario specificarne il package (a meno che siano in `java.lang`).

# Standard packages

Le API (Application Programming Interface) di Java sono organizzate in numerosi package.

```
java
	- applet
	- awt
	...
	- io
	- lang (il package che contiene anche String)
	- net
	- util

javax
	- swing
		- event
		- table
		...
	- sql
	- xml
```

## Importare le classi dai packages con `import`

> Per evitare di specificare il package di una classe ogni volta che viene usata, è sufficiente importare la classe.

Se scriviamo `import java.util.Scanner;`, poi potremo usare la classe `java.util.Scanner` semplicemente scrivendo `Scanner`.

> N.B.: Su [[metodologie di programmazione/Java]], l'import dei package **NON È RICORSIVO!!!** Bisogna importare i sotto-package necessari manualmente (anche se spesso gli IDE lo fanno per noi).

# Creare dei package

Una classe può essere inserita in un determinato package semplicemente:

- specificandolo all'inizio del file (parola chiave package)
- posizionando il file nella corretta sottocartella