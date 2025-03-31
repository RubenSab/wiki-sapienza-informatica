---
updated_at: 2025-03-27T14:15:01.504+01:00
---
> Il polimorfismo consiste nel fatto che una [[variabile]] di un tipo A può contenere un riferimento a un [[oggetto]] del tipo A o di una qualsiasi sua sotto[[classe]].

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