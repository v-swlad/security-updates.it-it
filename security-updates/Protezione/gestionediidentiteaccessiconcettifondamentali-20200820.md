---
TOCTitle: 'Gestione di identità e accessi: Concetti fondamentali'
Title: 'Gestione di identità e accessi: Concetti fondamentali'
ms:assetid: 'b8d50e80-f68c-447f-8825-67268728f0a7'
ms:contentKeyID: 20200820
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536220(v=TechNet.10)'
---

Concetti fondamentali
=====================

### Capitolo 7: Applicazioni

Aggiornato: 29 aprile 2004

Le applicazioni svolgono un ruolo fondamentale in qualsiasi strategia di gestione di identità e accessi. Per l'esecuzione dell'autenticazione e la valutazione dei diritti acquisiti che consentono di abilitare l'accesso alle risorse, le applicazioni prevedono l'utilizzo dei dati relativi alle identità digitali. Quando si scelgono o si sviluppano applicazioni, è fondamentale assicurarsi che le applicazioni siano compatibili con l'infrastruttura di gestione di identità e accessi in uso.

Le applicazioni in genere rientrano in una delle due seguenti categorie:

-   Applicazioni di terze parti pronte per l'uso o commerciali, quale Microsoft® Exchange Server 2003.

-   Applicazioni personalizzate o interne progettate dagli sviluppatore per soddisfare le specifiche esigenze di un'organizzazione.

Indipendentemente dal fatto che l'applicazione sia stata sviluppata o acquistata, è necessario che sia in grado di integrarsi in modo efficace nell'infrastruttura di gestione di identità e accessi dell'organizzazione. Tuttavia, i criteri coinvolti sono diversi e variano a seconda del tipo di applicazione che si intende integrare.

Il grado di semplicità o difficoltà di integrazione di un'applicazione con la piattaforma per la gestione di identità e accessi è determinato dall'architettura dell'applicazione e dai meccanismi in essa utilizzati per identificare i relativi utenti. Microsoft consiglia di identificare le applicazioni, classificarle ed esaminare le dipendenze tra le relative funzionalità e l'infrastruttura. Se un'applicazione non è compatibile con la piattaforma per la gestione di identità e accessi dell'organizzazione, sarà necessario modificare l'applicazione o l'infrastruttura.

**Nota:** dal punto di vista dello sviluppo delle applicazioni, è opportuno che nelle applicazioni non vengano progettati e implementati archivi di identità, protocolli di protezione (per l'autenticazione, l'autorizzazione e il controllo) o meccanismi di protezione dei dati personalizzati.

Nelle sezioni che seguono in questo capitolo vengono illustrati i metodi consigliati per l'integrazione delle applicazioni con la piattaforma Microsoft di gestione di identità e accessi e viene fornita una descrizione dettagliata delle tecniche da utilizzare per lo sviluppo, il test e la distribuzione delle applicazioni abilitate al riconoscimento delle identità. Nel documento relativo allo sviluppo di applicazioni abilitate al riconoscimento delle identità in questa serie vengono descritte in maggiore dettaglio le operazione che gli architetti e gli sviluppatori delle applicazioni devono eseguire per integrare le applicazioni nell'infrastruttura.

### Scelta delle applicazioni

Per la scelta di un'applicazione, i responsabili IT profondono in genere un notevole impegno per assicurare che l'applicazione sia in grado di fornire le funzionalità necessarie. Tuttavia, l'aspetto relativo alla modalità di integrazione dell'applicazione con la rete viene spesso trascurato, in particolare in relazione alla gestione delle identità.

Le applicazioni di terze parti sono in grado di identificare gli utenti mediante i seguenti metodi:

-   Integrazione con il servizio directory principale dell'organizzazione.

-   Collegamento al servizio directory principale mediante una connessione basata su standard.

-   Autenticazione in un altro servizio directory.

-   Uso di un archivio di identità separato.

