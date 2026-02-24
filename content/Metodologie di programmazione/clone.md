---
updated_at: 2025-04-03T14:11:45.795+02:00
---
> È un [[metodo]] [[modificatori di visibilità|protetto]] (per design del lingaggio) che serve per creare una ***shallow copy*** di un oggetto (ottimo se i [[campi]] sono tutti primitivi, ***fare attenzione*** se i metodi sono riferimenti a oggetti). È necessario perché l'operazione di assegnazione non effettua una copia dell'[[oggetto]], ma solo di riferimento all'oggetto.

> N.B.: `x.clone() != x` è sempre vero perché gli [[operatori]] `==` e `!=` controllano le locazioni in memoria dell'oggetto.

> N.B.: `clone()` non richiama il costruttore della classe.

Se si vuole fare una *deep copy* dei campi, riferimenti a altri oggetti compresi, bisogna fare l'[[overriding]] del metodo clone.

Implementazione della deep-copy di clone.

``` java
public intVector getCopy()
{
	try
	{
		IntVector v = (IntVector).clone();
		v.list = (ArrayList<Integer>)list.clone();
		return v;
	}
	catch(CloneNotSupportedException e){return e}
}
```