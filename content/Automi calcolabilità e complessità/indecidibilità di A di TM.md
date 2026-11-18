---
updated_at: 2026-11-18T09:09:31.100+01:00
---
> Teorema: $A_\text{TM}$ è indecidibile.

Dimostrazione: supponiamo per assurdo che $A_{\text{TM}}$ sia decidibile, cioè che esiste una [[macchina di Turing (TM)]] decisore $H$ che decide $A_{\text{TM}}$.

$$
H(\langle M,w\rangle) = \begin{cases} \text{accetta se}\ M(w) = \text{ACC} \\ \text{rifiuta altrimenti}\end{cases}
$$

($M$ è una qualsiasi TM)

Consideriamo un'altra $TM$ decisore che chiamiamo $D$:

- Su input $\langle M \rangle$ esegue $H$ su $\langle H, w = \langle M \rangle \rangle$ (riceve la codifica di se stessa come input).
- Se $H$ accetta rifiuto, altrimenti accetto.

Ora usiamo la tecnica della ***diagonalizzazione***: consideriamo una matrice infinita che associa ogni possibile TM $M_{n}$ e la sua codifica $\langle M_{n} \rangle$ al **comportamento** di $M_{n}$ in caso riceva $\langle M_{n} \rangle$ in input.

![[Pasted image 20261118085932.png]]

In questa matrice, ovviamente apparirà anche $D$, il cui comportamento è:

$$
D(\langle M\rangle) = \begin{cases} \text{accetta} \iff H\ \text{rifiuta}\ \langle M, \langle M \rangle \rangle \iff M\ \text{rifiuta}\ \langle M \rangle \\ \text{rifiuta} \iff H\ \text{accetta}\ \langle M, \langle M \rangle \rangle \iff M\ \text{accetta}\ \langle M \rangle\end{cases}
$$

e siccome $H$ è un decisore, anche $D$ lo è.

$$
D(\langle D \rangle) = \begin{cases} \text{accetta} \iff H\ \text{rifiuta}\ \langle D, \langle D \rangle \rangle \iff D\ \text{rifiuta}\ \langle D \rangle \\ \text{rifiuta} \iff H\ \text{accetta}\ \langle D, \langle D \rangle \rangle \iff D\ \text{accetta}\ \langle D \rangle\end{cases}
$$

Questa è una contraddizione, quindi $A_\text{TM}$ non è riconoscibile.