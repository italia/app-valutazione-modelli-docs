Requisiti tecnici e modalità di verifica per il modello Comuni
================================================================

Per il corretto funzionamento dell'App di valutazione, è necessario inserire dei **data attribute** all’interno dei tag HTML del sito.

.. note::
  
  I data attribute sono già presenti nei template HTML e nei temi CMS forniti da Designers Italia.


La chiave generale dell’attribute è ``data-element=*`` e va inserita all’interno dei tag HTML.

Per tutto ciò che è un URL, per esempio FAQ o Segnalazione disservizio, l'App controlla anche che l’URL nell’href del componente non sia nullo e, per alcuni casi specifici, che sia in HTTPS (vedi dettagli audit) e che riporti ad una pagina “funzionante”.

NB: Per tutto ciò che viene controllato sulla base di un vocabolario si utilizzano controlli non case-sensitive. 

Criterio C.SI.1.1
--------------------------------

**Condizioni di successo:** il sito utilizza almeno i font Titillium Web e Lora.

**Modalità di verifica:** tramite ricerca dello specifico attributo data-element, viene verificata la presenza dei font all'interno di una scheda servizio casualmente selezionata.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Mappatura:** In homepage all’interno di un tag <a> deve esserci l’attributo ``data-element="all-services"`` che riporta alla pagina con il listato servizi. All’interno della pagina servizi i servizi devono essere degli <a> con l’attributo ``data-element="service-link"`` che riportano al dettaglio servizio.

Criterio C.SI.1.2
-----------------------

**Condizioni di successo:** il sito usa la libreria Bootstrap Italia in una versione uguale o superiore alla 2.0.

**Modalità di verifica:** viene verificata la presenza della libreria Bootstrap Italia e la versione in uso individuando la proprietà CSS --bootstrap-italia-version all’interno del selettore :root o la variabile globale window.BOOTSTRAP_ITALIA_VERSION.

Criterio C.SI.1.3
-------------------------------

**Condizioni di successo:** nelle schede informative di servizio le voci indicate come obbligatorie sono presenti e sono nell'ordine corretto.

**Modalità di verifica:** viene verificato se le voci indicate come obbligatorie all'interno del documento di architettura dell'informazione sono presenti. Inoltre viene verificato se le voci obbligatorie presenti nell'indice della pagina sono nell'ordine corretto. La verifica viene effettuata su una scheda servizio casualmente selezionata, ricercando le voci indicate nella documentazione del modello tramite specifici attributi data-element.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Mappatura:** In homepage, all’interno di un tag <a>, deve esserci l’attributo ``data-element="all-services"`` che riporta alla pagina con il listato servizi. All’interno della pagina servizi i servizi devono essere degli <a> con l’attributo ``data-element="service-link"`` che riportano al dettaglio servizio. 

.. admonition:: example
   :class: admonition-example display-page
   
   <li>
     &nbsp;&nbsp;<a href="/template-servizi.html">
     &nbsp;&nbsp;<span>Servizi</span>
    &nbsp;</a>
   </li>

   <div>
    &nbsp;<h3><a href="/ template-dettaglio-servizio.html" data-element="service-link">Abbandono di rifiuti in aree private</a></h3>
     &nbsp;<p>Titolo servizio…</p>
   </div>


All’interno della scheda servizio devono esserci i seguenti attributi:

* ``data-element="page-index"``: Per controllo sequenzialità (e presenza) voci – deve essere un tag <ul> con l’attributo che contiene altri <li> e degli <a>. Voci controllate: "A chi è rivolto", "Come fare", "Cosa serve", "Cosa si ottiene", "Tempi e scadenze";
* ``data-element="service-title"``: Controllo presenza titolo – può essere un qualsiasi tag che contenga testo (h1, p etc..);
* ``data-element="service-description"``: Controllo presenza descrizione – può essere un qualsiasi tag che contenga testo (h1, p etc..);
* ``data-element="service-status"``: Controllo status del servizio – può essere un qualsiasi tag che contenga testo (h1, p etc..). La label deve contenere ALMENO il testo: attivo/disattivo/non attivo;
* ``data-element="service-topic"``: Controllo tag – un tag <a> che può contenere anche altri tag;
* ``data-element="service-area"``: Controllo presenza area responsabile del servizio  - un tag <a> che contiene l’attributo.

Voci delle quali viene verificata la presenza: titolo del servizio, categoria del servizio (contenuto breadcrumb), stato del servizio, descrizione breve, “A chi è rivolto”, “Come fare”, “Cosa serve”, “Cosa si ottiene”, “Tempi e scadenze”, “Accedi al servizio” (Canale fisico), “Condizioni di servizio”, “Contatti”, "Unità Organizzativa responsabile" e argomenti.

Voci delle quali viene verificata la presenza e sequenzialità all’interno dell’indice della pagina: “A chi è rivolto”, “Come fare”, “Cosa serve”, “Cosa si ottiene”, “Tempi e scadenze”, “Accedi al servizio”, “Condizioni di servizio” e “Contatti”. 

