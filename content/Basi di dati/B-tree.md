---
updated_at: 2026-03-10T17:08:30.343+01:00
---
# Cosa risolve il B-tree

- Il B-tree generalizza la struttura di indice dell'[[file con indice (ISAM)|ISAM]], ottimizzando le performance della ricerca.
- Inoltre è garantito che primo livello dell'B-tree (la radice) può entrare nella memoria principale durante l'utilizzo.

# Cos'è il B-tree

Il B-tree è un [[albero]] di blocchi che ha come **radice un unico blocco**, quindi può risiedere in memoria principale durante l’utilizzo del [[file]].

Il **primo record indice** di ogni blocco indice contiene **solo** un puntatore ad un blocco le cui chiavi sono minori di quelle nel blocco puntato dal secondo record indice.

Ogni blocco del **[[file]] indice** contiene:
- un puntatore che collega il blocco al sotto-albero più a sinistra.
- più record che memorizzano una coppia, i cui elementi sono:
	1. il **valore** della chiave del primo record della porzione del [[file]] accessibile attraverso il puntatore,
	2. il [[puntatore]] a un blocco al livello più basso, oppure a una **foglia**, cioè ad un blocco del **[[file]] principale**, il quale non contiene puntatori.

> N.B.: Per scelta progettuale, ogni blocco del B-tree è sempre pieno **almeno per metà dei BYTE (anche contando i puntatori)**, garantendo che il B-tree sia **bilanciato**.

# Operazioni

## Ricerca

Si parte dalla radice e si legge **un blocco alla volta**:
- se si è arrivati a un blocco del [[file]] principale, allora il record cercato deve trovarsi lì.
- se leggiamo un blocco del [[file]] indice, si cerca nel blocco un valore $\geq$ del valore della chiave cercata, ma $<$ del valore successivo nel blocco, e si segue il suo rispettivo puntatore verso il prossimo blocco a un livello inferiore.

È evidente che la ricerca richiede $h + 1$ accessi ($h$ = altezza dell'albero).

> N.B.: Dato che più i blocchi sono pieni, più $h$ è piccolo, meno costa la ricerca, è meglio che **TUTTI** i blocchi del B-tree abbiano la parte dei valori piena almeno per metà. d'altra parte, il caso **peggiore** sarebbe invece quello in cui ogni blocco è pieno per metà.

Il valore massimo di $h$ è
$$
\log_{\frac{\text{capienza di record in un blocco indice}}{2}}\left(\frac{\text{numero di record nel [[file]] principale}}{\text{capienza di record in un blocco principale}}\right)
$$

Dimostrazione da pag. 19 a 23 del pdf 24.

## Inserimento

Se nel blocco non c'è spazio per il nuovo record l'inserimento costa come una ricerca per trovare il blocco in cui inserire il record, quindi $h+1$

Se **tutto** l'albero è pieno bisogna **sdoppiare** un blocco per livello (due accessi per livello + 1 alla fine per la nuova radice), quindi $2h+1$.

## Cancellazione

$h+1$ (ricerca) $+1$ (riscrittura del blocco). Se il blocco rimane pieno per metà bisognerà fare altri accessi.

## Modifica

$h+1$ (ricerca) $+1$ (riscrittura del blocco) se la modifica non coinvolge campi della chiave, altrimenti corrisponde a una **cancellazione + inserimento**.

# Esempio

Supponiamo di avere un [[file]] di 170.000 record. Ogni record occupa 200 byte, di cui 20 per il campo chiave.
Ogni blocco contiene 1024 byte. Un puntatore a blocco occupa 4 byte.

## Se usiamo un B-tree e assumiamo che sia i blocchi indice che i blocchi del [[file]] sono pieni al minimo, quanti blocchi vengono usati per il livello foglia (file principale)

Ogni blocco può contenere al massimo $\left\lfloor\frac{1024}{200}\right\rfloor = 5$ record.

Per definizione, un blocco non può contenere meno di $\left\lceil\frac{5}{2}\right\rceil = 3$ record, quindi in questo contesto 3 è il numero di record in un blocco.

Considerando che **ogni chiave si trova su un livello foglia**, il numero di blocchi nel livello foglia sarà $\left\lceil\frac{170000}{3}\right\rceil = 56667$.

## e quanti per l’indice, considerando tutti i livelli non foglia ?

I blocchi foglia sono 56667 e l'albero di indici li deve indicizzare tutti.

Considerando che ogni blocco contiene 1024 byte e è formato da un puntatore iniziale (4 byte) e da $n$ coppie chiave-puntatore (20+4) byte, per occupare un blocco **a metà** servono 4 byte + $n$ coppie.

$$
4 + n(24) = \frac{1024}{2} \to \lceil n \rceil = 22\ \text{coppie}
$$
22 coppie corrispondono a 22 puntatori, più il puntatore iniziale sono 23.

Adesso [il calcolo è matematico](https://www.youtube.com/shorts/wCVMa-CHWuY).

1. Il primo livello di blocchi indice ha bisogno di $\left\lceil\frac{56667}{23}\right\rceil = 2464$ blocchi per indicizzare i 56667 blocchi del file principale;
2. il secondo livello di blocchi indice ha bisogno di $\left\lceil\frac{2464}{23}\right\rceil = 108$ blocchi per indicizzare i 2464 blocchi del primo livello;
3. il terzo livello di blocchi indice ha bisogno di $\left\lceil\frac{108}{23}\right\rceil = 5$ blocchi per indicizzare i 108 blocchi del secondo livello;
4. il quarto livello di blocchi indice ha bisogno di $\left\lceil\frac{5}{23}\right\rceil = 1$ blocchi per indicizzare i 5 blocchi del terzo livello: è la radice.

In totale l'albero del file indice occupa $2463 + 108 + 5 + 1 = 2578$ blocchi, distribuiti in 4 livelli.

### Osservazione **importante** sul numero dei livelli

Il fatto che ogni livello aveva $\frac{1}{23}$ nodi del livello sottostante, fa si che l'altezza $h$ dell'albero è esprimibile come:

$$
h = \left\lceil\log_{\text{puntatori per blocco}}{\text{blocchi foglia}}\right\rceil
$$

$$
 = \left\lceil\log_{\text{puntatori per blocco}}{\left(\frac{\text{numero di record nel file principale}}{\text{capienza di record in un blocco principale}}\right)}\right\rceil
$$

## Qual è il costo di una ricerca in questo caso?

Dato che ci sono 4 livelli di indici, di cui uno è la radice che è **sempre** in [[memoria]] principale, e in più c'è il livello dei blocchi del file principale, in totale la ricerca costa 4 accessi in **memoria secondaria**.