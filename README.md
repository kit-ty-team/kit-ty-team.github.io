# kit-ty-team.github.io

Pagina "link in bio" di **kit-ty**, pubblicata su <https://kit-ty-team.github.io> (GitHub Pages, branch `main`, cartella `/`).
È un unico file statico, `index.html`, con il CSS inline e nessuna risorsa esterna.

## Modificare i link

1. Apri `index.html`. Il commento in cima elenca tutti i placeholder, cioè i testi tra parentesi quadre come `[URL_INSTAGRAM]` o `[NOME_COLLEGA_1]`.
2. Sostituisci ogni placeholder, **parentesi comprese**, con il valore vero (es. `href="https://www.instagram.com/…"`).
   `[DESCRIZIONE_PROGETTO]` compare 3 volte: nel testo, nella meta description e in `og:description`.
3. Per togliere un bottone che non usi, cancella l'intero blocco `<li> … </li>` che lo contiene. Se una sezione resta vuota, cancella tutta la `<section>`.
4. Fai commit e push su `main`: GitHub Pages pubblica da solo in circa 1 minuto.

Per trovare i placeholder rimasti: `grep -n '\[[A-Z0-9_]*\]' index.html`

## Struttura

- `assets/cat-heads/`: teste di gatto SVG copiate da [marco-pedron/kit-ty](https://github.com/marco-pedron/kit-ty) (`docs/screenshots/cat-heads/`)
- `assets/og-image.png`, `assets/favicon-32.png`, `assets/apple-touch-icon.png`: PNG ricavate dalla testa `happy`, per le anteprime social e le icone
- `qr/`: QR code verso https://kit-ty-team.github.io (correzione d'errore H). Usa `kit-ty-qr.svg` per la stampa e `kit-ty-qr.png` per lo schermo; `kit-ty-qr-logo.png` ha il gatto al centro.
- `.nojekyll`: dice a GitHub Pages di servire i file così come sono, senza passarli da Jekyll
