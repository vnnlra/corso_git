# Capitolo 11 – Esempi pratici di branching

In questo capitolo mettiamo in pratica ciò che hai imparato sulla filosofia del branching. Vedrai come creare branch, spostarti tra essi, fare merge e affrontare i conflitti. È la parte più operativa e immediata del branching in Git.

---

## 🌱 1. Creare un nuovo branch

Il modo più semplice per creare un branch e spostarsi subito al suo interno è:

```bash
git checkout -b nome-branch
```

Esempio:

```bash
git checkout -b feature/login
```

Questo comando equivale a:

1. `git branch feature/login`
2. `git checkout feature/login`

---

## 🔀 2. Vedere tutti i branch

```bash
git branch
```

Il branch corrente è contrassegnato da un asterisco `*`.

---

## 🔁 3. Spostarsi tra branch

```bash
git checkout nome-branch
```

Esempio:

```bash
git checkout main
```

Ricorda: puoi cambiare branch **solo se non hai modifiche non salvate** (Git ti avvisa).

---

## 📝 4. Fare commit nel branch

Ogni branch è una linea di sviluppo indipendente. Puoi lavorare al tuo ritmo:

```bash
echo "Nuovo modulo" > modulo.txt
git add modulo.txt
git commit -m "Aggiunto modulo"
```

Questi commit rimarranno nel branch finché non verranno uniti a `main`.

---

## 🔀 5. Unire un branch alla branch principale (merge)

Quando hai finito una funzionalità:

```bash
git checkout main
git merge feature/login
```

Se Git può fondere i due rami automaticamente, vedrai un messaggio come:

```
Fast-forward
```

Se ci sono modifiche incompatibili, Git chiederà di risolvere un conflitto.

---

## ⚠️ 6. Risolvere un conflitto di merge (esempio semplice)

Supponiamo che due branch abbiano modificato la stessa riga di un file.
Quando fai merge, Git bloccherà il processo e modificherà il file così:

```
<<<<<<< HEAD
Versione nel branch main
=======
Versione nel branch feature/login
>>>>>>> feature/login
```

Devi:

1. modificare il file scegliendo la versione corretta (o combinandole);
2. rimuovere i marcatori `<<<<<<<`, `=======`, `>>>>>>>`;
3. salvare;
4. terminare il merge con:

```bash
git add nomefile
git commit
```

---

## 🗑️ 7. Eliminare un branch che non serve più

Dopo aver fatto il merge:

```bash
git branch -d nome-branch
```

Esempio:

```bash
git branch -d feature/login
```

Se vuoi forzare l’eliminazione (branch non ancora mergiato):

```bash
git branch -D nome-branch
```

---

## 🚀 8. Esempio completo di workflow

### Scenario: sviluppare una funzionalità

```bash
git checkout -b feature/profilo
# Modifica file e fai commit

git checkout main
git merge feature/profilo
git branch -d feature/profilo
```

### Scenario: correggere un bug urgente mentre lavori su una feature

```bash
git checkout -b feature/ricerca
# stai lavorando...

# arriva un bug urgente

git checkout -b fix/crash-home main
# correggi, fai commit

git checkout main
git merge fix/crash-home
git branch -d fix/crash-home

# torni al lavoro

git checkout feature/ricerca
```

---

## 🎓 9. Esercizi pratici per gli studenti

### 🔸 Esercizio 1 — Creare una funzionalità

1. Crea il branch `feature/saluto`.
2. Aggiungi un file `saluto.txt` con un messaggio.
3. Committa.
4. Fai merge in `main`.
5. Elimina il branch.

### 🔸 Esercizio 2 — Simulare un conflitto

1. Crea due branch: `vers1` e `vers2`.
2. Modifica la stessa riga di un file in entrambi.
3. Prova a fare merge e risolvi il conflitto.

### 🔸 Esercizio 3 — Workflow realistico

Riproduci lo scenario di bugfix urgente visto nel capitolo.

---

## 📚 Conclusione

Questi esempi rappresentano l’uso quotidiano dei branch in Git.
Nel capitolo successivo potresti esplorare **strategie avanzate** come Git Flow, rebase, branch temporanei o stashing.
