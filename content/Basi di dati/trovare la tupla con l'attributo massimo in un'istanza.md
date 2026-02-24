---
updated_at: 2026-01-26T18:16:02.227+01:00
---
<iframe src="https://stackoverflow.com/a/7882306" style="width: 100%; height: 500px; zoom: 90%"></iframe>

L'idea di base è che un attributo di una tupla ha valore massimo se non esiste un'altra tupla con lo stesso attributo dal valore maggiore, quindi bisogna eliminare tutte le tuple che hanno un'altra dal valore maggiore di loro.

# Esempio: [[relazione]] $A$

| nome    | a   |
| ------- | --- |
| Luca    | 1   |
| Marco   | 3   |
| Roberto | 2   |

## 1. Ridenominazione

$$
A_{1} = \rho_{\text{nome} \to \text{nome1},\ a \to a1}(A)
$$
$$
A_{2} = \rho_{\text{nome} \to \text{nome2},\ a \to a2}(A)
$$

| nome1   | a1  |
| ------- | --- |
| Luca    | 1   |
| Marco   | 3   |
| Roberto | 2   |

| nome2   | a2  |
| ------- | --- |
| Luca    | 1   |
| Marco   | 3   |
| Roberto | 2   |

## 2. Trovare le tuple NON massime

$$
B = \sigma_{a1 < a2}(A1 \times A2)
$$

| nome1   | a1  | nome2   | a2  |
| ------- | --- | ------- | --- |
| Luca    | 1   | Marco   | 3   |
| Luca    | 1   | Roberto | 2   |
| Roberto | 2   | Marco   | 3   |

$$
B = \pi_{\text{nome1, a1}}(B)
$$
| nome1   | a1  |
| ------- | --- |
| Luca    | 1   |
| Luca    | 1   |
| Roberto | 2   |

# 3. Ricavare le tuple massime

$$
A - B
$$
| nome    | a   |
| ------- | --- |
| Marco   | 3   |
