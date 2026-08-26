# Art History

Percorso autonomo e stratificato di storia dell'arte, costruito per una formazione ampia ma non specialistica, con particolare attenzione al moderno/contemporaneo e al rapporto con la pratica artistica.

## ▶ Inizia qui

### Mese 1 — Grecia → Roma → Cristianesimo/Bisanzio → Dal Medioevo a Giotto
- [Pagina operativa](programma/mese.html?m=01)
- [Fonte didattica canonica Markdown](programma/mese-01.md)

La pagina operativa carica direttamente il Markdown del mese e aggiunge tracker, Firebase, appunti, Quaderno, stati, link elaborati, feedback e revisione ChatGPT. Non esiste più una seconda copia didattica HTML da mantenere a mano.

## Prima di creare o modificare un mese
Leggere **[programma/STRUTTURA_STANDARD.md](programma/STRUTTURA_STANDARD.md)**. È la specifica corrente e prevale sulle vecchie convenzioni della repo.

## Architettura attuale
- `index.html` — homepage GitHub Pages.
- `programma/mese-XX.md` — **unica fonte canonica** di ogni mese.
- `programma/mese.html` — renderer comune per tutti i mesi (`?m=01`, `?m=02`, ecc.).
- `programma/mese-01.html` — solo redirect di compatibilità verso il renderer comune.
- `fonti/` — criteri e fonti ricorrenti.
- `appunti/` — documentazione sul sistema degli appunti; i contenuti personali effettivi sono in Firestore.
- `esercizi/` — metodo per analisi ed esercitazioni pratiche.
- `portfolio/` — criteri per selezionare produzioni e lavori.
- `verifiche/` — verifiche e sintesi di fine mese.

## Come creare il Mese 2
1. Leggere `programma/STRUTTURA_STANDARD.md` e `programma/mese-01.md`.
2. Creare `programma/mese-02.md` con i marcatori `<!-- task:... -->` per le attività obbligatorie e `<!-- study-tools:... -->` per i quaderni.
3. Non creare un nuovo HTML didattico: `programma/mese.html?m=02` funzionerà con lo stesso renderer.
4. Aggiungere il Mese 2 a `index.html`.
5. Verificare i link essenziali prima della pubblicazione.

## Metodo
Il percorso procede per strati successivi: prima una mappa ampia e riconoscibile della storia dell'arte, poi ritorni selettivi che aumentano la profondità. L'obiettivo non è esaurire ogni autore, ma riconoscere opere e trasformazioni fondamentali, leggere criticamente le immagini e tradurre alcuni problemi storici nella pratica artistica.

Le fonti hanno funzioni diverse: Smarthistory come asse storico-visivo; Heilbrunn Timeline/The Met come secondo asse cronologico-geografico e tecnico; Treccani per critica e metodo in italiano; OpenLearn quando aggiunge teoria trasversale. I contenuti sono distinti in **essenziali**, **approfondimenti consigliati** e **supporti visivi**.

## Dati e sincronizzazione
- Hosting: GitHub Pages.
- Dominio: `https://arte.3colors.it`.
- Autenticazione: Firebase Authentication / Google.
- Database: Cloud Firestore.
- I dati personali non vengono salvati nella repo pubblica.
- Progressi, appunti, elaborati, stati, link e feedback vengono salvati sotto il ramo Firestore dell'utente autenticato.

## Regola per nuove chat/agenti
Non ricostruire il progetto da questa README soltanto: leggere sempre `programma/STRUTTURA_STANDARD.md` e il mese precedente prima di creare il successivo.