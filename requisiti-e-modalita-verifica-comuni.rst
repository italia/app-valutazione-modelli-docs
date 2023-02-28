Requisiti tecnici e modalità di verifica per il modello Comuni
==============================================================

Di seguito sono riportati i criteri di conformità e le raccomandazioni verificabili tramite App di valutazione dell'adesione al modello Comuni.


Per il corretto funzionamento dell'App di valutazione, è necessario inserire dei **data attribute** all’interno dei tag HTML del sito. Questi vengono indicati separatamente per ognuno dei criteri. Alcuni data attribute sono valgono per più criteri.

La chiave generale dei data attribute è ``data-element=*`` e va inserita all’interno dei tag HTML.


.. note::
  
  I data attribute, dove possibile, sono già presenti nei materiali forniti da `Designers Italia <https://designers.italia.it/modello/comuni/>`_, sia all'interno dei template HTML che dei CMS messi a disposizione. Rimane tuttavia responsabilità dell'ente verificare che siano correttamente inseriti dove richiesto.
  
.. note::
  
  Per tutto ciò che è un URL, per esempio FAQ o Segnalazione disservizio, l'App controlla anche che l’URL nell’href del componente non sia nullo e, per alcuni casi specifici, che sia in HTTPS e che riporti ad una pagina “funzionante”. 
 
.. note::

  Per tutto ciò che viene controllato sulla base di un vocabolario si utilizzano controlli non case-sensitive.
  

Criterio C.SI.1.1 - Coerenza dell’utilizzo dei font (librerie di caratteri)
--------------------------------------------------------------------------------

**Condizioni di successo:** tutti i titoli (heading) e tutti i paragrafi delle pagine del sito in lingua italiana utilizzano esclusivamente i font Titillium Web, Lora o Roboto Mono come font di default.

**Modalità di verifica:** tramite ricerca di specifici attributi data-element, nelle pagine analizzate viene verificato che i font di default siano quelli richiesti all'interno di tutti gli <h> e <p>. La verifica viene svolta sulla homepage, N pagine di primo livello, N pagine di secondo livello, N pagine di terzo livello “Scheda servizio” e nella pagina di accesso  all’area riservata”.

**Requisiti tecnici:**

*Caricamento pagina di accesso all’area riservata*:

In homepage, se è presente un link alla pagina di accesso all'area riservata, questo deve contenere il ``data-element="personal-area-login"`` nel tag <a> contenente il link alla pagina.

*Caricamento pagine primo livello*:

In homepage, per poter identificare i link alle pagine di primo livello, nel menù principale identificato dal tag <div class="navbar"> i link alle pagine di primo livello devono contenere all'interno del tag <a class="nav-link"> i seguenti attributi:

- "Amministrazione": ``data-element="management"``
- "Novità": ``data-element="news"``
- "Servizi": ``data-element="all-services"``
- "Vivere il Comune": ``data-element="live"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

L'assenza di uno dei data-element (ad eccezione di quelli relativi a eventuali voci aggiuntive) porta all'impossibilità di esecuzione dell'audit in quanto non sarà possibile recuperare il link.


*Caricamento pagine di secondo livello*:

Per il caricamento delle pagine di secondo livello è necessario che i data-element alle pagine di primo livello siano correttamente posizionati all'interno dei link delle pagine di primo livello nel menù principale.

La pagina di primo livello "Amministrazione", identificata grazie al ``data-element="management"``, dovrà contenere il ``data-element="management-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Novità", identificata grazie al ``data-element="news"``, dovrà contenere il ``data-element="news-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Vivere il comune", identificata grazie al ``data-element="live"``, dovrà contenere due bottoni. Il bottone che porta alla pagina di secondo livello "Eventi" dovrà contenere ``data-element="live-button-events"`` e il bottone che porta alla pagina di secondo livello "Luoghi" dovrà contenere ``data-element="live-button-locations"``. Per entrambi i bottoni il data-element dovrà essere posizionato sul tag <button> e all'interno dell'attributo "onclick" del bottone dovrà essere presente il link alla pagina di secondo livello. La mancata individuazione di almeno un link attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.

Nel caso fossero presenti delle voci aggiuntive di primo livello esse vengono identificate attraverso il ``data-element=”custom-submenu”``. In ognuna di queste pagine è necessaria la presenza del ``data-element=”custom-category-link”`` all’interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello.


*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.


Criterio C.SI.1.2 - Libreria di elementi di interfaccia
----------------------------------------------------------

**Condizioni di successo:** la libreria Bootstrap Italia è presente e in uso in una versione uguale o superiore alla 2.0.

**Modalità di verifica:** in ogni pagina analizzata viene verificata la presenza della libreria Bootstrap Italia e la versione in uso, individuando la proprietà CSS --bootstrap-italia-version all’interno del selettore :root o la variabile globale window.BOOTSTRAP_ITALIA_VERSION.

Inoltre ogni pagina analizzata deve utilizzare almeno una tra le seguenti classi CSS di Bootstrap Italia