**Esempio:**

  <ul data-element="page-index">
    <li>
     <a>
        <span>A chi è rivolto</span>
     </a>
    </li>
  

  <h1 data-element="service-title">Iscrizione alla Scuola dell’infanzia</h1>
  

  <p data-element="service-description">Descrizione</p>
  <span data-element="service-status">Servizio attivo</span>
  

Criterio C.SI.1.5
-------------------

**Comportamento atteso:** l'App preleva un listato di vocaboli (argomenti) e ne controlla la presenza su vocabolari dati. 

**Template HTML su cui si effettua scraping:** template-homepage.html, template-argomenti.html

**Mappatura:** In homepage, all’interno di un tag <a>, deve esserci l’attributo ``data-element="all-topics"`` che riporta alla pagina template-argomenti.html. In template-argomenti deve esserci una lista di argomenti (tag <a>) con l’attributo ``data-element="topic-element"`` che contengono del testo con il nome dell’argomento. 

**Esempio:**

  <a href="/template-argomenti.html" 
    <span> Tutti gli argomenti...</span>
  </a>
  

  <a href="#" data-element="topic-element"><h3>Animale domestico</h3></a>
  

Criterio C.SI.1.6
--------------------

**Comportamento atteso:** l'App preleva le voci di menù di primo livello.

**Template HTML  su cui si effettua scraping:** template-homepage.html

**Mappatura:** In template-homepage deve esserci un <ul> con l’attributo ``data-element=”main-navigation”`` che contenga degli <li> e degli <a> in cui ci sono le label (può contenere altri tag). 

**Esempio:**

  <ul data-element="main-navigation">
    <li>
      <a>
        <span>Amministrazione</span>
     </a>
    </li>
    
Criterio C.SI.1.7
-------------------

**Comportamento atteso:** l'App preleva i titoli delle pagine di secondo livello che devono rispettare un vocabolario. 

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html

**Mappatura:** In homepage, la voce di menù “Servizi” deve essere un tag <a> con un un attributo ``data-element="all-services"``. L’href della voce Servizi deve riportare alla pagina template-servizi.html. All’interno della pagina, sotto la voce “Categoria” le card devono contenere degli <a> con l’attributo ``data-element="service-category-link"``. Verrà prelevato il titolo testuale della card.

**Esempio:**

  <a href=”/template-servizi.html"data-element="service">Servizi</a>


  <a data-element="service-page" href="/template-servizi-servizio.html">
  <h3 class="card-title t-primary title-xlarge">Agricoltura e pesca</h3>
  </a>

Criterio C.SI.2.1
-------------------

**Comportamento atteso:** l'App preleva una scheda di servizio casuale e controlla la presenza del componente per prenotare un appuntamento.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Mappatura:** In homepage, all’interno di un tag <a>, deve esserci l'attributo ``data-element="all-services"`` che riporta alla pagina con il listato servizi. All’interno della pagina “Servizi” i servizi devono essere degli <a> con l’attributo ``data-element="service-link"`` che riportano al dettaglio servizio. Nella pagina dettaglio servizio deve esserci un tag <a> che contiene l’attributo ``data-element="appointment-booking"``. Il tag può essere contenuto in altri (esempio: <li>).

**Esempio:**

  <li>
    <a href="#" data-element="appointment-booking">
      <svg class="icon icon-primary icon-sm">
      </svg><span>Prenota appuntamento</span>
   </a>
  </li>


Criterio C.SI.2.2
-----------------

**Comportamento atteso:** l'App preleva una scheda di servizio casuale e controlla la presenza della voce “Contatti” all’interno dell’indice.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Mappatura:** In homepage, all’interno di un tag <a>, deve esserci l'attributo ``data-element="all-services"`` che riporta alla pagina con il listato servizi. All’interno della pagina servizi, i servizi devono essere degli <a> con l’attributo ``data-element="service-link"`` che riportano al dettaglio servizio. All’interno della pagina di dettaglio servizio deve esserci un attributo ``data-element="page-index"`` – deve essere un tag <ul> – con l’attributo che contiene altri <li> che contenga la label “Contatti”.

**Esempio:**

  <ul data-element="page-index">
    <li>
      <a>
        <span>A chi è rivolto</span>
      </a>
    </li>
    
Criterio C.SI.2.3
--------------------

**Comportamento atteso:** l'App controlla la presenza del link alla sezione di FAQ sul footer.

**Template HTML su cui si effettua scraping:** template-homepage.html

**Mappatura:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla sezione FAQ. Il tag <a> deve avere l’attributo ``data-element="faq"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

  <a href="#" data-element="faq">Leggi le FAQ</a>


Criterio C.SI.2.4
-------------------

**Comportamento atteso:** Il crawler controlla la presenza del link alla sezione di Segnalazione disservizio sul footer.

**Template HTML su cui si effettua scraping:** template-homepage.html

