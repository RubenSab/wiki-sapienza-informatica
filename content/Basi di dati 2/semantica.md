---
updated_at: 2026-03-30T10:37:51.061+02:00
---
# Esempio di formula

Siano $\mathcal{F}, \mathcal{P}, \mathcal{V}$:

$$
\mathcal{F} = \{\text{zero}/0,\text{uno}/0,\text{triplo}/2\}
$$

$$
\mathcal{P} = \{\text{è pari}/1,\text{è doppio}/2,\neq/2,>/2\}
$$

$$
\mathcal{V} = \{X, Y\}
$$

E sia $\varphi$ la formula:

$$
\varphi: \forall X\ (X \neq \text{zero} \land \text{pari}(X)) \Longleftrightarrow \exists Y\ \text{è doppio}(Y, X) \land Y > \text{zero} \land \text{triplo}(X) > \text{zero}
$$

# Valutazione delle formule

Come facciamo a valutare $\varphi$? Cioè come troviamo una funzione $\text{eval}(\varphi) = T/\bot$ che valuti $\varphi$?

Ci serve un'**interpretazione**, definita in più passaggi:

1. **Pre-interpretazione**:
	- **Dominio**: un insieme di valori di interesse per **tutti** i termini, ad esempio $D = \{0, 1, 2, \dots\}$.
	- **Assegnamento delle variabili**: una funzione $I: \mathcal{V} \to \mathcal{D}$ ad esempio $I(X) = 3,\ I(Y) = 58$.
	- **Significato dei simboli di costante**: $I: \mathcal{F} \to \mathcal{D}$ ad esempio $I(\text{zero}) = 0,\ I(\text{uno}) = 1$.
2.  **Interpretazione**:
	- **Significato dei simboli di funzione**: $I: \mathcal{D} \to \mathcal{D}$ per funzioni di arità 1. Più in n generale per ogni funzione $f/k$ vale che $I: D^{k} \to D$.
	  Ad esempio $I(\text{triplo}) = \text{la funzione che a ogni elemento del dominio associa esso per tre}$.
	- **Significato dei simboli di predicato**: $I(p/k)\subseteq D^{k}$ (come le [[relazione|relazioni]]) ad esempio $I(\text{pari}) = \{0, 2, 4, \dots\}$ e $I(\text{doppio}) = \{(0, 0),\ (2, 1),\ (4, 2),\ \dots\}$.
	  Nota: l'interpretazione di $=, \neq, >, <, \geq, \leq$ si può omettere perché è standard.
3. **Valutazione dei termini**:
	- Funzione di pre-valutazione che valuta i termini:
	  *pre-eval*(termine) = elemento di $\mathcal{D}$.
	- Valutazione delle formule:
	  $\text{eval}(\varphi) = V/F$.
	  I quantificatori funzionano nel modo seguente:
		- $\text{eval}(\forall X\ \varphi) = V$ se per ogni $d \in D$ vale $\text{eval}^{I[X/d]}(\varphi) = V$.
		- $\text{eval}(\exists X\ \varphi) = V$ se esiste $d \in D$ vale $\text{eval}^{I[X/d]}(\varphi) = V$.


> Nota sui quantificatori: una formula ambigua senza parentesi come $\forall X\ \text{uomo}(X) \implies \exists Y\ \text{mortale}(X)$ contro-intuitivamente significa $\forall X\ (\text{uomo}(X) \implies \exists Y\ (\text{mortale}(X)))$, in base alla definizione di **formula quantificata** come $\forall/ \exists\ X \varphi$.

## Applicazione alla formula dell'esempio

$$
\varphi: \forall X\ (X \neq \text{zero} \land \text{pari}(X)) \iff \exists Y\ \text{è doppio}(Y, X) \land Y > \text{zero} \land \text{triplo}(X) > \text{zero}
$$

- $X = 0$:
	- $0 \neq 0 \land \text{pari}(0) \iff \exists Y\ \text{è doppio}(Y, 0) \land Y > 0 \land \text{triplo}(0) > 0$
	- $Y = 0$ (ciclo annidato):
		- $F \iff \text{è doppio}(0, 0) \land 0 > 0 \land \text{triplo}(0) > 0)$
		- $F \iff T \land F \land T$
		- $F \iff F$
		- $V$ ($\text{eval}(\phi) = V$ per l'interpretazione $X = 0,\ Y = 0$)
	- $Y = 1$
		- ...

Questo è un esempio della **non calcolabilità** della funzione $\text{eval}$ , perché consiste di un ciclo (eventualmente annidato) infinito.

Però la formula è evidentemente vera. 🤡🤡🤡🤡🤡🤡🤡🤡🤡🤡🤡🤡