---
updated_at: 2025-03-05T12:53:05.357+01:00
---
#todo
> Un **campo**, detto anche variabile di istanza, costituisce la *memoria privata* di un [[oggetto]].

Ogni campo ha:
- un [[tipo di dati]] (memoria)
- un nome fornito dal programmatore 

La dichiarazione di un campo avviene come segue

``` java
private [static] [final] tipo_di_dati nome;
```

- `private` o `public` determinano l'**[[accesso]] privato o pubblico del campo**.
- `[static]` se specificato indica che il campo **è condiviso da tutti**.
- `[final]` se specificato indica che il campo è una **costante**