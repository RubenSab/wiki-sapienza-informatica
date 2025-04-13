---
updated_at: 2025-04-08T09:53:35.628+02:00
---
> Da [[Java]] 8, è possibile specificare funzioni anonime utilizzando una notazione molto compatta, le [[espressione|espressioni]] lambda.

Esempio di espressione lambda:

``` Java
() -> { System.out.println("hello!"); }
```

Esempio di implementazione:

``` Java
@FunctionalInterface
public interface Runnable
{
	void run();
}
```

``` Java
Runnable r = () -> { System.out.println("hello!"); };
r.run(); // stampa "hello!"
```

# Come definire le espressioni lambda

``` Java
(param1, param2, ..., paramN) -> { System.out.println("hello!"); };
```

> N.B.:

- Le parentesi tonde sono opzionali se in input abbiamo un solo parametro.
- Le parentei graffe sono opzionali se in input abbiamo un solo parametro.
- Il tipo dei parametri è opzionale perché desunto dal contesto.
- Il return è opzionale se c'è una sola espressione di return.