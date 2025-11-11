---
updated_at: 2025-11-10T22:28:32.826+01:00
---
> L'insieme di [[dipendenza funzionale|dipendenze funzionali]] $F^{A}$ è definito come l'insieme di tutte le dipendenze funzionali definite con gli *assiomi di Armstrong*.

# Assiomi di Armstrong

- se $f \in F$ allora $f \in F^{A}$
- **Assioma della [[proprietà, tipi di relazioni e ordini|riflessività]]**: se $Y \subseteq X \subseteq R$ allora $(X \to Y) \in F^{A}$
  Esempio: `ID` determina `Nome`, quindi `ID` determina `Nome, ID`.
- **Assioma dell'aumento**: se $(X \to Y) \in F^{A}$ allora $\forall Z \subseteq R\ ((XZ \to YZ) \in F^{A})$
  Esempio: `ID` determina `Nome`, quindi `ID, Cognome` determina `Nome, Cognome`.
- **Assioma della [[proprietà, tipi di relazioni e ordini#^7703c4|transitività]]**: se $(X \to Y) \in F^{A} \land (Y \to Z) \in F^{A}$ allora $(X \to Z) \in F^{A}$
  Esempio: `Specie` determina `Regno` e `Regno` determina `Phylum`, quindi `Specie` determina `Phylum`.

Dimostreremo che $F^{+} = F^{A}$, cioè che la chiusura di un insieme di dipendenze funzionali $F$ può essere ottenuta a partire da $F$ applicando ricorsivamente gli assiomi di Armstrong.

## Conseguenze

Da questi assiomi, derivano tre regole necessarie per derivare nuove dipendenze funzionali in $F^{A}$ da quelle già trovate in $F_{A}$, fino a trovarle tutte.

- **Regola dell'unione**: se $X \to Y \in F^{A}$ e $X \to Z\in F^{A}$ allora $X \to YZ \in F^{A}$
  Esempio: `ID` determina `Nome` e `ID` determina `Cognome`, quindi `ID` determina `Nome, Cognome`
- **Della decomposizione**: se $X \to Y \in F^{A}$ e $Z\subseteq Y$ allora $X \to Z\in F^{A}$
  Esempio: `ID` determina `Nome, Cognome`, quindi `ID` determina `Nome`.
- **Della pseudotransitività**: se $X \to Y \in F^{A}$ e $WY \to Z\in F^{A}$ allora $WX \to Z\in F^{A}$
  Esempio: Se `Matricola` determina `Facoltà` e `Facoltà, CodiceEsame` determina `Docente` allora `Matricola, CodiceEsame` determina `Docente`.

### Dimostrazioni

#### Regola dell'unione

- Se $X \to Y \in F^{A}$ allora $X \to XY \in F^{A}$ per aumento,
- se $X \to Z \in F^{A}$ allora $XY \to YZ \in F^{A}$ per aumento,
- dato che $X \to XY \to YZ \in F^{A}$, per transitività si ha che $X \to YZ \in F^{A}$.

#### Regola della decomposizione

- Se $Z\subseteq Y$ allora $Y \to Z\in F^{A}$ per riflessività,
- se $X \to Y \in F^{A}$ allora $X \to Y \to Z$, quindi $X \to Z$ per transitività.

#### Regola della pseudotransitività

- Se $X \to Y \in F^{A}$ allora $WX \to WY \in F^{A}$ per aumento,
- se $WY \to Z\in F^{A}$ allora $WX \to WY \to Z$, quindi $WX \to Z$ per transitività.


[[chiusura di un insieme di attributi]]

# Dimostrazione $F^{+} = F^{A}$ #todo

Per dimostrare che $F^{A} = F^{+}$ bisogna verificare sia che $F^{A} \subseteq F^{+}$ che $F^{+} \subseteq F^{A}$.

## 1. Dimostrazione $F^{A} \subseteq F^{+}$

Si può procedere per [[induzione]], incrementando di 1 a ogni passo il numero di applicazioni di assiomi di Armstrong.

- Caso base $i=0$:   $f \in F^{A(0)} \implies f \in F \quad F \subset F^{+}$
- Ipotesi induttiva $i-1$:   $f \in F^{A(i-1)} \implies f \in F^{+}$ (assumiamo che tutte le dipendenze $f$ prodotte nel passo $i-1$ e nei passi precedenti sono soddisfatte da ogni istanza legale)
- Passo induttivo: se applichiamo qualsiasi assioma tra i 3, dobbiamo produrre un'istanza legale. Il passo induttivo si triforca, perché dobbiamo applicare a ripetizione gli altri 3 assiomi:

	1. $X \to Y$ per **riflessività** $\implies Y \subseteq X \quad \forall r\ \text{legale}\ \forall t_{1}[X]=t_{2}[X] \implies t_{1}[Y] = t_{2}[Y]$
	2. $X \to Y \in F^{A(i)}$ per **aumento** $\implies \exists V \to W \in F^{A(i-1)} \land Z \subset R \mid X = VZ \land Y = WZ$. $XW \to YW \quad \forall r\ \text{legale} \quad t_{1}[V]=t_{2}[V] \implies t_{1}[XW]=t_{2}[XW] \implies t_{1}[X]t_{1}[W] = t_{2}[X]t_{2}[W]$. $r\ \text{legale} \implies t_{1}[X] = t_{2}[X] \implies t_{1}[Y]=t_{2}[Y]$. $t_{1}[Y]t_{1}[W] = t_{2}[Y]t_{2}[W] \implies t_{1}[YW] = t_{2}[YW] \implies t_{1}[Z] = t_{2}[Z],\ (V \to Z) \in F^{+}$
	3. $X \to Y \in F^{A(i)}$ per **transitività** $\implies \exists (X \to Z) \in F^{A(i-1)} \land (Z \to Y) \in F^{A(i-1)}$. $\forall r\ \text{legale}\ t_{1}[X]=t_{2}[X] \implies t_{1}[Z]=t_{2}[Z] \implies t_{1}[Y]=t_{2}[Y]$ per ipotesi induttiva.

Abbiamo dimostrato che $F^{A} \subseteq F^{+}$.

## 2. Dimostrazione $F^{+} \subseteq F^{A}$

$X \to Y \in F^{+} \implies X \to Y \in F^{A}$

$X\to Y \in F^{+}$ è soddisfatta da ogni istanza legale.

Scelgo una istanza legale **ad hoc** senza perdita di generalità, perché è la dipendenza $X \to Y \in F^{+}$ a essere generica.


|       | $X^{+}$ (Chiusura di $X$) | $R-X^{+}$ (Attributi rimanenti) |
| ----- | ------------------------- | ------------------------------- |
| $t_1$ | 1 1 1 1 1 1 ...           | 1 1 1 1 1 1 ...                 |
| $t_2$ | 1 1 1 1 1 1 ...           | 0 0 0 0 0 0 ...                 |
1 = uguali
0 = diversi

Quest'istanza è legale? Cioè rispetta tutte le dipendenze in $F$?

Se soddisfa qualunque $V \to W \in F$ allora è legale.

- $t_{1}[V] = t_{2}[V] \implies$ dipendenza soddisfatta (dimostrazione classica)
	- Dimostrazione: $t_{1}[V] = t_{2}[V] \implies V \subseteq X^{+} \implies X \to V \in F^{A} \land V \to W \in F^{A} \underset{\text{transitività}}{\implies} X \to W \in F^{A}$
	  $\underset{\text{lemma 1}}{\implies} W \subseteq X^{+} \implies t_{1}[W]=t_{2}[W]$, quindi la dipendenza è soddisfatta.
	  Se l'istanza è legale $\land\ X \to Y \in F^{+} \implies X \to Y \in F^{+}$ è soddisfatta.
	  **Se** $t_{1}[X] = t_{2}[X]$ allora $t_{1}[y] = t_{2}[y]$: ciò è vero per il lemma 1 e per la riflessività, visto che $Y \in X^{+}$: $X \to Y \in F^{A}$.

- $t_{1}[V] \neq t_{2}[V] \implies$ dipendenza soddisfatta (dimostrazione per assurdo)