.it-header-wrapper
.it-nav-wrapper
.navbar
.it-brand-title
.row
.col
.card
.container
.variable-gutters
.section
.font-serif
.font-sans-serif
.font-monospace
.lead
.it-list
.link-list
.link-list-wrapper
.list-item
.text-primary
.text-secondary

La verifica viene svolta sulla homepage, N pagine di primo livello, N pagine di secondo livello, N pagine di terzo livello “Scheda servizio”, nella pagina di accesso all’area riservata e nella pagina della funzionalità di prenotazione appuntamento.

**Requisiti tecnici:** 

*Caricamento pagina di accesso all’area riservata*:

In homepage, se è presente un link alla pagina di accesso all'area riservata, questo deve contenere il ``data-element="personal-area-login"`` nel tag <a> contenete il link alla pagina.


*Caricamento pagina di prenotazione appuntamenti*:

Per caricare la pagina prenotazione appuntamenti è necessario che il ``data-element=”all-service”`` sia posizionato in homepage nel link della pagina di primo livello “Servizi”. In questa pagina di primo livello il link alla pagina di prenotazione appuntamenti deve contenere il ``data-element="appointment-booking"`` nel tag <a> contenente il link alla pagina.


*Caricamento pagine primo livello*:

In homepage, per poter identificare i link alle pagine di primo livello, nel menù principale identificato dal tag <div class="navbar"> i link alle pagine di primo livello devono contenere all'interno del tag <a class="nav-link"> i seguenti attributi:

- "Amministrazione": ``data-element="management"``
- "Novità": ``data-element="news"``
- "Servizi": ``data-element="all-services"``
- "Vivere il Comune": ``data-element="live"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

L'assenza di uno dei data-element (ad eccezione di quelli relativi a eventuali voci aggiuntive) porta all'impossibilità di esecuzione dell'audit in quanto non sarà possibile recuperare il link.


*Caricamento pagine di secondo livello*:

Per il caricamento delle pagine di secondo livello è necessario che i data-element alle pagine di primo livello siano correttamente posizionati all'interno dei link delle pagine di primo livello nel menù principale.

La pagina di primo livello "Amministrazione", identificata grazie al ``data-element="management"``, dovrà contenere il ``data-element="management-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Novità", identificata grazie al ``data-element="news"``, dovrà contenere il ``data-element="news-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Vivere il comune", identificata grazie al ``data-element="live"``, dovrà contenere due bottoni. Il bottone che porta alla pagina di secondo livello "Eventi" dovrà contenere ``data-element="live-button-events"`` e il bottone che porta alla pagina di secondo livello "Luoghi" dovrà contenere ``data-element="live-button-locations"``. Per entrambi i bottoni il data-element dovrà essere posizionato sul tag <button> e all'interno dell'attributo "onclick" del bottone dovrà essere presente il link alla pagina di secondo livello. La mancata individuazione di almeno un link attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.

Nel caso fossero presenti delle voci aggiuntive di primo livello esse vengono identificate attraverso il data-element=”custom-submenu”. In ognuna di queste pagine è necessaria la presenza del data-element=”custom-category-link” all’interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello.


*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.


**Esempi:**

.. literalinclude:: esempi-codice-comuni/c-si-1-2-a.html

.. literalinclude:: esempi-codice-comuni/c-si-1-2-b.html


Criterio C.SI.1.3 - Schede informative di servizio per il cittadino
------------------------------------------------------------------------

**Condizioni di successo:** nelle schede informative di servizio le voci obbligatorie e i relativi contenuti sono presenti e, dove richiesto, sono nell'ordine corretto.

**Modalità di verifica:** viene verificato se le voci indicate come obbligatorie all'interno del documento di architettura dell'informazione sono presenti e nell'ordine corretto, ricercandole all'interno della pagina e dell'indice tramite specifici data-element. Per essere ritenute valide, le voci devono avere contenuti associati della tipologia indicata all'interno del documento di architettura dell'informazione. La verifica viene effettuata su N schede servizio casualmente selezionata, ricercando le voci indicate nella documentazione del modello tramite specifici attributi data-element.

**Requisiti tecnici:**

*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il data-element="load-other-cards". La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.

**Esempio:**
   
.. literalinclude:: esempi-codice-comuni/c-si-1-3-a.html

*Controllo della presenza e ordine delle voci nelle “Schede servizio”*:

Per le pagine di terzo livello di servizi è necessaria la presenza del ``data-element="page-index"`` nell'indice della pagina identificato dal tag <ul>. Da questo indice vengono caricate le voci che si trovano dentro i tag <a> di ogni riga dell'indice indicata dal tag <li>. Le voci per le quali viene controllata la presenza nell'indice e il loro ordinamento sono:

- "A chi è rivolto"
- "Come fare"
- "Cosa serve"
- "Cosa si ottiene"
- "Tempi e scadenze"
- "Accedi al servizio",
- "Condizioni di servizio"
- "Contatti"

