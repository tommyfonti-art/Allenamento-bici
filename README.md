# Allenamento e alimentazione

App personale per il percorso di 4 mesi con coach, nutrizionista e consulente bici.
Sito statico, nessuna build necessaria: `index.html` è tutta l'app.

## Come vederla online (GitHub Pages)

Dopo il primo push, su GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: main / (root)**.
L'indirizzo sarà `https://tommyfonti-art.github.io/allenamento-bici/`.

## Attivare il salvataggio (Firebase, gratuito)

Finché `firebase-config.js` ha i valori finti, l'app funziona ma "Salva allenamento / peso / fisio" non fa nulla di persistente.

1. Vai su [console.firebase.google.com](https://console.firebase.google.com), accedi col tuo account Google.
2. **Aggiungi progetto**, dagli un nome (es. `diario-4-mesi`), continua con le impostazioni di default.
3. Nel progetto: **Build → Firestore Database → Crea database** → scegli una regione europea (es. `eur3`) → modalità **test** (va bene per iniziare, va sostituita se un giorno l'app diventa pubblica a tutti).
4. **Impostazioni progetto** (icona ingranaggio) → **Generale** → scorri fino a **Le tue app** → clicca l'icona web `</>` → registra l'app (basta un nickname).
5. Ti mostra un blocco `firebaseConfig = {...}`: copia quei valori dentro `firebase-config.js` al posto dei placeholder.
6. Fai commit e push (o chiedi a Claude di farlo).

Da quel momento l'app salva davvero, su un database solo tuo.

## Struttura

- `index.html` — tutta l'app (markup, stile, logica)
- `firebase-config.js` — le tue chiavi Firebase (non committare quelle vere in un repo pubblico se ci tieni alla privacy: puoi rendere il repo privato)

## Aggiornamenti

Per qualsiasi modifica (nuovi allenamenti, correzioni, nuove sezioni), basta chiederlo a Claude nella chat di Claude: aggiorna il codice e lo pubblica qui.
