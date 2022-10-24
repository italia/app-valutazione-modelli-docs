Requisiti tecnici e modalità di verifica per il modello scuole
======================================================================

Di seguito sono riportati i criteri di conformità e le raccomandazioni verificabili tramite App di valutazione dell'adesione al modello scuole.

Per il corretto funzionamento dell'App di valutazione, è necessario inserire dei **data attribute** all’interno dei tag HTML del sito.

.. note::
  
  I data attribute, dove possibile, sono già presenti nei materiali forniti da `Designers Italia <https://designers.italia.it/modello/scuole/>`_, sia all'interno dei template HTML che dei CMS messi a disposizione. Rimane tuttavia responsabilità dell'ente verificare che siano correttamente inseriti dovunque richiesto.


La chiave generale dell’attribute è ``data-element=*`` e va inserita all’interno dei tag HTML.

Per tutto ciò che è un URL, per esempio FAQ o Segnalazione disservizio, l'App controlla anche che l’URL nell’href del componente non sia nullo e, per alcuni casi specifici, che sia in HTTPS (vedi dettagli audit) e che riporti ad una pagina “funzionante”.

NB: Per tutto ciò che viene controllato sulla base di un vocabolario si utilizzano controlli non case-sensitive. 


Criterio C.SC.1.1
--------------------
**Condizioni di successo:** il sito utilizza almeno i font Titillium Web e Lora.

**Modalità di verifica:** tramite ricerca dello specifico attributo data-element, viene verificata la presenza dei font all'interno di una scheda servizio casualmente selezionata.

**Template HTML su cui si effettua scraping:** scuole-home.html, scuola-servizi-tipologia.html, scuole-servizio-generico.html

**Requisiti tecnici:** Il menù di secondo livello "Servizi" deve contenere voci (ad esempio "Servizi per il personale scolastico" e "Servizi per famiglie e studenti") entrambe con attributo data-element=”service-type” al fine di prelevare gli URL (in modo randomico) del listato servizi (contengono l’URL alla pagina scuola-servizi-tipologia), devono essere degli <a> con “href” e possono essere inclusi in altri tag (ad es: <li>).
Dalla pagina "scuola-servizi-tipologia" le card devono contenere una tag <a> con attributo ``data-element=”service-link”``. 



Criterio C.SC.1.2
-----------------------

**Condizioni di successo:** il sito usa la libreria Bootstrap Italia in una versione uguale o superiore alla 1.6.

**Modalità di verifica:** viene verificata la presenza della libreria Bootstrap Italia e la versione in uso individuando la proprietà CSS --bootstrap-italia-version all’interno del selettore :root o la variabile globale window.BOOTSTRAP_ITALIA_VERSION.

Criterio C.SC.1.3
----------------------

**Condizioni di successo:** se è in uso il tema CMS del modello scuole, la versione utilizzata è uguale o superiore alla 2.0.

**Modalità di verifica:** viene verificata la versione indicata nel file style.css ricercando la chiave "Text Domain: design_scuole_italia".

Criterio C.SC.1.4
-------------------

**Condizioni di successo:** le voci del menù di primo livello del sito sono esattamente quelle indicate nel documento di architettura dell'informazione e sono nell'ordine indicato (ovvero Scuola, Servizi, Novità, Didattica).

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, vengono identificate le voci presenti nel menù del sito, il loro ordine e confrontate con quanto indicato nel documento di architettura dell'informazione, applicando una tolleranza di massimo 3 voci aggiuntive;

**Template HTML su cui si effettua scraping:** scuole-home.html

**Requisiti tecnici:** Il tag <ul> deve avere l’attributo ``data-element=”menu”`` ed essere composto da <li> e <a>

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

Criterio C.SC.1.5
--------------------

**Condizioni di successo:** le voci del menù di secondo livello corrispondono a quelle indicate nel documento di architettura dell'informazione del modello scuole e sono nell'ordine corretto. 

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la correttezza e l'ordine delle voci del menù di secondo livello riferite alla voce di primo livello "Scuola".

**Template HTML su cui si effettua scraping:** scuole-home.html

**Requisiti tecnici:** Il tag <ul> deve avere l’attributo ``data-element=”school-submenu”`` ed essere composto da <li> (può contenere anche altri tag, ad esempio <a>). 

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

Criterio C.SC.2.1
--------------------

**Condizioni di successo:** il sito presenta una voce nel footer che riporta all'informativa privacy.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza di un link nel footer che riporti a una pagina esistente e con certificato HTTPS valido e attivo.