Per queste voci viene anche controllata la presenza di contenuto nella relativa sezione in pagina. Se la sezione non viene individuata la relativa voce risulterà mancante nella reportistica. In particolare:

- "A chi è rivolto": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-addressed"`` e che questo abbia almeno 3 caratteri;
- "Come fare": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-how-to"`` e che questo abbia almeno 3 caratteri;
- "Cosa serve": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-needed"`` e che questo abbia almeno 3 caratteri;
- "Cosa si ottiene": viene controllata la presenza di un tag <p> contenuto nel <div> con ``data-element="service-achieved"`` e che questo abbia almeno 3 caratteri;
- "Tempi e scadenze": viene controllata la presenza di un <p> contenuto nel <div> con ``data-element="service-calendar-text"`` e che questo abbia almeno 3 caratteri in un testo al di fuori del componente calendario oppure viene controllata la presenza del componente calendario individuando in pagina il tag <div> con ``data-element="service-calendar-list"``. È necessaria solo una di queste due condizioni per confermare la presenza della relativa sezione;
- "Accedi al servizio": viene controllata la presenza in pagina di almeno uno tra i componenti "Prenota appuntamento" (un tag <button> con ``data-element="service-booking-access"`` per il bottone che porta alla pagina di prenotazione appuntamenti), "Accesso online" (un tag <button> con ``data-element="service-online-access"`` per il bottone che porta alla pagina di accesso online), "Generic access" (un tag HTML con ``data-element="service-generic-access"`` per un componente diverso da quelli sopra identificati). È necessaria solo una di queste tre condizioni per confermare la presenza della relativa sezione;
- "Condizioni di servizio": viene controllata la presenza di un tag <a> con ``data-element="service-file"`` contenente il link al file dei "Termini e condizioni di servizio";
- "Contatti": viene controllata la presenza di un tag <div> con ``data-element="service-area"`` che identifica i contatti.


Viene inoltre controllata la presenza di altri componenti al di fuori dell'indice:

- "Titolo": viene controllata la presenza di un tag HTML con ``data-element="service-title"`` che identifica il titolo del servizio e che questo abbia almeno 3 caratteri;
- "Descrizione": viene controllata la presenza di un tag HTML con ``data-element="service-description"`` che identifica la descrizione del servizio e che questo abbia almeno 3 caratteri;
- "Stato": viene controllata la presenza di un tag HTML con ``data-element="service-status"`` che identifica lo stato del servizio;
- "Tassonomie argomenti": viene controllata la presenza di almeno un tag <a> con ``data-element="service-topic"`` che identificano gli argomenti del servizio (es. Turismo);
- "Categoria del servizio": viene controllata la presenza di un tag HTML con ``data-element="breadcrumb"`` che identifica la breadcrumb. In questo componente vengono individuati i testi relativi ai vari <li> e viene controllata la presenza di almeno 3 caratteri nel testo successivo a "Servizi";
- "Area": viene controllata la presenza di un tag HTML con ``data-element="service-area"`` che identifica l'area responsabile del servizio e che questo abbia almeno 3 caratteri.


*Esempio*:

.. literalinclude:: esempi-codice-comuni/c-si-1-3-g.html

.. literalinclude:: esempi-codice-comuni/c-si-1-3-h.html


.. note::

  Per quanto riguarda la sezione “Tempi e scadenze” e “Accedi al servizio” l’audit darà esito positivo in queste sezioni se almeno una delle condizioni sopra riportate sono rispettate per le rispettive sezioni.


Voci delle quali viene verificata la presenza all’interno della pagina:

- Categoria del servizio (la tipologia di servizio indicata nella breadcrumb),
- Titolo del servizio,
- Stato del servizio (nel caso in cui il servizio non è attivo deve essere indicato il Motivo dello stato),
- Descrizione breve,
- A chi è rivolto,
- Come fare,
- Cosa serve,
- Cosa si ottiene,
- Tempi e scadenze,
- Accedi al servizio,
- Condizioni di servizio,
- Contatti (indicando l’Unità Organizzativa responsabile),
- Argomenti.

Voci delle quali viene verificata la presenza e sequenzialità all’interno dell’indice della pagina:

- A chi è rivolto,
- Come fare,
- Cosa serve,
- Cosa si ottiene,
- Tempi e scadenze,
- Accedi al servizio,
- Condizioni di servizio,
- Contatti.


*Esempi:*

.. literalinclude:: esempi-codice-comuni/c-si-1-3-b.html

.. literalinclude:: esempi-codice-comuni/c-si-1-3-c.html

.. literalinclude:: esempi-codice-comuni/c-si-1-3-d.html

.. literalinclude:: esempi-codice-comuni/c-si-1-3-e.html

.. literalinclude:: esempi-codice-comuni/c-si-1-3-f.html
  

Criterio C.SI.1.4 - Utilizzo di temi per CMS (Content Management System)
----------------------------------------------------------------------------

