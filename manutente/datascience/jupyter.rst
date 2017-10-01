Datascience con Jupyter Notebook
********************************

============
Introduzione
============       
 
`Jupyter Notebook <http://jupyter.org/>`_ è un tool open-source che permette di eseguire codice in maniera interattiva. É diventato uno standard de facto per data science perché offre la possibilità di sviluppare analisi dati, generare grafici, costruire modelli di machine learning e molto altro, con i tuoi linguaggi di programmazione preferiti.

Abbiamo integrato Jupyter con la piattaforma big data del DAF cosi che si possa facilmente avere accesso ai dati disponibili, fare analisi e condividerle con la community. Jupyter vi permetterà di dialogare direttamente con il cluster Spark sia in Scala che in Python.

Questo breve How-To è pensato per fornire le informazioni basilari per configurare un notebook Jupyter utile per effettuare analisi sui dataset contenuti nel DAF, utilizzando la capacità di calcolo del cluster Spark.

Molti degli open data resi disponibili sono di modeste entità, per cui utilizzare Spark potrebbe sembrare (e di fatto lo è) come sparare ad una mosca con un cannone. Il vantaggio di questo approccio è quello di utilizzare un unico framework di analisi che si presta a scalare nativamente, ed è utile in caso di analisi che hanno bisogno di 'unire' congiuntamente molti dataset, il tutto fatto all'interno della stessa piattaforma. Per analisi più semplici, si consiglia di scaricare il dataset sulla propria macchina e utilizzare strumenti di analisi come Python (panda + scikit) o R.

==============
Configurazione
============== 
Il notebook del DAF è disponibile a questo indirizzo: `http://jupyter.org <http://jupyter.org/>`_
Una volta effettuato il login con le credenziali fornite per il dataportal, entrerete nella vostra home, che conterrà i notebook che avete creato (al primo accesso la home sarà vuota). 

Per iniziare una nuova analisi, la prima cosa da fare è scegliere l'ambiente di sviluppo (kernel) fra quelli disponibili, cliccando sul pulsante 'new' in alto a destra. Avete a disposizione le seguenti possibilità:

* 'PySpark': Notebook Python 2 integrato con Spark
* 'PySpark3': Notebook Python 3 integrato con Spark
* 'Python 3': Notebook Python
* 'Spark': Notebook Scala integrato con Spark
* 'SparkR': Notebook R integrato con Spark

.. image:: img_jupyter/conf_choosekernel.jpeg

Una volta effettuata la scelta, si aprirà un nuovo tab nel browser con il vostro nuovo notebook. La prima cosa da fare e' configurare la connessione al cluster Spark del DAF, specificando l'endpoint del server Livy e le vostre credenziali di accesso (Nelle prossime release, forniremo un semplice script che vi permetterà di effettuare questa operazione solo una volta, al momento dovrete autenticarvi presso il server ogni volta che aprite un nuovo notebook. We'll keep you posted!). Per fare ciò, eseguite i seguenti comandi nel primo quadrante disponibile, ed eseguite premendo [shift] + [invio]

.. image:: img_jupyter/conf_livyaddendpoint.jpeg

Si aprirà un pannello come mostrato in figura: cliccate nel tab 'Add Endpoint' e inserite le seguenti informazioni:

* Address: http://livy:8998
* Auth type: Basic_Access
* Username: il vostro username
* Password: la vostra password

Aggiungerete la configurazione cliccando il pulsante a destra (accanto a Password) 'Add Endpoint'. Ora spostatevi nel tab 'Create Session', scegliete nel menu a tendina 'Endpoint' l'endpoint che avete configurato sopra (http://livy:8998), date un nome alla sessione che state creando utilizzando il campo 'Name', scegliete il linguaggio che adeguato per il vostro notebook (nel nostro caso 'scala'), e cliccate il pulsante in fondo a destra 'Create Session'. Questa operazione, che durerà qualche decina di secondi, attiverà il collegamento con il cluster Spark con il quale sarete pronti a iniziare le vostre analisi! Per verificare che tutto sia andato a buon fine, dovrete aspettarvi una tabella con le informazioni ritornate da Yarn e la seguente frase conclusiva "SparkSession available as 'spark'."

.. image:: img_jupyter/conf_livycreatesession.jpeg


===================
Caricare un dataset
===================

Una volta attivata con successo una sessione Spark, avete l'ambiente pronto per iniziare la vostra analisi. La prima cosa da fare è creare uno Spark DataFrame con il dataset che volete analizzare, procedendo come segue:

* Identificate il dataset sul dataportal e tenete traccia del path indicato nella scheda informativa. Nel caso in esempio, abbiamo scelto il dataset '_19luoghidellacultura_a_35e6edb1_4dec_4553_aa7a_5395bdc4024c_a_csv'.
* Eseguite il seguente comando nel notebook, che chiede a Spark di creare un nuovo dataframe contenente il dataset specificato: 

.. code-block:: scala

   val df = (spark.read.format("csv")
        .option("header", "true")
        .option("inferSchema", "true")
        .load("/daf/opendata/_19luoghidellacultura_a_35e6edb1_4dec_4553_aa7a_5395bdc4024c_a_csv")
   )

* [Optional] Eseguite il seguente comando per ottenere lo schema del dataframe:

.. code-block:: scala

   df.printSchema

=====================
Risorse utili
=====================

Per chi volesse approfondire l'utilizzo di Spark e di Jupyter Notebook, suggeriamo una lista non esaustiva di risorse utili da cui partire:

 * http://spark.apache.org/docs/latest/sql-programming-guide.html
 * http://jupyter.org/

