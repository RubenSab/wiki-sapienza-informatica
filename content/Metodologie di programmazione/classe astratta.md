---
updated_at: 2026-02-26T22:20:06.276+01:00
---
> Una [[classe]] astratta (definita con la parola chiave abstract), NON può essere instanziata, quindi non possono esistere [[oggetto|oggetti]] per quella classe. Una classe astratta può avere anche dei [[metodo|metodi]] astratti.

Esempio:

``` java
/**
 * Classe astratta: non è possibile istanziarla
 */
public abstract class PersonaggioDisney
{
	/**
	 * Metodo astratto senza implementazione
	 */
	abstract void faPasticci()
}
```