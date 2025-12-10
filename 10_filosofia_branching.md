# Capitolo 10 – La filosofia del branching

Il branching è uno dei concetti più potenti e caratteristici di Git. Permette di creare **linee di sviluppo parallele**, sperimentare nuove idee, aggiungere funzionalità e correggere bug senza toccare o mettere in pericolo la versione stabile del progetto.

Git è progettato per rendere i branch **leggeri**, **veloci** e **sicuri**: creare un nuovo branch è praticamente immediato e non comporta nessuna copia fisica dell’intero progetto.

---

## 🌱 1. Perché esistono i branch

In un progetto reale, lo sviluppo raramente procede in una sola direzione. Si lavora a più attività in parallelo: nuove funzionalità, fix urgenti, esperimenti, riorganizzazioni del codice.

Senza dei branch, tutto questo avverrebbe nel ramo principale, generando confusione, instabilità e continui conflitti.

Con i branch, invece:

* ogni attività ha il proprio spazio dedicato;
* nessuna modifica interferisce con quella degli altri;
* la versione stabile rimane sempre utilizzabile.

In altre parole:

> **Un branch è una timeline indipendente del progetto.**

---

## 🧠 2. La filosofia: "Sperimenta senza rompere"

La branch principale (`main` o `master`) deve rimanere **pulita e stabile**. Tutte le modifiche che non sono pronte o non sono state verificate devono vivere in branch separati.

La filosofia del branching è quindi quella di permetterti di:

* fare test e prove senza rischi;
* sviluppare funzionalità complesse in più commit e con calma;
* annullare il lavoro facilmente se non funziona;
* lavorare in parallelo con altri senza intralci.

Git rende questo naturale: creare un branch costa pochissimo sia in termini di tempo che di spazio.

---

## 🔧 3. Quando creare un branch

Dovresti creare un branch **ogni volta che inizi un nuovo lavoro** che non può essere immediatamente integrato nel ramo principale.

Esempi tipici:

* una nuova funzionalità → `feature/login-utente`
* una correzione importante → `fix/errore-avvio`
* un esperimento → `experiment/nuova-idea`
* una riscrittura strutturale → `refactor/modulo-auth`

La regola generale:

> **Se una modifica non è pronta per finire su `main`, merita un branch a parte.**

---

## 🗃️ 4. I branch come "scatole isolate di lavoro"

Creare un branch significa prendere un punto della storia del progetto e continuare lo sviluppo da lì, separatamente dagli altri.

Nel tuo branch puoi:

* fare commit senza paura;
* tornare indietro;
* riscrivere la storia;
* cancellare tutto se serve.

Il resto del progetto non verrà toccato.

---

## 🔀 5. Integrare il lavoro: il merge

Quando una funzionalità è completa, il tuo lavoro viene integrato nella branch principale tramite il **merge**:

```bash
git checkout main
git merge nome-branch
```

Git unirà automaticamente le modifiche quando possibile.
Se due persone hanno modificato la stessa parte di codice, bisognerà risolvere un **conflitto di merge**.

Il merge fa parte della normale collaborazione in Git ed è reso molto semplice proprio grazie al branching.

---

## 🎯 6. Benefici del branching

Il branching permette:

* **sviluppo parallelo** senza interruzioni;
* **maggiore sicurezza** nella versione stabile;
* **organizzazione del lavoro** più chiara;
* **collaborazione efficiente** tra più sviluppatori;
* **sperimentazione libera** e reversibile.

Il risultato è un flusso di lavoro ordinato, prevedibile e robusto.

---

## 📚 7. In sintesi

> **Il branching è la chiave per uno sviluppo parallelo, sicuro e scalabile.**

È uno degli strumenti che rende Git superiore a molti altri sistemi di versionamento. Usarlo bene significa mantenere il progetto chiaro, stabile e facilmente estendibile.

Puoi ora approfondire:

* come si crea un branch (`git branch`, `git checkout -b`),
* come si passa da un branch all’altro,
* come si unisce il lavoro (`git merge`).

Questi aspetti saranno trattati nel capitolo successivo con esempi pratici.
