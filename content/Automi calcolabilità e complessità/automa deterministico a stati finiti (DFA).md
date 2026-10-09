---
updated_at: 2026-10-09T10:46:43.890+02:00
---
> Gli **automi a stati finiti, o DFA** (*Deterministic Finite-state Automaton*) sono [[automa|macchine a stati finiti]] in grado di accettare o rifiutare stringhe date loro in input carattere per carettere. Sono usati per applicazioni come parser dei compilatori e riconoscimento dei pattern nei dati.

> Un [[automa]] **deterministico** è un'automa il cui prossimo stato è **noto** e **unico**. I DFA sono deterministici.

# Definizione formale

Un DFA è una quintupla $(Q, \Sigma, \delta, q_{0}, F)$ tale che:

- $Q$ è un [[insieme]] finito di stati;
- $\Sigma$ è un insieme finito dei simboli dell'alfabeto che compongono tutti gli input possibili;
- $\delta: Q \times \Sigma \to Q$ è la [[funzione]] di transizione;
- $q_{0}$ è lo stato iniziale.
- $F \subseteq Q$ è l'insieme degli stati finali (anche detti *di accettazione*);

> Per un DFA, **Riconoscere/accettare** una stringa vuol dire trovarsi in uno stato finale al termine dell'esecuzione. **Rifiutare** una stringa vuol dire terminare l'esecuzione in uno stato non finale.

> Nonostante un DFA abbia un numero finito di stati, esso può processare stringhe di lunghezza **infinita** in tempo finito. Ad esempio, se si dà una stringa infinita $cabbb\ldots$ a un automa che riconosce le stringhe che iniziano con $ca$, l'automa accetterà la stringa appena riceverà $a$.

# A ogni DFA corrisponde un linguaggio

> Ogni DFA $M$ ***riconosce*** un [[linguaggio]] $A$ detto [[linguaggio regolare]]**, cioé l'insieme di tutte le stringhe che esso può accettare**.
> Formalmente, $A \subseteq \Sigma^{\star}$ (per esempio $\Sigma = \{0, 1\}^{\star}$, cioè tutte le stringhe binarie di lunghezza $\star$).

> "$M$ riconosce $A$" si scrive $L(M) = A$.

$$
U_{k \in \mathbb{N}}\ \{0, 1\}^{k} \equiv\ \text{tutte le stringhe binarie di}\ k \in \mathbb{N}\ \text{caratteri}
$$

- [[configurazione|Concetto di configurazione]]

# Esempi di automa

## 1.

![[Pasted image 20261009102047.png]]

- $Q = \{q_{1}, q_{2}, q_{3}\}$ è l'insieme di tutti gli stati
- $\Sigma = \{0, 1\}$ è l'alfabeto
- $\delta:$ sono le frecce nel diagramma
	- $\delta((q_{1}, 0)) = q_{1}$
	- $\delta((q_{1}, 1)) = q_{2}$
	- $\delta((q_{2}, 0)) = q_{3}$
	- $\delta((q_{2}, 1)) = q_{2}$
	- $\delta((q_{3}, 0)) = q_{2}$
	- $\delta((q_{3}, 1)) = q_{2}$
- $F = \{q_{2}\}$ è lo stato finale
- $q_{0} = q_{1}$ è lo stato iniziale

> N.B.: Se si disegna un automa incompleto (per semplicità) che raggiunto un carattere non sa che fare, per convenzione allora quella stringa non è contenuta nel linguaggio.

Esempio di esecuzione con input $w = 1101$:

- $q_{1} \overset{1}{\to} q_{2}$
- $q_{2} \overset{1}{\to} q_{2}$
- $q_{2} \overset{0}{\to} q_{3}$
- $q_{3} \overset{1}{\to} q_{2}$

L'automa termina il processing in $q2$, che è lo stato finale, quindi la stringa $1101$ viene riconosciuta.

# 2. progettare un DFA che accetta solo le stringhe che iniziano con "1"

$$
L = \{x \in \{0, 1\}^{\star}:\ x = 1y,\ y \in \{0, 1\}^{\star}\}
$$

![[Pasted image 20261009102318.png|505]]

$q_{1}$ è lo stato finale.

> N.B.: Per far rifiutare la stringa, bisogna far andare l'automa in loop su un vicolo cieco, detto *stato pozzo*.

### Correttezza

Bisogna dimostrare entrambe le tesi:

1. $x \in L \implies M(\text{accetta})$
2. $x \notin L \implies M(\text{rifiuta})$

Si può dimostrare sia per induzione che con $\delta^{\star}$, ma è scontato e noioso.

## 3. Esercizio per casa

$$
L = \{x \in \{0, 1\}^{\star}: \#_{1}(x) \geq 3\}
$$

![[automa 2.png]]