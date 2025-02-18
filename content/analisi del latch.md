#todo
## analisi del latch #AI
Un **latch** è un **elemento di memoria**: può **memorizzare un valore** finché non viene modificato dagli ingressi di **Set (S) e Reset (R)**. L’analisi serve a **capire come si evolve l’uscita nel tempo** rispetto agli ingressi.

Il metodo di **tagliare la linea di feedback** aiuta a trattare il latch **come una rete combinatoria** in un singolo istante, semplificando lo studio del suo comportamento.

Normalmente, un latch ha un ciclo di feedback, cioè un'uscita che ritorna come ingresso. Questo rende difficile analizzarlo direttamente.
L’idea è **sostituire l’uscita vecchia con una variabile temporanea** e poi esprimere la nuova uscita in funzione degli ingressi e della vecchia uscita.

In pratica, stiamo **scomponendo il funzionamento del latch passo dopo passo** invece di osservarlo come un sistema che cambia continuamente.

Si taglia la [[reti sequenziali|linea di feedback]]:

![[latch_tagliato.svg]]
1. **Scrivi l’equazione della nuova uscita BBB in termini della vecchia uscita $y_{\text{vecchia}}$ e degli ingressi.**

- Se il latch ha un NOR o NAND, usa la formula corrispondente.

2. **Usa De Morgan e semplifica l’equazione per esprimere $y_{\text{nuova}}$ in funzione degli ingressi.**

3. **Studia caso per caso (tabelle di verità parziali):**

- **Quando il reset è attivo?** → L'uscita deve diventare 0.
- **Quando il set è attivo?** → L'uscita deve diventare 1.
- **Quando entrambi sono 0?** → L'uscita deve mantenere il valore precedente.

4. **Verifica che il comportamento corrisponda a un latch (memorizzazione di stato).**