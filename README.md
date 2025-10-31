<div align="justify">

# GideonsDB
Programma di Database e Querying adibito a gestire operazioni di immagazzinamento e distribuzione di prodotti analoghe all'azione della Missione Internazionale dei Gedeoni (Prodotto non ufficiale e non affiliato a Gedeoni, The Gideons International)

[Installazione](#installazione)  
[Database](#database)  
[Contenuti](#contenuti)   
[Utilizzo del Programma e Gestione del Database](#utilizzo-del-programma-e-gestione-del-database)

# Installazione
Per installare il programma scarica la versione più recente dalla sezione [Releases](https://github.com/PenguinMB/GideonsDB/releases) del file **GideonsDB_x.x.x.zip**.  
Una volta scaricato il file zip, estraine i contenuti in una cartella a piacere. All'interno della cartella estratta "GideonsDB" si trova il file GideonsDB.exe da eseguire (Al momento è disponibile una versione per i soli sistemi Windows).  
Il programma non richiede installazioni di alcun tipo, è completamente portatile e perciò spostabile senza problema da una cartella all'altra del sistema utilizzato.

# Database
Il database è conservato localmente nella cartella /DB/, creata nella stessa cartella da cui è lanciato il programma, all'interno del file "GideonsDB.script". Il programma agisce modificando il file direttamente, e qualora il programma non individui il file nella suddetta directory, sarà generato un nuovo file di database in tale posizione.  
Nella versione 0.7.1 il file è invece creato, letto e conservato nella directory /Documenti/GideonsDB/.  

# Contenuti
Il database permette la gestione di quattro principali categorie: Magazzini, Prodotti, Transazioni e Distribuzioni. 

### Magazzino
Un Magazzino è costituito da un numero identificativo (ID, generato automaticamente) e il suo Nome.  
Ogni Magazzino può contenere al suo interno Prodotti, ma per definire quali prodotti si trovino in un dato Magazzino, vedi la sezione "Transazione".

### Prodotto
Un Prodotto è identificato dal suo Formato, dalla Lingua in cui è scritto e dal suo Colore.  
Ogni Prodotto può apparire in qualsiasi Magazzino, ma per definire quante unità di un Prodotto siano custodite in un dato 

### Transazione
Una Transazione descrive il passaggio di una certa quantità di un Prodotto specifico da un Magazzino ad un altro, oppure l'acquisizione da parte di un Magazzino di un certo Prodotto (Per esempio quando ottenuto/acquistato da terzi). La Transazione è quindi definita dalla data in cui è effettuata, il Prodotto coinvolto, il Magazzino in Uscita (che "dà" il prodotto, e che può anche essere definito come "Acquisizione" quando il Prodotto è ottenuto da un'origine esterna), il Magazzino in Entrata (che riceve il prodotto), e la quantità di Prodotto spostata.

### Distribuzione
Una Distribuzione descrive il trasferimento di una certa quantità di Prodotto da un Magazzino ad un ente terzo. La Distribuzione è quindi definita dalla data in cui è effettuata, il Prodotto coinvolto, il Magazzino in Uscita (che "dà" il prodotto), il nome dell'Ente che riceve il prodotto, il Tipo di Ente (Es: Scuola, Ospedale), e la quantità di Prodotto spostata. 

# Utilizzo del Programma e Gestione del Database
### Funzionalità di base
All'interno del programma sono presenti due pulsanti etichettati "Aggiungi [Magazzino/Prodotto]" che permettono in primis di definire l'esistenza di un dato Magazzino o Prodotto compilando le informazioni che caratterizzano le rispettive entità. Sono quindi presenti due pulsanti denominati "Nuova [Transazione/Distribuzione]", attraverso cui è possibile registrare operazioni di trasferimento che coinvolgono dati Magazzini e Prodotti precedentemente definiti.  
Per poter effettuare una delle due operazioni di trasferimento è necessario che il numero di unità di Prodotti disponibile nel Magazzino in uscita (cioè da cui vengono trasferiti) sia maggiore della quantità che si intende trasferire. Per aggiungere nuove unità di un Prodotto nel sistema non provenienti da un altro Magazzino già esistente, è necessario registrare una nuova Transazione e compilare il campo "Magazzino in Uscita" come **Acquisizione** (oppure lasciare vuoto il campo).
Similarmente, si può definire come "Acquisizione" anche la provenienza dei Prodotti in una Distribuzione se tali prodotti non siano stati prima depositati in un Magazzino.

### Interfaccia
Successivamente all'inserimento di un'entità nel Database, o premendo uno dei pulsanti "Visualizza [entità]" si ottiene una tabella di tutte le entità registrate per la rispettiva categoria scelta. Ogni colonna è ridimensionabile ed è possibile cambiare l'ordinamento delle righe per ogni singola colonna cliccando sul titolo della colonna. È inoltre possibile modificare l'ordine in cui le colonne sono mostrate.

Facendo doppio click con il pulsante sinistro del Mouse su una delle righe mostrate, è possibile **modificare** i dati della riga scelta (Per esempio cambiare nome ad un Magazzino, o la data in cui una transazione è stata effettuata). In fase di modifica è inoltre presente un pulsante con l'icona di un cestino: cliccando su di esso, dopo una richiesta di conferma sarà eliminata la riga corrispondente.  
**ATTENZIONE**: quando si elimina un dato Magazzino o Prodotto saranno eliminate anche tutte le Transazioni che lo coinvolgono, sia in entrata che in uscita.

Le dimensioni dell'Interfaccia possono essere modificate premendo i pulsanti **+** o **-** posizionati in basso a destra, oppure premendo CTRL e ruotando la rotella del Mouse, o premendo i pulsanti CTRL e **+** o **-** in contemporanea.

### Ricerca Dettagliata
Il pulsante "Ricerca Dettagliata" permette di effettuare ricerche approfondite sui dati già registrati, ponendo filtri e condizioni così da individuare direttamente i dati desiderati. Sono presenti tre tipi di ricerca: "Tutti gli X", "Tutti i Magazzini con Prodotto X", "Tutti i Prodotti nel Magazzino X" 
- "Tutti gli X" permette di individuare Tutti i Magazzini / Tutti i Prodotti / Tutte le Transazioni / Tutte le Distribuzioni che corrispondono a certi criteri.
- "Tutti i Magazzini con Prodotto X" individua, una volta scelto un dato Prodotto, tutti i Magazzini che lo contengono, e in quale quantità.
- "Tutti i Prodotti nel Magazzino X" identifica, una volta scelto un dato Magazzino, tutti i Prodotti contenuti al suo interno, e in che quantità.

Per ognuna di queste ricerche, una volta scelta la Categoria di interesse è presentata una nuova scelta: "Con caratteristica". Essa permette di scegliere appunto una caratteristica consona (Nome per un Magazzino; Formato, Lingua o Colore per un Prodotto...) alla categoria scelta e un criterio di uguaglianza (Uguale o Diverso, ma anche Maggiore o Minore per casi numerici), e il criterio a cui sottoporre l'uguaglianza (Per esempio i Prodotti con Lingua diversa dall'Italiano, le Transazioni effettuate nel 2024, i Magazzini che conservano più di 30 unità di un Prodotto...).  
Se questa opzione non è compilata, quando viene premuto "cerca" viene effettuata la ricerca scelta senza ulteriori filtri. Se è invece compilata correttamente, il programma genererà automaticamente un nuovo spazio per poter aggiungere una seconda condizione, da compilare come quella iniziale, e la possibilità di scegliere la congiunzione tra i due filtri (**"E"** oppure **"O"**). Se tra i due filtri è scelto **"E"** allora saranno restituiti tutti i risultati che soddisfano entrambe le condizioni; se è scelto **"O"** saranno restituiti tutti i risultati che corrispondono ad almeno una delle due condizioni.   
Finchè sono aggiunte condizioni, saranno resi disponibili nuovi spazi per aggiungerne ulteriori. Quando si è soddisfatti delle condizioni inserite basta non compilare gli ulteriori spazi aggiunti e premere il pulsante "Cerca".  
**ATTENZIONE**: le condizioni "E" e "O" possono essere messe in combinazione per generare filtri avanzati.
- Una condizione "O" successiva a uno o più "E" concatenerà gli "E" insieme contrapponendoli all'"O".  
Es: Cond. Iniziale + "E" + "E" + "O" restituisce tutti gli elementi che rispettano TUTTE le prime 3 condizioni allo stesso tempo, oppure l'ultima condizione.
- Una o più condizioni "E" successive a un "O" saranno considerate tutte insieme come parte dell'"O".  
Es: Cond. Iniziale + "O" + "E" + "E" resituisce tutti gli elementi che rispettano la condizione iniziale, oppure TUTTE E 3 le condizioni successive, quella dell'"O" e quelle dell'"E" successive.
- La concatenazione "O" + "E" può essere rotta attraverso un successivo "O".  
Es: Cond. Iniziale + "O" + "E" + "O" resituisce tutti gli elementi che rispettano la condizione iniziale, oppure le 2 condizioni successive, oppure quella finale.

</div>
