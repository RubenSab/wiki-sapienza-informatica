---
updated_at: 2025-03-11T11:31:15.922+01:00
---
#todo

> Sono collezioni (rappresentate fisicamente da cartelle) di [[classe|classi]] con funzionalità correlate e sotto-package.

> N.B.: quando si usa una classe, è necessario specificarne il package (a meno che siano in `java.lang`).

# Standarg packages

Le API (Application Programming Interface) di Java sono organizzate in numerosi package.

![[Pasted image 20250311111510.png]]

# Importare le classi

> Per evitare di specificare il package di una classe ogni volta che viene usata, è sufficiente importare la classe.

Se facciamo `import java.util.Scanner;`, poi potremo usare la classe `java.util.Scanner` semplicemente scrivendo `Scanner`.

> N.B.: Su [[Java]], l'import dei package **NON È RICORSIVO!!!** Bisogna importare i sotto-package necessari manualmente (anche se spesso gli IDE lo fanno per noi).

# Creare dei package
Una classe può essere inserita in un determinato package semplicemente:
- specificandolo all’inizio del file (parola chiave package)
- posizionando il file nella corretta sottocartella

Esempio di package:

![[Pasted image 20250311113121.png]]