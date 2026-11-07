# BLUFF-HAUS MANIA

Gioco completo in **un solo file** (`index.html`): codice, audio, 60 medaglioni, icona e manifest sono già dentro.
Non serve nessuna build e nessun server tuo. Le stanze online sono peer-to-peer (WebRTC con PeerJS), uguali per iPhone, Android e computer.

## File
| File | A cosa serve |
|---|---|
| `index.html` | Il gioco. È l'unico file necessario per pubblicare |
| `icons/icon-512.png`, `icon-192.png` | Icone dell'app (Android / installazione) |
| `icons/apple-touch-icon.png` | Icona per la schermata Home di iPhone |
| `icons/favicon-64.png` | Icona della scheda del browser |
| `medaglioni-60-anteprima.png` | Anteprima dei 60 medaglioni (solo per guardarli) |

Le icone PNG sono già incorporate dentro `index.html`: le trovi anche come file separati per usarle altrove (social, logo, store). Pubblicare solo `index.html` funziona.

## 1. Provarlo sul tuo computer (Visual Studio Code)
1. Apri la cartella in **VS Code** (File → Apri cartella).
2. Installa l'estensione **Live Server**, poi tasto destro su `index.html` → *Open with Live Server*.
   In alternativa, dal terminale: `npx serve`.

Non aprirlo con doppio clic: le stanze online richiedono un indirizzo `http(s)://`.

## 2. Mettere il progetto su GitHub (da VS Code)
1. Menu laterale **Source Control** → *Initialize Repository*.
2. Scrivi un messaggio (es. `prima versione`) → **Commit**.
3. **Publish Branch** → *Public* o *Private*, nome es. `bluff-haus-mania`.

Da terminale, in alternativa:
```
git init
git add .
git commit -m "prima versione"
git branch -M main
git remote add origin https://github.com/TUO-UTENTE/bluff-haus-mania.git
git push -u origin main
```

## 3. Pubblicare su Vercel
1. Vai su **vercel.com** → accedi con GitHub → **Add New… → Project**.
2. Scegli il repository → **Import**.
3. *Framework Preset*: **Other**. Lascia vuoti *Build Command* e *Output Directory*.
4. **Deploy**. In circa un minuto hai l'indirizzo `https://…vercel.app`.

Ogni *Commit + Push* su GitHub ripubblica da solo. Il file deve chiamarsi `index.html` e stare nella cartella principale.

## 4. Prova iPhone ↔ Android (consigliata prima di annunciarlo)
1. **iPhone**: apri il sito → scegli un gioco → *Create room* → annota il codice di 6 caratteri.
2. **Android**: apri lo stesso indirizzo → *Join with code* → inserisci il codice.
3. Ripeti invertendo i ruoli, poi con uno dei due su **rete dati mobile** e l'altro su Wi-Fi.

Se un gruppo di giocatori non riesce a connettersi (succede con alcuni operatori mobili), apri `index.html` e, in cima al file, trova il blocco commentato `OPZIONALE`: togli le due barre davanti alla riga `window.BH_ICE` e inserisci un tuo server TURN (es. piano gratuito di metered.ca). Poi *Commit + Push*.

## Note
- Il gioco carica **PeerJS** da `cdn.jsdelivr.net` e il font da Google Fonts: serve una connessione internet.
- Amici, classifica e invio BH funzionano tra dispositivi online nello stesso momento: i dati stanno sul telefono di ciascuno, non su un server.
- Il wallet è salvato nel browser: cancellare i dati del sito lo azzera.