**Condizioni di successo:** se è in uso il tema CMS del modello per i Comuni, la versione utilizzata è uguale o superiore alla 1.0.

**Modalità di verifica:** viene verificata in qualsiasi file .css in homepage la versione e la presenza di un testo specifico.

Il testo ricercato nei file .css è:

/*!
Theme Name: [contenuto]
Author: [contenuto]
Description: Design Comuni Italia [contenuto] [parola “WordPress” o “Drupal”] [contenuto]
Version: [numero della versione]
License: [contenuto]
Text Domain: design_comuni_italia
*/

  

Criterio C.SI.1.5 - Vocabolari controllati
---------------------------------------------

**Condizioni di successo:** gli argomenti utilizzati appartengono alla lista indicata all'interno del documento di architettura dell'informazione del modello Comuni alla voce "Tassonomia ARGOMENTI" o al vocabolario controllato EuroVoc.

**Modalità di verifica:** gli argomenti identificati all'interno della funzione di ricerca del sito vengono confrontati con l'elenco di voci presente nel documento di architettura dell'informazione e con il vocabolario controllato EuroVoc, usando nella ricerca specifici attributi data-element.

**Requisiti tecnici:** In homepage, all’interno di un tag <a>, deve esserci l’attributo ``data-element="all-topics"`` che riporta alla pagina template-argomenti.html. In template-argomenti deve esserci una lista di argomenti (tag <a>) con l’attributo ``data-element="topic-element"`` che contengono del testo con il nome dell’argomento. 

**Esempi:**

.. literalinclude:: esempi-codice-comuni/c-si-1-5-a.html

.. literalinclude:: esempi-codice-comuni/c-si-1-5-b.html
  
  

Criterio C.SI.1.6 - Voci di menù di primo livello
-------------------------------------------------------

**Condizioni di successo:** le voci del menù di primo livello del sito sono esattamente quelle indicate nel documento di architettura dell'informazione e sono nell'ordine indicato (ovvero Amministrazione, Novità, Servizi, Vivere il Comune).

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, vengono identificate le voci presenti nel menù del sito, il loro ordine e confrontate con quanto indicato nel documento di architettura dell'informazione, applicando una tolleranza di massimo 3 voci aggiuntive.

Viene verificata la presenza e la sequenzialità delle seguenti voci:

- *Amministrazione*
- *Novità*
- *Servizi*
- *Vivere il Comune* o *Vivere {nome_Comune}*


**Template HTML  su cui si effettua scraping:** template-homepage.html

**Requisiti tecnici:** In template-homepage deve esserci un <ul> con l’attributo ``data-element=”main-navigation”`` che contenga degli <li> e degli <a> in cui ci sono le label (può contenere altri tag). 

**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-1-6.html

    
Criterio C.SI.1.7 - Titoli delle pagine di secondo livello
---------------------------------------------------------------

**Condizioni di successo:** i titoli delle pagine di secondo livello corrispondono a quelli indicati nel capitolo "Conformità al modello Comuni" della Documentazione del Modello Comuni.

**Modalità di verifica:** tramite ricerca di specifici attributi data-element, viene verificato che i titoli delle card usate per rimandare alle pagine di secondo livello siano corretti e presenti sulle rispettive pagine genitore di primo livello. Nel caso della pagina di primo livello "Vivere il Comune", viene verificato che i titoli delle pagine di secondo livello raggiungibili da questa siano corretti. Nel conteggio vengono incluse anche le pagine di secondo livello raggiungibili da pagine di primo livello non indicate nella documentazione.

I titoli che vengono verificati sono:

- Per la sezione Amministrazione, “Organi di governo”, “Aree amministrative”, “Uffici”, “Enti e fondazioni”, “Politici”, “Personale amministrativo”, “Documenti e dati”;
- Per la sezione Novità, “Notizie”, “Comunicati”, “Avvisi”
- Per la sezione Servizi, “Educazione e formazione”, “Salute, benessere e assistenza”, “Vita lavorativa”, “Mobilità e trasporti”, “Catasto e urbanistica”, “Anagrafe e stato civile”, “Turismo”, “Giustizia e sicurezza pubblica”, “Tributi, finanze e contravvenzioni”, “Cultura e tempo libero”, “Ambiente”, “Imprese e commercio”, “Autorizzazioni”, “Appalti pubblici”, “Agricoltura e pesca”;
- Per la sezione Vivere il Comune o Vivere {nome_comune}, “Luoghi”, “Eventi”.

**Requisiti tecnici:** 

*Caricamento pagine primo livello*:

In homepage, per poter identificare i link alle pagine di primo livello, nel menù principale identificato dal tag <div class="navbar"> i link alle pagine di primo livello devono contenere all'interno del tag <a class="nav-link"> i seguenti attributi:

- "Amministrazione": ``data-element="management"``
- "Novità": ``data-element="news"``
- "Servizi": ``data-element="all-services"``
- "Vivere il Comune": ``data-element="live"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

