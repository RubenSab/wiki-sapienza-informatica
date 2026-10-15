---
updated_at: 2026-10-15T15:45:54.424+02:00
---
> È la regola di valutazione "pigra" che consiste nel ritardare la valutazione delle [[espressione|espressioni]] finché il loro valore non sia necessario per la valutazione di un'altra espressione.

Nella *semantica operazionale lazy* anche detta *call by **name*** o *call by need*, l'**ambiente** è una mappatura tra i nomi delle variabili e **espressioni** (anche dette [[chiusura|chiusure]]) corrispondenti, valutate solo nel momento della loro chiamata.

# Lazy dinamico

Nel lazy con [[scoping dinamico]] l'ambiente conserva solo le espressioni sintattiche pure, **senza** conservare anche l'ambiente in cui sono state definite, in quanto **le espressioni vengono risolte nell'ambiente in cui sono valutate, non nell'ambiente dove sono state scritte originariamente**.


$$
\text{Env} \ni E:\ \text{Var} \overset{\text{fin}}{\to}\text{Val} \cup \text{Exp}
$$

# Lazy statico

Il lazy con [[scoping statico]] **equivale semanticamente con la [[valutazione eager]] in linguaggi semplici** senza loop infiniti. Per mantenere vera questa uguaglianza, nello scoping statico ogni espressione in un'ambiente è mappata a una coppia (variabile, ambiente in cui la variabile è stata definita originariamente).

$$
\text{Env} \ni E:\ \text{Var} \to \text{Exp} \times \text{Env}
$$
---
#todo 

  #### Come cambiano le regole nel Lazy Statico:

L'ambiente mappa le variabili a coppie formate dall'espressione e dall'ambiente in cui è stata definita: $\text{Var} \to \text{Exp} \times \text{Env}$.

  

La regola del `let` in ambiente lazy statico cattura l'espressione insieme al suo ambiente $E$:

  

$$\frac{E[x \mapsto \langle M, E \rangle] \vdash N \to v}{E \vdash \text{let}\ x = M\ \text{in}\ N \to v}$$

Quando la variabile $x$ viene valutata, si estrae la chiusura $\langle M, E_m \rangle$ dall'ambiente e si valuta l'espressione $M$ nel suo ambiente originario $E_m$:

  

$$\frac{E_m \vdash M \to v}{E \vdash x \to v}\quad (\text{se } E(x) = \langle M, E_m \rangle)$$

> **Teorema di Corrispondenza:** Sotto opportune ipotesi, la semantica _Lazy Statica_ risulta equivalente alla semantica _Eager_ ($\text{Lazy Statico} = \text{Eager}$ in termini di risultati), pur differendo nell'ordine e nel numero di valutazioni (la lazy valuta solo ciò che serve ed al momento opportuno).
> 
>   

# 4. Casi Studio ed Esempi di Valutazione

### Esempio 1: Ambiguità sintattica

- `let x = 3 in x+1` $\to$ Non è ambiguo poiché l'operatore $+$ è associativo e la struttura sintattica standard lega il `let` verso destra.
    
      
    
- `let x = 3 in let x = 2 in x+x` $\to$ **Ambiguo**, poiché la precedenza strutturale non specifica se debba essere inteso come:
    
      
    1. `let x = 3 in (let x = 2 in x) + x`
        
          
        
    2. `let x = 3 in (let x = 2 in (x + x))`
        
          
        

### Esempio 2: L'espressione `let x = (let x = x in x) in 3`

- **Scoping Statico:** Genera un errore (la variabile $x$ interna non è definita o vi è unuso non valido).
    
      
    
- **Scoping Dinamico:** Sintatticamente viene accettato, ma durante la valutazione va in **loop infinito** (cattura ricorsivamente se stessa).
    
      
    - Con valutazione **Lazy**: Restituisce `3`, perché l'espressione interna legata a $x$ non viene mai valutata (essendo il corpo del `let` principale semplicemente la costante `3`).
        
          
        
    - Con valutazione **Eager**: Tenta di valutare subito l'argomento del `let` esterno, entrando in un **loop infinito**.
        
          
        

# 5. Esercizio: Equivalenza Logica

**Confronto tra:**

  

1. `let x = (let y = M in N) in L`
    
      
    
2. `let y = M in (let x = N in L)`
    
      
    

- **Sono logicamente equivalenti?**
    
    Non sempre in modo generale. $L$ si trova nello scope di $y$ nella seconda forma, mentre nella prima $y$ è confinato all'interno di $N$ e non è visibile in $L$ (a meno che $L$ non contenga a sua volta legami o conflitti). Se $L$ utilizza la variabile $y$, la prima forma fallisce o fa riferimento a un $y$ esterno (libero), mentre la seconda lega correttamente $y$ tramite il `let` più esterno. Dunque, i due termini non sono equivalenti a meno che $L$ non contenga variabili libere $y$ dipendenti da quel legame.