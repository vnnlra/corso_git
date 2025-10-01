# 🧠 Tutorial essenziale su Git

## 🔧 Cos’è Git?

**Git** è un sistema di controllo di versione distribuito. Permette di:
- tracciare le modifiche nel codice,
- collaborare con altri sviluppatori,
- gestire versioni diverse di un progetto.

---

## 📦 1. Installazione

**Su Debian/Ubuntu:**
```bash
sudo apt install git
```

**Su macOS (con Homebrew):**
```bash
brew install git
```

Verifica l’installazione:
```bash
git --version
```

---

## 🔐 2. Configurazione iniziale

```bash
git config --global user.name "Tuo Nome"
git config --global user.email "tu@email.com"
```

---

## 📁 3. Creazione o clonazione di un repository

**Creare un nuovo repository:**
```bash
mkdir mio-progetto
cd mio-progetto
git init
```

**Clonare un repository esistente:**
```bash
git clone https://github.com/utente/progetto.git
```

---

## ✅ 4. Ciclo di lavoro base

**Aggiungere file:**
```bash
git add nomefile        # aggiunge un singolo file
git add .               # aggiunge tutto
```

**Fare un commit:**
```bash
git commit -m "Messaggio descrittivo"
```

**Vedere lo stato:**
```bash
git status
```

**Vedere la cronologia:**
```bash
git log
```

---

## 🌐 5. Lavorare con un repository remoto

**Aggiungere un remoto:**
```bash
git remote add origin https://github.com/utente/progetto.git
```

**Inviare le modifiche (push):**
```bash
git push origin main
```

**Scaricare modifiche (pull):**
```bash
git pull origin main
```

> 🔁 Sostituisci `main` con `master` se necessario.

---

## 🌿 6. Branch (rami)

**Creare un nuovo ramo:**
```bash
git branch nuovo-ramo
```

**Passare a un ramo:**
```bash
git checkout nuovo-ramo
```

**Creare e passare a un nuovo ramo:**
```bash
git checkout -b feature-xyz
```

**Unire un ramo nel principale:**
```bash
git checkout main
git merge feature-xyz
```

---

## 🧼 7. Ignorare file

Crea un file `.gitignore` per escludere file e cartelle inutili.

### Esempio `.gitignore` per un progetto Bash:
```
# file temporanei
*.swp
*~
*.bak

# output di script
*.log

# backup personali
*.old

# file di sistema
.DS_Store

# directory da ignorare
tmp/
output/
```

---

## 🆘 8. Altri comandi utili

**Annullare modifiche non committate:**
```bash
git checkout -- nomefile
```

**Vedere le differenze:**
```bash
git diff
```

---

## 📚 Glossario Git

| Termine   | Definizione |
|-----------|-------------|
| **Repository** | Archivio del progetto con la cronologia delle modifiche. |
| **Commit** | Salvataggio puntuale di uno stato del progetto. |
| **Branch** | Ramo indipendente della cronologia del progetto. |
| **Merge** | Fusione di due rami. |
| **Stage / Staging Area** | Area temporanea dove si preparano i file prima del commit. |
| **HEAD** | Puntatore all'ultimo commit del ramo attivo. |
| **Remote** | Repository ospitato su server esterno (es. GitHub). |
| **Push** | Invio dei commit locali al repository remoto. |
| **Pull** | Recupero di modifiche dal repository remoto. |
| **Clone** | Copia locale di un repository remoto. |
| **Checkout** | Passaggio a un altro ramo o commit. |

---

## 🏁 Conclusione

Git è uno strumento potente, utile per qualunque tipo di progetto. Una volta padroneggiati i comandi di base, puoi esplorare funzionalità avanzate come `rebase`, `stash` e `tag`.
