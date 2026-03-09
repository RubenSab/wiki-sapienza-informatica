---
updated_at: 2026-03-07T17:38:00.431+01:00
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

## [[relazioni tra oggetti]]

- *is a*: si indicano con una freccia che termina con un triangolo vuoto.
- *has a*: si indicano con una semplice freccia dalla puntina nera.

### composizione

> Implica una relazione dove un child non può esistere indipendentemente dal parent.

Vengono indicate con una freccia che termina con un rombo pieno verso il parent.

### aggregazione

> Implica una relazione dove un figlio può esistere indipendentemente dal parent.

Vengono indicare con una freccia che termina con un rombo vuoto verso il parent.

### enumerazione

Si indica con un simbolo $\oplus$ con linee che collegano il campo verso i vari valori che può assumere il valore.

# Interfacce

L'[[ereditarietà]] di un'interfaccia da parte di una classe si indica con una freccia semplice tratteggiata.
