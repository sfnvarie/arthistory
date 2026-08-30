# Struttura standard dei mesi — specifica operativa

Questo file è la fonte di verità per creare o modificare i mesi del progetto **ArtHistory**. Una nuova chat o un agente deve leggerlo prima di intervenire.

## Obiettivo generale
Percorso autonomo e stratificato di storia dell'arte: prima una mappa ampia e solida, poi ritorni successivi di approfondimento. Evitare sia il manuale enciclopedico sia il percorso troppo superficiale. Il moderno/contemporaneo avrà spazio importante nei mesi successivi.

Il percorso costruisce in parallelo anche una **cronologia essenziale della filosofia e delle idee**, perché i problemi filosofici aiutano a contestualizzare le trasformazioni artistiche. Il rapporto arte ↔ filosofia va però formulato con rigore: distinguere sempre contemporaneità culturale, analogia di problemi e influenza storicamente documentata. Non trasformare semplici parallelismi in rapporti causali.

## Formato didattico obbligatorio
Ogni mese deve contenere:
1. Tesi/filo trasformativo del mese.
2. Obiettivo del mese.
3. Cosa bisogna sapere alla fine.
4. Libro/i di accompagnamento, se utili.
5. Capitoli/settimane con: Obiettivi; Dove studiare; Video essenziali; **Filosofia e idee del tempo**; Approfondimenti consigliati; Supporti visivi quando utili; Analisi/critica; Opere da riconoscere; Esercitazione di analisi; Esercitazione pratica artistica; Cosa sapere a fine capitolo; strumenti di appunti/quaderno.
6. Verifica storico-visiva.
7. **Linea del tempo Arte ↔ Filosofia**.
8. Verifica critica.
9. Portfolio pratico.
10. Sintesi finale e criterio di completamento.

## Regola di copertura dei periodi
Se una settimana dichiara esplicitamente un confronto tra due periodi o stili, **entrambi devono essere realmente studiati prima dell'esercizio**. Non basta che il secondo compaia solo nell'opera da confrontare o in una domanda finale.

Esempio guida: se si chiede **Classico vs Ellenismo**, il capitolo deve contenere almeno un materiale essenziale che spieghi l'Ellenismo, opere ellenistiche osservabili e il relativo contesto storico/filosofico. Il confronto non deve essere lasciato all'inferenza dello studente.

Prima di chiudere un capitolo verificare sempre: «Ogni concetto richiesto negli esercizi e nella verifica è stato prima introdotto con materiale sufficiente?».

## Filosofia e idee del tempo — regola permanente
Ogni capitolo deve includere una sezione breve e selettiva **Filosofia e idee del tempo** con:
- filosofi/scuole cronologicamente pertinenti;
- 2–4 concetti chiave utili a comprendere il clima culturale;
- almeno un riferimento puntuale studiabile quando il nesso è importante;
- un'indicazione esplicita di **come usare** quel riferimento per guardare le opere;
- distinzione fra influenza documentata e semplice confronto interpretativo.

La sezione non deve diventare un secondo corso completo di filosofia. Nel primo strato serve a costruire una mappa parallela: nomi, successione, concetti e nessi fondamentali. Nei ritorni successivi si approfondiscono i filosofi davvero decisivi per estetica e arti.

Esempi di linea progressiva da tenere presente: Socrate/Platone/Aristotele → scuole ellenistiche → neoplatonismo e pensiero cristiano → Agostino/Tommaso → Umanesimo e neoplatonismo rinascimentale → razionalismo/empirismo → Illuminismo/Kant → idealismo/Hegel → Marx/Nietzsche → Freud → fenomenologia/Benjamin/Heidegger e pensiero del Novecento, secondo pertinenza con i periodi artistici studiati.

## Fonti e criterio di selezione
- Preferire materiale puntuale e realmente studiabile, non homepage generiche.
- Italiano quando la qualità è adeguata; inglese quando il materiale è nettamente migliore.
- **Smarthistory**: asse storico-visivo principale.
- **Heilbrunn Timeline of Art History / The Met**: secondo asse strutturale, soprattutto per contesto cronologico-geografico, tecniche, oggetti e saggi collegati a opere reali.
- **Treccani e testi italiani affidabili**: critica, teoria, metodo e riferimenti filosofici quando adeguati.
- **OpenLearn**: teoria trasversale quando aggiunge qualcosa; non duplicare una materia già coperta bene altrove.
- **Musei e archivi visivi autorevoli**: supporto ad alta risoluzione per osservazione e riconoscimento; non trasformarli automaticamente in nuove letture obbligatorie.
- **Web Gallery of Art / Google Arts & Culture**: supporti visivi, soprattutto per Medioevo/Rinascimento e opere osservabili in dettaglio; non fonti teoriche principali.
- Libri: pochi e scelti. Non aggiungere un secondo manuale generale solo per aumentare la bibliografia.
- Distinguere sempre **Essenziali**, **Approfondimenti consigliati** e **Supporti visivi**.
- Un nuovo materiale entra solo se copre un buco, sostituisce una fonte peggiore o aggiunge un punto di vista realmente distinto.
- Prima di pubblicare un mese, verificare i link esterni essenziali.

