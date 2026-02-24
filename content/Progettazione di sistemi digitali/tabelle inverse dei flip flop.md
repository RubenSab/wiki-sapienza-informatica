# [[flip-flop set-reset (SR)]] e [[flip-flop SR master-slave]]

| $y, Y$ | $s, r$ (+ ragionamento)                                               |
| ------ | --------------------------------------------------------------------- |
| 00     | 0 $\delta$ (se si passa da 0 a 0 o si memorizza 0 o si resetta)       |
| 01     | 10 (funzione di set)                                                  |
| 10     | 01 (funzione di reset)                                                |
| 11     | $\delta$ 0 (se si passa da 1 a 1 o si memorizza 1 o non si fa niente) |
# [[flip-flop (JK)]]

| $y, Y$ | $j, k$ (+ ragionamento)                                                      |
| ------ | ---------------------------------------------------------------------------- |
| 00     | 0 $\delta$ (se si passa da 0 a 0 o si memorizza 0 o si resetta)              |
| 01     | 1 $\delta$ (se si passa da 0 a 1 o si resetta o le entrate erano entrambe 0) |
| 10     | $\delta$ 0 (se si passa da 1 a 0 o si setta o le entrate erano entrambe 1)   |
| 11     | $\delta$ 1 (se si passa da 1 a 1 o si memorizza 1 o si resetta)              |

# [[flip-flop delay (D)]]

| $y, Y$ | $d$ |
| ------ | --- |
| 00     | 0   |
| 01     | 1   |
| 10     | 0   |
| 11     | 1   |
# [[flip-flop toggle (T)]]

| $y, Y$ | $d$ |
| ------ | --- |
| 00     | 0   |
| 01     | 1   |
| 10     | 1   |
| 11     | 0   |