---
TOCTitle: 'Gestione di identità e accessi: Concetti fondamentali'
Title: 'Gestione di identità e accessi: Concetti fondamentali'
ms:assetid: '3fe987cb-ec23-4ca3-aa39-a81f5a7ec5b5'
ms:contentKeyID: 20200817
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536217(v=TechNet.10)'
---

Concetti fondamentali
=====================

### Capitolo 2: Terminologia e iniziative

Aggiornato: 29 aprile 2004

Una soluzione di *gestione di identità e accessi* consente, mediante una combinazione di processi, tecnologie e criteri, di gestire le identità digitali e specificare la relativa modalità di utilizzo per accedere alle risorse.

Data l'ampia gamma e l'eterogeneità degli archivi di identità, dei protocolli, dei meccanismi di crittografia, dei criteri e degli enti governativi che hanno l'esigenza di collaborare e interagire tra loro, le iniziative relative alla gestione di identità e accessi sono in genere più complesse rispetto alla maggior parte dei progetti IT. Una strategia completa è in grado di ridurre significativamente gli sforzi necessari per gestire le identità digitali in una rete di grandi dimensioni mediante l'implementazione di standard, la riduzione del numero degli archivi di identità, la definizione di relazioni di trust, la delega dell'amministrazione, il miglioramento dell'esperienza di accesso degli utenti e, nel contempo, il rafforzamento della protezione.

È necessario che una strategia aziendale per la gestione di identità e accessi includa risposte ben definite alle seguenti domande:

-   Quali sono i vantaggi che le iniziative relative alla gestione di identità e accessi devono offrire?

-   Quali problematiche ciascuna iniziativa deve risolvere?

-   Quali sono gli specifici fattori a livello di organizzazione che è necessario prendere in considerazione?

-   Quali progetti e soluzioni tecnologici e aziendali sono necessari per il supporto di ciascuna iniziativa?

È necessario che l'organizzazione abbia un'idea chiara degli specifici vantaggi che le iniziative migliorate relative alla gestione di identità e accessi devono offrire. Senza questa visione d'insieme il risultato finale non fornirà miglioramenti concreti e potrebbe contribuire a un aumento della complessità e della difficoltà di gestione del sistema.

Durante la valutazione dei potenziali vantaggi, è consigliabile non trascurare le problematiche relative all'implementazione di una specifica soluzione tecnologica. È opportuno raggiungere un certo equilibrio tra i vantaggi previsti e le dimensioni e la complessità di ciascuna soluzione.

### Terminologia relativa alla gestione di identità e accessi

I termini riportati di seguito descrivono i componenti o i processi all'interno della soluzione di gestione di identità e accessi. Questi termini vengono utilizzati e trattati in modo più approfondito nei documenti rimanenti di questa serie.

-   *Identità digitale*: identificativo univoco e attributo descrittivo di una persona, un gruppo, un dispositivo o un servizio. Esempi di identità digitali comprendono account di utenti o computer nel servizio directory Microsoft® Active Directory®, account di posta elettronica in Microsoft Exchange Server 2003, voci relative agli utenti in una tabella di database e credenziali di accesso per un'applicazione personalizzata.

-   *Credenziali*: si tratta in genere di informazioni correlate o derivate da un segreto posseduto da un'identità digitale, sebbene i segreti non siano coinvolti in tutti i casi. Esempi di credenziali includono password, certificati X.509 e informazioni biometriche.

-   *Identità di protezione*: identità digitale con una o più credenziali che può essere autenticata e autorizzata a interagire con la rete.

-   *Archivio di identità*: un archivio contenente identità digitali. Gli archivi di identità rappresentano in genere un tipo di directory o database gestito e accessibile tramite un provider, quale Active Directory o Microsoft SQL Server. Gli archivi delle identità possono essere centralizzati, ad esempio su un computer mainframe, o distribuiti. Un esempio di archivio di identità distribuito è rappresentato da Active Directory. Questi archivi contengono in genere schemi ben definiti relativi al tipo di informazioni che è possibile archiviare e al formato in cui è possibile memorizzarle e includono un tipo di algoritmo di crittografia o di hash per la protezione dell'archivio e dei componenti dell'identità digitale, ad esempio le credenziali. È possibile che gli archivi di identità personalizzati e meno recenti non dispongano di meccanismi di protezione particolarmente rigidi e che consentano di archiviare le password in testo normale (formato non crittografato).

-   *Sincronizzazione delle identità*: un processo che assicura che più archivi di identità contengano dati coerenti per una specifica identità digitale. Questo processo può essere eseguito mediante l'uso di metodi di programmazione, come gli script, o mediante un prodotto dedicato, quale Microsoft Identity Integration Server 2003, Enterprise Edition (MIIS 2003).

-   *Servizi di integrazione delle identità*: servizi che consentono di aggregare, sincronizzare e abilitare l'implementazione e l'annullamento dell'implementazione centralizzati delle informazioni sulle identità in più archivi di identità connessi. I servizi di integrazione delle identità vengono forniti da MIIS 2003 e Identity Integration Feature Pack (IIFP) per Active Directory.

-   *Implementazione*: un processo che prevede l'aggiunta di identità a un archivio di identità e la definizione dei diritti acquisiti e delle credenziali iniziali per le identità. L'annullamento dell'implementazione costituisce il processo inverso, in quanto determina l'eliminazione o la disattivazione di un'identità. L'implementazione e l'annullamento dell'implementazione vengono in genere utilizzati con i servizi di integrazione delle identità per la propagazione di aggiunte, eliminazioni e disattivazioni negli archivi delle identità connessi.

-   *Gestione del ciclo di vita delle identità*: i processi e le tecnologie che consentono di mantenere le identità digitali aggiornate e conformi ai criteri governativi. La gestione del ciclo di vita delle identità include la sincronizzazione delle identità, l'implementazione, l'annullamento dell'implementazione e la gestione costante degli attributi, delle credenziali e dei diritti acquisiti degli utenti.

-   *Autenticazione*: un processo che prevede il controllo delle credenziali di un'identità di protezione in base ai valori all'interno di un archivio di identità. I protocolli di autenticazione, quali Kerberos versione 5, Secure Sockets Layer (SSL), NTLM e Autenticazione del digest, consentono di proteggere il processo di autenticazione e impedire l'intercettazione delle credenziali.

-   *Diritto acquisito*: un insieme di attributi che specificano i privilegi e i diritti di accesso di un'identità di protezione autenticata. Tra i diritti acquisiti figurano ad esempio i diritti di accesso e i gruppi di protezione di Windows.

-   *Autorizzazione*: un processo che prevede la risoluzione dei diritti acquisiti di un utente con le autorizzazioni configurate in una risorsa per il controllo dell'accesso. L'autorizzazione nel sistema operativo Windows include gli elenchi di controllo di accesso (ACL) di file, cartelle, condivisioni e oggetti di directory. Applicazioni quali SQL Server, SharePoint™ Portal Server ed Exchange Server implementano i meccanismi di controllo dell'accesso sulle risorse che gestiscono. Gli sviluppatori delle applicazioni possono implementare il controllo dell'accesso basato sui ruoli tramite i ruoli di ASP.NET e Gestione autorizzazioni di Windows.

