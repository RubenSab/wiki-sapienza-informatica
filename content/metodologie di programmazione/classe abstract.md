---
updated_at: 2025-03-20T14:26:50.522+01:00
---
> Una [[classe]] astratta (definita con la parola chiave abstract), NON può essere istanziata, quindi non possono esistere [[oggetto|oggetti]] per quella classe. Una classe astratta può avere anche dei [[metodo|metodi]] astratti.

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