---
updated_at: 2025-04-03T13:20:56.932+02:00
---
> È un concetto cardine della [[programmazione orientata agli oggetti]]. È una forma di riuso del software, un meccanismo in cui una nuova [[classe]] (detta *sottoclasse*) è creata assorbendo i membri ([[campi]] e [[metodo|metodi]]) di una classe già esistente (della *superclasse*), aggiungendo nuovi membri e ridefinendo i metodi della superclasse (ma tipicamente non i campi).

Si dice che una sottoclasse *estende* la superclasse.

- [[upcasting e downcasting]]

> Si può controllare se un oggetto è un tipo o un sottotipo di un altra classe con l'operatore binario `<oggetto> instanceof <classe>`.

- [[this e super]]

> N.B.: extends può essere usato una e una sola volta da una classe, quindi l'[[ereditarietà multipla]] può essere realizzata solo con le interfacce. 

Esempio:

``` java
public class Forma
{
	public void disegna
	{
	...
	}
}

// la classe Triangolo estende (o eredita da) Forma
public class Triangolo extends Forma
{
	private double base;
	private double altezza;

	public Triangolo(double base, double altezza)
	{
		this.base = base;
		this.altezza = altezza;
	}

	public double getBase()
	{
		return base;
	}

	public double getAltezza()
	{
		return altezza;
	}
}
```

[[diagramma delle classi in UML]]

![[ereditarietàUML.svg]]