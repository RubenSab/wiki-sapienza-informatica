---
updated_at: 2026-03-15T17:25:38.005+01:00
---
costrutti di classe, associazione, attributo, generalizzazione tra
classi

# Specifica requisiti

Dei voli interessa:

- codice: stringa
- durata: intero (minuti)
- compagnia aerea
- aeroporto di partenza
- aeroporto di arrivo
- se sono voli charter o meno

Dei voli charter, oltre alle informazioni solite dei voli interessa:

- la tappe intermedie
- il modello di velivolo usato

Dei modelli di velivolo interessa:

- il nome

Delle tappe intermedie interessa:

- l'intero che indica il suo indice nel susseguirsi delle tappe: intero > 0
- aeroporto di partenza
- aeroporto di arrivo

Degli aeroporti interessa:

- codice
- nome
- città

Delle città interessa:

- nome: stringa
- numero di abitanti: intero >= 0
- nazione

Delle nazioni interessa:

- nome: stringa

Delle compagnie aeree interessa:

- nome: stringa
- anno di fondazione: intero
- città della direzione