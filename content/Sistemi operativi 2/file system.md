---
updated_at: 2026-03-03T12:02:43.637+01:00
---
Le differenze tra i file systems sono:

- dimensione massima della partizione
- dimensione massima del file
- lunghezza massima del nome del file
- se è un *journal file system* o meno.

# File system Linux

Questi file system possono essere [[comandi della bash (Bourne Again shell)#^2efd45|montati]] su Linux.

| Nome     | Journal | Partizione max (TB) | File max (TB) | Nome file (bytes) |
| -------- | ------- | ------------------- | ------------- | ----------------- |
| Ext2     | no      | 32                  | 2             | 255               |
| Ext3     | si      | 32                  | 2             | 255               |
| Ext4     | si      | 1000                | 16            | 255               |
| ReiserFS | si      | 16                  | 8             | 4032              |

## File system non Linux

Windows (montabili su Linux):

- NTFS
- FAT16
- FAT32
- FAT64