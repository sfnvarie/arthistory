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
- Italiano quando la qualità è adeguata; inglese accettabile per materiali molto buoni.
- Smarthistory: asse storico-visivo principale.
- Heilbrunn Timeline of Art History (The Met): secondo asse strutturale, soprattutto per contesto cronologico/geografico e saggi collegati alle opere.
- Treccani e testi italiani affidabili: critica, teoria, metodo.
- OpenLearn: teoria trasversale quando aggiunge qualcosa; non va ripetuto per coprire la stessa materia già affrontata altrove.
- Musei e archivi visivi autorevoli possono essere usati per riconoscimento e osservazione ad alta risoluzione.
- Libri: pochi e scelti, per continuità e profondità. Non aggiungere manuali generali solo per aumentare la bibliografia.
- Video: distinguere **Essenziali** e **Approfondimenti consigliati**. Gli approfondimenti validi non vanno eliminati solo per mantenere artificiosamente basso il carico; non contano però nel progresso obbligatorio.
- Evitare duplicazioni tra piattaforme se non portano un punto di vista realmente diverso.
- Prima di pubblicare un mese, verificare i link esterni essenziali.

## Unica fonte e generazione del sito
NON mantenere manualmente due versioni indipendenti dello stesso mese.

- `programma/mese-XX.md` è l'**unica fonte didattica canonica**: contenuti, link, consegne, classificazione essenziale/consigliato, opere e verifiche si modificano qui.
- Le pagine HTML mensili sono **output generati** dal Markdown tramite un template/interfaccia comune.
- Il template comune contiene presentazione, Firebase, login, progressi, appunti, Quaderno, stati, link, feedback e revisione ChatGPT.
- Un generatore/build deve produrre le pagine HTML e, preferibilmente, aggiornare anche la home/index dei mesi.
- Non correggere a mano un HTML generato per cambiare contenuti didattici: correggere il Markdown e rigenerare.
- Durante la migrazione il vecchio `mese-01.html` può restare operativo come riferimento, ma non deve diventare una seconda fonte da mantenere.

## Sito
- GitHub Pages pubblica la repo.
- Dominio: `https://arte.3colors.it`.
- Homepage: `index.html`.
- Ogni nuovo mese deve comparire nella homepage; idealmente questo indice viene aggiornato dal build.

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
Ogni pagina mensile generata deve avere:
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

## Regole didattiche emerse dal Mese 1
- Costruire ogni mese attorno a trasformazioni leggibili, non a una successione di nomi.
- Riutilizzare confronti tra settimane per creare continuità (es. Grecia → Roma → Bisanzio).
- Coprire più media quando sono storicamente decisivi: non ridurre la Grecia alla sola scultura; includere pittura vascolare, disegno e narrazione.
- Per Roma rendere esplicita la specificità architettonico-ingegneristica: arco, volta, cupola, calcestruzzo e costruzione dello spazio.
- Il passaggio tardoantico/cristiano non va presentato come semplice decadenza del naturalismo: frontalità, gerarchia e riduzione della profondità vanno lette anche come scelte funzionali e simboliche.
- Se una settimana comprime troppi secoli, dichiararne il carattere di ponte oppure redistribuire il carico. Nel Mese 1 Romanico/Gotico sono un ponte selettivo verso Giotto, non una trattazione autonoma esaustiva.
- Graduare la difficoltà degli esercizi pratici e tenere conto del carico complessivo della settimana.

## Stato attuale
Il Mese 1 esiste ancora in Markdown e HTML. Il Markdown deve diventare la fonte unica; l'HTML corrente implementa già Firebase e serve come riferimento funzionale per il template/generatore. Prima di costruire il Mese 2 va completata questa migrazione, così da non introdurre nuova doppia manutenzione.