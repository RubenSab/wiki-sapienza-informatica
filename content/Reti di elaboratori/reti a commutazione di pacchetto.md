---
updated_at: 2026-05-20T23:36:53.529+02:00
---
> La comunicazione fra due sistemi terminali della [[rete]] è discontinua e viene effettuata attraverso blocchi di dati detti **pacchetti** divisi in blocchi di dimensione fissa. Non bisogna creare percorsi e riservare alcuna risorsa per i singoli utenti. Gli switch memorizzano e inoltrano i pacchetti.

I blocchi possono prendere percorsi diversi e arrivare in ordine diverso alla destinazione, che dovrà riordinarli.

Per una rete con più $n > 2$ dispositivi e una linea di comunicazione con capacità minore di $n$ pacchetti, ogni router deve memorizzarli in una [[queue]] da svuotare man mano.

> In una rete a commutazione di pacchetto, la **congestione** è la situazione in cui il *carico* (numero di pacchetti inviati alla rete) è superiore della *capacità* della rete.