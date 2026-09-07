# GHISA — Log Allenamenti

App personale di tracking allenamenti. File statici, nessun build richiesto.

## Deploy su GitHub + Vercel

1. **Crea il repository**
   - Vai su [github.com/new](https://github.com/new)
   - Nome repo: `ghisa` (o quello che preferisci), può essere privato
   - Crea il repository vuoto

2. **Carica i file**
   - Nella pagina del repo appena creato, clicca "uploading an existing file"
   - Trascina dentro tutti i file di questa cartella: `index.html`, `manifest.json`, `icon.svg`, `sw.js`
   - Commit

3. **Collega Vercel**
   - Vai su [vercel.com](https://vercel.com) e accedi con il tuo account GitHub
   - "Add New..." → "Project"
   - Seleziona il repository `ghisa`
   - Non serve configurare nulla (nessun framework, nessun build command) — lascia tutto di default e clicca "Deploy"

4. **Ottieni il link**
   - Dopo ~30 secondi Vercel ti dà un URL tipo `ghisa-tuonome.vercel.app`
   - Aprilo su Chrome Android

5. **Installa sul telefono**
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
- L'app funziona anche offline dopo il primo caricamento (service worker con cache base).
- Nessuna dipendenza da build: React, Babel e i font sono caricati da CDN direttamente nell'HTML.
