---
updated_at: 2025-11-23T18:22:53.508+01:00
---
> Uno [[tabella|schema di relazione]] $R$ si può *decomporre* in più schemi, ognuno un [[sottoinsiemi|sottoinsieme]] degli attributi di $R$ su cui valgono le [[dipendenza funzionale|dipendenze funzionali]] ereditate da $R$, rilevanti per i suoi attributi. Ciò equivale a [[proiezione|proiettare]] ogni tupla dell'istanza originaria sugli attributi dei singoli sottoschemi.

Definizione formale:

> Una *decomposizione* di $R$ è una famiglia $\rho = \{R_{1}, \ldots, R_{K}\}$ di sottoinsiemi di $R$ che [[partizione|ricopre/partiziona]] $R$ ($\bigcup_{i=1}^{k} R_{i} = R$, i sottoinsiemi possono avere intersezione non vuota).

Gli schemi si decompongono

- per motivi di **performance** (le tuple di taglia più piccola aumentano la velocità e la capacità massima delle operazioni di lettura)
- o per raggruppare attributi semanticamente diversi, usati da **operazioni diverse**
- o per **ottenere** più schemi in [[3NF (terza forma normale)]] quando lo schema originale non è in 3NF.

Anche se uno schema è stato decomposto in più schemi in 3NF, **non è detto che la decomposizione è soddisfacente**, infatti ad esempio $R = ABC,\ F = \{A\to B, B \to C\}$, decomposto e poi ricomposto tramite il [[join naturale]] tra sue decomposizioni, non conserva $B \to C$.

```
R1 = A  B     R2 = A  C     R = A  B  C
     a1 b1         a1 c1        a1 b1 c1
     a2 b1         a2 c2        a2 b1 c2
```

# Criteri per distinguere una buona decomposizione da una svantaggiosa

1. Ogni sottoschema deve **essere in 3NF**.
2. La decomposizione deve **preservare tutte le dipendenze in $F^{+}$**, anche quelle [[dipendenza parziale|parziali]] e [[dipendenza transitiva|transitive]].
3. la decomposizione deve permettere di ricostruire **ogni** istanza legale **senza perdita di informazione** (ricostruzione mediante join senza perdita), che contro-intuitivamente può anche significare un'**aggiunta** di tuple sbagliate ("tuple Frankenstein" ottenute da pezzi di tuple giuste).

# Criterio 1: determinare se ogni sottoschema è in 3NF

Basta [[algoritmo per il calcolo delle chiavi|calcolare le chiavi]] di ogni sottoschema per controllare che ognuno sia in 3NF.

# Criterio 2: applicare l'[[algoritmo]] per determinare se la decomposizione preserva tutte le dipendenze

Sia $\rho = \{R_{1}, \ldots, R_{k}\}$ una decomposizione dello schema $R$, sul quale valgono le dipendenze funzionali $F$. Diciamo che $\rho$ **preserva** $F$ se

$$
F \equiv \bigcup_{i = 1}^{k} \pi_{R_{i}}(F)
$$

Dove $\pi_{R_{i}}(F) = \{X \to Y: X \to Y \in F^{+} \land XY \subseteq R_{i}\}$, cioè l'insieme delle dipendenze funzionali, anche quelle calcolate con gli [[chiusura di Armstrong|assiomi di Armstrong]], che valgono nello schema $R_{i}$ (che è il risultato della proiezione di $F$ su $R_{i}$).

Chiamiamo $G$ il risultato di $\bigcup_{i = 1}^{k} \pi_{R_{i}}(F)$. Per verificare $F \equiv G$, dobbiamo dimostrare che $F^{+} = G^{+}$, quindi $F^{+} \subseteq G^{+} \land G^{+} \subseteq F^{+}$.

Per **come abbiamo definito** $G$, sicuramente varrà **sempre** $G \subseteq F^{+}$, quindi per il *lemma delle chiusure* (vedi sotto) varrà $G^{+} \subseteq F^{+}$.

> Manca solo di verificare se nel caso specifico considerato vale $F^{+} \subseteq G^{+}$, quindi se $F \subseteq G^{+}$ (lemma delle chiusure): l'algoritmo controlla solo questo.

