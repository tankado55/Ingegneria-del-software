# UML
## Class Diagram

### Associazioni
Bisogna dare un nome alle associazioni!

Associazioni particolari:
* Aggregazione (rombo vuoto): "è un insieme di", ES: la distruzione di un automobile non comporta automaticamente quella delle sua parti.
* Composizione (rombo pieno): "è composto da", i componenti non possono esistere senza il contenitore, hanno lo stesso ciclo di vita, la cardinalità deve essere 1 dalla parte del rombo.
* Dipendenze (linea tratteggiata): ad esempio quando un metodo prende un oggetto di un certo tipo quindi si crea una dipendenza.
* Ereditarietà (freccia grossa verticale)

Graficamente vanno disegnati anche i package!

# Design Pattern

## Design pattern GoF (Gang of Four)

Sono classificati in:
* Creazionali, gestiscono la creazione dinamica degli oggetti all'interno di un sistema.
* Strutturali, micro-architetture statiche di utilizzo generale.
* Comportamentali, descrivono il comportamento di un'architettura di oggetti.

### Pattern Strutturali

* Adapter, usato per risolvere problemi di incompatibilità tra
interfacce.
* Bridge, usato per fornire più implementazioni ad
un’interfaccia.
* Composite, usato per trattare in modo uniforme oggetti
singoli e gruppi di oggetti.
* Visitor, usato per disaccoppiare le strutture dati (ad albero)
dagli algoritmi che le utilizzano.
* Façade, usato per fornire un’interfaccia unificata ad un
gruppo di oggetti.
* Proxy, usato per fornire funzionalità aggiuntive ad un
oggetto.

#### Adapter

L’adapter è uno dei pattern più usati:
* Consente a oggetti diversi di essere utilizzati insieme
anche se le rispettive interfacce non sono compatibili
* Aumenta il riuso delle classi perché consente di utilizzarle
in situazioni non previste inizialmente senza doverle
modificare

Un adapter viene usato
* Quando si vuole utilizzare una classe che non offre
un’interfaccia corretta, senza modificarla
* Per creare una classe che utilizza i servizi di un’altra
classe di cui non è ancora nota l’interfaccia

![Image of Adapter](https://github.com/tankado55/Ingegneria-del-software/blob/master/Adapter.PNG)

### Bridge

Un bridge viene usato quando
* Si vuole evitare di legare un’astrazione ad una sola
implementazione
* Ogni cambiamento di un’implementazione non è
influente sugli utilizzatori
* Per nascondere dettagli implementativi

Se ho più di una implementazione e voglio che l'utente la scelga il più tardi possibile (esempio look and feel diverso).




