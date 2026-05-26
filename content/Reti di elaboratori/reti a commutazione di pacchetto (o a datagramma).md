---
updated_at: 2026-05-26T09:46:26.315+02:00
---
> La comunicazione fra due sistemi terminali della [[rete]] è discontinua e viene effettuata attraverso blocchi di dati detti **pacchetti** divisi in blocchi di dimensione fissa. Non bisogna creare percorsi e riservare alcuna risorsa per i singoli utenti. I pacchetti vengono inoltrati dai [[router]] utilizzando l'indirizzo [[IP (Internet Protocol)]] dell'host destinatario.

Le [[protocolli di rete|tabelle di routing]] mappano intervalli di indirizzi IP destinazione (memorizzati come *prefissi*) a interfacce di output.

> Un **prefisso** IP è una stringa binaria più corta di un indirizzo IP. Può esprimere intervalli di indirizzi IP. Ad esempio se la stringa `..1010` è più corta di 2 caratteri di un indirizzo IP, allora può esprimere gli indirizzi `..101000`, `..101001`, `..101010` e `..101011`.

In casi di corrispondenze multiple di usa sempre il prefisso più lungo.

I blocchi possono prendere percorsi diversi e arrivare in ordine diverso alla destinazione, che dovrà riordinarli.

Per una rete con più $n > 2$ dispositivi e una linea di comunicazione con capacità minore di $n$ pacchetti, ogni router deve memorizzarli in una [[queue]] da svuotare man mano.

> In una rete a commutazione di pacchetto, la **congestione** è la situazione in cui il *carico* (numero di pacchetti inviati alla rete) è superiore della *capacità* della rete.