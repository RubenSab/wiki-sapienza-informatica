---
updated_at: 2025-04-10T13:19:56.952+02:00
---
> Le interfacce sono uno strumento che Java mette a disposizione per consentire a più [[classe|classi]] (anche molto diverse tra loro, slegate da relazioni *is-A*) di fornire e implementare un insieme di [[metodo|metodi]] comuni. Definiscono e standardizzano l'interazione fra [[oggetto|oggetti]] tramite un insieme limitato di operazioni.

> N.B.: Un metodo di default (pre implementato) in un'interfaccia non è sovrascrivibile.

Specificano solo le azioni/comportamenti che un oggetto può compiere, senza implementarle, quindi sono completamente astratte (se non definiamo metodi di default con la parola chiave `default`).

Sono classi che possono contenere soltanto:

- Costanti
- Metodi astratti (implicitamente `public abstract`)
- Campi (`public static final`)
- Metodi default e statici (da Java 8 in poi)
- Metodi privati (da  Java 9 in poi)

Non contengono costruttori e variabili locali.

> N.B.: Le [[relazioni tra oggetti]] *is-a* del [[polimorfismo]] valgono anche per le interfacce, inoltre un'interfaccia ne può estendere un'altra.

- [[interfaccia iterabile]]
- [[interfacce notevoli]]
- [[interfacce funzionali]]
## Esempio

### Interfaccia

``` java
public interface SupportoRiscrivibile
{
	int TIMES = 1000;
	void leggi();
	void sccrivi();
}
```
### Classe che la implementa

``` java
public class Nastro implements SupportoRiscrivibile, altraInterfaccia, ancoraUnAltraInterfaccia, etc

{
	private Pellicola pellicola;

	@Override
	public void leggi()
	{
		...
	}

	@Override
	public void scrivi()
	{
		...
	}
}
```