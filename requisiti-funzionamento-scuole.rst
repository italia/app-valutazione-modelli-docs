Requisiti di funzionamento per il modello scuole
=================================================

Per il corretto funzionamento dell'App di valutazione, è necessario inserire dei **data attribute** all’interno dei tag HTML del sito.

.. note::
  
  I data attribute sono già presenti nei template HTML e nei temi CMS forniti da Designers Italia.


La chiave generale dell’attribute è ``data-element=*`` e va inserita all’interno dei tag HTML.

Per tutto ciò che è un URL, per esempio FAQ o Segnalazione disservizio, l'App controlla anche che l’URL nell’href del componente non sia nullo e, per alcuni casi specifici, che sia in HTTPS (vedi dettagli audit) e che riporti ad una pagina “funzionante”.

NB: Per tutto ciò che viene controllato sulla base di un vocabolario si utilizzano controlli non case-sensitive. 


Criterio C.SC.1.1
--------------------

**Comportamento atteso:** L'audit preleva una scheda servizio casuale a partire dal listato di servizi e ne ricava i font presenti.

**Template HTML su cui si effettua scraping:** scuole-home.html, scuola-servizi-tipologia.html, scuole-servizio-generico.html

**Mappatura:** Il menù di secondo livello "Servizi" deve contenere voci (ad esempio "Servizi per il personale scolastico" e "Servizi per famiglie e studenti") entrambe con attributo data-element=”service-type” al fine di prelevare gli URL (in modo randomico) del listato servizi (contengono l’URL alla pagina scuola-servizi-tipologia), devono essere degli <a> con “href” e possono essere inclusi in altri tag (ad es: <li>).
Dalla pagina "scuola-servizi-tipologia" le card devono contenere una tag <a> con attributo ``data-element=”service-link”``. 


C.SC.1.4
-----------

**Comportamento atteso:** L'Audit controlla le voci del menù di primo livello del sito web

**Template HTML su cui si effettua scraping:** scuole-home.html

**Mappatura:** Il tag <ul> deve avere l’attributo ``data-element=”menu”`` ed essere composto da <li> e <a>

**Esempio:**

<ul data-element="menu">
  <li>
    <a href="#">
      Scuola
    </a>
 </li>
 <li>
    <a href="#">
      Servizi
    </a>
 </li>
 …
</ul>

C.SC.1.5
---------------

**Comportamento atteso:** L'audit controlla le voci di menù di secondo livello della voce di primo livello "Scuola"

**Template HTML su cui si effettua scraping:** scuole-home.html

**Mappatura:** Il tag <ul> deve avere l’attributo ``data-element=”school-submenu”`` ed essere composto da <li> (può contenere anche altri tag, ad esempio <a>). 

**Esempio:**

<ul data-element="school-submenu">
  <li>
    <a href="#">Presentazione</a>
  </li>
  <li>
    <a href="#">I luoghi della scuola</a>
  </li>
  …
</ul>

C.SC.2.1
-----------

**Comportamento atteso:** L'audit controlla la presenza della privacy-policy

**Template HTML su cui si effettua scraping:** scuole-home.html

**Mappatura:** Il tag <a> deve avere l’attributo ``data-element=”privacy-policy-link”`` e contenere un “href” (può essere contenuto in altri tag, ad esempio <li> …). Il tag deve essere presente all’interno del tag <footer>. 

**Esempio:**

<footer>
…
<li>
<a href="#" data-element="privacy-policy-link">Privacy Policy</a>
</li>
…
</footer>

C.SC.2.2
-----------

**Comportamento atteso:** L'audit controlla la presenza della dichiarazione di accessibilità

**Template HTML su cui si effettua scraping:** scuole-home.html

**Mappatura:** Il tag <a> deve avere l’attributo ``data-element=”accessibility-link”`` e contenere un “href” (può essere contenuto in altri tag, ad esempio <li> …). Il tag deve essere presente all’interno del tag <footer>. 

