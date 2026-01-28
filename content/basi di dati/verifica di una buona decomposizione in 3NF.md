---
updated_at: 2026-01-27T10:23:29.370+01:00
---
> Uno [[tabella|schema di relazione]] $R$ si può *decomporre* in più schemi, ognuno un [[sottoinsiemi|sottoinsieme]] degli attributi di $R$ su cui valgono le [[dipendenza funzionale|dipendenze funzionali]] ereditate da $R$, rilevanti per i suoi attributi. Ciò equivale a [[proiezione|proiettare]] ogni tupla dell'istanza originaria sugli attributi dei singoli sottoschemi.

Definizione formale:

> Una *decomposizione* di $R$ è una famiglia $\rho = \{R_{1}, \ldots, R_{K}\}$ di sottoinsiemi di $R$ che [[partizione|ricopre/partiziona]] $R$ ($\bigcup_{i=1}^{k} R_{i} = R$, ma i sottoinsiemi possono avere intersezione non vuota).

Gli schemi si decompongono

- per motivi di **performance** (le tuple di taglia più piccola aumentano la velocità e la capacità massima delle operazioni di lettura)
- o per raggruppare attributi semanticamente diversi, usati da **operazioni diverse**
- o per **ottenere** più schemi in [[3NF (terza forma normale)]] quando lo schema originale non è in 3NF.

