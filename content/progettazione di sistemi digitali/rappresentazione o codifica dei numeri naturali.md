---
updated_at: 2025-03-04T12:46:17.769+01:00
---
$\Sigma = \{0, 1\}$ (esempio di alfabeto di codifica).

> Ogni informazione è suddivisa in registri di 32, 64 o n_bit: un valore prefissato che indica il massimo di bit disponibili per comporla.

Questo limita il numero di informazioni possibili che un registro può codificare.

>**ESEMPIO**:
>Dobbiamo comporre una stringa con solo 3 simboli. Quante stringhe possiamo comporre?
>Dipende dalla [[cardinalità (o potenza)]] dell'alfabeto di [[funzioni di codifica e decodifica|codifica]], ad esempio se abbiamo l'alfabeto binario (Σ = {0, 1}) ne possiamo comporre $2^3$, mentre se usiamo l'alfabeto italiano (Σ = {a, b, ..., z}) ne possiamo comporre $21^3$.
>Nel primo caso, dato che il registro usa 3 bit, possiamo rappresentare solo $2^3$ informazioni diverse (in cui dobbiamo comporre/$scomporre tutto il flusso di informazioni).

Il modo naturale di codificare i [[numeri naturali]] in [[sistema binario]], è contando usando l'ordine posizionale, proprio dei [[sistemi numerici posizionali]].