Exchange Server 2003 fornisce un esempio di applicazione in grado di integrarsi completamente con un servizio directory. Exchange estende lo schema del servizio directory Microsoft Active Directory® e aggiunge gli attributi delle cassette postali agli account utente in Active Directory. A differenza di Exchange 5.5, Exchange 2000 Server e Exchange Server 2003 non gestiscono un database di directory separato. L'integrazione completa con un servizio directory fornisce il modo più semplice per implementare la gestione delle identità a livello di applicazione.

Alcune applicazioni non sono in grado di integrarsi completamente con un servizio directory, ma possono autenticare gli utenti in una directory mediante connessioni basate su standard. Un esempio è rappresentato da applicazioni che prevedono l'utilizzo del protocollo di autenticazione Kerberos versione 5 per l'esecuzione dell'autenticazione in Active Directory, come SAP R/3, che fa parte dell'ambiente dell'organizzazione fittizia Contoso cui si è fatto riferimento negli altri documenti di questa serie.

È possibile che le applicazioni eseguano l'autenticazione in un altro servizio directory diverso dal servizio directory principale dell'organizzazione. Questa non è una situazione ideale, in quanto sarà necessario eseguire la sincronizzazione tra la directory principale e la directory utilizzata dall'applicazione. Un prodotto di metadirectory, quale Microsoft Identity Integration Server 2003, Enterprise Edition (MIIS 2003), è in grado di fornire questa sincronizzazione tramite gli agenti di gestione che si connettono agli archivi di identità più comuni.

La situazione meno appropriata è rappresentata da uno scenario in cui l'applicazione ha un archivio di identità proprietario dedicato e non sono disponibili strumenti per importare/esportare i dati sulle identità in un formato supportato da MIIS 2003. In questa specifica situazione, è possibile utilizzare MIIS 2003 per sincronizzare l'archivio delle identità dell'applicazione con il servizio directory principale. Tuttavia, se si segue questa procedura, la gestione delle identità nell'archivio delle identità dell'applicazione diventerà un processo manuale, costoso e soggetto a errori.

