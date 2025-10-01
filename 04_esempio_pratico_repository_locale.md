# Esempio pratico minimale con Git

```bash
# 1. Creo una nuova cartella e ci entro
mkdir progetto-git
cd progetto-git

# 2. Inizializzo il repository
git init

# 3. Creo un file di testo
echo "Ciao Git!" > readme.txt

# 4. Aggiungo il file all'area di staging
git add readme.txt

# 5. Faccio il primo commit
git commit -m "Primo salvataggio del progetto"

# 6. Modifico il file
echo "Seconda riga del file." >> readme.txt

# 7. Salvo di nuovo i cambiamenti
git add readme.txt
git commit -m "Aggiunta seconda riga"

# 8. Guardo la cronologia
git log --oneline
```
**nota**:
dopo ogni istruzione controllare lo stato della repository con:

```bash
git status
```
## [Torna a README](tutorial_git.md)