**Mappatura:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla Segnalazione disservizio. Il tag <a> deve avere l’attributo ``data-element="report-inefficiency"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

  <a href="#" data-element="report-inefficiency">Segnalazione disservizio</a>
  

Criterio C.SI.2.5
-------------------

**Comportamento atteso:** Il crawler controlla la presenza del componente feedback su una pagina di primo livello estratta casualmente e su una di secondo livello dei servizi estratta casualmente.

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-servizi-servizio.html

**Mappatura:** In homepage all’interno del menù le voci di primo livello devono essere degli <a> con i seguenti tag: ``data-element="management"``, ``data-element="all-services"``, ``data-element="news"``, ``data-element="live"``. L’href deve riportare alle pagine di primo livello in cui deve esserci un componente (un wrapper) come un <div> che contiene l’attributo ``data-element="feedback"``. 
L’href della voce Servizi deve riportare alla pagina template-servizi.html. All’interno della pagina, sotto la voce “Categoria” le card devono contenere degli <a> con l’attributo ``data-element="service-category-link"``
che riportano alla pagina di secondo livello servizio in cui deve esserci un componente (un wrapper) come un <div> che contiene l’attributo ``data-element="feedback"``.

**Esempio:**
  
  <a href=”/template-servizi.html" data-element="all-services">Servizi</a>


  <a data-element="service-category-link" href="/template-servizi-servizio.html">
  <h3 class="card-title t-primary title-xlarge">Agricoltura e pesca</h3>
  </a>


  <div data-element="feedback">
    <div>
      <div>
        <h2>Quanto sono utili le informazioni in questa pagina?</h2>
      </div>

Criterio C.SI.3.2
-------------------

**Comportamento atteso:** l'App verifica la presenza della dichiarazione di accessibilità nel footer.

**Template HTML su cui si effettua scraping:** template-homepage.html

**Mappatura:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla dichiarazione di accessibilità. Il tag <a> deve avere l’attributo ``data-element="accessibility-link"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

  <a href="#" data-element="accessibility-link">Dichiarazione di accessibilità</a>

Criterio C.SI.3.3
--------------------

**Comportamento atteso:** l'App verifica la presenza della privacy policy nel footer. 

**Template HTML su cui si effettua scraping:** template-homepage.html

**Mappatura:** All’interno del footer della pagina (tag <footer>) deve esserci un tag <a> che contiene l’href alla privacy policy. Il tag <a> deve avere l’attributo ``data-element="privacy-policy-link"``. (L’<a> può essere contenuto in altri tag, esempio <li>) 

**Esempio:**

  <a href="#" data-element="privacy-policy-link">Informativa privacy</a>
  

Criterio C.SE.5.1
-----------------

**Comportamento atteso:** l'App preleva l’url per accedere all’area personale e applica gli audit di sicurezza per la verifica del certificato.  

**Template HTML su cui si effettua scraping:** template-homepage.html

**Mappatura:** In homepage all’interno di un tag <a> deve esserci l'attributo ``data-element="personal-area-login"``. 

**Esempio:**

  <a href="#" data-element=”personal-area-login”>
    <span> Accedi all'area personale</span>
  </a>

Criterio C.SE.5.2
-----------------_

**Comportamento atteso:** l'App preleva l’url per accedere all’area personale e applica gli audit di verifica del sottodominio.  

**Template HTML su cui si effettua scraping:** template-homepage.html

**Mappatura:** In homepage all’interno di un tag <a> deve esserci l'attributo ``data-element="personal-area-login"``. 

**Esempio:**

  <a href="#" data-element=”personal-area-login”>
    <span> Accedi all'area personale</span>
  </a>


Raccomandazione R.SI.1.1
-----------------

**Comportamento atteso:** l'App preleva i metatag da una pagina servizio casuale e ne controlla la struttura: presenza delle chiavi con relativa valorizzazione. 

**Template HTML su cui si effettua scraping:** template-homepage.html, template-servizi.html, template-dettaglio-servizio.html

**Mappatura:** In homepage all’interno di un tag <a> deve esserci l’attributo ``data-element="all-services"`` che riporta alla pagina con il listato servizi. All’interno della pagina servizi i servizi devono essere degli <a> con l’attributo ``data-element="service-link"`` che riportano al dettaglio servizio. All’interno dell’HTML della pagina servizio deve esserci un attributo <script> che contiene come valore un JSON di metatag. Il tag <script> deve avere l'attributo ``data-element="metatag"``.

**Esempio:**

  <script data-element="metatag" type="application/ld+json">
  {
    "name": "Iscrizione alla Scuola dell’infanzia",
      "serviceType": "P1Y",
    "serviceOperator": {
      "name": "Lorem"
    },
    "areaServed": {
      "name": "Lorem ipsum"
    },
    "audience": {
      "name": ""
    },
    "availableChannel": {
      "serviceUrl": "Lorem ipsum",
      "serviceLocation": {
        …
      }
    }
  }