> N.B.: È sempre possibile trovare una decomposizione in 3NF valida, ma non vale lo stesso per la forma normale di [[3NF (terza forma normale)#^2d0ddd|Boyce-Codd]].

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

Basta [[algoritmo per il calcolo delle chiavi|calcolare le chiavi]] di ogni sottoschema e vedere se **tutte** le dipendenze funzionali definite su di esso sono compatibili con la definizione di 3NF per controllare che ogni sottoschema sia in 3NF.

# Criterio 2: applicare l'[[algoritmo]] per determinare se la decomposizione preserva tutte le dipendenze

Sia $\rho = \{R_{1}, \ldots, R_{k}\}$ una decomposizione dello schema $R$, sul quale valgono le dipendenze funzionali $F$. Diciamo che $\rho$ **preserva** $F$ se

$$
F \equiv \bigcup_{i = 1}^{k} \pi_{R_{i}}(F)
$$

Dove $\pi_{R_{i}}(F) = \{X \to Y: X \to Y \in F^{+} \land XY \subseteq R_{i}\}$, cioè l'insieme delle dipendenze funzionali, anche quelle calcolate con gli [[chiusura di Armstrong|assiomi di Armstrong]], che valgono nello schema $R_{i}$ (che è il risultato della proiezione di $F$ su $R_{i}$).

> Praticamente, $G$ è una [[partizione]] di $F$.

Chiamiamo $G$ il risultato di $\bigcup_{i = 1}^{k} \pi_{R_{i}}(F)$. Per verificare $F \equiv G$, dobbiamo dimostrare che $F^{+} = G^{+}$, quindi $F^{+} \subseteq G^{+} \land G^{+} \subseteq F^{+}$.

> N.B.: Per **come abbiamo definito** $G$, sicuramente varrà **sempre** $G \subseteq F^{+}$, quindi per il *lemma delle chiusure* (vedi sotto) varrà $G^{+} \subseteq F^{+}$.

Manca solo di verificare se nel caso specifico considerato vale $F^{+} \subseteq G^{+}$, quindi se $F \subseteq G^{+}$ (lemma delle chiusure): l'algoritmo controlla solo questo.

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
	2. if $Y \not\subset X^{+}_{G}$: `successo` := `false`
3. return `successo`

> Cioè basta verificare che una sola dipendenza non appartiene a $G^{+}$ per dire che $F \not\subseteq G^{+} \implies F \not\equiv G$.

## Come calcolare $X_{G}^{+}$ dell'algoritmo sopra?

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
		2. for $j := 1$ to $k$:
			1. $S := S \cup ((Z \cap R_{j})^{+}_{F} \cap R_{j})$
4. return $Z$


### Dimostrazione della validità dell'algoritmo

#todo pag. 22 pdf 13

# Criterio 3: applicare l'algoritmo per determinare se ogni istanza legale è ricostruibile tramite join naturale

## Operatore $m_{\rho}(r)$

Una decomposizione $\rho = \{R_{1}, \ldots, R_{k}\}$ di $R$ ha un *join senza perdita* se $\forall r\ \text{legale}\ (r = \pi_{R_{1}}(r) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{R_{k}}(r))$.

> Per aiutarci nella dimostrazione, definiamo l'operatore unario $m_{\rho}()$ "m rho" che agisce su un'istanza $r$ di $R$.

$$
m_{\rho}(r) = \pi_{R_{1}}(r) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{R_{k}}(r)
$$

Osserviamo che gode delle seguenti proprietà:

1. $r \subseteq m_{\rho}(r)$
2. $\pi_{Ri}(m_{\rho}(r)) = \pi_{Ri}(r)$
3. $m_{\rho}(m_{\rho}(r)) = m_{\rho}(r)$

**Dimostrazione di 1**: Sia $t$ una tupla di $r$. $\forall i \in [1, k]\quad t[R_{i}] \in \pi_{R_{i}}(r)$, che è un sottoinsieme di $m_{\rho}(r)$, quindi $t \in m_{\rho}(r)$.

**Dimostrazione di 2**: $\pi_{Ri}(m_{\rho}(r)) = \pi_{Ri}(\pi_{R_{1}}(r) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{R_{k}}(r)) = \pi_{Ri}(r)$

**Dimostrazione di 3**: $m_{\rho}(m_{\rho}(r)) = \pi_{R_{1}}(m_{\rho}(r)) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{R_{k}}(m_{\rho}(r))$, ma per la proprietà 2 sappiamo che $\pi_{Ri}(m_{\rho}(r)) = \pi_{Ri}(r)$, quindi $m_{\rho}(m_{\rho}(r)) = \pi_{R_{1}}(r) \ \triangleright \! \! \triangleleft \ \ldots \ \triangleright \! \! \triangleleft \ \pi_{R_{k}}(r) = m_{\rho}(r)$ per definizione.

## Algoritmo per verificare se esiste un join senza perdita (tempo polinomiale)

**Input**: uno schema $R$, un insieme di dipendenze $F$ su $R$, una decomposizione $\rho = \{R_{1}, \ldots, R_{k}\}$ di $R$.

**Output**: Una booleana che indica se esiste o meno un join senza perdita.

1. Costruisci una tabella $r$ nel modo seguente: $r$ ha $|R|$ colonne e $|\rho|$ righe.
   all'incrocio dell'i-esima riga e della j-esima colonna metti il simbolo $a_{j}$ se l'attributo $A_{j} \in R_{i}$, altrimenti metti il simbolo $b_{ij}$.
2. (fase iterativa di modifica dell'istanza) for every $X \to Y \in F$:
	1. if ci sono due tuple $t_{1}$ e $t_{2}$ in $r$ tali che $t_{1}[X] = t_{2}[X]$ e $t_{1}[Y] \neq t_{2}[Y]$:
		1. for every $A_{j}$ in $Y$:
			1. if $t_{1}[A_{j}] = a_{j}$ then $t_{2}[A_{j}] := t_{1}[A_{j}]$
			   else $t_{1}[A_{j}] := t_{2}[A_{j}]$
			2. if $r$ ha una riga con tutte "a" o $r$ non è cambiato:
				1. return `true`
3. return `false`

> N.B.: $a_{j}$ e $b_{ij}$ sono solo etichette, valori particolari contenuti nel dominio dell'attributo $A_{j}$ e possiamo considerare tutti i valori $a_{j}$ uguali fra loro, ma ciò non vale per $b_{ij}$.

> N.B.: Nell'algoritmo diamo precedenza alle $a$, che non diventano **mai** $b$.

### Dimostrazione della validità dell'algoritmo

#todo pag 25 pdf 15
 
### Esempio

Si hanno:

- $R = (A, B, C, D, E)$
- $F = (C \to D, AB \to E, D \to B)$
- $\rho = \{AC, ADE, CDE, AD, B\}$

Determinare se $R$, così decomposto, ha un join senza perdita.

Costruzione iniziale della tabella:

|     | A      | B      | C      | D      | E      |
| --- | ------ | ------ | ------ | ------ | ------ |
| AC  | **a1** | b12    | **a3** | b14    | b15    |
| ADE | **a1** | b22    | b23    | **a4** | **a5** |
| CDE | b31    | b32    | **a3** | **a4** | **a5** |
| AD  | **a1** | b42    | b43    | **a4** | b45    |
| B   | b51    | **a2** | b53    | b54    | b55    |

#### Prima iterazione

 - $C \to D$: la prima e la terza riga coincidono sull'attributo a3, quindi cambiano b14 in a4 in modo che $C \to D$ sia soddisfatta (si cambiano sempre le b in a, **mai** il contrario).

|     | A      | B          | C      | D             | E      |
| --- | ------ | ---------- | ------ | ------------- | ------ |
| AC  | **a1** | b12        | **a3** | b14 -> **a4** | b15    |
| ADE | **a1** | b22 -> b12 | b23    | **a4**        | **a5** |
| CDE | b31    | b32 -> b12 | **a3** | **a4**        | **a5** |
| AD  | **a1** | b42 -> b12 | b43    | **a4**        | b45    |
| B   | b51    | **a2**     | b53    | b54           | b55    |
 - $AB \to E$: la dipendenza funzionale è già soddisfatta, in quanto non ci sono (ancora) tuple uguali su AB e diverse su E.
 - $D \to B$: nelle prime quattro righe D=a4, quindi cambiamo b22 in b12, b32 in b12,
b42 in b12 (potevano scegliere una diversa sostituzione delle b, purché le rendesse
tutte uguali)

#### Seconda iterazione

- $C \to D$ è già soddisfatta.
- $AB \to E$: sostituiamo b15 e b45 con a5

|     | A      | B          | C      | D             | E             |
| --- | ------ | ---------- | ------ | ------------- | ------------- |
| AC  | **a1** | b12        | **a3** | b14 -> **a4** | b15 -> **a5** |
| ADE | **a1** | b22 -> b12 | b23    | **a4**        | **a5**        |
| CDE | b31    | b32 -> b12 | **a3** | **a4**        | **a5**        |
| AD  | **a1** | b42 -> b12 | b43    | **a4**        | b45 -> **a5** |
| B   | b51    | **a2**     | b53    | b54           | b55           |

#### Terza iterazione

- $C \to D$ è già soddisfatta
- $AB \to E$ è già soddisfatta
- $D \to B$ è già soddisfatta

Non c'è una riga con tutte a, il join **non** è senza perdita.