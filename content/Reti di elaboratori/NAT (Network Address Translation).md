---
updated_at: 2026-06-01T18:55:00.521+02:00
---
> Problema: le organizzazioni vogliono blocchi di [[IP (Internet Protocol)|IP]] contigui e espandibili per indirizzare le loro [[rete|reti]], ma i blocchi successivi possono essere stati comprati da altre società. Ciò si può risolvere con gli indirizzi privati + [[NAT (Network Address Translation)]].

C'è una rete privata (con indirizzi IP privati) collegata a un [[router]] NAT, a sua volta collegato a [[Internet]]. I router abilitati al NAT non appaiono a Internet come router ma come un singolo dispositivo con un IP.

Un unico IP è sufficiente per tutti gli host di una rete locale. È possibile cambiare indirizzi privati e ISP senza nessun cambiamento o comunicazione.

I dispositivi interni non sono esplicitamente indirizzabili e visibili a Internet.

# Funzionamento

- Il router NAT riceve il datagramma,
- sostituisce l'IP di origine con il proprio sul lato [[WAN (Wide Area Network)]],
- modifica il numero di [[porta]] di origine del pacchetto con uno nuovo.

# Critiche

- NAT viola lo [[stack protocollare TCP-IP]] perché elabora i pacchetti oltre il livello di rete (fino alle porte, appartenenti al trasporto).
- Usa il numero di porta per identificare host e non processi.
- I Router abilitati al NAT sono dei middleman in connessioni punto-punto, interferendo anche con il concetto di applicazione peer to peer.