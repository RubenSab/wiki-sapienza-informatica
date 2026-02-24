---
updated_at: 2025-03-31T18:35:57.167+02:00
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