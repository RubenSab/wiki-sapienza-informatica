---
updated_at: 2025-10-23T17:22:37.037+02:00
---
> L'insieme di [[dipendenza funzionale|dipendenze funzionali]] $F^{A}$ è definito nel modo seguente, con gli *assiomi di Armstrong*:

- se $f \in F$ allora $f \in F^{A}$
- **assioma della [[proprietà, tipi di relazioni e ordini|riflessività]]**: se $Y \subseteq X \subseteq R$ allora $(X \to Y) \in F^{A}$
- **assioma dell'aumento**: se $(X \to Y) \in F^{A}$ allora $\forall Z \subseteq R\ ((XZ \to YZ) \in F^{A})$
- **assioma della transitività**: se $(X \to Y) \in F^{A} \land (Y \to \mathbb{Z} \in F^{A})$ allora $(X \to Z) \in F^{A}$

Dimostreremo che $F^{+} = F^{A}$, cioè che la chiusura di un insieme di dipendenze funzionali $F$ può essere ottenuta a partire da $F$ applicando ricorsivamente gli assiomi di Armstrong.

#todo

- regola dell'unione
- della decomposizione
- pseudotransitività


- [[chiusura di un insieme di attributi]]

# Dimostrazione $F^{+} = F^{A}$

Per dimostrare che $F^{A} = F^{+}$ bisogna verificare $F^{A} \subseteq F^{+} \land F^{+} \subseteq F^{A}$

Si può procedere per [[induzione]], incrementando di 1 a ogni passo il numero di applicazioni di assiomi di Armstrong.

Caso base: $i=0 \quad (X \to Y) \in F^{A} \quad (X \to Y) \in F \implies (X \to Y) \in F^{+} \quad F \subseteq F^{+}$

Ipotesi induttiva: $i-1 \quad (X \to Y) \in F^{A(i-1)} \quad (X \to Y) \in F^{+}$ è soddisfatta da ogni istanza legale.

Il passo induttivo si triforca, perché dobbiamo applicare a ripetizione gli altri 3 assiomi:

1. $V \to Z$ per riflessività $\implies \mathbb{Z} \subseteq V \quad \forall r\ \text{legale}\ \forall t_{1}[V]=t_{2}[V] \implies t_{1}[Z] = t_{2}[Z]$
2. $V \to Z$ per aumento $\implies \exists X \to Y \in F^{A(i-1)} \land W \subseteq R \mid V = XW \land \mathbb{Z} = YW$. $XW \to YW \quad \forall r\ \text{legale} \quad t_{1}[V]=t_{2}[V] \implies t_{1}[XW]=t_{2}[XW] \implies t_{1}[X]t_{1}[W] = t_{2}[X]t_{2}[W]$. $r\ \text{legale} \implies t_{1}[X] = t_{2}[X] \implies t_{1}[Y]=t_{2}[Y]$. $t_{1}[Y]t_{1}[W] = t_{2}[Y]t_{2}[W] \implies t_{1}[YW] = t_{2}[YW] \implies t_{1}[Z] = t_{2}[Z],\ (V \to Z) \in F^{+}$
3. $V \to Z$ per transitività $\implies \exists (V \to W) \in F^{A(i-1)} \land (W \to \mathbb{Z}) \in F^{A(i-1)}$. $\forall r\ \text{legale}\ t_{1}[V]=t_{2}[V] \implies t_{1}[W]=t_{2}[W]$ per ipotesi induttiva. $\implies t_{1}[Z]=t_{2}[Z] \implies V \to Z \in F^{+}$

Abbiamo dimostrato che $F^{A} \subseteq F^{+}$.

