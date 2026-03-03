---
updated_at: 2026-03-03T15:02:25.855+01:00
---
> Un **protocollo** definisce le regole del **formato** e il significato dei **pacchetti** della comunicazione tra un mittente, un destinatario e tutti i sistemi intermedi.

# Layering

> In situazioni molto semplici si usa un solo protocollo, mentre per altre più complesse si dividono i compiti tra più livelli, ognuno con il suo protocollo: si parla quindi di **layering di protocolli**.

- [[servizio]]
- [[layer interface]]

Un esempio di layering di protocolli è una comunicazione cifrata per posta, dove c'è un protocollo per gestire il testo in chiaro, uno per gestire il testo cifrato e un altro per le lettere inviate per posta. Ogni livello può quindi gestire **lo stesso tipo di dati bidirezionalmente**: ad esempio il livello del testo cifrato può sia cifrare che decifrare.

Ogni livello può essere considerato come una black box **facilmente sostituibile**, perché il layering dei protocolli per natura è **modulare** e separa servizi e implementazione.