**Esempio:**

<footer>
…
<li>
<a href="#" data-element="accessibility-link">Dichiarazioni di accessibilita</a>
</li>
…
</footer>


Raccomandazione R.SC.1.1
----------------------------

**Comportamento atteso:** L'audit controlla la presenza di determinati vocaboli alla pagina "Risultati ricerca" sotto la voce "Argomenti".

**Template HTML su cui si effettua scraping:** scuole-home.html, scuole-risultati-ricerca.html

**Mappatura:** Il bottone (<button>) "cerca" deve avere attributo ``data-element=”search-modal-button”`` in modo da poterne simulare l'apertura. Il tag <input> di testo deve avere attributo ``data-element=”search-modal-input”`` in modo da poter essere inserito testo di ricerca. Infine, il bottone per cercare (avvia ricerca) deve avere ``data-element=”search-submit”``. 
La pagina risultati ricerca deve contenere un listato di argomenti <ul> con attributo ``data-element=”all-topics”``; deve contenere degli <li> (può contenere altri tag). 

**Esempio:**

<button type="button" data-element="search-modal-button">
<input data-element="search-modal-input" placeholder="Cerca servizi, notizie o documenti">
<button type="button data-element="search-submit">
 
<ul data-element="all-topics">
  <li>
    <div class="custom">
       <label class="custom-control-label"> Verso il liceo</label>
    </div>
  </li>
  <li>
    <div class="custom">
       <label class="custom-control-label">Comunicati</label>
    </div>
  </li>
…
</ul>


Raccomandazione R.SC.1.2
---------------------------

**Comportamento atteso:** L'audit preleva una scheda servizio casuale a partire dal listato di servizi e ne ispeziona gli elementi.

**Template HTML su cui si effettua scraping:** scuole-home.html, scuola-servizi-tipologia.html, scuole-servizio-generico.html

**Mappatura:** Il menù di secondo livello "Servizi" deve contenere voci (ad esempio "Servizi per il personale scolastico" e "Servizi per famiglie e studenti") entrambe con attributo ``data-element=”service-type”`` al fine di prelevare gli URL (in modo randomico) del listato servizi (contengono l’URL alla pagina scuola-servizi-tipologia), devono essere degli <a> con “href” e possono essere inclusi in altri tag (ad es: <li>).

Dalla pagina "scuola-servizi-tipologia" le card devono contenere una tag <a> con attributo ``data-element=”service-link”``.

Si atterra quindi sulla pagina "scuole-servizio-generico" che contiene le componenti da ispezionare: 