L'assenza di uno dei data-element (ad eccezione di quelli relativi a eventuali voci aggiuntive) porta all'impossibilità di esecuzione dell'audit in quanto non sarà possibile recuperare il link.


*Caricamento voci di secondo livello*:

- "Amministrazione": nella pagina di primo livello, le card sotto la voce “Categoria” dovranno contenere un tag <a> con ``data-element=”management-category-link”`` dal quale verrà prelevato il testo;
- "Novità": nella pagina di primo livello, le card sotto la voce “Categoria” dovranno contenere un tag <a> con ``data-element=”news-category-link”`` dal quale verrà prelevato il testo.
- "Servizi": nella pagina di primo livello, le card sotto la voce “Categoria” dovranno contenere un tag <a> con ``data-element=”service-category-link”`` dal quale verrà prelevato il testo.
- "Vivere il Comune": la pagina di primo livello dovrà contenere due bottoni. Il bottone che porta alla pagina di secondo livello "Eventi" dovrà contenere ``data-element="live-button-events"`` e il bottone che porta alla pagina di secondo livello "Luoghi" dovrà contenere ``data-element="live-button-locations"``. Per entrambi i bottoni il data-element dovrà essere posizionato sul tag <button> e all'interno dell'attributo "onclick" del bottone dovrà essere presente il link alla pagina di secondo livello. In queste pagine di secondo livello dovrà essere presente un tag HTML con ``data-element=”page-name”`` che identifica il titolo della pagina.
- Eventuali voci aggiuntive: nel caso il sito avesse voci di menù di primo livello aggiuntive esse dovranno contenere il ``data-element=”custom-submenu”``. In queste pagine è necessario inserire il ``data-element=”custom-category-link”`` per le card sotto la voce “Categoria”.


**Esempi:**

.. literalinclude:: esempi-codice-comuni/c-si-1-7-a.html

.. literalinclude:: esempi-codice-comuni/c-si-1-7-b.html


Criterio C.SI.2.1 - Prenotazione appuntamenti
------------------------------------------------------

**Condizioni di successo:** la funzionalità di prenotazione di un appuntamento presso lo sportello è presente in tutte le schede servizio che lo richiedono.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza del componente "Prenota appuntamento" all'interno di una scheda servizio selezionata casualmente. Questo test non ha una condizione di fallimento in quanto dipende dal servizio specifico. analizzato; 

**Requisiti tecnici:**

*Caricamento pagina primo livello*:

In homepage, per poter identificare il link alla pagina di primo livello "Servizi", nel menù principale identificato dal tag <div class="navbar"> il link alla pagina deve contenere, all'interno del tag <a class="nav-link">, il ``data-element="all-services"``.

L'assenza del data-element porta all'impossibilità di esecuzione dell'audit in quanto non sarà possibile recuperare il link.

*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.

*Controllo breadcrumb*:

Nelle schede servizio e anche nella pagina di primo livello “Servizi” deve esserci un tag <a> che contiene l’attributo ``data-element="appointment-booking"``. Nella pagina identificata dal link è necessaria la presenza di un tag <ul>/<ol> con ``data-element=”breadcrumb”`` contenente altri tags <li>. Viene recuperato il testo da questi tags e viene controllata la presenza di un testo con almeno 3 caratteri successivo al livello “/Servizi”.


**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-2-1.html


Criterio C.SI.2.2 - Richiesta di assistenza / contatti
----------------------------------------------------------

**Condizioni di successo:** i contatti dell'ufficio preposto all'erogazione del servizio sono presenti in tutte le schede servizio.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza della voce "Contatti" all'interno dell'indice di una scheda servizio selezionata casualmente.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Requisiti tecnici:**

*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.

*Controllo sui contatti*:

All’interno della pagina di dettaglio servizio deve esserci tag <ul> con zzdata-element="page-index"zz contenente altri tags <li> con la label “Contatti”. E nella pagina è necessaria la presenza di un componente che contiene ``data-element=”service-area”``.

**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-2-2.html
    
    
Criterio C.SI.2.3 - Richiesta di assistenza / domande frequenti
----------------------------------------------------------------------------

**Condizioni di successo:** nel footer del sito è presente un link contenente le espressioni "FAQ" oppure "domande frequenti" che invia a una pagina di domande frequenti.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza del link nel footer che invii ad una pagina esistente e che il testo del link contenga almeno una delle espressioni richieste, senza fare distinzione tra caratteri minuscoli o maiuscoli.

**Template HTML su cui si effettua scraping:** template-homepage.html

**Requisiti tecnici:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla sezione FAQ. Il tag <a> deve avere l’attributo ``data-element="faq"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-2-3.html


Criterio C.SI.2.4 - Segnalazione disservizio
-----------------------------------------------

**Condizioni di successo:** nel footer del sito è presente un link per la segnalazione di un disservizio che contenga le espressioni "disservizio" oppure "segnala disservizio" oppure "segnalazione disservizio".

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza del link nel footer che invii ad una pagina esistente e che il testo del link contenga almeno una delle espressioni richieste, senza fare distinzione tra caratteri minuscoli o maiuscoli.

