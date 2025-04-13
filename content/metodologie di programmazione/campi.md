---
updated_at: 2025-04-08T09:14:37.510+02:00
---
> Un **campo**, detto anche [[variabile]] di istanza (perché l'oggetto è un'istanza della sua [[classe]]), costituisce la *memoria privata* di un [[oggetto]].

Ogni campo ha:
- un [[tipi]] (memoria)
- un nome fornito dal programmatore

La dichiarazione di un campo avviene come segue

``` java
private [static] [final] tipo_di_dati nome;
```

- `private` o `public` sono i [[modificatori di visibilità]] determinano l'**accesso privato o pubblico del campo**.
- `[static]` se specificato indica che il campo **è condiviso da tutte le istanze della classe**.
- `[final]` se specificato indica che il campo è una **costante**

> I campi di una classe possono essere dichiarati **static**: un campo static (dichiarato con la **parola chiave** `static`) è relativo all'intera classe, NON al singolo oggetto istanziato.

- Un campo static esiste in una sola locazione di memoria, allocata prima di qualsiasi oggetto della classe in una zona speciale di memoria nativa chiamata **MetaSpace**.
- Viceversa, per ogni campo non static esiste una locazione di memoria per ogni oggetto, allocata a seguito dell’istruzione `new`; questo perché ogni oggetto della stessa classe ha gli stessi campi ma di diversi valori, quindi serve memorizzare ognuno di questi valori diversi in locazioni diverse.