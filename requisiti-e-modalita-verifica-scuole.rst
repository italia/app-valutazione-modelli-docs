Requisiti tecnici e modalità di verifica per il modello scuole
==============================================================

Di seguito sono riportati i criteri di conformità e le raccomandazioni verificabili tramite App di valutazione dell'adesione al modello scuole.

Per il corretto funzionamento dell'App di valutazione, è necessario inserire dei **data attribute** all’interno dei tag HTML del sito. Questi vengono indicati separatamente per ognuno dei criteri. Alcuni data attribute valgono per più criteri.

La chiave generale dei data attribute è ``data-element=*`` e va inserita all’interno dei tag HTML.


.. note::
  
  I data attribute, dove possibile, sono già presenti nei materiali forniti da `Designers Italia <https://designers.italia.it/modello/scuole/>`_, sia all'interno dei template HTML che del tema CMS messi a disposizione. Rimane tuttavia responsabilità dell'ente verificare che siano correttamente inseriti dovunque richiesto.

.. note::

  Per tutto ciò che è un URL, per esempio l’informativa privacy, l'App controlla anche che l’URL nell’href del componente non sia nullo e, per alcuni casi specifici, che sia in HTTPS (vedi dettagli audit) e che riporti ad una pagina “funzionante”..

.. note::

  Per tutto ciò che viene controllato sulla base di un vocabolario si utilizzano controlli non case-sensitive. 


Criterio C.SC.1.1 - Coerenza dell'utilizzo dei font
---------------------------------------------------------

**Condizioni di successo:** tutti i titoli (heading) e tutti i paragrafi delle pagine del sito in lingua italiana utilizzano esclusivamente i font Titillium Web, Lora o Roboto Mono come font di default.

**Modalità di verifica:** ricercando specifici attributi data-element, nelle pagine analizzate viene verificato che i font di default siano quelli richiesti all'interno di tutti gli <h> e <p>. La verifica viene svolta sulla homepage, N pagine di primo livello, N pagine di secondo livello, N pagine di terzo livello “Scheda servizio”.

**Requisiti tecnici:**

*Caricamento pagine di primo livello*:

In homepage, nel menù principale identificato dal tag <ul> i link alle pagine di primo livello devono contenere, all'interno del tag <a>, il ``data-element="overview"`` (sulla voce "Panoramica"). Questo deve accadere per tutte le voci richieste ("Scuola", "Servizi", "Novità", "Didattica") e per tutte le voci aggiuntive inserite nel menù di primo livello, permettendo di identificare i link alle pagine di primo livello. L’assenza del data-element in ognuna delle 4 voci richieste porta all’impossibilità di esecuzione dell’audit in quanto non sarà possibile recuperare i link.


*Caricamento pagine di secondo livello*:

In homepage, nel menù principale i sotto-menù (menù di secondo livello) che contengono i link alle pagine di secondo livello devono contenere, all'interno del tag <ul>, i seguenti attributi:

- "Scuola": ``data-element="school-submenu"``
- "Servizi": ``data-element="services-submenu"``
- "Novità": ``data-element="news-submenu"``
- "Didattica": ``data-element="teaching-submenu"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

All'interno di questi sotto-menù i link alle pagine di secondo livello dovranno essere contenuti in tag <a> dentro i tag <li> del menù.

La mancata individuazione di almeno un link per ogni sotto-menù (ad eccezione di quelli relativi a eventuali voci aggiuntive) attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.


*Caricamento pagine di terzo livello "scheda servizio"* :

In homepage, nel sotto-menù della voce di primo livello "Servizi", ognuno dei link a pagine di secondo livello deve contenere il ``data-element="service-type"`` nel tag <a>.

Nelle pagine a cui ognuno di questi link rimanda, dovrà essere presente il ``data-element=“service-link”`` nei tag <a> contenenti i link alle pagine di terzo livello “schede servizio”. Se la pagina possiede un paginatore è necessaria la presenza di un tag <a> con ``data-element=“pager-link”`` per permettere di visualizzare i link a tutte le schede servizio.

La mancata individuazione di almeno un link attraverso il ``data-element=“service-link”`` porta all’impossibilità di esecuzione dell’audit.

**Esempi**

Menu principale:

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-a.html


Pagina di primo livello "Servizi":

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-b.html


