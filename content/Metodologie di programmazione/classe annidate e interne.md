---
updated_at: 2025-04-08T11:41:17.179+02:00
---
> Le [[classe|classi]] possono essere *top-level*, cioè trovarsi più in alto di tutte le altre classi, oppure essere *nested* (annidate), cioè essere definite all'interno di altre classi.

Le classi annidate vengono definite all'interno della definizione della classe *top-level* che le contengono; inoltre dalla classe interna si possono accedere a tutti i membri della classe esterna, e la classe interna diventa un membro di quella esterna, quindi si possono usare i [[modificatori di visibilità]] per la sua definizione.

> Le classi annidate possono essere classi statiche o non statiche, quest'ultime vengono dette *interne*.

Sono utili perché:

- raggruppano in modo logico le classi,
- incrementano l'[[incapsulamento]] e l'information hiding,
- aumentano la leggibilità e la mantenibilità del codice.

# Classi interne

> Sono classi interne non necessariamente statiche.

Dato che l'accesso ai membri della classe esterna e della classe interna avviene allo stesso modo, bisogna disambiguare nel caso che più membri abbiano lo stesso nome:

- Se nella classe interna viene usato soltanto [[this e super|this]] si fa riferimento ai campi e ai metodi di quella classe.
- Per far riferimento alla classe esterna è necessario usare `NomeClasseEsterna.this` al posto di `this`.

# Classi annidate

> Sono classi annidate statiche.