**Template HTML su cui si effettua scraping:** template-homepage.html

**Requisiti tecnici:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla Segnalazione disservizio. Il tag <a> deve avere l’attributo ``data-element="report-inefficiency"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-2-4.html
  

Criterio C.SI.2.5 - Valutazione dell’esperienza d’uso, chiarezza delle pagine informative
--------------------------------------------------------------------------------------------

**Condizioni di successo:** la funzionalità per valutare la chiarezza informativa è presente su tutte le pagine di primo e secondo livello del sito; 

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza del componente su una pagina di primo livello selezionata casualmente e su una pagina di secondo livello selezionata casualmente a partire dalla pagina "Servizi".

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-servizi-servizio.html

**Requisiti tecnici:** 

*Caricamento pagine primo livello*:

In homepage, per poter identificare i link alle pagine di primo livello, nel menù principale identificato dal tag <div class="navbar"> i link alle pagine di primo livello devono contenere all'interno del tag <a class="nav-link"> i seguenti attributi:

- "Amministrazione": data-element="management"
- "Novità": data-element="news"
- "Servizi": data-element="all-services"
- "Vivere il Comune": data-element="live"
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

L'assenza di uno dei data-element (ad eccezione di quelli relativi a eventuali voci aggiuntive) porta all'impossibilità di esecuzione dell'audit in quanto non sarà possibile recuperare il link.


*Caricamento pagine di secondo livello*:

Per il caricamento delle pagine di secondo livello è necessario che i data-element alle pagine di primo livello siano correttamente posizionati all'interno dei link delle pagine di primo livello nel menù principale.

La pagina di primo livello "Amministrazione", identificata grazie al ``data-element="management"``, dovrà contenere il ``data-element="management-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Novità", identificata grazie al ``data-element="news"``, dovrà contenere il ``data-element="news-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Vivere il comune", identificata grazie al ``data-element="live"``, dovrà contenere due bottoni. Il bottone che porta alla pagina di secondo livello "Eventi" dovrà contenere ``data-element="live-button-events"`` e il bottone che porta alla pagina di secondo livello "Luoghi" dovrà contenere ``data-element="live-button-locations"``. Per entrambi i bottoni il data-element dovrà essere posizionato sul tag <button> e all'interno dell'attributo "onclick" del bottone dovrà essere presente il link alla pagina di secondo livello. La mancata individuazione di almeno un link attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.

Nel caso fossero presenti delle voci aggiuntive di primo livello esse vengono identificate attraverso il ``data-element=”custom-submenu”``. In ognuna di queste pagine è necessaria la presenza del ``data-element=”custom-category-link”`` all’interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello.


*Controllo componente di valutazione*:

All’interno delle pagine di primo e secondo livello verrà analizzato il componente che contiene l’attributo ``data-element=”feedback”``. La presenza di questo componente è obbligatoria per il risultato positivo di questo audit.

Di questo componente con ``data-element=”feedback”`` vengono analizzate le sue parti:

- Domanda iniziale: individuato attraverso l’attributo ``data-element=”feedback-title”``. Questo è da inserire all’interno dell’<h2> che contiene la domanda iniziale;
- Scala di valutazione: individuati attraverso l’attributo ``data-element=”feedback-rate-{N}”`` nella <label> del input. {N} viene sostituito con il valore di quel input. (es: data-element= “feedback-rate-1”, associato al valore minimo “1”);
- Componente di follow up positivo: questo componente comprende tutte le parti per permettere all’utente di fornire un feedback positivo. Esso viene individuato attraverso l’attributo ``data-element=”feedback-rating-positive”`` nel <fieldset> che contiene domanda e risposte. Per la domanda viene inserito l’attributo ``data-element=”feedback-rating-question”`` nella <legend> contente la domanda. Per le risposte viene inserito l’attributo ``data-element=”feedback-rating-answer”`` nella <label> contenente ogni risposta. 
- Componente di follow up negativo: questo componente comprende tutte le parti per permettere all’utente di fornire un feedback negativo. Esso viene individuato attraverso l’attributo ``data-element=”feedback-rating-negative”`` nel <fieldset> che contiene domanda e risposte. Per la domanda viene inserito l’attributo ``data-element=”feedback-rating-question”`` nella <legend> contente la domanda. Per le risposte viene inserito l’attributo ``data-element=”feedback-rating-answer”`` nella <label> contenente ogni risposta;
- Campo di testo libero: individuato attraverso l’attributo ``data-element=”feedback-input-text”`` dentro <input> della casella di testo per fornire una risposta libera alla fine del feedback. 



**Esempi:**
  
.. literalinclude:: esempi-codice-comuni/c-si-2-5-a.html

.. literalinclude:: esempi-codice-comuni/c-si-2-5-b.html

.. literalinclude:: esempi-codice-comuni/c-si-2-5-c.html