Criterio C.SC.1.2 - Libreria di elementi di interfaccia
------------------------------------------------------------

**Condizioni di successo:** la libreria Bootstrap Italia è presente e in uso in una versione uguale o superiore alla 1.6.

**Modalità di verifica:** in ogni pagina analizzata viene verificata la presenza della libreria Bootstrap Italia e la versione in uso, individuando la proprietà CSS --bootstrap-italia-version all’interno del selettore :root o la variabile globale window.BOOTSTRAP_ITALIA_VERSION.

Inoltre ogni pagina analizzata deve presentare almeno una tra le seguenti classi CSS di Bootstrap Italia:

- .row 
- .col 
- .card 
- .container 
- .variable-gutters 
- .section 
- .font-serif 
- .font-sans-serif 
- .font-monospace 
- .lead 
- .it-list 
- .link-list 
- .link-list-wrapper 
- .list-item 
- .text-primary 
- .text-secondary

La verifica viene svolta sulla homepage, N pagine di primo livello, N pagine di secondo livello e N pagine di terzo livello “Scheda servizio”.


**Requisiti tecnici**:

*Caricamento pagine di primo livello*:

In homepage, nel menù principale identificato dal tag <ul> i link alle pagine di primo livello devono contenere, all'interno del tag <a>, il ``data-element="overview"`` (sulla voce "Panoramica"). Questo deve accadere per tutte le voci richieste ("Scuola", "Servizi", "Novità", "Didattica") e per tutte le voci aggiuntive inserite nel menù di primo livello, permettendo di identificare i link alle pagine di primo livello. L’assenza del data-element in ognuna delle 4 voci richieste porta all’impossibilità di esecuzione dell’audit in quanto non sarà possibile recuperare i link.


*Caricamento pagine di secondo livello*:

In homepage, nel menù principale i sotto-menù (menù di secondo livello) che contengono i link alle pagine di secondo livello devono contenere, all'interno del tag <ul>, i seguenti attributi:

- "Scuola": ``data-element="school-submenu"``
- "Servizi": ``data-element="services-submenu"``
- "Novità": ``data-element="news-submenu"``
- "Didattica": ``data-element="teaching-submenu"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

All'interno di questi sotto-menù i link alle pagine di secondo livello dovranno essere contenuti in tag <a> dentro i tag <li> del menù.

La mancata individuazione di almeno un link per ogni sotto-menù (ad eccezione di quelli relativi a eventuali voci aggiuntive) attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.



*Caricamento pagine di terzo livello "Scheda servizio"*:

In homepage, nel sotto-menù della voce di primo livello "Servizi", ognuno dei link a pagine di secondo livello deve contenere il ``data-element="service-type"`` nel tag <a>.

Nelle pagine a cui ognuno di questi link rimanda, dovrà essere presente il ``data-element=“service-link”`` nei tag <a> contenenti i link alle pagine di terzo livello “schede servizio”. Se la pagina possiede un paginatore è necessaria la presenza di un tag <a> con ``data-element=“pager-link”`` per permettere di visualizzare i link a tutte le schede servizio.

La mancata individuazione di almeno un link attraverso il ``data-element=“service-link”`` porta all’impossibilità di esecuzione dell’audit.


**Esempi**

Menu principale:

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-a.html


Pagina di primo livello "Servizi":

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-b.html



Criterio C.SC.1.3 - Utilizzo di temi per CMS (Content Management System)
---------------------------------------------------------------------------

**Condizioni di successo:** se è in uso il tema CMS del modello scuole, la versione utilizzata è uguale o superiore alla 2.0.

**Modalità di verifica:** viene verificato l'uso del tema CMS del modello e la versione in uso ricercando uno specifico testo all'interno di tutti i file .CSS presenti in pagina.

Il testo ricercato nei file .css è:

.. literalinclude:: esempi-codice-scuole/c-sc-1-3.html


Criterio C.SC.1.4 - Voci di menù di primo livello
-----------------------------------------------------

**Condizioni di successo:** le voci del menù di primo livello del sito sono esattamente quelle indicate nel documento di architettura dell'informazione e sono nell'ordine indicato (ovvero Scuola, Servizi, Novità, Didattica).

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, vengono identificate le voci presenti nel menù del sito, il loro ordine e confrontate con quanto indicato nella Documentazione del modello scuole, applicando una tolleranza di massimo 3 voci aggiuntive.

