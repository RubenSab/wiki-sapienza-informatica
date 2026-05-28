---
updated_at: 2026-05-27T22:59:07.881+02:00
---
> **Broadcast** (al contrario di Unicast) è l'invio di un pacchetto da un nodo della [[rete]] a tutti gli altri. Per renderlo possibile esiste l'**[[indirizzi IP|Indirizzo IP]] broadcast**.

Si può eseguire con:

- **Uncontrolled flooding**: appena un nodo riceve un pacchetto broadcast lo duplica e lo invia a tutti i nodi vicini, tranne a quello da cui lo ha ricevuto. Il problema è la formazione di cicli infiniti di copie di pacchetti.
- **Sequence number controlled flooding**: appena un nodo riceve un pacchetto broadcast controlla se è nella sua mappa da indirizzi IP a numeri di sequenza dei pacchetti già copiati e inoltrati. Se non c'è, lo duplica e lo inoltra.
- **Reverse path forwarding**: duplica e inoltra il pacchetto ai vicini solo se è arrivato da un link che appartiene cammino minimo verso la sorgente.
  Riduce il numero di pacchetti, ma ci sono ancora copie ridondanti che vengono ricevute e scartate dai [[router]]. ^7289b8
- **[[grafo#^a7b73d|Spanning tree]]**: Si costruisce il MST della rete prima di poter utilizzare il broadcast. Lo si accresce gradualmente prendendo un nodo come centro, verso cui ogni nodo invia un messaggio di join in unicast, aggiungendo nuovi archi.
  I pacchetti vengono inoltrati solo sugli archi del MST. Ogni router riceve solo una copia del pacchetto.