Criterio C.SI.2.6 - Valutazione dell'esperienza d'uso, chiarezza informativa della scheda di servizio
----------------------------------------------------------------------------------------------------------------


**Requisiti tecnici**:

*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link alla pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio". Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.


*Controllo componente di valutazione*:

All’interno delle pagine di primo e secondo livello verrà analizzato il componente che contiene l’attributo ``data-element=”feedback”``. La presenza di questo componente è obbligatoria per il risultato positivo di questo audit.

Di questo componente con ``data-element=”feedback”`` vengono analizzate le sue parti:

- Domanda iniziale: individuato attraverso l’attributo ``data-element=”feedback-title”``. Questo è da inserire all’interno dell’<h2> che contiene la domanda iniziale.
- Scala di valutazione: individuati attraverso l’attributo ``data-element=”feedback-rate-{N}”`` nella <label> del input. {N} viene sostituito con il valore di quel input. (es: data-element= “feedback-rate-1”, associato al valore “1”);
- Componente di follow up positivo: questo componente comprende tutte le parti per permettere all’utente di fornire un feedback positivo. Esso viene individuato attraverso l’attributo ``data-element=”feedback-rating-positive”`` nel <fieldset> che contiene domanda e risposte. Per la domanda viene inserito l’attributo ``data-element=”feedback-rating-question”`` nella <legend> contente la domanda. Per le risposte viene inserito l’attributo ``data-element=”feedback-rating-answer”`` nella <label> contenente ogni risposta;
- Componente di follow up negativo: questo componente comprende tutte le parti per permettere all’utente di fornire un feedback negativo. Esso viene individuato attraverso l’attributo ``data-element=”feedback-rating-negative”`` nel <fieldset> che contiene domanda e risposte. Per la domanda viene inserito l’attributo ``data-element=”feedback-rating-question”`` nella <legend> contente la domanda. Per le risposte viene inserito l’attributo ``data-element=”feedback-rating-answer”`` nella <label> contenente ogni risposta;
- Campo di testo libero: individuato attraverso l’attributo ``data-element=”feedback-input-text”`` dentro <input> della casella di testo per fornire una risposta libera alla fine del feedback.



Criterio C.SI.3.1 - Cookie
----------------------------------

**Condizioni di successo:** il dominio di tutti i cookie già presenti nel sito, ovvero senza che sia stata espressa una preferenza da parte dell’utente riguardo il loro uso, è corrispondente al dominio del sito web del Comune.

**Modalità di verifica:** viene verificato che al caricamento di ogni pagina analizzata il dominio dei cookie identificati sia corrispondente al dominio del sito web. L'audit controlla il dominio dei cookie sull’homepage, su N schede servizio, su N pagine di primo livello, su N pagine di secondo livello e per la sezione “Vivere il comune” solo nella pagina a cui si viene portati all’onclick di “Tutti gli eventi” nella quale vengono prelevate le pagine di terzo livello.

**Requisiti tecnici:**

*Caricamento pagina di accesso all’area riservata*:

In homepage, se è presente un link alla pagina di accesso all'area riservata, questo deve contenere il ``data-element="personal-area-login"`` nel tag <a> contenete il link alla pagina.

*Caricamento pagina di prenotazione appuntamenti*:

Per caricare la pagina prenotazione appuntamenti è necessario che il ``data-element=”all-service”`` sia posizionato in homepage nel link della pagina di primo livello “Servizi”. In questa pagina di primo livello il link alla pagina di prenotazione appuntamenti deve contenere il ``data-element="appointment-booking"`` nel tag <a> contenente il link alla pagina.

*Caricamento pagine primo livello*:

In homepage, per poter identificare i link alle pagine di primo livello, nel menù principale identificato dal tag <div class="navbar"> i link alle pagine principali devono contenere all'interno del tag <a class="nav-link"> i seguenti attributi:

- "Amministrazione": ``data-element="management"``
- "Novità": ``data-element="news"``
- "Servizi": ``data-element="all-services"``
- "Vivere il Comune": ``data-element="live"``
- Eventuali voci aggiuntive: ``data-element=”custom-submenu”``

L'assenza di uno dei data-element (ad eccezione di quelli relativi a eventuali voci aggiuntive) porta all'impossibilità di esecuzione dell'audit in quanto non sarà possibile recuperare il link.

*Caricamento pagine di secondo livello*:

Per il caricamento delle pagine di secondo livello è necessario che i data-element alle pagine di primo livello siano correttamente posizionati all'interno dei link delle pagine di primo livello nel menù principale.

La pagina di primo livello "Amministrazione", identificata grazie al ``data-element="management"``, dovrà contenere il ``data-element="management-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Novità", identificata grazie al ``data-element="news"``, dovrà contenere il ``data-element="news-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-category-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello. La mancata individuazione di almeno un link attraverso questo data-element porta all'impossibilità di esecuzione dell'audit.