**Requisiti tecnici:** Nell’elemento del menù, il tag <ul> deve avere l’attributo ``data-element=”menu”`` ed essere composto da <li> e <a>.

**Esempio:**

.. literalinclude:: esempi-codice-scuole/c-sc-1-4.html


Criterio C.SC.1.5 - Voci di menu di secondo livello
------------------------------------------------------------

**Condizioni di successo:** tutte le voci del menù di secondo livello usate fanno riferimento alla voce di primo livello corrispondente secondo quanto indicato nella Documentazione del modello scuole.

**Modalità di verifica:**  ricercando specifici attributi data-element, vengono verificate le voci di secondo livello usate rispetto ad ognuna delle voci di primo livello del menù. Nel conteggio vengono incluse anche le voci di secondo livello riferite a voci di primo livello non indicate nella documentazione.


**Requisiti tecnici:** In homepage, nel menù principale i sotto-menù (menù di secondo livello) che contengono i link alle pagine di secondo livello devono contenere, all'interno del tag <ul>, i seguenti attributi:

- "Scuola": ``data-element="school-submenu"``
- "Servizi": ``data-element="services-submenu"``
- "Novità": ``data-element="news-submenu"``
- "Didattica": ``data-element="teaching-submenu"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

Attraverso questi data-element vengono caricate le voci dei sotto-menù per eseguire il controllo richiesto. La mancata individuazione di almeno una voce (ad eccezione delle voci aggiuntive) per ogni sotto-menù porta all’impossibilità di esecuzione dell’audit.


**Esempio:**

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-a.html

Criterio C.SC.2.1 - Informativa privacy
------------------------------------------

**Condizioni di successo:** il sito presenta una voce nel footer che riporta a una pagina sicura riguardante l'informativa sulla privacy.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza di un link nel footer che riporti a una pagina esistente e con certificato HTTPS valido e attivo.

**Requisiti tecnici:** Il tag <a> deve avere l’attributo ``data-element=”privacy-policy-link”`` e contenere un “href” (può essere contenuto in altri tag, ad esempio <li> …). Il tag deve essere presente all’interno del tag <footer>.

**Esempio:**

.. literalinclude:: esempi-codice-scuole/c-sc-2-1.html


Criterio C.SC.2.2 - Dichiarazione di accessibilità
---------------------------------------------------------

**Condizioni di successo:** il sito presenta una voce nel footer che riporta a una dichiarazione di accessibilità AGID valida per il sito.

**Modalità di verifica:** ricercando uno specifico attributo data-element, viene verificata la presenza del link nel footer dell’homepage, che riporti a una pagina esistente, che l'url della pagina di destinazione inizi con "https://form.agid.gov.it/view/" e che la pagina contenga l'url del sito della scuola.

**Requisiti tecnici:** All’interno del footer dell’homepage (tag <footer>) deve esserci un tag <a> che contiene l’href alla dichiarazione di accessibilità. Il tag <a> deve avere l’attributo ``data-element="accessibility-link"``. L’<a> può essere contenuto in altri tag, esempio <li>. 

**Esempio:**

.. literalinclude:: esempi-codice-scuole/c-sc-2-2.html


Criterio C.SC.2.3 - Cookie
--------------------------------

**Condizioni di successo:** il dominio di tutti i cookie già presenti nel sito, ovvero senza che sia stata espressa una preferenza da parte dell’utente riguardo il loro uso, è corrispondente al dominio del sito web della scuola.

**Modalità di verifica:** ricercando specifici attributi data-element, viene verificato che al caricamento di ogni pagina analizzata il dominio dei cookie identificati sia corrispondente al dominio del sito web. La verifica viene eseguita sulla homepage, in N pagine di primo livello, in N pagine di secondo livello, in N pagine di terzo livello “Scheda servizio” e in N pagine di terzo livello “Luogo”.

**Requisiti tecnici**:

*Caricamento pagine di primo livello*:

