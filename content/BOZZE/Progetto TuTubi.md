---
updated_at: 2026-05-27T17:07:31.781+02:00
---
OUtente:
- nome
- data di iscrizione
- cronologia
- insieme di playlist

Video:
- titolo
- durata
- descrizione
- nome del file
- categoria
- tag (1..\*)
- se è un'eventuale risposta a un altro video (un utente non può rispondere a un suo stesso video)
- censura

Categoria:
- nome

Tag:
- nome

Censura:
- motivo

VideoVisto:
- sequenza dei video con data, ora e numero di visualizzazioni per utente
- valutazione in stelle (0..5) (un utente non può valutare un suo stesso video e voltare solo video che ha visto)

Commento:
- Utente
- Video visto
- testo
- data
- ora

Playlist:
- collezione ordinata di video
- nome
- data di creazione
- visibilità (pubblica o privata)