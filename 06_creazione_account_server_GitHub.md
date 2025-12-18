# Capitolo 08 – Creare un account GitHub e usare il Token di accesso (PAT)

## 1) Creazione dell’account
1. Vai su https://github.com
2. Clicca in alto a destra su “Sign up”.
3. Inserisci:
   - Email (riceverai un codice di verifica).
   - Password forte (almeno 8 caratteri; meglio con numeri e simboli).
   - Username (sarà pubblico).
4. Completa il test anti-bot e verifica l’email inserendo il codice ricevuto.
→ A questo punto l’account è attivo.

## 2) Password vs Token (PAT)
- La password serve per accedere al sito web di GitHub.
- Per usare Git in HTTPS (push/pull/clone) non si usa la password ma un **Personal Access Token (PAT)**.
- Puoi creare più token, ognuno con permessi (scope) e scadenze diverse; puoi revocarli in qualsiasi momento.

## 3) Creare un token
1. Accedi a GitHub, poi vai in: Settings → Developer settings → Personal access tokens.
2. Scegli:
   - “Fine-grained tokens” (consigliato) **oppure** “Tokens (classic)”.
3. Imposta:
   - Expiration (es. 90 giorni).
   - Scope/permessi minimi necessari (per Git di solito “repo”).
4. Conferma su “Generate token”.
5. Copia subito il token mostrato (non verrà più visualizzato).
6. Salvalo in modo sicuro (password manager).

## 4) Usare il token al posto della password (HTTPS)
Alla prima operazione Git che richiede autenticazione, ti verrà chiesto:
- Username: il tuo username GitHub.
- Password: incolla il **token** generato.

Esempio tipico di flusso locale:
- Configura Git con i tuoi dati:
```bash
    git config --global user.name "Nome Cognome"
    git config --global user.email "tuaemail@example.com"
```
- Crea un repo locale e fai il primo commit:
```bash
    mkdir progetto-git
    cd progetto-git
    git init
    echo "Ciao GitHub!" > readme.txt
    git add readme.txt
    git commit -m "Primo commit"
```
- Collega il remoto (sostituisci con il tuo URL):
```bash
    git remote add origin https://github.com/tuo-utente/progetto-git.git
```
- Primo push (imposta anche il tracking):
```bash
    git push -u origin HEAD
```
  → Qui Git chiederà username e “password”: inserisci il **token**.

(Opzionale) Memorizzare le credenziali per non reinserirle ogni volta:
```bash
    git config --global credential.helper store
```

## 5) In sintesi
- La password: solo per accedere al sito.
- Il PAT (token): per Git via HTTPS.
- Tieni i permessi del token al minimo necessario, imposta una scadenza e rigeneralo se compromesso.

## [Torna a README](README.md)