-   *Trust*: uno stato che descrive i contratti tra parti e sistemi differenti per la condivisione delle informazioni sulle identità. Un trust viene in genere utilizzato per estendere l'accesso alle risorse in modo controllato ed eliminare nel contempo il sovraccarico amministrativo che altrimenti si verificherebbe durante la gestione delle identità di protezione dell'altra parte. I meccanismi di trust includono i trust tra insiemi di strutture in Windows Server 2003 e i trust tra le aree di autenticazione che utilizzano il protocollo di autenticazione Kerberos versione 5.

-   *Federazione*: uno speciale tipo di relazione di trust stabilita oltre le aree di confine della rete interna tra organizzazioni distinte.

-   *Controllo di protezione*: un processo che prevede la registrazione e il riepilogo degli eventi di autorizzazione e autenticazione significativi e delle modifiche agli oggetti Identità. Le organizzazioni presentano sostanziali differenze in merito alla relativa definizione degli eventi significativi. È possibile registrare i record dei controlli di protezione nel registro eventi di protezione di Windows.

-   *Gestione dell'accesso*: i processi e le tecnologie per il controllo e il monitoraggio dell'accesso alle risorse in conformità ai criteri governativi. La gestione dell'accesso include l'autenticazione, l'autorizzazione, i meccanismi di trust e il controllo di protezione.