## Unica fonte canonica: niente doppia manutenzione
`programma/mese-XX.md` è l'**unica fonte didattica canonica**.

Non mantenere più due versioni indipendenti Markdown + HTML.

### Rendering operativo
- `programma/mese.html` è il renderer comune riutilizzabile.
- Si apre con `programma/mese.html?m=XX`.
- Il renderer carica `mese-XX.md`, lo trasforma in pagina operativa e aggiunge Firebase, tracker, appunti e Quaderno.
- `mese-01.html` resta solo come redirect di compatibilità verso `mese.html?m=01`.
- Per un nuovo mese si crea **solo** `mese-XX.md` e si aggiunge il link alla home. Non copiare il vecchio HTML.

### Marcatori nel Markdown
Per rendere interattiva un'attività obbligatoria usare:

```md
<!-- task:w2-video1 -->
- [ ] Titolo attività — link
```

L'ID deve essere stabile nel tempo. Non rinumerare vecchi ID dopo che esistono progressi salvati.

Per inserire appunti + quaderno + stato + link + feedback usare alla fine di ogni capitolo:

```md
<!-- study-tools:w2 -->
```

Lo stesso schema vale per `w1`, `w2`, `w3`, `w4`, `final` e mesi futuri.

## Sito
- GitHub Pages pubblica la repo.
- Dominio: `https://arte.3colors.it`.
- Homepage: `index.html`.
- Ogni nuovo mese deve comparire nella homepage.
- I link esterni del corso devono aprirsi in una nuova scheda, così la pagina di studio resta aperta.

## Firebase
Progetto Firebase: `arthistory-658f3`.
Servizi usati: Firebase Authentication con Google + Cloud Firestore.

Struttura Firestore:
`users/{uid}/months/mese-XX`

Il documento mensile contiene almeno:
- `progress`;
- `notes`;
- `work`;
- `statuses` (`todo`, `doing`, `done`, `reviewed`);
- `links`;
- `feedback`;
- `updatedAt`.

Le regole Firestore devono consentire lettura/scrittura solo all'utente autenticato nel proprio ramo `users/{uid}/...`.

## Esperienza utente
Ogni mese renderizzato deve avere:
- login Google + logout;
- percentuale di avanzamento;
- checkbox sincronizzate tra dispositivi;
- fallback locale quando non autenticato;
- appunti brevi con autosalvataggio;
- editor ampio **Quaderno di lavoro**;
- stato elaborato;
- campo link foto/video/file;
- campo feedback/revisione;
- pulsante **Copia per revisione ChatGPT**;
- layout comodo da tablet e telefono, senza scorrimento orizzontale.

## Revisione AI
Non inserire chiavi OpenAI/API nel frontend pubblico. Flusso attuale:
1. svolgimento nel Quaderno;
2. `Copia per revisione ChatGPT`;
3. incolla in ChatGPT;
4. conserva il feedback ricevuto nel campo dedicato.

## Metodo degli esercizi
Gli esercizi devono tradurre problemi storico-artistici in pratica visiva/audiovisiva. Per ogni prova pratica: problema storico → scelta formale → risultato → cosa cambiare.

## Regole didattiche emerse dal Mese 1
- Costruire ogni mese attorno a trasformazioni leggibili, non a una successione di nomi.
- Riutilizzare confronti tra settimane per creare continuità.
- Coprire più media quando sono storicamente decisivi: la Grecia non può ridursi alla sola scultura; pittura vascolare, disegno e narrazione sono parte essenziale del primo strato.
- Il **Kritios Boy** è un passaggio essenziale perché rende visibile la transizione Arcaico → Classico prima del Doriforo.
- **L'Ellenismo va studiato esplicitamente** prima di chiedere un confronto Classico → Ellenismo: contesto dopo Alessandro, ampliamento dei soggetti, pathos, teatralità, movimento, realismo e coinvolgimento dello spettatore.
- La filosofia va mantenuta in parallelo alla cronologia artistica: per la Grecia classica Platone/Aristotele e il problema della mimesi; per l'Ellenismo stoicismo, epicureismo e altre scuole come contesto culturale, senza ridurre l'arte a illustrazione della filosofia.
- Per Roma rendere esplicita la specificità architettonico-ingegneristica: arco, volta, cupola, calcestruzzo e costruzione dello spazio interno.
- Il passaggio tardoantico/cristiano non va presentato come semplice decadenza del naturalismo.
- Se una settimana comprime troppi secoli, dichiararne il carattere di ponte. Nel Mese 1 Romanico/Gotico sono un ponte selettivo verso Giotto e verranno ripresi nei successivi strati.
- Graduare la difficoltà degli esercizi pratici; nella micro-sequenza di Giotto conta la chiarezza della relazione spaziale, non la complessità tecnica del montaggio.
- Non aggiungere fonti solo perché interessanti: completezza significa coprire i nodi importanti, non accumulare link.

## Stato attuale
Il Mese 1 è migrato al modello a fonte unica: `mese-01.md` contiene i contenuti aggiornati; `mese.html` li rende operativi. I mesi successivi devono partire da questa architettura.