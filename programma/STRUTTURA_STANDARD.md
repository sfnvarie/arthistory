# Struttura standard dei mesi — specifica operativa

Questo file è la fonte di verità per creare o modificare i mesi del progetto **ArtHistory**. Una nuova chat o un agente deve leggerlo prima di intervenire.

## Obiettivo generale
Percorso autonomo e stratificato di storia dell'arte: prima una mappa ampia e solida, poi ritorni successivi di approfondimento. Evitare sia il manuale enciclopedico sia il percorso troppo superficiale. Il moderno/contemporaneo avrà spazio importante nei mesi successivi.

## Formato didattico obbligatorio
Ogni mese deve contenere:
1. Obiettivo del mese.
2. Cosa bisogna sapere alla fine.
3. Libro/i di accompagnamento, se utili.
4. Capitoli/settimane con: Obiettivi; Dove studiare; Video essenziali; Approfondimenti consigliati; Analisi/critica; Opere da riconoscere; Esercitazione di analisi; Esercitazione pratica artistica; Appunti personali; Quaderno di lavoro; Cosa sapere a fine capitolo.
5. Verifica storico-visiva.
6. Verifica critica.
7. Portfolio pratico.
8. Sintesi finale e criterio di completamento.

## Fonti e criterio di selezione
- Preferire materiale puntuale e realmente studiabile, non homepage generiche.
- Italiano quando la qualità è adeguata; inglese accettabile per materiali molto buoni, soprattutto Smarthistory.
- Smarthistory: asse storico-visivo principale.
- Treccani e testi italiani affidabili: critica, teoria, metodo.
- OpenLearn: teoria trasversale quando aggiunge qualcosa; non va ripetuto per coprire la stessa materia già affrontata altrove.
- Libri: pochi e scelti, per continuità e profondità.
- Video: distinguere **Essenziali** e **Approfondimenti consigliati**. Gli approfondimenti validi non vanno eliminati solo per mantenere artificiosamente basso il carico; non contano però nel progresso obbligatorio.
- Evitare duplicazioni tra piattaforme se non portano un punto di vista realmente diverso.

## Versioni dei mesi
Per ogni mese mantenere due file:
- `mese-XX.md`: fonte didattica leggibile e documentazione completa del programma.
- `mese-XX.html`: versione operativa del sito, mobile/tablet friendly.

Il Markdown NON è il tracker operativo. Le checkbox Markdown sono solo descrittive. Il tracciamento reale avviene nell'HTML.

## Sito
- GitHub Pages pubblica la repo.
- Dominio previsto/attivo: `https://arte.3colors.it`.
- Homepage: `index.html`.
- Ogni nuovo mese deve essere aggiunto alla homepage.

## Firebase
Progetto Firebase: `arthistory-658f3`.
Servizi usati:
- Firebase Authentication, provider Google.
- Cloud Firestore.

Dominio del sito deve essere autorizzato in Firebase Authentication.

Struttura Firestore corrente per ogni utente:
`users/{uid}/months/mese-XX`

Il documento mensile contiene almeno:
- `progress`: stato delle attività obbligatorie;
- `notes`: appunti brevi per capitolo;
- `work`: elaborati lunghi/quaderno;
- `statuses`: stato degli elaborati (`todo`, `doing`, `done`, `reviewed`);
- `links`: collegamenti a elaborati pratici/file esterni;
- `feedback`: revisioni ricevute;
- `updatedAt`.

Le regole Firestore devono consentire lettura/scrittura solo all'utente autenticato nel proprio ramo `users/{uid}/...`.

## Esperienza utente HTML
Ogni pagina mensile deve avere:
- login Google + logout;
- percentuale di avanzamento;
- checkbox sincronizzate tra dispositivi;
- fallback locale quando non autenticato;
- appunti brevi con autosalvataggio;
- editor ampio **Quaderno di lavoro** per testi/esercizi;
- stato dell'elaborato;
- campo link per foto/video/file;
- campo feedback/revisione;
- pulsante **Copia per revisione ChatGPT**, che copia consegna + elaborato + link + richiesta di revisione;
- layout comodo da tablet e telefono.

## Revisione AI
Non inserire chiavi OpenAI/API nel frontend pubblico. Al momento il flusso corretto è:
1. svolgimento nel Quaderno;
2. pulsante `Copia per revisione ChatGPT`;
3. incolla in ChatGPT;
4. feedback ottenuto può essere salvato nel campo `Feedback / revisione ricevuta`.

In futuro un'integrazione AI diretta richiede backend sicuro e va progettata separatamente.

## Metodo degli esercizi
Gli esercizi non devono sembrare compiti scolastici fini a se stessi. Devono tradurre problemi storico-artistici in pratica visiva/audiovisiva. Per ogni prova pratica: problema storico → scelta formale → risultato → cosa cambiare.

## Stato attuale
Il Mese 1 esiste in Markdown e HTML. L'HTML implementa già Firebase, progressi, appunti, quaderno, stati, link, feedback e copia per revisione ChatGPT. I mesi successivi devono partire da questa architettura, non dalla vecchia versione a sole checkbox/localStorage.