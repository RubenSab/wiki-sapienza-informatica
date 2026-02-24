---
updated_at: 2025-03-11T10:16:36.877+01:00
---
> È un [[metodo]] che ha lo stesso nome (case-sensitive) della [[classe]] a cui appartiene, serve a inizializzare i [[campi]] di un [[oggetto]] della sua classe ai valori di default. Se non è specificato, Java crea per ogni classe un *costruttore di default* "vuoto", cioè senza parametri.

Una classe può avere anche più costruttori che DEVONO differire nel **numero** e nel **tipo** di parametri

# esempio

Realizziamo una [[classe]] che può:

- incrementare il conteggio di 1
- ottenere il conteggio corrente
- resettare resettare il conteggio

```java
/**
 * Valore intero del contatore
 */
public class Counter {

	private int value;

	public void count() {
		value ++;
	}

	public int getValue() {
		return value;
	}

```

Definiamo due costruttori diversi:

``` java
	/**
	 * Costruttore della classe
	 */
	public Counter()
	{
		value = 0 // Inizializzazione dei campi
	}
	
	/**
	 * Costruttore della classe con valore iniziale
	 */
	public Counter(int initialValue)
	{
		value = initialValue; // Inizializzazione dei campi
	}

}
```

I due `Counter` appartengono alla stessa classe, ma sono stati inizializzati con campi diversi grazie a costruttori diversi.

``` java
static public void main(String[] args)
{
	Counter contatore1 = new Counter();
	Counter contatore2 = new Counter(42);

	System.out.println("valore del contatore1: "+contatore1.getvalue());
	System.out.println("valore del contatore2: "+contatore1.getvalue());
}
```

Ora implementiamo il reset:

1. prima definiamo un metodo senza argomenti che azzera il contatore:

``` java
public void reset(){
	value = 0;
}
```

1. ora miglioriamo `reset()`, vogliamo resettarslo a un valore specifico se passiamo un argomento. Potremmo creare un nuovo metodo, ma si preferisce usare l'[[overloading]].
``` java
public void reset(int newValue) {
	value = newWalue;
} 
```