- Titolo con attributo ``data-element=”service-title”`` che può essere un tag qualsiasi (h1, p, etc..). Viene controllata la presenza del Titolo della scheda servizio.
- Descrizione con attributo ``data-element=”service-description”`` che può essere un tag qualsiasi (h1, p, etc..). Viene controllata la presenza della Descrizione della scheda servizio.
- La breadcrumb <ul>/<ol> con attributo ``data-element=”breadcrumb”`` che contiene i tag <li> che possono contenere altri tag. Viene controllato che all’interno della breadcrumb della scheda siano contenuti i valori: "Famiglie e studenti" o "Personale scolastico". 
- La sezione "A cosa serve" con ``data-element=”used-for”`` che può essere un tag qualsiasi. Viene controllata la presenza della sezione “A cosa serve” della scheda servizio.
- Gli argomenti con ``data-element=”topic-list”`` in un tag <a>.  Viene controllata la presenza di almeno una voce “argomenti” all’interno della scheda servizio. 
- Gli elementi del luogo con ``data-element=”places”`` che contenga i tag <span> per la label e <p> per il valore relativo alla label. Controlla la presenza della card “luogo” e alcuni elementi al suo interno, quali: "indirizzo", "orari", "gps", “email”, “PEC” e “telefono”. Il controllo viene effettuato sulla presenza della label e sulla sua valorizzazione (cioè le label devono chiamarsi “indirizzo”, “orari” etc..). NB: Per quanto riguarda le coordinate GPS viene controllato che l’URL della mappa contenga il valore “map” (in modo da coprire più servizi di mappe possibili) mentre per quanto riguarda gli orari viene controllato tramite Regexp che il valore della label “orari” contenga un orario in formato in ore, minuti oppure ore, minuti e secondi. 
- Il componente per le strutture responsabili che abbia un wrapper con ``data-element=”structures”`` e che contenga un tag <a> con l’url (href) alla Struttura responsabile del servizio. Viene controllata la presenza dell’elemento. 
- Il componente metadati con ``data-element=”metadata”`` che può essere un tag qualsiasi il cui testo contenga le stringhe “pubblicato” o “revisionato”.
- Il componente indice <ul>/<ol> con ``data-element=”page-index”`` che contenga <li> e <a> in cui devono essere presenti le voci da ispezionare. Su questo menù vengono controllate sia in presenza che in sequenzialità (cioè una voce per essere in posizione corretta deve avere la precedente e la successiva come descritto dal modello). Le voci che vengono controllate sono: "Cos'è", "Come si accede al servizio", "Cosa serve", "Tempi e scadenze", “Contatti” e “Ulteriori informazioni”. 

Voci delle quali viene verificata la presenza: titolo, tipologia (contenuto breadcrumb), tassonomia argomenti, descrizione breve, “Cos’è”, “A cosa serve”, “Come si accede al servizio”, indirizzo (Sede canale fisico), posizione GPS tramite mappa (Sede canale fisico), orario per il pubblico (Sede canale fisico), email (Sede canale fisico), PEC (Sede canale fisico), telefono (Sede canale fisico), “Cosa serve”, “Tempi e scadenze”, “Struttura responsabile del servizio” e metadati.
Voci delle quali viene verificata la presenza e sequenzialità all’interno dell’indice della pagina: "Cos'è", "Come si accede al servizio", "Cosa serve", "Tempi e scadenze", “Contatti” e “Ulteriori informazioni”.

**Esempio:**

<a href="/scuole-servizio-tipologia.html" data-element="service-type"> Servizi per il personale scolastico</a>
 
<div>
<a href="/design-scuole-pagine-statiche/build/scuole-serviziogenerico.html" data-element="service-link">Ricevimento genitori</a>
<a href="/design-scuole-pagine-statiche/build/scuole-servizio-generico.html" data-element="service-link">PagoPa</a>
…
</div>
 
<h1 data-element="service-title">Titolo del servizio, esempio di titolo</h1>
<p data-element="service-description">Titolo alternativo / Sottotitolo di un servizio, esempio di titolo alternativo / sottotitolo</p>
 
<ol data-element="breadcrumb">
  <li><a href="#" title="Vai alla pagina: Home">Home</a></li>
  <li><a href="#" title="Vai alla pagina: Servizi">Servizi</a></li>
  <li><span>Servizio mensa</span></li>
</ol>
 
<h3 class="h6" data-element="used-for">A cosa serve</h3>
 
<div>
  <a href="#" title="Vai all'argomento: Famiglia" data-element="topic-list">Famiglia</a>
  <a href="#" title="Vai all'argomento: Pagamenti" data-element="topic-list"
>Pagamenti</a>
  <a href="#" title="Vai all'argomento: Alimentazione" data-element="topic-list"
>Alimentazione</a>
</div>
 
 
<ul data-element="places">
  <li>
    <div class="location-title">
      <span>Indirizzo</span>
    </div>
    <div class="location-content">
      <p>Via Vaglia, 6, 00139 - Roma RM</p>
    </div>
  </li>
 
<div data-element="structures">
  <div>
    <a href="https://www.google.it">
…
 
 
 
<p data-element="metadata">
