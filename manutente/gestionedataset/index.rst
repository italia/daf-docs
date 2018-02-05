****************
Gestione Dataset
****************
L'inserimento e la gestione dei dataset sul DAF è concesso a specifiche utenze dell'organizzazione che assumono il ruolo di *editor*. Tali operazioni possono essere eseguite sfruttando le funzionalità presenti nel menu *Azioni > Dataset*.

===============================
Inserimento di un nuovo dataset
===============================
La funzione *Carica* consente di definire un flusso di acquisizione per un nuovo dataset associato all'organizzazione. I dati dovranno poi essere caricati attraverso il canale che verrà istaurato. Al momento l'unica modalità accettata è quella batch su SFTP. A breve si potrà istruire il sistema per interrogare periodicamente un WS che espone il dataset.

Il cruscotto di registrazione di compone di 3 passi.

Nel primo è possibile caricare un file campione rappresentativo del dataset oggetto del flusso. Il tipo supportato al momento è il CSV, a breve sarà possibile caricare anche fil JSON. Questo permette al sistema di inferire la struttura del dataset (campi e tipi dei campi) e di proporla all'utente. In primo luogo indicare se il dataset è privato; in caso contrario, il dataset sarà automaticamente aggiunto tra quelli friubili liberamente al di fuori dell'organizzazione e come open data [1]_. Successivamente, per ogni campo del dataset è possibile indicare:

* tipo del campo: al momento non è possibile modificare quando inferito dal sistema
* concetto semantico: individuare nelle ontologie installate il concetto espresso dal campo; il sistema fornisce suggerimenti man mano che viene valorizzato
* descrizione: inserire una descrizione per il campo
* tags:
* obbligatorietà: indicare se il campo è obbligatorio o meno
* tipo della colonna: 

Per aiutare nella compilazione, un riquadro affiancato sul lato destro permette di visualizzare un campione dei valori contenuti nel file.

Nella seconda pagina fornire le seguenti informazioni:

* titolo: il titolo, l'identificativo univoco del dataset all'interno del DAF
* nome: nome del dataset
* descrizione: descrizione completa del dataset
* categoria: 
* licenza: tipo di licenza associata al dataset
* organizzazione: organizzazione alla quale il dataset appartiene, e che avrà visibilità su di esso se privato

Come ultimo passaggio, indicare:

* dominio
* sottodominio

al momento trascurare i seguenti:

* se il dataset definisce uno standard
* se il dataset segue uno standard
* il tipo di lettura del dataset
* il tipo di dataset

Al termine viene fornito un riepilogo, con l'indicazione del path SFTP sul quale è possibile caricare i dati. Il nuovo dataset è visibile nell'elenco mostrato cliccando sulla casella di ricerca presente in alto. Si ricordi però che non è presente ancora alcun dato.

Caricamento via SFTP
====================
L'host è ``daf.teamdigitale.governo.it (porta 22)`` al quale è possibile collegarsi con l'utente editor. Al primo accesso viene chiesto di modificare la password (il che modifica anche la password richiesta per accedere alla sezione privata del data portal).

Caricare il/i file relativi al dataset definito in precedenza al path che sarà stato creato dal sistema. La struttura segue la convenzione ``/home/utente/dominio/sottodominio/dataset/``.

Tutti i file che verranno man mano caricati in tale cartella incrementeranno il contenuto del dataset. Un processo in ascolto si occuperà di acquisire i file al massimo entro qualche minuto, in base alle dimensioni del file.

Caricamento con interrogazione di web service
=============================================
Disponibile a breve

===============================
Gestione dei propri dataset
===============================

Disponibile a breve


.. [1] funzionalità disponibile a breve