La pagina di primo livello "Vivere il comune", identificata grazie al ``data-element="live"``, dovrà contenere due bottoni. Il bottone che porta alla pagina di secondo livello "Eventi" dovrà contenere ``data-element="live-button-events"`` e il bottone che porta alla pagina di secondo livello "Luoghi" dovrà contenere ``data-element="live-button-locations"``. Per entrambi i bottoni il data-element dovrà essere posizionato sul tag <button> e all'interno dell'attributo "onclick" del bottone dovrà essere presente il link alla pagina di secondo livello. La mancata individuazione di almeno un link attraverso questi data-element porta all'impossibilità di esecuzione dell'audit.

Nel caso fossero presenti delle voci aggiuntive di primo livello esse vengono identificate attraverso il ``data-element=”custom-submenu”``. In ognuna di queste pagine è necessaria la presenza del ``data-element=”custom-category-link”`` all’interno dei tag <a> contenenti i link di atterraggio alle pagine di secondo livello.


*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.


*Caricamento pagine di quarto livello "Evento"*:

Per il caricamento di queste pagine di quarto livello è necessario che il ``data-element=”live”`` della pagina di primo livello "Vivere il Comune" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale e che il ``data-element="live-button-events"`` sia correttamente posizionato nel bottone che porta alla pagina di secondo livello “Eventi”.

La pagina di secondo livello "Eventi", dovrà contenere il ``data-element="event-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di quarto livello degli eventi. Se nella pagina è presente un bottone che permette di caricare altri link agli eventi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. 




Criterio C.SI.3.2 - Dichiarazione di accessibilità
-------------------------------------------------------

**Condizioni di successo:** il sito presenta una voce nel footer che riporta a una dichiarazione di accessibilità AgID valida per il sito.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza di un link nel footer che riporti a una pagina esistente, che l'url della pagina di destinazione inizi con "https://form.agid.gov.it/view/" e che la pagina contenga l'url del sito del Comune.

**Requisiti tecnici:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla dichiarazione di accessibilità. Il tag <a> deve avere l’attributo ``data-element="accessibility-link"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-3-2.html


Criterio C.SI.3.3 - Informativa privacy
--------------------------------------------

**Condizioni di successo:** il sito presenta una voce nel footer che riporta all'informativa privacy.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza di un link nel footer che riporti a una pagina esistente e con certificato HTTPS valido e attivo.

**Template HTML su cui si effettua scraping:** template-homepage.html

**Requisiti tecnici:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla privacy policy. Il tag <a> deve avere l’attributo ``data-element="privacy-policy-link"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

.. literalinclude:: esempi-codice-comuni/c-si-3-3.html


Criterio C.SI.3.4 - Licenza e attribuzione
-------------------------------------------------

**Requisiti tecnici**:

All’interno del footer della homepage(tag <footer>) deve esserci un tag <a> che contiene l’href alla pagina delle note legali. Il tag <a> deve avere l’attributo ``data-element="legal-notes"``. L’<a> può essere contenuto in altri tag, esempio <li>.

All’interno della pagina individuata da questo link dovrà essere presente un tag HTML con ``data-element=”legal-notes-section”`` che identifica il titolo della sezione da analizzare e uno o più tag <p> con ``data-element=”legal-notes-body”`` associati a ogni <p> contenente il testo della sezione.



Criterio C.SI.5.2 - Dominio istituzionale
--------------------------------------------


**Requisiti tecnici**:

*Caricamento pagina di accesso all’area riservata*:

In homepage, se è presente un link alla pagina di accesso all'area riservata, questo deve contenere il ``data-element="personal-area-login"`` nel tag <a> contenete il link alla pagina.



Raccomandazione R.SI.1.1 - Metatag
---------------------------------------

**Condizioni di successo:** le voci delle schede servizio presentano tutti i metatag richiesti dal modello.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza e correttezza dei metatag indicati nella sezione "Dati strutturati e interoperabilità" della documentazione in una scheda servizio selezionata casualmente.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Requisiti tecnici:** 

*Caricamento pagine di terzo livello "Scheda servizio"*:

Per il caricamento di queste pagine di terzo livello è necessario che il data-element alla pagina di primo livello "Servizi" sia correttamente posizionato all'interno del link della pagina di primo livello nel menù principale.

La pagina di primo livello "Servizi", identificata grazie al ``data-element="all-services"``, dovrà contenere il ``data-element="service-link"`` all'interno dei tag <a> contenenti i link di atterraggio alle pagine di terzo livello “Scheda servizio”. Se nella pagina è presente un bottone che permette di caricare altri link ai servizi attraverso una chiamata AJAX esso dovrà contenere il ``data-element="load-other-cards"``. La mancata individuazione di almeno un link attraverso il ``data-element="service-link"`` porta all'impossibilità di esecuzione dell'audit.

All’interno dell’HTML delle pagine “Scheda servizio” deve esserci un attributo <script> che contiene come valore un JSON di metatag. Il tag <script> deve avere l'attributo ``data-element="metatag"``.


**Esempio:**

.. literalinclude:: esempi-codice-comuni/r-si-1-1.html
