---
updated_at: 2025-10-02T15:36:15.684+02:00
---
> La vista è una [[tabella]] che funge da visualizzazione di più tabelle fuse in una singola tabella. Ciò permette una maggiore modularità, riusabilità e spesso anche privacy dei singoli componenti della [[base di dati]].

Esempio:

Corsi:

| Corso       | Docente | Aula |
| ----------- | ------- | ---- |
| Matematica  | Mario   | A    |
| Informatica | Luigi   | B    |

Aule:

| Nome | Edificio    | Piano |
| ---- | ----------- | ----- |
| A    | Palazzo     | 2     |
| B    | Laboratorio | 1     |

vista CorsiSedi:

| Corso      | Aula | Edificio    | Piano |
| ---------- | ---- | ----------- | ----- |
| Matematica | A    | Palazzo     | 2     |
| Luigi      | B    | Laboratorio | 1     |
