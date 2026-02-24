---
updated_at: 2026-01-26T12:15:08.757+01:00
---
> È l'operazione binaria che consente di selezionare le tuple del [[prodotto cartesiano]] delle due [[relazione|relazioni]] che soddisfano una condizione del tipo $A\Theta B$, dove:

- $\Theta$ è un operatore di confronto
- $A$ è un attributo dello schema del primo operando
- $B$ è un attributo dello schema del secondo operando
- $\text{Dom(A)} = \text{Dom}(B)$

Osservazioni: $r1 \triangleright \triangleleft\ r2 = \sigma_{A\Theta B}(r1\times r2)$

> N.B.: 

Esercizio: Nomi dei docenti non residenti a Roma che insegnano nel secondo semestre.

- Corso(codice, titolo, programma, semestre)
- Docente(codice, cf, cognome, nome, città residenza)
- Insegna(docente, corso)

$$
\text{corsi2} = \sigma_{\text{semestre} = 2} (\text{corsi})
$$

$$
\text{docentiNonRoma} = \sigma_{\text{città residenza} \neq \text{"Roma"}}(\text{docente})
$$

$$
\text{corsi2} \underset{\text{insegna.corso = corsi2.codice}}{\triangleright \triangleleft\ }  \text{insegna}\ \underset{\text{insegna.docente = docentiNonRoma.codice}}{\triangleright \triangleleft\ } \text{docentiNoRoma}
$$

$\sigma_{\text{città residenza} \neq \text{roma}}((\text{docente} \triangleright \triangleleft\ \text{insegna})\triangleright \triangleleft\ \text{corso})$