In homepage, nel menù principale identificato dal tag <ul> i link alle pagine di primo livello devono contenere, all'interno del tag <a>, il ``data-element="overview"`` (sulla voce "Panoramica"). Questo deve accadere per tutte le voci richieste ("Scuola", "Servizi", "Novità", "Didattica") e per tutte le voci aggiuntive inserite nel menù di primo livello, permettendo di identificare i link alle pagine di primo livello. L’assenza del data-element in ognuna delle 4 voci richieste porta all’impossibilità di esecuzione dell’audit in quanto non sarà possibile recuperare i link.


*Caricamento pagine di secondo livello*:

In homepage, nel menù principale i sotto-menù (menù di secondo livello) che contengono i link alle pagine di secondo livello devono contenere, all'interno del tag <ul>, i seguenti attributi:

- "Scuola": ``data-element="school-submenu"``
- "Servizi": ``data-element="services-submenu"``
- "Novità": ``data-element="news-submenu"``
- "Didattica": ``data-element="teaching-submenu"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

All'interno di questi sotto-menù i link alle pagine di secondo livello dovranno essere contenuti in tag <a> dentro i tag <li> del menù.

La mancata individuazione di almeno un link per ogni sotto-menù (ad eccezione di quelli relativi a eventuali voci aggiuntive) attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.


*Caricamento pagine di terzo livello "Scheda servizio"*:

In homepage, nel sotto-menù della voce di primo livello "Servizi", ognuno dei link a pagine di secondo livello deve contenere il ``data-element="service-type"`` nel tag <a>.

Nelle pagine a cui ognuno di questi link rimanda, dovrà essere presente il ``data-element=“service-link”`` nei tag <a> contenenti i link alle pagine di terzo livello “schede servizio”. Se la pagina possiede un paginatore è necessaria la presenza di un tag <a> con ``data-element=“pager-link”`` per permettere di visualizzare i link a tutte le schede servizio.

La mancata individuazione di almeno un link attraverso il ``data-element=“service-link”`` porta all’impossibilità di esecuzione dell’audit.


*Caricamento pagine di terzo livello “Luogo”*:

In homepage, nel sotto-menù della voce di primo livello “Scuola” è necessaria la presenza del ``data-element=”school-locations”`` nel tag <a> contenente il link alla pagina “I luoghi”.

In questa pagina è necessaria la presenza del ``data-element=”location-link”`` nel tag <a> nelle cards contenenti i link alle pagine di terzo livello “Luogo”.


**Esempi**:

Menu principale:

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-a.html


Pagina di primo livello "Servizi":

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-b.html


I luoghi della scuola:

.. literalinclude:: esempi-codice-scuole/c-sc-2-3.html


Criterio C.SC.3.1 - Certificato HTTPS
------------------------------------------

**Condizioni di successo:** il sito utilizza un certificato https valido e non obsoleto secondo le raccomandazioni AGID.

**Modalità di verifica:** viene verificato che il certificato https del sito sia valido e attivo.



Raccomandazione R.SC.1.1 - Vocabolari controllati
------------------------------------------------------

**Condizioni di successo:** gli argomenti utilizzati appartengono alla lista indicata all'interno del documento di architettura dell'informazione del modello scuole alla voce "Le parole della scuola" e l’elenco completo degli argomenti utilizzati è presente nella pagina dei risultati di ricerca.

**Modalità di verifica:** tramite ricerca di specifici attributi data-element, gli argomenti identificati all'interno della funzione di ricerca del sito vengono confrontati con l'elenco di voci presente nel documento di architettura dell'informazione.

**Requisiti tecnici:** Il bottone (<button>) "cerca" in homepage deve avere l’attributo ``data-element=”search-modal-button”`` in modo da poterne simulare l'apertura. Il tag <input> di testo deve avere attributo ``data-element=”search-modal-input”`` in modo da poter essere inserito testo di ricerca. Infine, il bottone per cercare (avvia ricerca) deve avere ``data-element=”search-submit”``. La pagina risultati ricerca deve contenere un listato di argomenti <ul> con attributo ``data-element=”all-topics”`` contenente degli <li> (può contenere altri tag).

**Esempio:**

.. literalinclude:: esempi-codice-scuole/r-sc-1-1.html


Raccomandazione R.SC.1.2 - Schede informative di servizio
----------------------------------------------------------------

**Condizioni di successo:** nelle schede informative di servizio le voci obbligatorie e i relativi contenuti sono presenti e, dove richiesto, sono nell'ordine corretto.