**Template HTML su cui si effettua scraping:** scuole-home.html

**Requisiti tecnici:** Il tag <a> deve avere l’attributo ``data-element=”privacy-policy-link”`` e contenere un “href” (può essere contenuto in altri tag, ad esempio <li> …). Il tag deve essere presente all’interno del tag <footer>. 

**Esempio:**

<footer>
…
<li>
<a href="#" data-element="privacy-policy-link">Privacy Policy</a>
</li>
…
</footer>

Criterio C.SC.2.2
-------------------

**Condizioni di successo:** il sito presenta una voce nel footer che riporta alla dichiarazione di accessibilità di AGID valida.

**Modalità di verifica:** tramite ricerca di uno specifico attributo data-element, viene verificata la presenza di un link nel footer che riporti a una pagina esistente che sia quella contenente la dichiarazione di accessibilità (il link deve iniziare con "https://form.agid.gov.it/view/").

**Template HTML su cui si effettua scraping:** scuole-home.html

**Requisiti tecnici:** Il tag <a> deve avere l’attributo ``data-element=”accessibility-link”`` e contenere un “href” (può essere contenuto in altri tag, ad esempio <li> …). Il tag deve essere presente all’interno del tag <footer>. 

**Esempio:**

<footer>
…
<li>
<a href="#" data-element="accessibility-link">Dichiarazioni di accessibilita</a>
</li>
…
</footer>


Criterio C.SC.2.3
---------------------

**Condizioni di successo:** il sito presenta solo cookie idonei come definito dalla normativa.

**Modalità di verifica:** viene verificato che il dominio dei cookie identificati sia corrispondente al dominio del sito web. Se nella pagina analizzata non vengono rilevati cookie non verrà generata una tabella di risultati.


Criterio C.SC.3.1
---------------------

**Condizioni di successo:** il sito utilizza un certificato https valido e non obsoleto secondo le raccomandazioni AGID.

**Modalità di verifica:** viene verificato che il certificato https del sito sia valido e attivo.



Raccomandazione R.SC.1.1
----------------------------

**Condizioni di successo:** gli argomenti utilizzati appartengono alla lista indicata all'interno del documento di architettura dell'informazione del modello scuole alla voce "Le parole della scuola". 

**Modalità di verifica:** tramite ricerca di specifici attributi data-element, gli argomenti identificati all'interno della funzione di ricerca del sito vengono confrontati con l'elenco di voci presente nel documento di architettura dell'informazione.

**Template HTML su cui si effettua scraping:** scuole-home.html, scuole-risultati-ricerca.html

**Requisiti tecnici:** Il bottone (<button>) "cerca" deve avere attributo ``data-element=”search-modal-button”`` in modo da poterne simulare l'apertura. Il tag <input> di testo deve avere attributo ``data-element=”search-modal-input”`` in modo da poter essere inserito testo di ricerca. Infine, il bottone per cercare (avvia ricerca) deve avere ``data-element=”search-submit”``. 
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

**Condizioni di successo:** nelle schede informative di servizio le voci indicate come obbligatorie sono presenti e sono nell'ordine corretto.

**Modalità di verifica:** tramite ricerca di specifici attibuti data-element, viene verificato se le voci indicate come obbligatorie all'interno del documento di architettura dell'informazione sono presenti e se le voci obbligatorie presenti nell'indice della pagina sono nell'ordine corretto. La verifica viene effettuata su una scheda servizio casualmente selezionata.

**Template HTML su cui si effettua scraping:** scuole-home.html, scuola-servizi-tipologia.html, scuole-servizio-generico.html

**Requisiti tecnici:** Il menù di secondo livello "Servizi" deve contenere voci (ad esempio "Servizi per il personale scolastico" e "Servizi per famiglie e studenti") entrambe con attributo ``data-element=”service-type”`` al fine di prelevare gli URL (in modo randomico) del listato servizi (contengono l’URL alla pagina scuola-servizi-tipologia), devono essere degli <a> con “href” e possono essere inclusi in altri tag (ad es: <li>).

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


Raccomandazione Localizzazione IP
-------------------------------------

**Condizioni di successo:** l'indirizzo IP fa riferimento a un datacenter localizzato su territorio europeo.

**Modalità di verifica:** viene verificato che la localizzazione dell'IP rientri all'interno di uno dei confini degli stati membri dell'Unione Europea.
