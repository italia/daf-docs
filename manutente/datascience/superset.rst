*******************************
Data Visualization con Superset
*******************************

`Superset <https://github.com/apache/incubator-superset>`_ è un'applicatione Web open-source di Business Intelligence, sviluppata da AirBnB, con cui è possibile creare grafici ('slices' nel gergo di Superset), dashboard ed eseguire query SQL.
Superset è stato integrato con il DAF per offrire agli utenti la possibilità di creare le proprie analisi e condividerle con la community in modalità self-service.

Questa sezione è pensata per fornire indicazioni utili alla creazione di tabelle e grafici.
Per approfondimenti sulle funzionalità e sulle modalità d'uso di Superset, si rimanda alle documentazione suggerita nella sezione 'Risorse Utili' di questa guida.

========================================
Configurazione e aggiunta  di un dataset
========================================
Un utente può accedere alla homepage di Superset direttamente dal Dataportal e utilizzarlo per creare datastories e dashboard che integrano le analisi realizzate.
Nel menù laterale sinistro della sezione privata del Dataportal è infatti presente un pulsante 'Business Intelligence' (:superset:`/`) che abilita l'accesso a Superset.
Una volta entrati in Superset, si accede alla lista delle dashboard create nell'ambito dell'organizzazione a cui afferisce l'utente che ha effettuato l'accesso.
Superset adotta infatti un approccio self-service: questo significa che ciascun utente, da un lato, potrà provvedere alla creazione delle nuove tabelle utili alle analisi, dei grafici e delle dashboard; dall'altro potrà riutilizzare le tabelle, i grafici e le dashboard creati dalla community.
Chiaramente quest'ultima possibilità impone anche una certa disciplina nell'uso dello strumento, per evitare di interferire con le analisi fatte dagli altri utenti dell'organizzazione.

Il primo step nell'uso di Superset consiste nell'individuazione dei dataset oggetto di analisi.
Nella homepage selezionare la voce 'Tables' dal menu a tendina 'Sources'.

.. image:: img_superset/conf_tableadd_1.jpeg

Comparirà la lista delle tabelle precedentemente importate dall'utente, o da un altro membro della sua organizzazione, dai database già configurati in Superset [1]_.

Scorrendo la lista è possibile trovare e selezionare la tabella che contiene il dataset di interesse, anche aiutandosi, all'occorrenza, con i filtri attivabili cliccando sul bottone in alto a destra 'Add Filter'.

.. image:: img_superset/conf_tableadd_2.jpeg

Alternativamente, è possibile importare una nuova tabella.
Una volta individuato il dataset di interesse utilizzando il Dataportal, sarà necessario copiare il riferimento al dataset presente nelle schede di dettaglio del dataset stesso.
Tornado nella sezione Tables su Superset, cliccare sul bottone '+' in alto a destra.
Si aprirà la pagina 'Add Table' in cui sarà possibile selezionare il database di interesse ('opendata' nel caso di esempio) e indicare il nome della tabella che sarà il riferimento precedentemente copiato dalla scheda informativa del dataset.
Infine, cliccare sul bottone 'Save' in basso a sinistra.

.. image:: img_superset/conf_tableadd_3.jpeg

Nel caso in esempio, è stato selezionato il dataset dei luoghi della cultura di Matera.


================================
Esplorare un dataset con SQL Lab
================================

Prima di costruire un grafico, si consiglia di analizzare il contenuto del dataset scelto.
Superset offre nativamente una console per eseguire query SQL, a cui si può accedere cliccando su 'SQL Lab' e poi su 'SQL Editor'.

.. image:: img_superset/conf_sqllab_1.jpeg


=================================
Creazione di un grafico ('Slice')
=================================

Il prossimo step è creare un grafico con il dataset importato.
Come appena visto, utilizzando 'SQL Editor', il dataset contiene informazioni georeferenziate sui luoghi della cultura di Matera, per cui potrebbe essere una buona idea graficarle su una mappa utilizzando l'integrazione con MapBox.

A tal fine, cliccare sul menu 'Slices' posto nella barra in alto: comparirà l'elenco di slices già creati.
Anche in questo caso è possibile utilizzare filtri per cercare il grafico di interesse.
Per crearne uno nuovo, cliccare il bottone '+' in alto a destra.

.. image:: img_superset/conf_sliceadd_1.jpeg

Comparirà un menu dove si dovrà indicare la tabella da cui prendere i dati ('datasource'), e il tipo di visualizzazione da utilizzare.
Per graficare su una mappa selezionare 'Matbox'.
Infine cliccare sul bottone in basso a sinistra 'Create New Slice'.

.. image:: img_superset/conf_sliceadd_2.jpeg

L'ultimo step consiste nel configurare il grafico.
Nel caso in esempio vanno impostate le seguenti informazioni:

* latitudine e longitudine
* 'label', ovvero il testo che comparirà all'interno del punto disegnato sulla mappa
* 'Viewpoint' con le informazioni di latitudine, longitudine e zoom di default che verranno utilizzate per la visualizzazione iniziale.

Infine, eseguire la query che aggiorna il grafico, cliccando sul bottone 'Query' in alto a sinistra, e salvare la 'slice' cliccando sul pulsante 'Save'.

.. image:: img_superset/conf_sliceadd_3.jpeg


==========================
Creazione di una dashboard
==========================

Le dashboard sono aggregazioni di 'slices' utili a tenere su un unico pannello i grafici di interesse.
Per creare una dashboard in Superset occorre:

* Cliccare sul menu 'Dashboard' in alto
* Cliccare sul pulsante '+' in alto a sinistra
* Compilare i campi con le informazioni utili per la dashboard, come 'Title', 'Slug'(per rendere richiamabile tramite un url la dashboard), 'Slices' (in cui elencare le slices che si vuole utilizzare nella dashboard; nel caso in esempio abbiamo selezionato 'Matera - Luoghi Cultura' e 'Heatmap') e 'Owners' (in cui indicare chi puó contribuire alla dashboard).
* Cliccare il bottone 'Save' in basso a sinistra.

.. image:: img_superset/conf_dashboardadd_1.jpeg



=============
Risorse utili
=============

Superset è un tool molto potente e, conseguentemente, complesso.
Per utilizzare in pieno le sue funzionalità si rimanda a guide specifiche sul tema, di cui si riportano alcuni riferimenti non esaustivi.

* https://superset.incubator.apache.org/
* http://de.straba.us/2017/08/15/creare-dashboard-con-superset/


.. [1] il DAF propone alcune tabelle pre-caricate a beneficio degli utenti che vogliono familiarizzare con Superset
