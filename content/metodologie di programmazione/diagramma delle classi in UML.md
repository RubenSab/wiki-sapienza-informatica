---
updated_at: 2025-03-25T19:01:25.249+01:00
---
# Package

Un [[package]] si rappresenta come un rettangolo che all'interno può contenere [[classe|classi]] e altri metodi.

# Classi

Una [[classe]] si rappresenta come un rettangolo diviso orizzontalmente in tre sezioni: la prima contiene il nome (eventualmente preceduto dal tag `<abstract>` per le [[classe astratta|classi astratte]]), la seconda contiene i campi nel formato `-campo:tipo_di_dati` e la terza contiene i metodi nel formato:
`simbolo_della_visibilità metodo(campo:tipo_in_input,...): tipo_in_output`.

![[Pasted image 20250312122639.png]]
![[Pasted image 20250312122708.png]]
## visibilità di campi e metodi

La [[modificatori di visibilità|visibilità]] si rappresenta così:

| visibilità | prefisso |
| ---------- | -------- |
| publica    | +        |
| privata    | -        |
| protetta   | #        |
| package    | ~        |

## relazioni tra oggetti

> Due [[oggetto|oggetti]] possono avere relazioni di tipo "_is a_" (l'oggetto è un'istanza di una classe/ due oggetti sono uguali) e "_has a_" (l'oggetto "contiene" un altro oggetto).
### relazioni is-A (estensione)

> Implicano una gerarchia di [[ereditarietà]].

Si indicano con una freccia che termina con un triangolo vuoto.

### relazioni has-A (associazione)

> Implicano un "contenimento" (in realtà riferimento) di un oggetto in un altro.

Si indicano con una semplice linea a cui va accostato il numero di istanze dell'oggetto contenuto (vicino a quest'ultimo).

### dipendenza

> Un oggetto fa uso di un altro oggetto nel suo codice.

Si indica con una semplice freccia dalla puntina nera

### composizione

> Implica una relazione dove un child non può esistere indipendentemente dal parent.

Vengono indicate con una freccia che termina con un rombo pieno verso il parent.

### aggregazione

> Implica una relazione dove un figlio può esistere indipendentemente dal parent.

Vengono indicare con una freccia che termina con un rombo vuoto verso il parent.

### enumerazione

Si indica con un simbolo $\oplus$ con linee che collegano il campo verso i vari valori che può assumere il valore.