**Modalità di verifica:** ricercando specifici attributi "data-element", la presenza e l'ordine delle voci richieste viene verificato ricercandoli all'interno della pagina e dell'indice. Per essere ritenute valide, le voci devono avere contenuti associati della tipologia indicata all'interno del documento di architettura dell'informazione. La verifica viene svolta su N pagine di terzo livello “Scheda servizio”.

**Requisiti tecnici:** 

*Caricamento pagine di terzo livello "Scheda servizio"*:

In homepage, nel sotto-menù della voce di primo livello "Servizi", ognuno dei link a pagine di secondo livello deve contenere il ``data-element="service-type"`` nel tag <a>.

Nelle pagine a cui ognuno di questi link rimanda, dovrà essere presente il ``data-element=“service-link”`` nei tag <a> contenenti i link alle pagine di terzo livello “schede servizio”. Se la pagina possiede un paginatore è necessaria la presenza di un tag <a> con ``data-element=“pager-link”`` per permettere di visualizzare i link a tutte le schede servizio.

La mancata individuazione di almeno un link attraverso il ``data-element=“service-link”`` porta all’impossibilità di esecuzione dell’audit.


*Controllo della presenza e ordine delle voci nella scheda servizio*:

All'interno delle pagine di terzo livello "schede servizio" è necessaria la presenza del ``data-element="page-index"`` nell'indice della pagina identificato dal tag <ul>. Da questo indice vengono caricate le voci che si trovano dentro i tag <a> di ogni riga dell'indice indicata dal tag <li>. Le voci per le quali viene controllata la presenza nell'indice e il loro ordinamento sono:

- "Cos'è"
- "Come si accede al servizio"
- "Cosa serve"
- "Tempi e scadenze"
- "Contatti"
- "Ulteriori informazioni"

Per queste voci (ad eccezione di "Contatti") viene anche controllata la presenza di contenuto nella relativa sezione in pagina. Se la sezione non viene individuata la relativa voce risulterà mancante nella reportistica. In particolare:

- "Cos'è": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-what-is"`` e che questo abbia almeno 3 caratteri;
- "Come si accede al servizio": per confermare la presenza in pagina della relativa sezione è sufficiente sia presente uno di questi 3 componenti: "Prenota appuntamento" (un tag <button> con ``data-element="service-booking-access"`` per il bottone che porta alla pagina di prenotazione appuntamenti), "Accesso online" (un tag <button> con ``data-element="service-online-access"`` per il bottone che porta alla pagina di accesso online) e/o "Accesso generico" (un tag HTML con ``data-element="service-generic-access"`` per un componente diverso da quelli sopra identificati);
- "Cosa serve": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-needed"`` e che questo abbia almeno 3 caratteri;
- "Tempi e scadenze": per confermare la presenza in pagina della relativa sezione è sufficiente sia presente uno di questi 2 componenti: "Testo" (è necessario un <p> contenuto nel <div> con ``data-element=“service-calendar-text”`` e che questo abbia almeno 3 caratteri in un testo al di fuori del componente calendario) e/o "Calendario" (un componente calendario contenuto in un tag <div> con ``data-element=“service-calendar-list”``).
- "Ulteriori informazioni": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-more-info"`` e che questo abbia almeno 3 caratteri.

Viene inoltre controllata la presenza di altri componenti al di fuori dell'indice:

- "Titolo": viene controllata la presenza di un tag HTML con ``data-element="service-title"`` che identifica il titolo del servizio e che questo abbia almeno 3 caratteri;
- "Tipologia servizio": viene controllata la presenza di un tag HTML con ``data-element="breadcrumb"`` che identifica la breadcrumb. In questo componente vengono individuati i testi relativi ai vari <li> e viene controllata la presenza di almeno 3 caratteri nel testo successivo a "Servizi";
- "Tassonomie argomenti": viene controllata la presenza di almeno un tag <a> con ``data-element="topic-list"`` che identificano gli argomenti del servizio;
- "Descrizione breve": viene controllata la presenza di un tag HTML con ``data-element="service-description"`` che identifica la descrizione del servizio e che questo abbia almeno 3 caratteri;
- "A cosa serve": viene controllata la presenza di un tag HTML con ``data-element="used-for"`` e che questo abbia almeno 3 caratteri;
- "Luogo" (contenuto nella sezione "Come si accede al servizio"): viene controllata la presenza di tag <span> per la label e <p> per il valore relativo alla label con il ``data-element=”places”``. Controlla la presenza della card “Luogo” e alcuni elementi al suo interno, quali: "Indirizzo", "Orari", "Gps", “Email”, “PEC” e “Telefono”. Il controllo viene effettuato sulla presenza della label e sulla sua valorizzazione (cioè le label devono chiamarsi “Indirizzo”, “Orari”, ecc). Per quanto riguarda le coordinate GPS viene controllato che l’URL della mappa contenga il valore “map” (in modo da coprire più servizi di mappe possibili) mentre per quanto riguarda gli orari viene controllato tramite Regexp che il valore della label “Orari” contenga un orario in formato in ore, minuti oppure ore, minuti e secondi;
- "Struttura responsabile del servizio" (contenuta nella sezione "Contatti"): viene controllata la presenza di un tag <a> con ``data-element="structures"`` che identifica la struttura responsabile per il servizio;
- "Metadati": viene controllata la presenza di "pubblicato" o "revisione" nel testo del tag HTML con ``data-element="metadata"``. Il testo viene trasformato in minuscolo durante il controllo.



**Esempi:**

Menu principale:

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-a.html

Pagina di primo livello "Servizi":

.. literalinclude:: esempi-codice-scuole/c-sc-1-1-b.html


Indice della pagina "Scheda servizio":

.. literalinclude:: esempi-codice-scuole/r-sc-1-2-a.html


Corpo della pagina "Scheda servizio":

.. literalinclude:: esempi-codice-scuole/r-sc-1-2-b.html



Raccomandazione R.SC.2.2 - Licenza e attribuzione
------------------------------------------------------

**Condizioni di successo**: nella pagina delle noti legali viene indicato che i dati, documenti e informazioni riportati sul sito sono rilasciati con licenza CC-BY 4.0.

**Modalità di verifica**: ricercando uno specifico attributo "data-element", viene verificato che la pagina delle note legali sia raggiungibile dal footer e che questa contenga una sezione intitolata "Licenza dei contenuti" riportante la seguente dicitura

“In applicazione del principio open by default ai sensi dell’articolo 52 del decreto legislativo 7 marzo 2005, n. 82 (CAD) e salvo dove diversamente specificato (compresi i contenuti incorporati di terzi), i dati, i documenti e le informazioni pubblicati sul sito sono rilasciati con `licenza CC-BY 4.0 <https://creativecommons.org/licenses/by/4.0/legalcode.it>`_. Gli utenti sono quindi liberi di condividere (riprodurre, distribuire, comunicare al pubblico, esporre in pubblico), rappresentare, eseguire e recitare questo materiale con qualsiasi mezzo e formato e modificare (trasformare il materiale e utilizzarlo per opere derivate) per qualsiasi fine, anche commerciale con il solo onere di attribuzione, senza apporre restrizioni aggiuntive.”

**Requisiti tecnici**: All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla pagina delle note legali. Il tag <a> deve avere l’attributo data-element="legal-notes". L’<a> può essere contenuto in altri tag, esempio <li>. All’interno della pagina individuata da questo link dovrà essere presente un tag HTML con l’attributo ``data–element=”legal-notes-section”`` da inserire nel <h> contenente il titolo della sezione da analizzare e uno o più tag <p> con attributo data-element=”legal-notes-body” inseriti in ogni <p> contenente il testo della sezione da analizzare.

**Esempi**:

.. literalinclude:: esempi-codice-scuole/r-sc-2-2-a.html

.. literalinclude:: esempi-codice-scuole/r-sc-2-2-b.html


Raccomandazione R.SC.3.1 - Velocità e tempi di risposta
----------------------------------------------------------

**Condizioni di successo**: il sito presenta livelli di prestazioni (media pesata di 6 metriche standard) pari o superiori a 50.

**Modalità di verifica**: l’homepage del sito viene testata in modalità “mobile” con Lighthouse.


Test aggiuntivo Localizzazione IP
---------------------------------

**Condizioni di successo:** l'indirizzo IP fa riferimento a un datacenter localizzato su territorio europeo.

**Modalità di verifica:** viene verificato che la localizzazione dell'IP rientri all'interno di uno dei confini degli stati membri dell'Unione Europea.
