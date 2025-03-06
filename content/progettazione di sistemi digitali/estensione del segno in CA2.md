---
updated_at: 2025-03-04T12:50:31.692+01:00
---
Si usa per rappresentare su più bit un valore in [[complemento a 2 (CA2)]].

- Se il bit più significativo è 0, allora a sinistra si aggiungono degli 0, altrimenti si aggiungono degli 1.

```
Esempio:
-3 = 1101
estendiamo la lunghezza del registro di 2 bit
1101 -> 111101

si può verificare che in CA2:
1101 = -2^3 + 2^2 + 2^0 = -3
111101 = -2^5 (MSB) + 2^4 + 2^3 + 2^2 + 2^0 = -3

```