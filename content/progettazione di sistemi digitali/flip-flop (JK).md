*J e K sono etichette arbitrarie per i due input del flip-flop*

> Un flip-flop JK differisce da un [[flip-flop set-reset (SR)]] solamente dal fatto che quando i due input sono a 1, lo stato in uscita del flip-flop è il complemento dello stato memorizzato l'istante precedente.

![[flip-flop JK.png]]

*(immagine da [engineeringbyte.com](https://www.engineeringbyte.com/verify-truth-table-of-jk-flip-flop-7476-experiment))*
# funzionamento

- J (set) è abilitato solo quando lo stato è 0 e il clock è attivo.
- K (reset) è abilitato solo quando lo stato è 1 e il clock è attivo.

| J   | K   | y(t+1)            |
| --- | --- | ----------------- |
| 0   | 0   | $y(t)$            |
| 0   | 1   | 0                 |
| 1   | 0   | 1                 |
| 1   | 1   | $\overline{y(t)}$ |

# tabella inversa
| $y, Y$ | $j, k$ (+ ragionamento)                                                      |
| ------ | ---------------------------------------------------------------------------- |
| 00     | 0 $\delta$ (se si passa da 0 a 0 o si memorizza 0 o si resetta)              |
| 01     | 1 $\delta$ (se si passa da 0 a 1 o si resetta o le entrate erano entrambe 0) |
| 10     | $\delta$ 0 (se si passa da 1 a 0 o si setta o le entrate erano entrambe 1)   |
| 11     | $\delta$ 1 (se si passa da 1 a 1 o si memorizza 1 o si resetta)              |
