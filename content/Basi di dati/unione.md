---
updated_at: 2025-10-07T16:57:01.691+02:00
---
> È l'operazione binaria commutativa che consente di costruire una [[relazione]] che contiene tutte le tuple che appartengono ad almeno uno dei due operandi.

Si denota con il simbolo $\cup$.

> N.B..: I due operandi devono essere *union compatibili*, cioè tali che:

- hanno lo stesso numero di attributi,
- gli attributi corrispondenti, in ordine, devono appartenenti allo stesso dominio,
- per avere senso bisogna che abbiamo anche **un significato omogeneo** (es: l'unione tra prezzi e ore non ha senso, anche se sono entrambi numeri).

> N.B.: L'unione può portare alla perdita di chiavi, ma ciò non compromette l'unibilità.

Esempio:

Team1 (chiave Codice):

| Nome  | Codice | Ruolo           |
| ----- | ------ | --------------- |
| Marco | C1     | Amministrazione |
| Paolo | C2     | Marketing       |

Team2 (chiave Codice):

| Nome   | Codice | Ruolo         |
| ------ | ------ | ------------- |
| Andrea | C1     | Programmatore |
| Matteo | C2     | Artista       |

Team1 $\cup$ Team2 (la chiave Codice è stata persa):

| Nome   | Codice | Ruolo           |
| ------ | ------ | --------------- |
| Marco  | C1     | Amministrazione |
| Paolo  | C2     | Marketing       |
| Andrea | C1     | Programmatore   |
| Matteo | C2     | Artista         |

Bisogna prevedere delle chiavi che non verranno perse dopo l'unione, ad esempio il codice fiscale.