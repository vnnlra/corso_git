# Capitolo 09 – Ripristinare versioni precedenti del progetto

Una delle funzioni più potenti di Git è la possibilità di **tornare indietro nel tempo**, recuperando versioni precedenti dei file o dell’intero progetto.

Ogni commit rappresenta uno **snapshot**, cioè una fotografia completa dello stato del progetto in un determinato momento.

---

## 1) Vedere la cronologia per scegliere a quale versione tornare

Per visualizzare la cronologia dei commit:

```bash
git log --oneline
```

Esempio:

```
a3f91c2 Aggiunta seconda riga
8bd12ef Primo salvataggio del progetto
```

Ogni commit è identificato da un **hash**, che rappresenta in modo univoco quella versione del progetto.

---

## 2) Ripristinare un singolo file da un commit precedente

Questo comando permette di **ripristinare un singolo file** a una versione precedente, **senza modificare la storia del progetto**.

È utile quando:

* un file è stato modificato per errore
* si vuole recuperare una versione passata di un solo file
* non si vuole annullare un intero commit

### Sintassi

```bash
git checkout <id-commit> -- nomefile
```

### Esempio

```bash
git checkout 8bd12ef -- readme.txt
```

Risultato:

* il file viene riportato allo stato del commit indicato
* il file risulta **modificato** nella working directory
* la cronologia del progetto **non viene alterata**

Per rendere permanente il ripristino è necessario salvare la modifica con un nuovo commit:

```bash
git add readme.txt
git commit -m "Ripristinato readme.txt a una versione precedente"
```

---

## 3) Annullare un commit creando un nuovo commit (`git revert`)

Il comando `git revert` serve per **annullare un commit**, creando un **nuovo commit** che applica l’operazione inversa.

Questo comando:

* non modifica la storia esistente
* è sicuro anche nei repository condivisi
* lavora sulla **cronologia del progetto**, non sui singoli file

### Sintassi

```bash
git revert <id-commit>
```

### Esempio

```bash
git revert a3f91c2
```

Risultato:

* Git crea un nuovo commit che annulla le modifiche introdotte dal commit indicato
* lo stato dei file torna equivalente a quello precedente a quel commit

### Nota importante

Se Git risponde con un messaggio come:

```
non c'è nulla di cui eseguire il commit,
l'albero di lavoro è pulito
```

significa che **il commit indicato non ha effetti nello stato attuale del progetto**
(ad esempio perché le modifiche sono già state annullate da commit successivi).

In questo caso `git revert` **non produce alcun nuovo commit**.

Se invece si vuole ripristinare un singolo file, è necessario usare il comando visto nel paragrafo precedente.

---

## 4) Tornare indietro cancellando la storia successiva (`git reset --hard`)

Questo comando riporta il progetto **esattamente** allo stato di un commit precedente, eliminando tutti i commit successivi.

⚠️ **Attenzione**: è un’operazione distruttiva.

Usare questo comando **solo se non è stato fatto push** e il repository non è condiviso.

### Sintassi

```bash
git reset --hard <id-commit>
```

### Effetti

* il progetto torna allo stato del commit indicato
* tutti i commit successivi vengono eliminati dalla cronologia locale
* le modifiche non salvate vengono perse

---

## 5) Eliminare modifiche non ancora salvate

Se un file è stato modificato ma **non è ancora stato aggiunto allo staging**, è possibile annullare le modifiche.

Ripristinare un singolo file:

```bash
git restore nomefile
```

Ripristinare tutti i file modificati:

```bash
git restore .
```

---

## 6) Confrontare le versioni (`git diff`)

Prima di ripristinare una versione è spesso utile confrontare le differenze.

Vedere le modifiche non ancora salvate:

```bash
git diff
```

Confrontare due commit:

```bash
git diff <commit1> <commit2>
```

Confrontare un file in una versione precedente:

```bash
git diff <commit> -- nomefile
```

---

## 7) Tabella riepilogativa

| Obiettivo                  | Comando                         | Effetto                              | Sicurezza    |
| -------------------------- | ------------------------------- | ------------------------------------ | ------------ |
| Ripristinare un file       | `git checkout <commit> -- file` | Ripristina solo quel file            | Sicuro       |
| Annullare un commit        | `git revert <commit>`           | Crea un nuovo commit di annullamento | Molto sicuro |
| Tornare indietro nel tempo | `git reset --hard <commit>`     | Elimina la storia successiva         | Pericoloso   |
| Eliminare modifiche locali | `git restore`                   | Annulla modifiche non salvate        | Sicuro       |
| Confrontare versioni       | `git diff`                      | Mostra le differenze                 | Sicuro       |

---

## Conclusione

Git offre diversi strumenti per recuperare versioni precedenti dei file o del progetto.

Scegliere il comando corretto permette di:

* evitare la perdita di dati
* mantenere una cronologia chiara
* lavorare in sicurezza anche in ambienti condivisi

Git diventa così una vera **macchina del tempo** per il tuo progetto.
