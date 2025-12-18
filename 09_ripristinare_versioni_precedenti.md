# Capitolo 09 - Ripristinare versioni precedenti del progetto

Una delle funzioni più potenti di Git è la possibilità di **tornare indietro nel tempo**, recuperando versioni precedenti dei file o dell’intero progetto. Ogni commit è infatti uno **snapshot**, una fotografia completa del progetto in quel momento.

---

## 1) Vedere la cronologia per scegliere a quale versione tornare

```bash
git log --oneline
```

Esempio:

```
a3f91c2 Aggiunta seconda riga
8bd12ef Primo salvataggio del progetto
```

Ogni commit ha un **hash**, usato come ID della versione.

---

## 2) Ripristinare un singolo file da un commit precedente

Usa questo se vuoi ripristinare un file ma **non modificare la storia**:

```bash
git checkout <id-commit> -- nomefile
```

Esempio:

```bash
git checkout 8bd12ef -- readme.txt
```

Il file torna allo stato di quel commit. Puoi poi salvarlo con un nuovo commit.

---

## 3) Annullare un commit creando un nuovo commit (metodo sicuro)

```bash
git revert <id-commit>
```

Questo comando crea un nuovo commit che annulla quello selezionato. È il metodo consigliato se il repository è condiviso.

Esempio:

```bash
git revert a3f91c2
```

Risultato: compare un nuovo commit chiamato "Revert ...".

---

## 4) Tornare indietro cancellando la storia successiva (*operazione distruttiva*)

Da usare solo se **non hai fatto push**.

```bash
git reset --hard <id-commit>
```

Esempio:

```bash
git reset --hard 8bd12ef
```

Effetti:

* Il repository torna esattamente alla versione di quel commit.
* Tutti i commit successivi vengono **eliminati** dalla storia locale.

⚠️ Non usare con repository condivisi.

---

## 5) Eliminare modifiche non ancora committate

Se hai modificato un file ma non hai ancora fatto commit:

Ripristinare un file:

```bash
git restore nomefile
```

Ripristinare tutto:

```bash
git restore .
```

---

## 6) Confrontare le versioni prima di ripristinare (git diff)

Prima di ripristinare una versione è utile vedere **cosa è cambiato**.

### Vedere le modifiche non ancora committate

```bash
git diff
```

### Confrontare due commit

```bash
git diff <commit1> <commit2>
```

### Confrontare un file in due versioni

```bash
git diff <commit> -- nomefile
```

### Confrontare la working directory con un commit precedente

```bash
git diff <commit>
```

Questi confronti aiutano a decidere se usare **revert**, **restore** o **reset**.

---

## 7) Tabella riepilogativa

| Obiettivo                                         | Comando                         | Effetto                                                | Sicurezza                |
| ------------------------------------------------- | ------------------------------- | ------------------------------------------------------ | ------------------------ |
| Recuperare un file da una vecchia versione        | `git checkout <commit> -- file` | Riscrive solo quel file                                | Sicuro                   |
| Annullare un commit creando un nuovo commit       | `git revert <commit>`           | Mantiene la storia, aggiunge un commit di annullamento | Molto sicuro             |
| Tornare indietro cancellando la storia successiva | `git reset --hard <commit>`     | Riscrive la cronologia                                 | Pericoloso (solo locale) |
| Eliminare modifiche non committate                | `git restore`                   | Ripristina i file modificati                           | Sicuro                   |
| Confrontare differenze                            | `git diff`                      | Mostra cosa è cambiato                                 | Sicuro                   |

---

## 8) Esempio pratico

Riprendiamo l’esempio del file *readme.txt* con due commit.

```bash
git log --oneline
# trova l'ID del primo commit

git checkout <id_primo_commit> -- readme.txt
```

La seconda riga verrà rimossa dal file. Per renderla permanente:

```bash
git add readme.txt
git commit -m "Ripristinato readme alla versione iniziale"
```

---

## Conclusione

Questi strumenti permettono di recuperare errori, esplorare versioni passate e mantenere una storia pulita. Git diventa così una vera **macchina del tempo** per il tuo progetto.
