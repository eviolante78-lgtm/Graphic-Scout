# Basket Graphic Scout

App per lo scout del basket: tiri sul campo, statistiche per giocatore e periodo, minuti di gioco.
Funziona nel browser, si installa su tablet/telefono/PC come una vera app e **salva tutto in locale**
sul dispositivo (anche offline). Nessun server, nessun account.

## Cosa contiene

| File | A cosa serve |
|------|--------------|
| `index.html` | L'app completa (un solo file) |
| `manifest.webmanifest` | Nome, colori e icone per l'installazione |
| `sw.js` | Service worker: fa funzionare l'app offline |
| `icons/` | Icone (pallone da basket e penna da tablet bianca) |
| `.nojekyll` | Dice a GitHub Pages di pubblicare i file così come sono |

## Pubblicare su GitHub (GitHub Pages)

1. Crea un repository su GitHub (per esempio `basket-graphic-scout`), pubblico o privato con Pages abilitato.
2. Carica **tutto il contenuto di questa cartella** nella radice del repository
   (da web: *Add file → Upload files*, trascina i file e la cartella `icons`; compreso `.nojekyll`).
   Da terminale:
   ```bash
   git init
   git add .
   git commit -m "Basket Graphic Scout"
   git branch -M main
   git remote add origin https://github.com/TUO-UTENTE/basket-graphic-scout.git
   git push -u origin main
   ```
3. Su GitHub: **Settings → Pages → Build and deployment**
   - Source: *Deploy from a branch*
   - Branch: `main`, cartella `/ (root)` → *Save*
4. Dopo circa un minuto l'app è online su
   `https://TUO-UTENTE.github.io/basket-graphic-scout/`

L'installazione richiede HTTPS: GitHub Pages lo fornisce in automatico.

## Installare l'app

- **iPad / iPhone (Safari):** apri il link → pulsante Condividi → *Aggiungi a Home*.
- **Tablet / telefono Android (Chrome):** apri il link → menu ⋮ → *Installa app* (o *Aggiungi a schermata Home*).
- **PC (Chrome / Edge):** icona di installazione nella barra degli indirizzi.

Dopo la prima apertura con connessione, l'app funziona anche senza rete.

## Salvataggio dei dati

Tutto viene salvato automaticamente nel browser del dispositivo (`localStorage`):
giocatori, avversari, convocati, tiri, statistiche, minuti, zona da 3 punti.

- Chiudendo e riaprendo l'app ritrovi la partita com'era.
- I dati restano **solo su quel dispositivo**: un altro tablet o un altro browser parte da zero.
- Se cancelli i dati del sito dalle impostazioni del browser, i dati vanno persi.
- Per iniziare una nuova partita: ingranaggio ⚙ → **Azzera dati partita**
  (azzera tiri, statistiche e minuti; giocatori, avversari e convocati restano).

## Aggiornare l'app

Sostituisci `index.html` nel repository e fai commit. Per forzare l'aggiornamento sui dispositivi
che hanno già l'app, cambia anche `CACHE` in `sw.js` (per esempio da `basket-scout-v3` a `basket-scout-v4`).
I dati salvati non vengono toccati.

## Provarla in locale

```bash
python3 -m http.server 8080
```
poi apri `http://localhost:8080` (il service worker funziona anche su localhost).
