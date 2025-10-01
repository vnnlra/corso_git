# Esempio pratico: collegare un repository locale a uno remoto

## 1) Crea un progetto locale
(oppure usa quello creato ne paragrafo 04)
```bash
mkdir progetto-git
cd progetto-git
git init
echo "Ciao Git!" > readme.txt
git add readme.txt
git commit -m "Primo commit"
```
## 2) Crea un repository remoto
- Vai su **GitHub** (o GitLab, Bitbucket) e crea un nuovo repository **vuoto**
  (senza README, senza LICENSE).
- Copia l’URL HTTPS, ad esempio:
  https://github.com/tuo-utente/progetto-git.git

## 3) Collega il repository locale al remoto
```bash
git remote add origin https://github.com/tuo-utente/progetto-git.git
git remote -v   # verifica che 'origin' punti all’URL corretto
```
## 4) Invia i commit locali al remoto
```bash
git push -u origin HEAD
```
👉 Questo comando carica il tuo branch attuale sul remoto e lo collega in modo che da ora in poi basti scrivere:
- git push
- git pull

queste operazioni ti chiederanno di inserire il tuo nome utente e una password che non è quella con cui ti sei registrato su GitHub. L'accreditamento avviene con un **token**, la procedura per ottenerlo è descritta nel paragrafo [Generare un Personal Access Token](06_creazione_account_server_GitHub.md)

## 5) Verifica dal sito
Vai sulla pagina GitHub/GitLab del repository: vedrai readme.txt e la cronologia con il **primo commit**.

## [Torna a README](README.md)