## Lemma delle chiusure: $X \subseteq Y^{+} \implies X^{+} \subseteq Y^{+}$

Questo lemma ci permette di verificare l'equivalenza tra $F^{+}$ e $G^{+}$ in [[complessità temporale|tempo polinomiale]], senza dover calcolare chiusure.

### Dimostrazione

Ipotesi: $F \subseteq G^{+}$

Tesi: $F^{+} \subseteq G^{+}$

Sia $f \in F^{+}-F$ ($f \notin F^{+}$).

1. Ogni dipendenza funzionale in $F$ può essere derivata da $G$ con gli assiomi di Armstrong da $G$ per ipotesi e perché $F^{+} = F^{A}$.
2. $f$ è derivabile con gli assiomi di Armstrong da $F$ perché $F^{+} = F^{A}$.
3. se $f$ è derivabile da $F$ e ogni dipendenza in $F$ può essere derivata da $G$, allora $f$ è derivabile da $G$ con gli assiomi di Armstrong, quindi $F^{+} \subseteq G^{+}$.

## Algoritmo $F \subseteq G^{+}$

**Input**: Gli insiemi di dipendenze funzionali $F$ e $G$ su $R$.

**Output**: La variabile booleana `successo`, vera se $F \subseteq G^{+}$.

1. `successo` := true
2. for $X \to Y$ in $F$:
	1. calcola $X^{+}_{G}$
	2. if $Y \not\subset X^{+}_{G}$: `successo` := false
3. return `successo`

> Cioè basta verificare che una sola dipendenza non appartiene a $G^{+}$ per dire che $F \not\subseteq G^{+} \implies F \not\equiv G$.

## Come calcolare $X_{G}^{+}$ nello step 2.1 dell'algoritmo sopra?

Se volessimo usare l'[[algoritmo per il calcolo della chiusura di un insieme di attributi]], dovremmo prima calcolare $G$, che per definizione richiede il calcolo di $F^{+}$, ma ciò richiede tempo esponenziale; però esiste un altro algoritmo per il calcolo di $X^{+}_{G}$ da $F$.

**Input**: uno schema $R$, un insieme di dipendenze $F$ su $R$, una decomposizione $\rho = \{R_{1}, \ldots, R_{k}\}$, un sottoinsieme $X \subseteq R$.

**Output**: $X^{+}_{G}$ salvata nella variabile $Z$.

1. $Z := X$
2. $S := \emptyset$
3. for $i:=1$ to $k$:
	1. $S := S \cup ((Z \cap R_{i})^{+}_{F} \cap R_{i})$
	   calcolare questa chiusura $((Z \cap R_{i})^{+}_{F}$ non richiede tempo esponenziale, perché si calcola direttamente sull'insieme delle dipendenze funzionali di $R_{i}$, che è molto più piccolo di $F$ completo.
	2. while $S \not\subset Z$:
		1. $Z := Z \cup S$
		2. for $i := 1$ to $k$
		3. $S := S \cup ((Z \cap R_{i})^{+}_{F} \cap R_{i})$
4. return $Z$

### Dimostrazione della validità dell'algoritmo

#todo pag. 22 pdf 13

# Criterio 3: applicare l'algoritmo per determinare se ogni istanza legale è ricostruibile tramite join naturale

Una decomposizione $\rho = \{R_{1}, \ldots, R_{k}\}$ di $R$ ha un *join senza perdita* se $\forall r\ \text{legale}\ (r = \pi_{R1}(r) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{RK}(r))$.

> Per aiutarci nella dimostrazione, definiamo l'operatore unario $m_{\rho}()$ che agisce su un'istanza $r$ di $R$.

$$
m_{\rho}(r) = \pi_{R1}(r) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{RK}(r)
$$

Osserviamo che gode delle seguenti proprietà:

1. $r \subseteq m_{\rho}(r)$
2. $\pi_{Ri}(m_{\rho}(r)) = \pi_{Ri}(r)$
3. $m_{\rho}(m_{\rho}(r)) = m_{\rho}(r)$

#todo pag 13 pdf 15