# Tutorial essenziale Git

Questo tutorial riassume i concetti fondamentali di Git attraverso i termini del glossario del corso.
Non sostituisce i capitoli precedenti, ma serve come **ripasso compatto** e come riferimento rapido durante le esercitazioni.

---

## Cos’è Git

**Git** è un sistema di controllo di versione distribuito.
Permette di:

* tracciare le modifiche nel tempo
* lavorare in modo ordinato sullo stesso progetto
* collaborare senza perdere il controllo delle versioni

---

## Installazione

Su Debian/Ubuntu:

```bash
sudo apt install git
```

Verifica dell’installazione:

```bash
git --version
```

---

## Configurazione iniziale

Prima di iniziare a lavorare, è necessario configurare il nome e l’email:

```bash
git config --global user.name "Tuo Nome"
git config --global user.email "tu@email.com"
```

---

## Repository

Un **repository** è l’archivio del progetto.
Contiene:

* i file del progetto
* la cronologia completa delle modifiche

Un repository può essere:

* **locale** (sul proprio computer)
* **remoto** (su un server come GitHub)

Creazione di un repository locale:

```bash
git init
```

Clonazione di un repository remoto:

```bash
git clone URL-del-repository
```

---

## Commit

Un **commit** è il salvataggio di uno stato preciso del progetto.
Ogni commit rappresenta una versione coerente dei file.

Creare un commit:

```bash
git commit -m "Messaggio descrittivo"
```

---

## Stage / Staging Area

La **staging area** è un’area intermedia tra i file modificati e il commit.

Flusso tipico:

1. modifichi i file
2. li aggiungi allo stage
3. crei il commit

Aggiungere file allo stage:

```bash
git add nomefile
git add .
```

---

## Stato e cronologia

Verificare lo stato dei file:

```bash
git status
```

---

## Log

Il comando **log** mostra la cronologia dei commit.
È utile per:

* vedere l’elenco delle versioni disponibili
* capire l’ordine con cui sono state fatte le modifiche
* recuperare l’ID di un commit (utile per revert)

Mostrare la cronologia:

```bash
git log
```
O anche:

```bash
git log --oneline
```
per avere una versione più compatta della cronologia

---

## HEAD

**HEAD** è un puntatore che indica l’ultimo commit del ramo attivo.
Quando si crea un nuovo commit, HEAD avanza automaticamente.

---

## Branch

Un **branch** è un ramo indipendente della cronologia del progetto.
Serve per sviluppare funzionalità o sperimentare senza interferire con il lavoro principale.

Il branch principale è solitamente chiamato `main`.

Creare un nuovo branch:

```bash
git branch nuovo-branch
```

Passare a un branch:

```bash
git checkout nuovo-branch
```

---

## Merge

Il **merge** unisce due branch, fondendo le loro modifiche.

Il merge viene eseguito dal branch che deve ricevere le modifiche:

```bash
git merge nome-branch
```

---

## Remote

Un **remote** è un repository ospitato su un server esterno, come GitHub.

Il remote principale si chiama solitamente `origin`.

Visualizzare i remote configurati:

```bash
git remote -v
```

---

## Push e Pull

Inviare i commit locali al repository remoto:

```bash
git push origin main
```

Dopo il primo push, il branch locale viene collegato a quello remoto.
Da quel momento è sufficiente usare:

```bash
git push
```

Scaricare le modifiche dal repository remoto:

```bash
git pull origin main
```

Analogamente, dopo il primo pull è possibile usare semplicemente:

```bash
git pull
```

bash
git push origin main

````

Scaricare le modifiche dal repository remoto:
```bash
git pull origin main
````

---

## Diff

Il comando **diff** mostra le differenze tra versioni dei file:

```bash
git diff
```

---

## Restore

Il comando **restore** ripristina file modificati non ancora committati:

```bash
git restore nomefile
```

---

## Reset e Revert

Il comando **reset** sposta HEAD indietro nel tempo modificando la storia del repository:

```bash
git reset
```

⚠️ Da usare con cautela, soprattutto nei repository condivisi.

Il comando **revert** annulla un commit creando un nuovo commit:

```bash
git revert ID_commit
```

---

## .gitignore

Il file **.gitignore** indica a Git quali file o cartelle non devono essere tracciati.

Esempio:

```text
*.o
*.log
build/
```

---

## Conclusione

Git permette di lavorare in modo ordinato, sperimentare senza rischi e collaborare efficacemente.
Conoscere i termini fondamentali del glossario significa comprendere davvero il funzionamento di Git.


## [Torna a README](README.md)
