---
updated_at: 2025-10-05T17:32:36.259+02:00
---
> È una sequenza di operazioni (concretamente un [[processo]]) che costituiscono un'unica operazione logica che agisce sulla [[database]].

Deve essere:

- isolata;
- lasciare risultati permanenti nella base di dati;
- non violare i vincoli;
- eseguita completamente (*committed*): se si interrompe bisogna annullare i suoi effetti e rieseguirla o non essere eseguita affatto (*rolled back*).

> Per ripristinare un valore corretto sul DB bisogna disporre di un *transaction log*, che contiene i dettagli delle operazioni, valori precedenti e seguenti la modifica, e una *dump* (compia periodica del DB).