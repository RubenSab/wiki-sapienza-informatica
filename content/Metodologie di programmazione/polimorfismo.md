---
updated_at: 2025-04-01T09:40:10.176+02:00
---
> Il polimorfismo è la possibilità di creare [[oggetto|oggetti]] di tipo [[ereditarietà|superclasse]] (anche [[classe astratta|astratta]]!!!) usando i costruttori delle sue sottoclassi, rendendo i metodi della superclasse un'interfaccia comune a cui l'oggetto istanziato dalla sottoclasse si può riferire. Ciò rende possibile l'[[upcasting e downcasting]].

> Il polimorfismo si basa sul fatto che una [[variabile]] di un tipo A può contenere un riferimento a un [[oggetto]] del tipo A o di una qualsiasi sua sotto[[classe]].

Esempio:

``` java
Animale a = new Gatto();
a = new Chihuahua();
```

Ciò è possibile grazie al [[binding]] dinamico.

Si usa quando vogliamo utilizzare oggetti diversi ma con caratteristiche comuni.

Per esempio

``` java
ArrayList<Forma> forme = new Arraylist<>();

/* riempi la lista di forme */

for (Forma f: forme) {
	f.disegna()
}
```

disegnerà correttamente le forme diverse, tutti oggetti di classi diverse (come Triangolo, Quadrato, etc.) che [[ereditarietà|ereditano]] dalla superclasse Forma.