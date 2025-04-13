---
updated_at: 2025-04-08T09:42:17.636+02:00
---
> È possibile definire [[classe|classi]] anonime che implementano un'[[interfaccia]] o [[ereditarietà|estendono]] una classe. Sono utilizzate esclusivamente per creare un'unica istanza.

Ad esempio sono utili per creare iteratori al volo.

``` Java
TipoDaEstendereNonAnonimo unicoRiferimentoAOggetto = new TipoDaEstendereNonAnonimo()
{
	// codice della classe anonima
}
```

Esempio:

``` Java
public interface Formula
{
	double calculate(int a);
	default double sqrt(int a) { return Math.sqrt(a); }
}


```

Da [[Java]] 8 è disponibile l'annotazione `@FunctionalInterface`, che garantisce che l'interfaccia sia dotata esattamente di un solo metodo astratto.

``` Java
@FunctionalInterface
public interface Runnable
{
	void run();
}
```

Sono necessarie per definire [[espressione lambda]].