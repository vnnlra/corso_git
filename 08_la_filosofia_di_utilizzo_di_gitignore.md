# Capitolo 08 – La filosofia di utilizzo di `.gitignore`

Il file `.gitignore` serve a dire a Git **quali file non devono essere tracciati**. È uno strumento semplice ma fondamentale per mantenere un repository pulito, leggibile e privo di “rumore”.

Git funziona al meglio con i **file di testo**, ma molti progetti generano file temporanei, binari o specifici della macchina locale: questi non dovrebbero essere salvati nella cronologia.

---

## 🎯 Obiettivi del `.gitignore`

1. **Evitare di salvare file inutili** nella storia del progetto.
2. **Ridurre i conflitti** causati da file generati automaticamente o specifici di un singolo ambiente.
3. **Mantenere il repository leggero** evitando file binari pesanti o temporanei.
4. **Rendere il progetto portabile**, eliminando dipendenze da configurazioni locali.

---

## 📌 Cosa NON dovrebbe essere tracciato

### 🔹 1. File generati automaticamente

Esempi:

* file di compilazione (`*.o`, `*.class`)
* cartelle come `build/`, `dist/`, `node_modules/`
* file generati dall'editor (`*.swp`, `*.tmp`)

Questi file **non fanno parte del progetto**, ma vengono ricreati ogni volta.

### 🔹 2. File con informazioni sensibili

* password,
* token,
* chiavi SSH,
* configurazioni private.

⚠️ Importante: se un file con dati sensibili è stato già committato, `.gitignore` **non basta** a rimuoverlo dalla storia!

### 🔹 3. File specifici della macchina

* configurazioni dell’ambiente di sviluppo,
* file di cache,
* output temporanei.

Esempi comuni:

```
.DS_Store
Thumbs.db
.vscode/
.idea/
```

---

## 🧠 Filosofia generale: "traccia solo ciò che conta"

Il repository deve contenere **solo i file che descrivono il progetto**, non quelli che derivano dal funzionamento degli strumenti.

Quindi:

* ✔️ *traccia il codice sorgente*,
* ✔️ *traccia la documentazione*,
* ✔️ *traccia gli script necessari*,
* ❌ *non traccia ciò che viene generato automaticamente*,
* ❌ *non traccia ciò che è personale*,
* ❌ *non traccia ciò che può cambiare da una macchina all'altra*.

Il principio è lo stesso della pulizia del proprio ambiente di lavoro:

> **il repository deve contenere solo ciò che serve davvero, e niente di superfluo.**

---

## 📁 Esempio di `.gitignore` ragionato

```
# File temporanei dell’editor
*.swp
*.tmp
*~

# File binari
*.o
*.exe
*.class

# Directory generate automaticamente
/build/
/dist/
/node_modules/

# File di sistema
.DS_Store
Thumbs.db

# Configurazioni personali
.vscode/
.idea/
```

---

## 📝 Regola d’oro

> **Se un file può essere rigenerato o è personale, non dovrebbe stare nel repository.**

Il `.gitignore` non è solo un elenco tecnico, ma uno strumento che esprime la
**filosofia di ordine, pulizia e riproducibilità del progetto**.
