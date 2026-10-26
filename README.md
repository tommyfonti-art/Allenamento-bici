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

## PDF per il coach

Nella pagina **Allenamento**, il riquadro **Per il coach** crea un PDF con tutte le schede di allenamento: per ogni esercizio ripetizioni e kg di ogni serie, più le note scritte da te. I valori vengono dalla seduta in corso (sul telefono o online); se una scheda non ne ha, usa l'ultima seduta salvata. Il PDF si può condividere (dove il telefono lo permette), aprire o scaricare. È scritto direttamente dall'app, senza librerie esterne.

## Aggiornamenti

Per qualsiasi modifica (nuovi allenamenti, correzioni, nuove sezioni), basta chiederlo a Claude nella chat di Claude: aggiorna il codice e lo pubblica qui.
