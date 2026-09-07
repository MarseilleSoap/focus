# GHISA — Log Allenamenti

App personale di tracking allenamenti. File statici, nessun build richiesto.

## Deploy su GitHub + Vercel

1. **Crea il repository**
   - Vai su [github.com/new](https://github.com/new)
   - Nome repo: `ghisa` (o quello che preferisci), può essere privato
   - Crea il repository vuoto

2. **Scarica le 3 librerie locali (una volta sola)**
   - Apri questi 3 link nel browser, poi da ciascuno fai "Salva pagina con nome" (o click destro → Salva link con nome) salvando ESATTAMENTE con questi nomi:
     - https://unpkg.com/react@18/umd/react.production.min.js → salva come `react.production.min.js`
     - https://unpkg.com/react-dom@18/umd/react-dom.production.min.js → salva come `react-dom.production.min.js`
     - https://unpkg.com/@babel/standalone/babel.min.js → salva come `babel.min.js`
   - Metti questi 3 file dentro una cartella chiamata `vendor` (dentro la cartella del progetto, insieme agli altri file)

3. **Carica i file**
   - Nella pagina del repo appena creato, clicca "uploading an existing file"
   - Trascina dentro: `index.html`, `manifest.json`, `icon.svg`, `sw.js`, e la cartella `vendor` con i 3 file al suo interno (GitHub mantiene la struttura delle cartelle trascinate)
   - Commit

4. **Collega Vercel**
   - Vai su [vercel.com](https://vercel.com) e accedi con il tuo account GitHub
   - "Add New..." → "Project"
   - Seleziona il repository `ghisa`
   - Non serve configurare nulla (nessun framework, nessun build command) — lascia tutto di default e clicca "Deploy"

5. **Ottieni il link**
   - Dopo ~30 secondi Vercel ti dà un URL tipo `ghisa-tuonome.vercel.app`
   - Aprilo su Chrome Android

6. **Installa sul telefono**
   - Su Chrome Android, apri il link
   - Tocca i tre puntini in alto a destra → "Installa app" (o "Aggiungi a schermata Home")
   - Ti compare l'icona GHISA sulla home, si apre a schermo intero come un'app vera

## Aggiornare l'app in futuro

Ogni volta che vuoi una modifica:
1. Chiedimela in chat, ti do il file `index.html` aggiornato
2. Vai sul repository GitHub → apri `index.html` → matita "Edit" in alto a destra
3. Incolla il contenuto nuovo, Commit
4. Vercel ripubblica da solo in ~30 secondi, l'icona sul telefono si aggiorna automaticamente al prossimo apertura

## Note tecniche

- I dati (allenamenti, record, traguardi) sono salvati nel `localStorage` del browser del telefono — restano lì finché non cancelli i dati del sito da Chrome. Non si sincronizzano tra più dispositivi.
- L'app funziona interamente offline dopo il primo caricamento: React, ReactDOM e Babel sono file locali (cartella `vendor/`) e vengono messi in cache dal service worker insieme al resto — nessuna richiesta di rete a caricamento avvenuto, nessun font esterno.
- Nessuna dipendenza da build: tutto gira come file statici, nessun npm/webpack richiesto.
- Se in futuro aggiorni `sw.js`, cambia il numero di versione in `CACHE_NAME` (es. `ghisa-cache-v3`) per forzare l'aggiornamento della cache sul telefono.
