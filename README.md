# Art History

Percorso autonomo e stratificato di storia dell'arte, costruito per una formazione ampia ma non specialistica, con particolare attenzione al moderno/contemporaneo e al rapporto con la pratica artistica.

## ▶ Inizia qui

### Mese 1 — Grecia → Roma → Cristianesimo/Bisanzio → Medioevo/Giotto
- [Versione operativa HTML](programma/mese-01.html)
- [Fonte didattica Markdown](programma/mese-01.md)

La versione HTML è quella da usare quotidianamente: progressi, appunti e quaderno di lavoro sono sincronizzati tramite Firebase quando si accede con Google.

## Prima di creare o modificare un mese
Leggere **[programma/STRUTTURA_STANDARD.md](programma/STRUTTURA_STANDARD.md)**. È la specifica corrente e prevale sulle vecchie convenzioni della repo.

## Architettura attuale
- `index.html` — homepage GitHub Pages.
- `programma/` — programma didattico e pagine HTML operative.
- `fonti/` — criteri e fonti ricorrenti.
- `appunti/` — documentazione sul sistema degli appunti; gli appunti effettivi dell'utente sono salvati in Firestore, non nella repo pubblica.
- `esercizi/` — metodo per analisi ed esercitazioni pratiche.
- `portfolio/` — criteri per selezionare produzioni e lavori.
- `verifiche/` — verifiche e sintesi di fine mese.

## Metodo
Il percorso procede per strati successivi: prima una mappa ampia e riconoscibile della storia dell'arte, poi ritorni selettivi che aumentano la profondità. L'obiettivo non è esaurire ogni autore, ma riconoscere opere e trasformazioni fondamentali, leggere criticamente le immagini e tradurre alcuni problemi storici nella pratica artistica.

Per i materiali video si distinguono **essenziali** e **approfondimenti consigliati**. Gli approfondimenti possono essere numerosi se realmente validi, ma non devono pesare sul completamento obbligatorio del mese.

## Dati e sincronizzazione
- Hosting: GitHub Pages.
- Dominio: `arte.3colors.it`.
- Autenticazione: Firebase Authentication / Google.
- Database: Cloud Firestore.
- I dati personali non vengono salvati nella repo pubblica.
- Progressi, appunti, elaborati, stati, link e feedback vengono salvati sotto il ramo Firestore dell'utente autenticato.

## Regola per nuove chat/agenti
Non ricostruire il progetto da questa README soltanto: leggere sempre `programma/STRUTTURA_STANDARD.md` e il mese precedente prima di creare il successivo.