[](#mainsection)[Inizio pagina](#mainsection)

### Sviluppo delle applicazioni

Durante lo sviluppo di applicazioni interne, è necessario che gli architetti e gli sviluppatori delle applicazioni prendano in considerazione tre approcci fondamentali:

-   **Integrazione delle applicazioni:** scelta di applicazioni in grado di integrarsi o di interagire con l'infrastruttura.

-   **Flusso delle identità:** scelta di una combinazione appropriata dei tre modelli fondamentali per l'autenticazione front-end e back-end.

-   **Autorizzazione:** scelta di una combinazione dei due modelli fondamentali per l'autorizzazione.

Le scelte operate in queste tre aree hanno effetto sul tipo di codice che gli sviluppatori di applicazioni devono implementare per l'autenticazione, l'autorizzazione e il controllo. In un'applicazione ben integrata, non è necessario implementare praticamente alcun codice abilitato al riconoscimento delle identità, in quanto le operazioni necessarie vengono eseguite automaticamente dall'infrastruttura sottostante.

L'integrazione delle applicazioni si basa sugli stessi fattori illustrati nella sezione precedente "Scelta delle applicazioni".

**Nota:** Active Directory Application Mode (ADAM) è una nuova modalità di Active Directory che gli sviluppatori possono utilizzare per sviluppare applicazioni integrate in servizi directory.

#### Abilitazione del flusso di identità

Esistono tre diversi modelli per consentire lo spostamento delle identità degli utenti autenticati in ambienti distribuiti, noto anche come flusso di identità. Questi modelli sono riportati di seguito:

-   Rappresentazione/delega

-   Sottosistema trusted o attendibile

-   Mapping delle credenziali

##### Uso del modello di rappresentazione/delega

La *rappresentazione* consente l'esecuzione di un processo server mediante l'uso delle credenziali di protezione del client. Quando il server rappresenta il client, le eventuali operazioni eseguite dal server vengono effettuate mediante le credenziali del client. Tuttavia, la rappresentazione non consente al server di accedere alle risorse remote per conto del client. Questo accesso richiede la *delega*. La delega è più potente e consente al processo server di eseguire chiamate ad altri computer quando svolge il ruolo di client.

##### Uso del modello di sottosistema attendibile

Con questo modello, il servizio di livello intermedio utilizza un'identità fissa per accedere ai servizi e alle risorse a valle. Il contesto di protezione del chiamante originale non passa attraverso il servizio a livello di sistema operativo, sebbene l'applicazione possa scegliere di trasmettere l'identità del chiamante originale a livello applicazione. Questa operazione potrebbe essere necessaria per fornire il supporto per i requisiti di controllo back-end o per l'autorizzazione e l'accesso ai dati per singoli utenti.

Il nome del modello deriva dal fatto che il servizio a valle (probabilmente un database) considera attendibile il servizio a monte per autorizzare i chiamanti.

##### Uso del modello di mapping delle credenziali

Il modello di mapping delle credenziali consente di allineare un insieme di credenziali a un altro in una tabella di mapping. È possibile utilizzare le credenziali mappate per creare una nuova connessione a un altro sistema. Esistono due tipi di modelli di mapping delle credenziali: un modello prevede l'utilizzo del mapping diretto delle credenziali, mentre l'altro prevede l'utilizzo del mapping indiretto dei "ticket" che vengono successivamente scambiati con le credenziali. È possibile utilizzare il modello di mapping delle credenziali nel caso in cui il sistema di destinazione non supporti il protocollo di autenticazione Kerberos versione 5 o non utilizzi Active Directory come archivio di identità.

#### Implementazione delle autorizzazioni

Una volta identificato l'utente, l'applicazione deve essere in grado di determinare le risorse a cui l'utente può accedere tramite l'autorizzazione. Di seguito sono riportati i due modelli di autorizzazione delle applicazioni:

-   Elenco di controllo di accesso (ACL)

-   Controllo dell'accesso basato sui ruoli (RBAC)

##### Uso del modello di elenchi di controllo di accesso

Il modello ACL consente di garantire la protezione di una risorsa, ad esempio un file, una cartella, una stampante o un oggetto del servizio directory, mediante l'utilizzo di un ACL, ovvero un elenco di utenti e gruppi, con le autorizzazioni (di tipo Consenti e Nega) per ciascun utente o gruppo. Quando un utente richiede l'accesso alla risorsa, le autorizzazioni di accesso dell'utente vengono valutate insieme alle autorizzazioni di accesso di tutti i gruppi di cui l'utente è membro. All'utente viene quindi concesso o negato l'accesso in base a tali autorizzazioni di accesso.

Il modello ACL è particolarmente adatto all'utilizzo con oggetti persistenti ben definiti, ma non funziona in determinati ambienti, quali applicazioni LOB (Line-Of-Business) o applicazioni Web. La gestione di questi tipi di applicazioni, applicazioni di flussi di lavoro e oggetti transitori richiede l'utilizzo di un modello differente.

##### Uso del controllo dell'accesso basato sui ruoli

In RBAC viene utilizzato il concetto di ruolo. Un ruolo è in genere una qualifica professionale, ad esempio "Dirigente", "Cassiere" o "Dirigente del settore vendite". RBAC consente di associare tali ruoli alle autorizzazioni delle applicazioni in modo che l'amministrazione del controllo dell'accesso possa essere eseguita in base al ruolo di un utente.

RBAC converte quindi l'appartenenza al ruolo di un utente nelle autorizzazioni delle applicazioni. Poiché vengono concesse a livello di ruolo, le autorizzazioni possono essere interrogate e modificate per il ruolo senza esaminare le specifiche risorse.

Dopo che gli amministratori hanno creato i ruoli e assegnato autorizzazioni a tali ruoli, potrebbe essere necessario apportare solo modifiche minime ai ruoli o alle autorizzazioni. L'unica modifica da apportare prevede l'assegnazione di utenti o gruppi ai ruoli.

Nel documento relativo allo sviluppo di applicazioni abilitate al riconoscimento delle identità in questa serie vengono descritte in maggiore dettaglio le operazione che gli architetti e gli sviluppatori delle applicazioni devono eseguire per integrare le applicazioni nell'infrastruttura.

[](#mainsection)[Inizio pagina](#mainsection)