[](#mainsection)[Inizio pagina](#mainsection)

### Requisiti aziendali

I recenti progressi compiuti nel settore dell'elaborazione distribuita, soprattutto tramite Internet, hanno dato come risultato la proliferazione di applicazioni e altri meccanismi per l'accesso alle informazioni in un'organizzazione tipica. Le organizzazioni desiderano inoltre garantire un accesso protetto ai beni informatici per dipendenti, partner e clienti e, nello stesso tempo, continuare a espandersi, ridurre i costi degli accessi, rafforzare la protezione e assicurare la conformità ai requisiti normativi.

L'accesso protetto ai beni informatici deve essere fornito all'interno di ambienti IT sempre più complessi. Le applicazioni personalizzate o i pacchetti applicativi dispongono in genere di propri strumenti di autenticazione e autorizzazione e di strumenti per la creazione e la gestione degli account utente che non prevedono l'integrazione con una piattaforma completa per la gestione di identità e accessi. Tali applicazioni producono in genere informazioni sulle identità digitali isolate e non correlate nonché un aumento della complessità.

Questi sistemi complessi e difficili da gestire rendono difficoltoso per il reparto IT fornire l'accesso ai beni informatici e soddisfare i requisiti aziendali delle organizzazioni a cui forniscono assistenza. Un'infrastruttura per la gestione di identità e accessi implementata in modo corretto e basata su una robusta piattaforma per la gestione di identità e accessi può consentire al reparto IT di soddisfare questi requisiti aziendali.

#### Riduzione del costo totale di proprietà

Se all'interno di un'organizzazione non vengono definiti meccanismi ben progettati, automatici e controllabili che consentano di abilitare il controllo dell'accesso, i costi da sostenere per implementare e gestire una soluzione completa per la gestione degli accessi risulteranno piuttosto elevati. I dati riportati di seguito sono stati estrapolati dal PricewaterhouseCoopers/Meta Group Survey 2002 intitolato "The Value of Identity Management", disponibile sul sito Web della società all'indirizzo http://www.pwcglobal.com. Questi dati includono i principali esempi dei costi associati alla gestione delle identità digitali.

-   **Accesso e autenticazione:** La riduzione della quantità di tempo impiegato per l'accesso a sistemi differenti può migliorare significativamente la produttività dei dipendenti. L'utente medio trascorre 16 minuti al giorno per l'autenticazione e l'accesso. Per un'organizzazione di grandi dimensioni, che nell'indagine viene identificata come costituita da 10.000 utenti, questo periodo di tempo equivale a 2.666 ore o 1,3 anni misurati in equivalenti a tempo pieno (FTE, Full-Time Equivalent) al giorno.

-   **Gestione del ciclo di vita delle identità:** è fondamentale che il personale IT di un'organizzazione concentri le proprie energie su attività che rivestono grande importanza a livello aziendale, come assicurare la disponibilità delle risorse e garantire la protezione della rete. Il tempo dedicato alla gestione delle identità tramite l'uso di meccanismi inefficienti potrebbe essere impiegato in modo più efficace per l'esecuzione di attività più importanti. Il tempo medio dedicato alla gestione degli utenti, degli archivi utenti, del processo di autenticazione e del controllo dell'accesso è quantificabile in 54.180 ore all'anno. Anche un miglioramento dell'efficienza del 25% sarebbe equivalente a 13.545 ore (o 6,7 FTE) per un'organizzazione di grandi dimensioni.

-   **Reimpostazione delle password:** il 45% delle chiamate al servizio di assistenza riguarda la reimpostazione delle password. L'automazione della reimpostazione delle password consente di ridurre di circa un terzo il volume delle chiamate. È stato stimato che per un'organizzazione costituita da 10.000 utenti questo tipo di operazione determina un risparmio annuale sui costi pari a $648.000.

-   **Dati duplicati:** l'eliminazione dei dati duplicati relativi alle identità può semplificare i processi di amministrazione e ridurre il costo totale di proprietà. Il 38% degli utenti esterni e il 75% degli utenti interni sono contenuti in più archivi di dati. Si stima che il risparmio medio in termini di tempo per la gestione centralizzata e consolidata degli archivi utente è equivalente a 1.236 ore all'anno per le organizzazioni di grandi dimensioni.

Le organizzazioni che affrontano i problemi relativi alla gestione di identità e accessi possono ridurre significativamente il costo totale di proprietà. Anche modifiche di entità minima, quale la riduzione del numero di chiamate al servizio di assistenza per la reimpostazione delle password, può produrre un significativo incremento della produttività per gli utenti finali e gli operatori del servizio di assistenza.

#### Miglioramento della protezione

Con il termine protezione si intendono tutte le misure aventi come scopo non solo quello di impedire intrusioni dall'esterno, ma anche quello di stabilire a chi o a cosa consentire l'accesso e il livello di accesso da concedere. I dipendenti, i consulenti, i clienti e i partner commerciali hanno diverse esigenze di accesso ai dati e alle applicazioni. È fondamentale per un'organizzazione definire e implementare criteri di gestione degli accessi che consentano solo agli utenti autorizzati di accedere a informazioni riservate.

La protezione implica inoltre una gestione efficace dei processi operativi. Processi di gestione inadeguati relativi agli account che rappresentano dipendenti, partner e clienti possono causare un aumento dei rischi di protezione. La gestione degli account di milioni di clienti in linea può ad esempio comportare un sovraccarico dei tradizionali sistemi di gestione degli account utente. Le organizzazioni inoltre non hanno sui dipendenti dei partner lo stesso controllo che hanno sugli account dei propri dipendenti.

La gestione controllata di identità e accessi consente alle organizzazioni di estendere l'accesso ai relativi sistemi informatici senza compromettere la protezione. Le organizzazioni forniscono questo accesso esteso gestendo con precisione i diritti acquisiti e modificando o negando immediatamente i diritti di accesso.

Alla gestione di identità e accessi sono in genere associate le seguenti attività di protezione:

-   **Miglioramento dell'applicazione** **dei criteri degli account:** è possibile migliorare la protezione gestendo gli account in base a standard predefiniti. L'applicazione di criteri per gli account prevede la definizione di regole e procedure per l'implementazione di misure di protezione avanzate. Alcuni esempi includono la necessità per gli amministratori di utilizzare smart card e la verifica che tutti gli utenti dispongano di password complesse e che le modifichino di frequente.

-   **Rimozione di account non aggiornati:** la protezione dei computer può essere migliorata in modo significativo mediante la rimozione tempestiva degli account non aggiornati. È necessario che le organizzazioni disattivino gli account relativi a dipendenti, consulenti, partner e clienti quando non sono più necessari. Se non vengono disattivati, i possessori degli account originali potranno utilizzarli in modo improprio per ottenere l'accesso non autorizzato ai sistemi. Gli account non aggiornati sono bersagli particolarmente interessanti per intrusi e utenti malintenzionati, in quanto è probabile che dispongano di credenziali statiche obsolete ed esiste una minore probabilità che un eventuale uso improprio o una violazione potenziale di tali account venga rilevata.

-   **Miglioramento della protezione dei dati delle applicazioni:** per soddisfare i requisiti di protezione aziendali, è necessario che le applicazioni siano in grado di trasferire i dati tramite meccanismi protetti. È necessario che l'accesso ai dati riservati preveda meccanismi di autenticazione e autorizzazione appropriati e che per tali dati venga garantito un livello di protezione adeguato sulla rete in modo da impedire a potenziali intrusi di intercettarli (sniffing).

-   **Implementazione di meccanismi di autenticazione avanzati:** le tecniche di autenticazione e le credenziali più comunemente utilizzate potrebbero non fornire il livello di protezione necessario per le applicazioni e i dati di importanza cruciale. Microsoft consiglia di utilizzare quando possibile meccanismi di autenticazione avanzati, quali il protocollo Kerberos versione 5 e le tecnologie di infrastruttura a chiave pubblica (PKI) per migliorare la protezione globale delle risorse di elaborazione.

-   **Gestione delle credenziali con i servizi directory:** oltre alle numerose possibilità di utilizzo all'interno di un'organizzazione, i servizi directory sono in grado di fornire specifici vantaggi in termini di protezione. I metodi di autenticazione avanzati, quali smart card e biometrica, consentono ad esempio di migliorare notevolmente il livello di protezione dell'organizzazione. Purtroppo, tali sistemi introducono un certo livello di complessità e dati aggiuntivi sugli utenti che richiedono una gestione rigorosa e l'accessibilità da una posizione centrale. La distribuzione di questi sistemi è più semplice quando viene implementata un'infrastruttura di directory altamente affidabile.

-   **Miglioramento dell'autorizzazione:** l'autorizzazione deve essere abbastanza flessibile da fornire sia l'accesso generale che l'accesso preciso alle risorse. L'accesso generale consente ad esempio a tutti i dipendenti di accedere a una specifica applicazione, mentre l'accesso preciso consente ai dipendenti addetti al reparto vendite di eseguire una determinata operazione in un'applicazione tra le ore 9:00 e le ore 17:00. È opportuno mappare in modo logico gli utenti a specifici ruoli, ad esempio il ruolo di amministratore di database, operatore dell'assistenza tecnica o utente di applicazioni, nel contesto di un'organizzazione o un'applicazione.

-   **Gestione dei diritti acquisiti tramite l'implementazione:** un sistema di implementazione realizzato correttamente impone l'applicazione coerente dei criteri per la richiesta e l'approvazione dei diritti acquisiti. L'applicazione risulta semplificata quando tutte le unità aziendali sono in grado di seguire facilmente lo stesso processo. Un sistema di implementazione fornisce inoltre un itinerario di controllo che consente di registrare quando e da chi eventuali decisioni sono state prese ed eventuali approvazioni sono state concesse.

-   **Implementazione della gestione del ciclo di vita delle identità:** un processo di gestione del ciclo di vita delle identità consente di mantenere i diritti acquisiti degli utenti aggiornati nel corso di un'intera carriera. Se ad esempio un dipendente viene trasferito dal reparto finanziario al reparto di marketing, il processo di gestione del ciclo di vita delle identità potrà chiudere e rimuovere l'accesso del dipendente alle applicazioni finanziarie e fornirgli l'accesso alle applicazioni di marketing. I processi di gestione del ciclo di vita delle identità possono essere manuali o automatici. I processi automatici in genere aumentano il livello di protezione all'interno di un'organizzazione, in quanto consentono di rimuovere e concedere l'accesso in modo più tempestivo.

-   **Riduzione della superficie soggetta ad attacchi:** più archivi di identità implicano un aumento del rischio di violazione degli account utente nel caso in cui ciascun archivio non venga gestito in base a uno standard comune elevato. Analogamente, un'ampia gamma di meccanismi di autenticazione in genere indica che i pericoli per l'intero sistema sono meno noti e possono essere ridotti con minore facilità. La riduzione del numero totale di meccanismi e sistemi di protezione implica che quelli rimanenti possono essere gestiti e protetti in modo più efficace.

-   **Garanzia della conformità delle azioni degli utenti ai criteri aziendali:** Single Sign On (SSO) assicura una più agevole conformità degli utenti ai criteri di gestione delle password di un'organizzazione. In situazioni in cui è necessario ricordare e gestire più password, è naturale che gli utenti creino password semplici o annotino password complesse che potrebbero essere lasciate prive di protezione nell'area di lavoro.

#### Miglioramento dell'accesso

Per migliorare l'accesso ai beni informatici, è necessario che le tecnologie di gestione di identità e accessi soddisfino i seguenti requisiti:

-   Consentire l'immediata produttività e l'accesso dei dipendenti alle risorse informatiche tramite un'efficace implementazione degli account e dell'hardware.

-   Consentire un incremento della produttività dei dipendenti fornendo l'accesso remoto alle principali applicazioni all'esterno dell'ambiente della rete interna dell'organizzazione.

-   Consentire ai partner di partecipare direttamente alle applicazioni aziendali in modo gestito e controllato, con una conseguente semplificazione dei processi che si estendono oltre i limiti aziendali.

-   Conquistare nuovi clienti tramite informazioni personalizzate e offrendo l'opportunità di richiedere prodotti e sevizi in linea. Migliorare l'esperienza degli utenti e la soddisfazione dei clienti al fine di incrementare i profitti della società.

-   Assicurare i risparmi sui costi mediante l'implementazione della federazione, il che implica per l'azienda maggiori opportunità di collaborazione diretta con i partner senza la necessità di farsi carico della gestione delle identità e delle credenziali del personale dei partner che partecipano a tale processo.

Soddisfacendo questi importanti requisiti per la gestione di identità e accessi, le organizzazioni potranno ottenere un incremento della produttività dei dipendenti, una riduzione dei costi e il miglioramento dell'integrazione delle attività aziendali.

#### Conformità alle normative

L'identità è diventata rapidamente un punto focale di molti criteri governativi e normativi. Questa enfasi è il risultato della crescente attenzione posta sulla privacy, in quanto nei sistemi informatici viene archiviato un numero sempre maggiore di informazioni personali. Il controllo dell'accesso alle informazioni dei clienti e dei dipendenti non rappresenta solo una buona prassi aziendale, in quanto un'organizzazione che non è in grado di garantire meccanismi di controllo adeguati è soggetta a significative responsabilità legali e finanziarie.

L'integrità dei dati o la conformità ai requisiti di isolamento è ora regolata dalle leggi in vigore. Potrebbe essere necessario che le organizzazioni negli stati Uniti soddisfino i requisiti di uno dei seguenti standard normativi:

-   Sarbanes-Oxley Public Company Accounting Reform and Investor Protection Act.

-   Gramm-Leach-Bliley Financial Services Modernization Act.

-   Health Insurance Portability and Accountability Act (HIPAA).

Queste normative hanno un notevole impatto sulle organizzazioni, come dimostrato dalla regola di protezione dell'HIPAA che impone il rispetto di rigorose linee guida in merito alla modalità di gestione dei dati sanitari personali da parte delle organizzazioni che operano nel settore sanitario. Queste linee guida includono aspetti quali controlli, gestione dell'accesso e autorizzazione appropriati. Un'efficace infrastruttura per la gestione di identità e accessi consente di associare in modo preciso i record dei pazienti all'interno di diversi sistemi informatici al paziente di interesse. Inoltre, un'infrastruttura di questo tipo consente di controllare l'accesso ai record e di autenticare le identità di coloro che li esaminano.

Le organizzazioni negli Stati Uniti non sono le uniche a dover assicurare la conformità al crescente numero di regolamentazioni e legislazioni vigenti, come dimostrato da statuti quali l'European Union's Data Protection Directive del 1998 e il Personal Information Protection and Electronic Documents Act (PIPEDA), emanato in Canada, che impongono il rispetto di rigorose linee guida concernenti le informazioni relative alle identità. Esistono inoltre numerose leggi locali che disciplinano le modalità di archiviazione e utilizzo dei dati relativi alle identità.

La conformità alle normative assicura che le organizzazioni soddisfino i requisiti di riservatezza, autenticazione, autorizzazione e controllo previsti da tutte le normative applicabili.

#### Fusioni e acquisizioni

L'integrazione dei sistemi di gestione di identità e accessi di un'organizzazione in seguito a fusioni o acquisizioni rappresenta una vera e propria sfida e implica specifiche opportunità. Per ottimizzare il valore della nuova organizzazione, è necessario che il personale IT utilizzi standard comuni per combinare i dati e le informazioni delle organizzazioni appena acquisite e renderli disponibili ai dipendenti il prima possibile.

L'integrazione dei sistemi di gestione di identità e accessi svolge un ruolo particolarmente importante nel garantire a tutti i dipendenti della nuova organizzazione il livello appropriato di accesso ai dati consolidati. Inoltre, per garantire costi di amministrazione adeguati, è necessario consolidare gli archivi di identità ridondanti e i processi di gestione non più necessari per la nuova organizzazione.

Tra i problemi affrontati dal reparto IT durante i processi di fusione e acquisizione figurano:

-   Garanzia della compatibilità degli archivi delle identità delle due organizzazioni.

-   Combinazione degli account di ciascun sistema in un sistema consolidato.

-   Utilizzo della federazione per unire i sistemi di gestione di identità e accessi tramite relazioni di trust.

-   Sincronizzazione degli archivi delle identità, che rappresenta in genere una soluzione a breve termine accettabile quando il consolidamento immediato di sistemi differenti non è praticabile durante una fusione o un'acquisizione.

-   Aggiornamento dei criteri di protezione per incorporare e soddisfare i nuovi requisiti normativi che vengono definiti in seguito a una fusione o acquisizione.

[](#mainsection)[Inizio pagina](#mainsection)

### Iniziative in una strategia di gestione di identità e accessi

Diverse sono le motivazioni aziendali che spingono le organizzazioni verso la determinazione e l'implementazione di una strategia di gestione di identità e accessi. Per garantire le migliori probabilità di successo e facilitare il conseguimento dei risultati desiderati, è necessario che tale strategia sia in linea con gli obiettivi aziendali. È opportuno che nel progetto vengano rispettate le seguenti priorità:

-   **Il rapido conseguimento dei risultati consente di migliorare il supporto delle iniziative da parte della direzione.** Il raggiungimento di risultati rapidi che non richiedono l'investimento di grossi capitali consentirà di creare interesse e rafforzare l'approvazione del corpo direttivo.

-   **Affrontare le aree ad alto rischio il prima possibile.** Gli aspetti relativi alla protezione rappresentano in genere le principali aree problematiche che le aziende devono affrontare il più rapidamente possibile.

-   **Gli standard e l'infrastruttura costituiscono in genere i prerequisiti per altre iniziative.** A seconda degli investimenti effettuati in passato, la definizione di standard tramite criteri specifici e l'implementazione dell'infrastruttura per supportarli potrebbero risultare troppo onerose in termini sia di costo che di impegno. Tuttavia, investimenti di questa entità sono giustificati considerando il fatto che sono alla base del successo della maggior parte degli altri progetti.

Ciascuna organizzazione che stia valutando l'opportunità di implementare una strategia di gestione di identità e accessi dovrà prendere in considerazione una combinazione univoca di obiettivi e priorità. Nelle seguenti sezioni vengono illustrate alcune delle iniziative più comuni, ciascuna delle quali è costituita da uno o più progetti aziendali e tecnologici, tra cui:

-   Definizione dei criteri di protezione e accesso.

-   Determinazione degli standard relativi ai servizi directory e alla protezione.

-   Implementazione dell'aggregazione e della sincronizzazione delle identità.

-   Automazione dei processi di implementazione e annullamento dell'implementazione.

-   Consolidamento di archivi di identità.

-   Gestione avanzata delle password.

-   Attivazione dell'interoperabilità e dei servizi Single Sign On.

-   Potenziamento dei meccanismi di autenticazione.

-   Miglioramento dell'accesso per dipendenti, clienti e partner.

-   Definizione dei criteri di controllo della protezione.

-   Aggiornamento degli standard per l'approvvigionamento di applicazioni software.

-   Definizione degli standard di sviluppo del software per l'utilizzo delle identità.

-   Sviluppo e migrazione delle applicazioni abilitate al riconoscimento delle identità.

#### Definizione dei criteri di protezione e accesso

La maggior parte dei criteri di protezione aziendali scritti che coinvolgono persone, processi e tecnologie può essere implementata direttamente nei servizi directory, mentre altri verranno controllati da processi e sistemi specifici che forniscono il supporto per l'applicazione dei criteri di protezione. I criteri di accesso delle organizzazioni specificano a livello globale le regole aziendali relative all'accesso a specifiche applicazioni o gruppi di applicazioni. Questi criteri di accesso vengono in genere definiti in termini di ruolo, risorsa, operazione e restrizioni.

Di seguito sono riportati alcuni esempi di criteri di accesso e protezione e delle relative regole:

-   Criteri di gestione degli account, che possono stabilire che gli account non aggiornati devono essere eliminati periodicamente dagli archivi delle identità.

-   Criteri di gestione delle password, che possono stabilire che le password degli account devono essere modificate periodicamente e definiscono i requisiti di lunghezza minima e complessità per le password.

-   Criteri di controllo della protezione, che possono definire quali azioni devono essere segnalate.

-   Informativa sul trattamento dei dati personali, che può definire "il diritto alla privacy" (libertà da comunicazioni non desiderate come la posta indesiderata) e regole relative alla riservatezza dei dati personali (la possibilità per gli utenti di controllare la raccolta e l'utilizzo delle relative informazioni personali).

-   Criteri di gestione dell'accesso, che prevedono quanto segue:

    -   L'accesso VPN richiede una smart card o un altro tipo di autenticazione basata su più fattori.

    -   Applicazioni specifiche richiedono l'autenticazione biometrica.

    -   L'accesso Extranet a determinati sistemi è limitato agli utenti autenticati e attivato dai servizi firewall di tipo edge.

    -   L'accesso degli amministratori di dominio richiede una smart card.

    -   Le connessioni dei computer a sistemi di alto valore richiedono l'utilizzo della crittografia IPSec.

    -   Vengono applicate restrizioni operative, ad esempio *"* i prelievi sugli account dei clienti possono essere effettuati dai cassieri di banca solo tra le ore 9:00 e le ore 17:00.*"*

##### Vantaggi

Di seguito sono riportati i potenziali vantaggi derivanti dalla definizione dei criteri di protezione e accesso:

-   Aumento del livello di protezione all'interno dell'organizzazione.

-   Maggiore protezione di specifici sistemi ad alto valore.

-   Miglioramento dei controlli di protezione.

-   Garanzia della conformità alle normative.

##### Problemi

Di seguito sono riportati i problemi associati alla definizione dei criteri di accesso e protezione:

-   Definizione dei requisiti di protezione appropriati per ciascun scenario di accesso.

-   Implementazione dei criteri con le tecnologie scelte nel rispetto di eventuali vincoli e limitazioni.

-   Gestione dell'aumento del carico di lavoro e dell'efficienza ridotta causati da un incremento della protezione senza automazione.

-   Utilizzo di meccanismi di protezione più complessi.

-   Gestione di requisiti di protezione in conflitto.

#### Determinazione degli standard relativi ai servizi directory e alla protezione

Indipendentemente dal servizio utilizzato, Active Directory o un servizio alternativo, la creazione di un servizio directory standard costituisce un elemento chiave per la gestione di identità e accessi. Tuttavia, le organizzazioni rilevano spesso la necessità di utilizzare più di un servizio directory. Fusioni, acquisizioni e la disponibilità di una vasta gamma di applicazioni possono introdurre due, tre o più servizi directory in un'organizzazione. Un'efficace strategia di gestione di identità e accessi consolida questi servizi nel numero minimo di archivi di identità che collettivamente diventano i servizi directory standard dell'organizzazione.

Sebbene i servizi directory consentano di applicare gli standard relativi ai criteri di protezione, è possibile che le organizzazioni rilevino significative differenze nelle relative operazioni interne. Un reparto potrebbe ad esempio essere stato creato in seguito a un'acquisizione che include un servizio directory separato e un criterio di protezione che differisce dal servizio directory esistente dell'organizzazione. Poiché gli standard di protezione relativi alle identità sono in genere strettamente integrati con i servizi directory, è opportuno che vengano illustrati insieme.

La definizione degli standard di protezione e dei servizi directory è un prerequisito necessario per la determinazione degli standard di approvvigionamento e sviluppo delle applicazioni, in quanto consente di mantenere bassi i costi di gestione e di estendere l'accesso in modalità protetta.

##### Vantaggi

Di seguito sono riportati i potenziali vantaggi derivanti dalla definizione dei servizi directory standard e degli standard di protezione unificati:

-   Riduzione del sovraccarico amministrativo.

-   Semplificazione dell'implementazione.

-   Aumento del livello di protezione all'interno dell'organizzazione.

##### Problemi

Di seguito sono riportati i problemi associati alla definizione dei servizi directory standard e degli standard di protezione unificati:

-   Piattaforme e applicazioni line-of-business (LOB) con specifiche esigenze di directory.

-   Criteri di protezione incompatibili che non è possibile soddisfare.

-   Problemi interni alle organizzazioni, quale l'autonomia dei reparti.

-   Requisiti normativi per i limiti a livello di gestione e informazioni all'interno delle organizzazioni, quali istituzioni finanziarie (ad esempio tenere separato il settore dei servizi bancari personali dal settore delle assicurazioni).

-   Individuazione di un protocollo di autenticazione comune che possa essere utilizzato dalle applicazioni e dagli archivi di identità esistenti all'interno dell'organizzazione.

-   Presentazione dei diritti acquisiti in un formato comune che possa essere utilizzato da sistemi e applicazioni differenti all'interno dell'organizzazione.

Ulteriori informazioni sulla definizione degli standard di protezione e dei servizi directory sono disponibili nel documento "Piattaforma e infrastruttura" in questa serie.

#### Implementazione dell'aggregazione e della sincronizzazione delle identità

In molti casi, non è conveniente eseguire la migrazione degli archivi delle identità e delle applicazioni in un servizio directory standard. Tuttavia, in genere, è possibile ridurre i costi di gestione e ridurre al minimo le perdite di produttività mediante l'integrazione di tali sistemi in modo da condividere le relative informazioni sulle identità e creare e gestire gli stessi diritti acquisiti tramite criteri comuni.

L'aggregazione delle identità prevede il collegamento di più identità digitali provenienti da numerosi archivi di identità. Senza l'integrazione delle identità non è possibile in alcun modo riconoscere ad esempio che "Li, George Z." nel sistema delle risorse umane (HR, Human Resources) corrisponde a "George Li" nella rete Intranet e a "G. Li" nella directory di posta elettronica. L'aggregazione e la sincronizzazione delle identità consentono all'organizzazione di creare e gestire un'identità digitale completa tramite i servizi di integrazione delle identità, come quelli forniti da MIIS 2003.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dall'aggregazione e dalla sincronizzazione delle identità:

-   Riduzione del sovraccarico amministrativo associato al collegamento delle informazioni sulle identità contenute in più archivi di identità.

-   Aumento delle informazioni aziendali fornite da una visualizzazione unificata di tutte le identità digitali all'interno dell'organizzazione.

-   Amministrazione migliorata delle identità da un singolo archivio di identità.

##### Problemi

Di seguito vengono riportati i problemi specifici associati all'aggregazione di più archivi di identità:

-   Individuazione di tutti gli archivi di identità gestiti all'interno dell'organizzazione.

-   Raggiungimento di un accordo sulle modalità di aggregazione degli archivi delle identità e sincronizzazione delle informazioni.

-   Capacità di determinare quali attributi sono posseduti da specifici archivi di identità.

-   Instaurazione di un rapporto di collaborazione tra i reparti delle risorse umane, IT, legale e altre divisioni aziendali partecipanti.

-   Determinazione dell'origine autorevole di vari attributi che costituiscono l'identità digitale utilizzata all'interno dell'organizzazione.

-   Creazione di una visualizzazione globale delle informazioni sulle identità per l'organizzazione.

-   Controllo delle modifiche tramite una visualizzazione globale di tutte le informazioni sulle identità dell'organizzazione.

-   Sincronizzazione delle informazioni sulle identità contenute in archivi di identità differenti all'interno dell'organizzazione.

Ulteriori informazioni su questo argomento sono disponibili nel documento "Aggregazione e sincronizzazione delle identità" in questa serie.

#### Automazione dei processi di implementazione e annullamento dell'implementazione

Le organizzazioni desiderano che i nuovi dipendenti e consulenti siano produttivi il più rapidamente possibile, in quanto non possono permettersi lunghi periodi di inattività in cui il personale attende per ore, giorni o persino settimane di ottenere l'accesso alle applicazioni.

L'implementazione automatica consente di utilizzare una nuova voce contenuta in un archivio di identità e creare le voci corrispondenti in ciascun archivio di identità gestito. L'annullamento dell'implementazione opera in senso inverso, in quanto rileva una modifica in un archivio, ad esempio la disattivazione di un account, e propaga tale modifica agli altri archivi delle identità. Pertanto, la modifica di un valore in un singolo campo di uno degli archivi di identità connessi, quale la modifica dello stato di un dipendente da "dipendente" a "ex dipendente" nel sistema di gestione delle risorse umane, può comportare la disattivazione o l'eliminazione di una serie di identità digitali in più archivi nel giro di pochi minuti.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dai processi automatici di implementazione e annullamento dell'implementazione:

-   Costi ridotti tramite la creazione e l'eliminazione automatiche di account in più archivi di identità.

-   Incremento della produttività mediante la riduzione del tempo necessario per creare account, password e diritti di accesso per i nuovi dipendenti.

-   Generazione automatica degli attributi necessari, quali cassette postali e nomi di account.

-   Semplificazione della gestione dell'appartenenza ai gruppi.

-   Semplificazione della gestione dei ruoli.

-   Aumento della protezione tramite la revoca immediata dei diritti di accesso di tutti i dipendenti che lasciano l'organizzazione.

##### Problemi

Di seguito sono riportati i problemi correlati ai processi automatici di implementazione e annullamento dell'implementazione:

-   Determinazione del processo aziendale che porta all'implementazione.

-   Determinazione dei reparti e delle approvazioni necessari per l'implementazione di nuovi account.

-   Gestione dei ritardi dei processi aziendali che hanno effetto sulla tempestività dell'implementazione e sulla protezione dell'annullamento dell'implementazione.

-   Sostituzione delle attività manuali esistenti con processi automatici che includono il flusso di lavoro e il controllo.

-   Implementazione di identità digitali in più archivi di identità.

-   Creazione e gestione di un insieme coerente di diritti acquisiti per gli utenti di applicazioni con archivi di identità o meccanismi di autorizzazione differenti.

-   Raccolta rapida delle informazioni necessarie per assicurare un'implementazione tempestiva.

#### Consolidamento di archivi di identità

Oltre all'aggregazione e alla sincronizzazione dei dati sulle identità, è consigliabile prendere in considerazione la riduzione del numero di archivi di identità in uso. Se ad esempio un'organizzazione dispone di due applicazioni che utilizzano il protocollo Lightweight Directory Access Protocol (LDAP) per l'autenticazione e l'autorizzazione, potrebbe essere possibile combinare archivi di identità LDAP separati in un singolo archivio.

I dati sulle identità potrebbero essere sincronizzati e gestiti tra gli archivi di identità tramite meccanismi in gran parte automatizzati. Tuttavia, la gestione di questi meccanismi e le eccezioni che si verificheranno quasi certamente generano un maggiore carico di gestione e un aumento della superfice soggetta ad attacchi.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dal consolidamento degli archivi delle identità:

-   Riduzione del sovraccarico di gestione.

-   Riduzione del costo totale di proprietà mediante l'eliminazione di server e licenze.

-   Riduzione dei requisiti di gestione dei server.

-   Aggiornamenti hardware e software meno costosi.

-   Semplificazione della distribuzione delle applicazioni.

##### Problemi

Di seguito sono riportati i problemi associati al consolidamento degli archivi delle identità:

-   Creazione di uno schema aggregato in un singolo archivio di identità.

-   Differenze tra le implementazioni del protocollo LDAP o di altri protocolli in archivi di identità differenti.

-   Migrazioni delle applicazioni.

#### Gestione avanzata delle password

La gestione delle password perfeziona ulteriormente il processo di aggregazione delle identità. Questo processo coinvolge numerose aree, quali la definizione e l'applicazione dei criteri di gestione delle password, la modifica e la reimpostazione delle password e la propagazione delle modifiche delle password a tutti gli archivi di identità connessi. La gestione delle password consente ad esempio agli utenti di modificare le relative password di accesso alla rete, le credenziali degli account SAP, le credenziali di posta elettronica e le password del sito di collaborazione Extranet con un'unica operazione. Consente inoltre il raggruppamento con criteri per password complesse in sistemi di importanza critica e criteri per password più semplici in altri sistemi che non sono in grado di gestire i moderni standard relativi al livello di complessità delle password.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dalla gestione delle password:

-   Costi di supporto e amministrazione ridotti, in quanto il personale dell'assistenza tecnica non deve reimpostare le password degli utenti per più archivi di identità.

-   Maggiore protezione mediante la limitazione del numero di password che gli utenti devono ricordare e la riduzione della necessità di annotare le password complesse.

-   Incremento della protezione derivante dall'applicazione coerente dei criteri di gestione delle password relativamente agli elementi dei criteri, quali i requisiti relativi alla complessità e alla lunghezza delle password.

-   Riduzione dei tempi di inattività mentre gli utenti attendono di ricevere assistenza dall'assistenza tecnica per la reimpostazione delle relative password.

##### Problemi

Di seguito sono riportati i problemi associati alla gestione delle password:

-   Gestione di più criteri di gestione delle password che prevedono requisiti differenti per lunghezza e complessità.

-   Gestione degli intervalli della cronologia e della scadenza delle password in più piattaforme.

-   Determinazione dei sistemi che non devono essere coinvolti nella propagazione delle password a causa di archivi di identità o tecniche di autenticazione carenti dal punto di vista della protezione e altri punti deboli.

-   Registrazione delle modifiche delle password da più piattaforme, se necessario.

-   Accesso e trasmissione in modo protetto di password aggiornate agli archivi delle identità.

-   Verifica della validità dell'identità degli utenti che richiedono la reimpostazione di una password.

-   Garanzia che le password appena reimpostate vengano inviate in modo protetto all'utente finale.

-   Gestione delle applicazioni e dei servizi che contengono password con valori prefissati o configurate in modalità locale.

Ulteriori informazioni su questo argomento sono disponibili nel documento "Gestione delle password" in questa serie.

#### Attivazione dell'interoperabilità e del servizio Single Sign On

Gli scenari relativi all'interoperabilità tra piattaforme diverse variano notevolmente da organizzazione a organizzazione, in quanto ciascuno prevede l'integrazione di una combinazione univoca di servizi directory, database, applicazioni e archivi di identità associati.

L'interoperabilità e i metodi Single Sign On (SSO) prevedono quanto segue:

-   Integrazione con il sistema operativo server (utilizzato da prodotti quali Microsoft Exchange Server 2003 e SQL Server 2000).

-   Utilizzo di un protocollo di autenticazione protetto basato su standard, quale il protocollo di autenticazione Kerberos versione 5.

-   Utilizzo dell'autorizzazione e dell'autenticazione LDAP per applicazioni o piattaforme che non supportano il protocollo Kerberos versione 5.

-   Utilizzo del mapping delle credenziali e del servizio Enterprise SSO (utilizzato da prodotti quali Microsoft BizTalk® Server 2004, SharePoint Portal Server 2003 e Host Integration Server 2004).

-   Sincronizzazione dei nomi utente e propagazione delle password su più piattaforme e applicazioni. Questo metodo non fornisce un vero e proprio servizio SSO, ma riduce la necessità per gli utenti di ricordare più password e nomi utente. Viene abilitato tramite i miglioramenti apportati ai processi di gestione delle password e di sincronizzazione delle identità.

-   Implementazione del servizio SSO Web per gli scenari Intranet ed Extranet.

##### Vantaggi

Di seguito sono riportati i vantaggi offerti dall'interoperabilità e dal servizio Single Sign On (SSO):

-   Semplificazione della distribuzione delle applicazioni.

-   Raggiungimento di standard più elevati per l'autenticazione e la protezione dei dati in rete.

-   Riduzione della quantità di tempo impiegata dagli utenti per eseguire ripetutamente l'autenticazione in più archivi di identità tramite SSO Intranet.

##### Problemi

Di seguito sono riportati i problemi correlati all'interoperabilità e al servizio Single Sign On:

-   Scelta dei meccanismi appropriati per le piattaforme disponibili nell'organizzazione.

-   Scelta tra i meccanismi SSO Web e di rete in cui sono disponibili entrambe le opzioni.

-   Scelta della modalità e del momento in cui utilizzare i servizi directory LDAP per l'autenticazione e l'autorizzazione.

-   Scelta del momento in cui riconfigurare le applicazioni e le piattaforme per l'implementazione della propagazione delle password.

-   Differenze nei protocolli LDAP o nelle implementazioni degli schemi.

-   Gestione di variazioni di entità minima nelle implementazioni dei meccanismi di autenticazione basati su standard.

Ulteriori informazioni sull'interoperabilità e sul servizio SSO Intranet sono disponibili nel documento relativo alla gestione degli accessi alle reti Intranet in questa serie.

#### Potenziamento dei meccanismi di autenticazione

Esistono molte ragioni per scegliere di implementare meccanismi di autenticazione più avanzati. Questa iniziativa potrebbe far parte di un piano generale che prevede il rafforzamento della protezione delle risorse di elaborazione dell'organizzazione, potrebbe essere una risposta a uno specifico pericolo o, nel peggiore dei casi, potrebbe essere una risposta a un attacco portato a buon fine. Infine, per garantire il non-ripudio o una capacità simile, potrebbe essere necessario soddisfare gli standard di settore o normativi.

La maggior parte delle organizzazioni continua a utilizzare combinazioni di nome utente e password per l'autenticazione nelle relative applicazioni e risorse. I meccanismi di autenticazione basati su password possono variare da meccanismi molto protetti a meccanismi protetti a meccanismi completamente non protetti, a seconda dell'implementazione dell'applicazione, del protocollo, dell'archivio di identità e della lunghezza e della complessità della password.

Attualmente, è disponibile un'ampia gamma di meccanismi e tecnologie non basati su password dotati di un maggiore livello di protezione, quali i certificati digitali X.509, i token per hardware basati sul tempo, noti anche come password da utilizzare una sola volta (OTP, One-Time Password), o la conferma secondaria mediante l'uso dell'autenticazione biometrica.

La combinazione di meccanismi (o fattori) di autenticazione differenti per creare l'autenticazione a più fattori consente di ottenere il massimo livello possibile di protezione. La combinazione, ad esempio, di un certificato digitale X.509 su una smart card (un oggetto fisico) con un codice PIN (un dato noto solo all'utente che ne fa uso) che sblocchi la chiave privata associata al certificato determina la creazione di una credenziale estremamente affidabile, il che garantisce a sua volta l'autenticazione avanzata.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dal potenziamento dei meccanismi di autenticazione:

-   Maggiore protezione.

-   Conformità ai requisiti normativi che richiedono opzioni aggiuntive di convalida durante l'accesso alle risorse.

##### Problemi

Di seguito sono riportati i problemi associati al potenziamento dei meccanismi di autenticazione:

-   Valutazione del costo dell'infrastruttura aggiuntiva a fronte della necessità di una maggiore protezione.

-   Integrazione di meccanismi di protezione delle credenziali e di protocolli di autenticazione più avanzati in piattaforme e applicazioni differenti.

-   Necessità di evitare una maggiore complessità della gestione e degli utenti finali. Meccanismi a più fattori in genere determinano un aumento del numero di potenziali problemi che possono verificarsi, come la possibilità che gli utenti smarriscano le smart card o dimentichino il relativo PIN.

-   Riduzione al minimo dei costi e delle risorse associati alla distribuzione dell'hardware per il supporto delle credenziali, quali smart card e token OTP.

#### Miglioramento dell'accesso per dipendenti, clienti e partner

La maggior parte delle organizzazioni desidera ottimizzare i relativi sistemi informatici per accrescere la propria competitività sulla concorrenza mediante l'estensione dell'accesso a un maggior numero di tipi di utenti, applicazioni e reti. A questo approccio si fa in genere riferimento con l'espressione "espansione del perimetro della rete", in quanto i firewall intorno alla rete dell'organizzazione non forniscono più una singola barriera per impedire intrusioni dall'esterno.

L'accesso dei clienti alle informazioni e alle applicazioni garantisce ad esempio nuove opportunità commerciali. I partner commerciali semplificano le catene di fornitura mediante l'integrazione dei sistemi di inventario, spedizione, finanziari e sviluppo dei prodotti, il che consente loro di condividere informazioni riservate su prezzi, prodotti e supporto. I dipendenti hanno maggiori opportunità di collaborare e comunicare in remoto in quanto lavorano a stretto contatto con clienti e partner.

##### Vantaggi

Di seguito sono riportati i principali vantaggi derivanti dal miglioramento dell'accesso:

-   Sviluppo rapido delle applicazioni.

-   Distribuzione più rapida delle applicazioni.

-   Maggiore controllo dell'accesso alle risorse.

-   Miglioramento dell'esperienza degli utenti finali.

-   Riduzione del sovraccarico amministrativo.

##### Problemi

Tra i numerosi problemi associati al miglioramento dell'accesso per gli utenti esterni figurano:

-   Integrazione con le applicazioni esistenti.

-   Scelta degli archivi di identità appropriati.

-   Scelta dei meccanismi di autenticazione appropriati per ciascuna classe di utenti.

-   Scelta di un modello di autorizzazione appropriato.

-   Scalabilità dei meccanismi di autenticazione e autorizzazione.

-   Gestione delle identità per molti partner e clienti.

-   Concessione agli utenti dell'accesso alle risorse appropriate, in base al ruolo svolto nell'organizzazione e alle applicazioni in uso.

-   Natura complessa del processo di definizione di relazioni di trust tra le organizzazioni dei partner.

I concetti correlati alla concessione a dipendenti, clienti e partner di un accesso protetto alle applicazioni interne e alla possibilità di utilizzo dei servizi Single Sign On sono illustrati nel documento relativo alla gestione degli accessi alle reti Extranet in questa serie.

#### Definizione dei criteri di controllo della protezione

Un'organizzazione tipica dispone di criteri di protezione che richiedono il controllo sia a livello di piattaforma che di applicazione. Uno dei principali vantaggi derivanti dall'implementazione di alcune iniziative di gestione di identità e accessi descritte in questo capitolo è rappresentato dal consolidamento degli archivi delle identità, delle piattaforme e dei meccanismi di autenticazione e autorizzazione. Questo consolidamento rende il controllo più semplice e affidabile in quanto il numero di posizioni e le modalità in cui gli eventi di protezione vengono generati risultano ridotti.

Il passaggio successivo prevede che l'organizzazione esamini in dettaglio i tipi di controllo necessari e le modalità di acquisizione, archiviazione e utilizzo delle informazioni di controllo.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dalla definizione di un criterio di controllo della protezione:

-   Riduzione degli effetti di un controllo di protezione esterno.

-   Migliore capacità di intraprendere azioni legali in caso di attacchi alla protezione.

-   Migliore capacità di rilevare eventuali attacchi in tempo reale, avvisando in tal modo gli amministratori della necessità di avviare procedure di emergenza.

-   Migliore capacità di applicare in modo retroattivo criteri difficile da applicare al momento in cui si verifica l'evento.

##### Problemi

Di seguito sono riportati i problemi associati alla definizione di uni criterio di controllo della protezione:

-   Meccanismi di controllo differenti in piattaforme e applicazioni.

-   Funzionalità di controllo differenti con diversi gradi di specificità.

-   Requisiti di controllo differenti per le diverse unità aziendali di un'organizzazione.

-   Consolidamento dei report di controllo in una posizione centrale.

-   Applicazione di filtri ai volumi di informazioni.

-   Generazione di report significativi.

-   Archiviazione di grandi quantità di dati di controllo.

#### Aggiornamento degli standard per l'approvvigionamento di applicazioni software

Le applicazioni sono in genere la causa principale della complessità dei sistemi di gestione di identità e accessi. Le applicazioni in genere introducono diversi tipi di archivi di identità, di meccanismi di autenticazione e di criteri di autorizzazione. Una volta standardizzati i criteri relativi ai servizi directory, alla protezione e all'accesso, è importante stabilire o aggiornare gli standard aziendali per l'approvvigionamento del software in modo che le nuove applicazioni software si integrino efficacemente con gli altri sistemi dell'organizzazione.

La scelta di software di fornitori di software indipendenti (ISV, Independent Software Vendor) deve essere basata in parte sulla capacità di tali applicazioni di integrarsi con i servizi directory selezionati e di soddisfare i criteri di protezione e accesso stabiliti.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dall'aggiornamento degli standard di approvvigionamento del software:

-   Distribuzione rapida di nuove applicazioni.

-   Semplicità di integrazione con l'infrastruttura di gestione di identità e accessi.

-   Costo totale di proprietà ridotto.

-   Maggiore protezione.

-   Formazione semplificata per gli utenti finali.

-   Incremento della produttività per gli utenti finali.

##### Problemi

Di seguito sono riportati i problemi associati all'aggiornamento degli standard di approvvigionamento del software:

-   Individuazione delle applicazioni software adeguate con le funzionalità appropriate.

-   Identificazione dei componenti opzionali che è possibile utilizzare o acquistare.

-   Selezione del software per ottimizzare la protezione.

-   Selezione del software per ottimizzare la produttività.

#### Definizione degli standard di sviluppo del software per l'utilizzo delle identità

La rapida evoluzione delle esigenze di un'organizzazione genera la necessità di utilizzare nuove applicazioni per l'implementazione delle nuove funzionalità aziendali. L'impostazione e l'applicazione degli standard di sviluppo che definiscono la modalità di interazione delle applicazioni con l'infrastruttura di gestione di identità e accessi costituiscono la base per una riduzione del costo totale di proprietà e il miglioramento della protezione.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dalla definizione degli standard di sviluppo del software per l'utilizzo delle identità:

-   Eliminazione della necessità di affrontare nuovi problemi di gestione delle identità.

-   Possibilità di sviluppare le applicazioni in modo più rapido.

-   Costi amministrativi ridotti.

-   Maggiore protezione grazie alla riduzione della superfice di attacco.

##### Problemi

Di seguito sono riportati i problemi associati alla definizione degli standard di sviluppo del software:

-   Determinazione di un'origine autorevole per le informazioni sulle identità da cui possono trarre vantaggio le nuove applicazioni.

-   Garanzia che le applicazioni utilizzino gli archivi di identità e le funzionalità di autenticazione e autorizzazione esistenti.

-   Creazione e pubblicazione di linee guida ben definite, integrate con qualsiasi metodologia SDLC (System Development Life Cycle), relative alla modalità di integrazione delle applicazioni con l'infrastruttura per la gestione di identità e accessi.

-   Formazione degli sviluppatori interni ed esterni su come seguire queste linee guida.

#### Sviluppo e migrazione delle applicazioni con supporto delle identità

Dopo che un'organizzazione ha stabilito gli standard per lo sviluppo delle applicazioni, è possibile sviluppare nuove applicazioni tramite l'uso di questi standard. È necessario inoltre che le applicazioni esistenti abbiano lo stesso livello di integrazione con l'infrastruttura per la gestione di identità e accessi.

A tal fine, è opportuno eseguire un inventario e suddividere in categorie le applicazioni esistenti. È bene prendere in considerazione il valore di ciascuna applicazione, le informazioni in esse disponibili e le caratteristiche di protezione corrispondenti per determinare l'importanza relativa. Bilanciare questi elementi con il costo associato alla migrazione o alla modifica di ciascuna applicazione per assegnare delle priorità alle applicazioni in modo da determinare quali applicazioni sia necessario migrare per prime.

##### Vantaggi

Di seguito sono riportati i vantaggi derivanti dallo sviluppo e dalla migrazione delle applicazioni con supporto delle identità:

-   Sovraccarico amministrativo ridotto per la gestione delle identità.

-   Maggiore protezione.

-   Garanzia della coerenza all'interno delle applicazioni.

##### Problemi

Di seguito sono riportati i problemi associati allo sviluppo e alla migrazione delle applicazioni con supporto delle identità:

-   Comprensione della modalità di funzionamento delle applicazioni in modo da poter prendere le giuste decisioni in merito al metodo più efficace per eseguirne l'integrazione.

-   Scelta di una piattaforma per la migrazione delle applicazioni.

-   Scelta di un linguaggio o un ambiente appropiato per lo sviluppo delle applicazioni.

-   Scelta di un archivio di identità che soddisfi i requisiti dell'organizzazione e delle applicazioni.

-   Scelta delle tecniche di autorizzazione e autenticazione necessarie per soddisfare specifici requisiti.

Informazioni sulle tecniche necessarie per la creazione di applicazioni che si integrano con la piattaforma Microsoft di Gestione di identità e accessi sono disponibili nel documento relativo allo sviluppo di applicazioni ASP.NET abilitate al riconoscimento delle identità in questa serie.

[](#mainsection)[Inizio pagina](#mainsection)
