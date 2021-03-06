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

#### Bridge

Un bridge viene usato quando
* Si vuole evitare di legare un’astrazione ad una sola
implementazione
* Ogni cambiamento di un’implementazione non è
influente sugli utilizzatori
* Per nascondere dettagli implementativi

Se ho più di una implementazione e voglio che l'utente la scelga il più tardi possibile (esempio look and feel diverso).

![Image of Bridge](https://github.com/tankado55/Ingegneria-del-software/blob/master/Bridge.PNG?)

```java
public class BridgePatternDemo {
   public static void main(String[] args) {
      Shape redCircle = new Circle(100,100, 10, new RedCircle());  // il RedCircle è un implementazione concreta
      Shape greenCircle = new Circle(100,100, 10, new GreenCircle());

      redCircle.draw();    //draw andrà a chiamare la funzione dell'implementazione concreta passando lo stato interno	
      greenCircle.draw();
   }
}
```

#### Composite

Consente ad oggetti utilizzatori di creare
strutture ad albero in modo che sia possibile
trattare in modo uniforme
* Oggetti foglia
* Oggetti contenitore

Un composite viene usato quando si vuole:
* Rappresentare gerarchie di oggetti
* Consentire di ignorare le differenze tra oggetti
foglia e oggetti contenitore

ES: le leaf sono i bottoni e i composite sono i jpanel, quando un composite chiama operation, operation viene chiamata su tutti i figli in modo ricorsivo.

Containers that contain Elements, each of which could be a Container.

![Image of Composite](https://github.com/tankado55/Ingegneria-del-software/blob/master/Composite.PNG)

#### Visitor

Represent an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.

Do the right thing based on the type of two objects.

![Image of Visitor](https://github.com/tankado55/Ingegneria-del-software/blob/master/Visitor.PNG)

#### Facade

Una Façade viene utilizzata quando:
* Si vuole offrire un’interfaccia uniforme ad
un sotto-sistema complesso
* Si vuole disaccoppiare un sotto-sistema
dai suoi utilizzatori, riducendo le interdipendenze

piu o meno il databaseManager che abbiamo fatto.

![Image of Facade](https://github.com/tankado55/Ingegneria-del-software/blob/master/Facade.PNG?)

#### Proxy

Un proxy è un delegato di un altro oggetto

I proxy hanno diversi usi:
* Per controllare l’accesso alle risorse, Ad esempio, per implementare politiche di sicurezza
* Per implementare una gestione soffisticata di un
oggetto (Accesso sincronizzato o persistenza)
* Per implementare oggetti remoti: (Uso più noto e comune) Il proxy e l’oggetto reale sono su due host diversi.

ha la stessa interfaccia dell'oggetto originale ma posso controllare da quale thread è stato chiamato ecc.

There are four common situations in which the Proxy pattern is applicable.

1. A virtual proxy is a placeholder for "expensive to create" objects. The real object is only created when a client first requests/accesses the object.

2. A remote proxy provides a local representative for an object that resides in a different address space. This is what the "stub" code in RPC and CORBA provides.

3. A protective proxy controls access to a sensitive master object. The "surrogate" object checks that the caller has the access permissions required prior to forwarding the request.

4. A smart proxy interposes additional actions when an object is accessed. Typical uses include: 
* Counting the number of references to the real object so that it can be freed automatically when there are no more references (aka smart pointer),
* Loading a persistent object into memory when it's first referenced,
* Checking that the real object is locked before it is accessed to ensure that no other object can change it.

![Image of Proxy](https://github.com/tankado55/Ingegneria-del-software/blob/master/Proxy.PNG)

### Pattern Creazionali

Offrono soluzioni per risolvere le problematiche
legate alla creazione degli oggetti:

* Abstract factory, utilizzata per creare oggetti senza
conoscerne l’implementazione concreta
* Builder, usato per creare oggetti complessi
indipendentemente dalla loro rappresentazione interna
* Prototype, usato per creare oggetti partendo da un’istanza
prototipo
* Singleton, usato per garantire che una sola istanza di un
oggetto venga creata nel sistema

#### Factory method e Abstract Factory

Definizione Factory pattern: Fornisce un interfaccia per creare oggetti, ma lascia alle sottoclassi il compito di decidere quale classe istanziare.

Problem: If an application is to be portable, it needs to encapsulate platform dependencies. These "platforms" might include: windowing system, operating system, database, etc. Too often, this encapsulation is not engineered in advance, and lots of #ifdef case statements with options for all currently supported platforms begin to procreate like rabbits throughout the code.

Questo codice rende indipendente il codice client scritto nell'interfaccia dal codice che si occupa della creazione dell'oggetto, scritto nelle sottoclassi.



![Image of Factory3](https://github.com/tankado55/Ingegneria-del-software/blob/master/Factory3.png?raw=true)

![Image of Factory4](https://github.com/tankado55/Ingegneria-del-software/blob/master/Factory4.PNG?raw=true)

Un abstract factory fornisce un interfaccia per la creazione di una famiglia di di prodotti(ingredienti per pizza), passando varie factory come parametro del costruttore dell'interfaccia concreta avremo varie implementazioni ma il codice del client rimane lo stesso.

![Image of Factory5](https://github.com/tankado55/Ingegneria-del-software/blob/master/Factory5.PNG?raw=true)

![Image of Factory6](https://github.com/tankado55/Ingegneria-del-software/blob/master/Factory6.PNG?raw=true)

Entrambi i pattern incapsulano la creazione degli oggetti e permettono di rendere indipendente il codice dai tipi concreti.

![Image of FactoryUML4](https://github.com/tankado55/Ingegneria-del-software/blob/master/FactoryUML4.png?raw=true)

![Image of FactoryUML5](https://github.com/tankado55/Ingegneria-del-software/blob/master/FactoryUML5.PNG?raw=true)

#### Builder

Ad esempio lo string builder, evita di fare dei prodotti parziali, in questo modo aggiungo tutte le stringhe che voglio e quando finisco genero quella finale.

#### Prototype

Rimpiazzo le new con una chiamata  prototype.clone();

![Image of Prototype](https://github.com/tankado55/Ingegneria-del-software/blob/master/Prototype.PNG)

#### Singleton

![Image of Singleton](https://github.com/tankado55/Ingegneria-del-software/blob/master/Singleton.PNG?)

Il costruttore è private quindi solo il codice della classe può chiamarlo!

Il Singleton Pattern assicura che una classe abbia solamente un istanza, e fornisce un punto di accesso globale.

A differenza di una variabile globale abbiamo il vantaggio di avere una lazy instantiation.

### Pattern Comportamentali

1. Definiscono strutture di collaborazione tra
oggetti
2. Definiscono protocolli di comunicazioni tra
oggetti

I più comuni e più usati sono
* Command, usato per incapsulare l’astrazione di
richiesta
* Iterator, usato per incapsulare la navigazione di
un oggetto composto


#### Command

Si usa per memorizzare la lista dei metodi che ho chiamato e in quale stato. (per implementare undo) oppure se Si vuole consentire di creare una richiesta in molti modi diversi.

Esempi d'uso:
La computazione del metodo vero a proprio può avvenire anche molto dopo aver creato gli oggetti di tipo Command

* Telecomando

* Coda di comandi da eseguire, per gestire e limitare l'esecuzione, possono essere eseguiti anche da thread diversi.

* Logging, aggiungendo a command altri metodi come store() e load(), oppure per implementare una transazione (o tutto o niente)

#### Iterator

Implementa un meccanismo di accesso a
oggetti aggregati in modo sequenziale
* Un iteratore naviga sequenzialmente un oggetto
aggregato

Un iteratore viene utilizzato:
* Per accedere al contenuto di un oggetto aggregato
in modo indipendente da come i componenti sono
memorizzati nell’oggetto aggregato
* Quando si vuole offrire diverse politiche di
attraversamento di un oggetto aggregato

![Image of Iterator](https://github.com/tankado55/Ingegneria-del-software/blob/master/Iterator.PNG)

# Serializzazione

Se voglio che la mia classe possa essere serializzata: implements Serializable, l'interfaccia non ha alcun metodo da implementare.

Se voglio che una variabile di istanza non venga serializzata bisogna segnarla "transient"!

Da mettere dentro la classe:
private static final long serialVersionUID = 20171114;

```java
private boolean salva() {
		try (
			FileOutputStream fileOutputStream = new FileOutputStream("contatore.ser");
			
			ObjectOutputStream objectOutputStream = new ObjectOutputStream(fileOutputStream);
		) {
			objectOutputStream.writeObject(this);

			return true;
		} catch (Throwable throwable) {
			throwable.printStackTrace();
			
			return false;
		}
	}
```

Se voglio salvare l'oggetto nel db, quello che ritorna la seguente funzione lo etto in un SerialBlob e lo metto nel DB

```java
protected byte[] serializza(Serializable oggetto) throws IOException {
		ByteArrayOutputStream byteArrayOutputStream = new ByteArrayOutputStream();
			
		ObjectOutputStream objectOutputStream = new ObjectOutputStream(byteArrayOutputStream);
			
		objectOutputStream.writeObject(oggetto);
			
		return byteArrayOutputStream.toByteArray();
	}
```

# Socket

Una socket è un oggetto che rappresenta una connessione tra 2 macchine.

Per leggere:
1. Crea una connessione socket: `Socket chatSocket = new Socket("127.0.0.1", 5000);`
2. Crea in InputStreamReader concatenato alla socket: `InputStreamReader stream = new InputStreamReader(chatSocket.getInputStream();`
3. Crea un BufferedReader e leggi: `BufferedReader reader = new BufferedReader(stream);  String message = reader.readline();`

Per scrivere:
1. Crea una connessione socket: `Socket chatSocket = new Socket("127.0.0.1", 5000);`
2. Crea un Print Writer concatenato alla socket: `PrintWriter writer = new PrintWriter(chatSocket.getOutputStream());`
3. Scrivi qualcosa: `writer.println("messaggio da inviare");`

## lato server

1. Crea una socketserver: ServerSocket serversocket = new ServerSocket(4242);
2. Crea una nuova socket per counicare con il client: Socket socket = serversocket.accept();

Per non piantare il server dopo che fa un accept:
```java
for(;;) {
				Socket socket = serverSocket.accept();

				Servant servant = new Servant(this, socket);
				
				new Thread(servant).start();
			}

```
# Java RMI

Tutti gli oggetti remoti estendono l'interfaccia Remote e tutti i loro metodi throws RemoteException.

RMI STUB: è il client helper (l'oggetto proxy), RMI SKELETON: è il service helper che sta sul server.

## Come implementare il servizio remoto

1. Creare un interfaccia remota (mettere extends Remote all'interfaccia), definisce i metodi che il client può chiamare in modo remoto, tutti gli argomenti e i tipi di ritorno devono essere serializabili o primitivi.

2. Creare l'implementazione dei metodi remoti.

### Codice lato server

```java
try {
			LocateRegistry.createRegistry(2000);
			
			System.out.println("Registry attivato");
			
			Object mutex = new Object();
			
			synchronized (mutex) {
				mutex.wait();
			}
		} catch (Throwable throwable) {
			throwable.printStackTrace();
		}
```	  

```java
try {
	Registry registry = LocateRegistry.getRegistry("127.0.0.1", 2000);

	Sommatore s1 = new SommatoreImpl();
			
	Remote esportato1 = UnicastRemoteObject.exportObject(s1, 0); //esportato1 è lo STUB
						
	registry.rebind("oggetto1", esportato1);
			
	System.out.println("Oggetto 1 disponibile");		
			
			
     } catch (Throwable throwable) {
	     throwable.printStackTrace();
     }
```	  

### Codice lato client

```java

try {
	Registry registry = LocateRegistry.getRegistry("127.0.0.1", 2000);
			
	GestorePunti gestorePunti2 = (GestorePunti)registry.lookup("oggetto2"); //mi ritorna lo STUB

	if(gestorePunti2 != null) 
		Punto s = gestorePunti2.puntoMedio(new Punto(3, 4), new Punto(5, 6));
							
								
	} catch (Throwable throwable) {
			throwable.printStackTrace();
	}
```

# JDBC

```java
public static void main(String[] args) {
		try {
			MemoriaOggetti memoria = new MemoriaOggettiDerby("jdbc:derby://localhost/Oggetti");
		} catch (Throwable throwable) {
			throwable.printStackTrace();
		}
	}
```

```java
try (
			Connection connessione = DriverManager.getConnection(url);
			PreparedStatement insert = connessione.prepareStatement("INSERT INTO OGGETTI(CLASSE, DATI) VALUES (?, ?)", RETURN_GENERATED_KEYS);
			PreparedStatement update = connessione.prepareStatement("UPDATE OGGETTI SET DATI=? WHERE ID=?");
		) {
			connessione.setAutoCommit(false);

			insert.setString(1, classe.getName());

			insert.setBlob(2, new SerialBlob(new byte[0]));
				
			insert.execute();

			ResultSet chiavi = insert.getGeneratedKeys();
			
			chiavi.next();

			int id = chiavi.getInt(1);

			chiavi.close();
			
			connessione.commit();
			
		} catch(Throwable throwable) {			
			throw new PersistenteException(throwable);
		}
```

# Multi-Thread

1. implements Runnable e implementare il metodo run()
2. Instanziare un oggetto Thread e chiamare start(), ad esempio: new Thread(mioOggetto).start()

# Servlet

```java
@SuppressWarnings("serial")
@WebServlet("/stato")
public class StatoSensori extends HttpServlet {

	@Override
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		try {
			Class.forName("org.apache.derby.jdbc.ClientDriver");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		}
		try (
				
				Connection con = DriverManager.getConnection("jdbc:derby://localhost/esame");
				PreparedStatement select = con.prepareStatement("SELECT * FROM STATO");
				ResultSet righeTabella = select.executeQuery();   //la resultset va chiusa!
			) {
			
			HttpSession session = request.getSession();

			session.setAttribute("righeTabella", righeTabella);
			
			request.getRequestDispatcher("visualizza_tabella.jsp").forward(request, response);
			
			
		} catch (Throwable throwable) {
			throwable.printStackTrace();
		}
		
		
	}
	
	@Override
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}
}
```
