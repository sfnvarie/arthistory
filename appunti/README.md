# Appunti

Gli appunti personali NON devono essere salvati nella repo pubblica.

Nel sito operativo ogni capitolo/settimana ha:
- **Appunti personali**: note brevi, dubbi, concetti, collegamenti.
- **Quaderno di lavoro**: spazio ampio per esercizi, testi, riflessioni e sviluppi più lunghi.

Quando l'utente è autenticato con Google, questi contenuti vengono salvati in Cloud Firestore sotto il proprio ramo utente e sincronizzati tra dispositivi. Senza login esiste solo il fallback locale del browser.

Struttura logica corrente nel documento mensile Firestore:
- `notes`: appunti brevi;
- `work`: elaborati lunghi/quaderno;
- `statuses`: stato del lavoro;
- `links`: collegamenti a file, immagini o video;
- `feedback`: revisioni ricevute.

Per qualunque modifica futura leggere `../programma/STRUTTURA_STANDARD.md`.