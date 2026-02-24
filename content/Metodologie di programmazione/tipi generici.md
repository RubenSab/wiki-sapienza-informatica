---
updated_at: 2025-05-18T21:51:57.081+02:00
---
> I tipi generici in [[Java]] sono un modello di programmazione che permette di definire con una sola dichiarazione un insieme di [[metodo|metodi]] o di [[classe|classi]] **indipendenti** dai [[tipi]] degli argomenti. Questo è possibile perché i tipi generici possono sostituire qualsiasi tipo **derivato** (per quelli primitivi c'è l'[[classe wrapper|autoboxing]]).

# Classi generiche

> N.B.: Per le classi generiche non vale l'ereditarietà dei tipi generici, ma comunque rimane l'ereditarietà tra classi. Quindi l'[[upcasting e downcasting]] tra tipi generici sono impossibili.
## Creazione

Per definire una classe che usa tipi generici, bisogna scrivere il nome della classe seguito dal nome del tipo generico, delimitato dalle *parentesi angolari*. Se ce n'è più di uno bisogna separarli con le virgole.

Per convenzione i tipi generici sono chiamati con le lettere T, S, etc. ed E se sono i tipi degli elementi di una collection.

Lo si usa come un qualsiasi altro tipo di classe.

``` java
public class Valore<T>
```

Per istanziare la classe basterà specificare un tipo da sostituire a quello generico:

``` java
Valore<Integer> i = new Valore<>(42);
```

``` java
Coppia<String> coppia = new Coppia<>("hello", "hi");
```

> N.B.: Si può anche scrivere `Valore<Object>` e far gestire il tipo, o i tipi, in modo automatico:

``` java
Coppia<Object> coppia = new Coppia<>('a', 1);
```

Nella fase della creazione non è servito specificare il tipo tra le parentesi angolari grazie al meccanismo dell'*inferenza automatica* del tipo generico.

## Estensione e specificazione 

È possibile estendere le classi generiche e specificare i tipi della nuova classe:

``` java
public class Coppia<T, S> ...
```

``` java
public class NomeCognome extends Coppia<String, String> ...
```

``` java
public class Data extends Coppia<Integer, Coppia<Integer, Integer>> ...
```

# [[interfaccia|Interfacce]] generiche

Esempio: le [[interfacce notevoli]] Comparable e Comparator sono generiche:

``` java
public interface Comparable<T>
{
	int compareTo(T o);
}

public interface Comparator<T>
{
	int compare(T o1, T o2)
}
```

Si può anche definire un'interfaccia generica inserendo un **vincolo di comparabilità** (o di qualsiasi altro genere) sul tipo generico, cioè un'interfaccia che **lavora sono con tipi confrontabili** (che implementano `Comparable<T>`).

``` java
public interface MinMax<T extends Comparable<T>> {
    T min();
    T max();
}
```

``` java
public class MyClass<T extends Comparable<T>> implements MinMax<T> {
// ...
}
```

# Metodi generici

Per definire un metodo generico è necessario anteporre il tipo generico tra parentesi angolari al tipo di ritorno:

``` java
static public <T> void esamina(ArrayList<T> lista)
{
	for (T elemento : lista):
		System.out.println(elemento.toString())
}
```

Se si vuole lavorare con un tipo generico ma non serve sapere quale esso sia, si può usare il [[jolly]].