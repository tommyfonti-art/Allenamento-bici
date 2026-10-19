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

## Schede modificabili

Nelle pagine **Allenamento** e **Fisio** il pulsante **Modifica schede** permette di creare, rinominare, duplicare, spostare ed eliminare le schede, e di aggiungere, cambiare, riordinare ed eliminare gli esercizi (nome, serie, ripetizioni, recupero in secondi, nota). Durante l'allenamento serie, ripetizioni e recupero sono solo in lettura. Le schede stanno nel documento `settings/schede` di Firestore (con una copia sul dispositivo).

## Sezioni personali (PDF, foto, appunti)

In **Impostazioni → Sezioni personali** si creano nuove voci del menu in alto (si rinominano, si eliminano e si spostano con le frecce di «Ordine del menu»). In ogni sezione si caricano PDF e foto (massimo 8 MB l'uno; le foto vengono ridotte a 2000 pixel), che si possono aprire, scaricare, rinominare ed eliminare, e c'è un riquadro per gli appunti. L'elenco delle sezioni sta in `settings/sezioni`; ogni documento sta in `documenti/{id}` e i suoi byte, divisi in parti da 800 KB, in `documenti_parti/{id}_{n}` (nessun bisogno di Firebase Storage).

## Aggiornamenti

Per qualsiasi modifica (nuovi allenamenti, correzioni, nuove sezioni), basta chiederlo a Claude nella chat di Claude: aggiorna il codice e lo pubblica qui.
