---
TOCTitle: 'Guida alla pianificazione della conformità allo standard PCI DSS (Payment Card Industry Data Security Standard)'
Title: 'Guida alla pianificazione della conformità allo standard PCI DSS (Payment Card Industry Data Security Standard)'
ms:assetid: '6687efc1-44db-4015-ae35-d1a853dc8a06'
ms:contentKeyID: 15480175
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Bb821241(v=TechNet.10)'
---

Guida alla pianificazione della conformità allo standard PCI DSS (Payment Card Industry Data Security Standard)
===============================================================================================================

##### On This Page

[![Introduzione](images/Bb821241.arrow_px_down(it-it,TechNet.10).gif)](#enaa)[Introduzione](#enaa)
[![Come adempiere ai requisiti dello standard PCI DSS](images/Bb821241.arrow_px_down(it-it,TechNet.10).gif)](#emaa)[Come adempiere ai requisiti dello standard PCI DSS](#emaa)
[![Appendici](images/Bb821241.arrow_px_down(it-it,TechNet.10).gif)](#eaaa)[Appendici](#eaaa)

### Introduzione

La *Guida alla pianificazione della conformità allo standard PCI DSS (Payment Card Industry Data Security Standard)* è stata pensata per aiutare le organizzazioni ad adempiere ai requisiti dello standard PCI DSS (Payment Card Industry Data Security Standard). In particolare, questa guida è dedicata ai commercianti che accettano le carte di pagamento, agli istituti finanziari che elaborano le transazioni con carte di pagamento e ai provider di servizi, ovvero alle aziende che offrono servizi di elaborazione delle transazioni con carte di pagamento o di archiviazione dei dati. Le soluzioni IT per ognuno di questi gruppi devono adempiere a tutti i requisiti PCI DSS. Questa guida costituisce un'integrazione alla [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true) (in inglese) che presenta un approccio di tipo strutturale alla creazione dei controlli IT come parte delle iniziative per la conformità ai vari standard e alle varie normative. Questa guida descrive inoltre i prodotti e le soluzioni tecnologiche Microsoft utili per l'implementazione dei controlli IT atti ad agevolare la conformità ai requisiti PCI DSS e agli altri obblighi normativi dell'organizzazione.

**Nota**   Alle organizzazioni che, nell'ambito delle loro offerte di servizi, offrono sportelli ATM/bancomat, Microsoft offre assistenza per l'architettura e la protezione del software, dei sistemi e delle reti che supportano questi dispositivi. Per ulteriori informazioni, vedere la pagina dei download dell'[Industry Center Banking](http://msdn2.microsoft.com/en-us/architecture/86e3451d-8219-46af-bf99-4a610e4bf1f4.aspx) (in inglese) sul sito Web di MSDN.

Questa guida non contiene tutte le informazioni sulla conformità ai requisiti PCI DSS valide per ogni organizzazione. Per informazioni su problemi specifici, rivolgersi al proprio consulente legale o al proprio revisore.

L'introduzione di questa guida include le seguenti sezioni:

-   **Riepilogo generale**. Questa sezione offre un'ampia panoramica dei requisiti PCI DSS e degli obiettivi primari di questa guida. In particolare, descrive le informazioni di cui i manager IT hanno bisogno per pianificare le conformità ai requisiti PCI DSS.

-   **Destinatari della guida** Questa sezione descrive il pubblico a cui si rivolge la guida, lo scopo e l'ambito della pubblicazione e gli avvertimenti e le dichiarazioni di non responsabilità relativamente alle limitazioni della guida.

-   **Cos'è lo standard PCI DSS (Payment Card Industry Data Security Standard)?** Questa sezione offre una panoramica dello standard PCI DSS e dei suoi requisiti.

-   **Pianificazione della conformità allo standard PCI DSS**. Questa sezione illustra l'uso di un framework atto a favorire la conformità ai requisiti PCI DSS. L'approccio descritto include la creazione di vari tipi di controlli IT, le modalità di interazione di tali controlli e l'importanza di tali componenti nelle iniziative che l'organizzazione intraprende per adempiere ai requisiti PCI DSS e agli altri obblighi normativi.

-   **Il processo di controllo dello standard PCI DSS**. Questa sezione offre una panoramica del processo di controllo dei requisiti PCI DSS utilizzato dai revisori per valutare la conformità dell'organizzazione a tale requisiti.

Data la natura integrativa di questo white paper alla *The* *Regulatory Compliance Planning Guide*, si consiglia di consultare anche questa guida per la pianificazione di una soluzione completa per la conformità a tutti i requisiti normativi applicabili all'organizzazione.

#### Riepilogo generale

La conformità allo standard PCI DSS è obbligatoria per tutte le organizzazioni che si occupano dell'elaborazione, dell'archiviazione o della trasmissione di dati relativi a transazioni effettuate con carte di pagamento. I requisiti definiti in questo standard, sviluppato dal PCI Security Standards Council, sono mirati alla creazione del livello di protezione minimo accettabile per i titolari di carta che utilizzano i servizi dell'organizzazione.

Il raggiungimento della conformità è un processo piuttosto complesso, per via dei tre problemi descritti di seguito. Il primo è che la conformità ai requisiti PCI DSS può avere un certo impatto sull'organizzazione. Per questo motivo, è importante coordinare le iniziative di conformità dei singoli reparti ed elaborare una strategia di conformità globale. Il secondo problema è costituito dal fatto che l'organizzazione potrebbe essere soggetta all'osservanza di vari tipi di normative, ognuna con un tipo diverso di requisiti. È normale che molte aziende abbiano difficoltà a capire come rispondere in modo appropriato a tutti questi requisiti contenendo i costi per le procedure e i processi necessari a garantire l'osservanza delle normative. Il terzo problema è costituito dal fatto che lo standard PCI DSS, come molte altre normative, parla dei controlli IT solo en passant, lasciando i manager IT a dover decidere da soli cosa fare per ottenere e mantenere questa conformità.

La *Guida alla pianificazione della conformità allo standard PCI DSS (Payment Card Industry Data Security Standard)* si rivolge ai manager IT responsabili dell'osservanza degli obblighi dello standard PCI DSS all'interno dell'organizzazione. Il suo scopo è aiutare questi manager a capire come iniziare ad adempiere a molti dei requisiti di controllo IT della loro organizzazione, inclusi i requisiti di conformità allo standard PCI DSS. A tal fine, la guida fornisce informazioni sulle soluzioni da utilizzare in questo processo.

Per una discussione più completa su come adempiere ai diversi standard normativi, vedere la [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true).

**Importante**   Questa guida non contiene informazioni di tipo legale. Il suo contenuto è costituito unicamente da informazioni pratiche e tecniche sulla conformità alle normative. Per un consiglio su come adempiere ai requisiti normativi, è bene non affidarsi esclusivamente a questa guida. Per informazioni su problemi specifici, rivolgersi al proprio consulente legale o al proprio revisore.

#### Destinatari del documento

La *Guida alla pianificazione della conformità allo standard PCI DSS (Payment Card Industry Data Security Standard)* è destinata principalmente alle persone che, nella loro organizzazione, sono responsabili della raccolta, dell'elaborazione, della trasmissione e nell'archiviazione dei dati sui titolari di carta nel rispetto dei requisiti di protezione e affidabilità e nell'osservanza della privacy. I destinatari di questa guida includono i manager IT che, nella loro organizzazione, occupano le seguenti posizioni:

-   **CIO (Chief Information Officer)** con l'incarico di provvedere alla distribuzione e al funzionamento dei sistemi e dei processi IT.

-   **CISO (Chief Information Security Officer)** con l'incarico di sviluppare il piano globale di protezione delle informazioni e garantire la conformità ai criteri di protezione delle informazioni.

-   **CFO (Chief Financial Officer)** con l'incarico di controllare l'intero ambiente dell'organizzazione.

-   **CPO (Chief Privacy Officer)** con l'incarico di implementare i criteri per la gestione delle informazioni personali, inclusi i criteri a supporto della conformità alle leggi sulla protezione della privacy e dei dati personali.

-   **TDM (Technical Decision Maker)** con l'incarico di identificare le soluzioni tecnologiche appropriate per la risoluzione di specifici problemi di business.

-   **Manager delle operazioni IT** con l'incarico di gestire i sistemi e i processi che eseguono il programma di conformità allo standard PCI DSS.

-   **Architetti della protezione IT** con l'incarico di progettare i sistemi di controllo e protezione IT atti a fornire il livello di protezione adeguato a soddisfare le esigenze di business dell'organizzazione.

-   **Architetti dell'infrastruttura IT** con l'incarico di progettare le infrastrutture in grado di supportare i controlli e le funzioni di protezione IT sviluppate dagli Architetti della protezione IT.

-   **Consulenti e partner** con l'incarico di raccomandare o implementare le procedure consigliate per il raggiungimento degli obiettivi di conformità allo standard PCI DSS.

Oltre a quelli sopra elencati, anche i seguenti destinatari possono trovare utile questa guida:

-   **Responsabili di rischio/conformità** con l'incarico di gestire il rischio globale derivante dalla conformità ai requisiti PCI DSS.

-   **Manager del controllo IT** con l'incarico di controllare i sistemi IT e ridurre il carico di lavoro dei revisori IT interni ed esterni.

#### Cos'è lo standard PCI DSS (Payment Card Industry Data Security Standard)?

Lo standard PCI (Payment Card Industry) DSS (Data Security Standard) è un insieme di requisiti pensato per garantire la sicurezza delle informazioni sui titolari di carte di credito e debito, indipendentemente dalle loro modalità o posizioni di raccolta, elaborazione, trasmissione e archiviazione. Sviluppato dai membri fondatori del PCI Security Standards Council, che includono America Express, Discover Financial Services, JCB, MasterCard Worldwide e Visa International, questo standard mira a incoraggiare l'adozione internazionale di misure di protezione dei dati coerenti e omogenee.

I requisiti dello standard PCI DSS riguardano aziende e organizzazioni che gestiscono dati sui titolari di carta nel normale svolgimento della loro attività. In particolare, i requisiti PCI DSS riguardano istituti finanziari, commercianti e provider di servizi che gestiscono questo tipo di dati nel corso di una loro tipica giornata lavorativa. Lo standard PCI DSS è costituito da un elenco di requisiti di protezione in termini di gestione, criteri, procedure, architettura di rete, progettazione di software e altre misure di tutela dei dati sui titolari di carta.

La versione 1.1 rappresenta il rilascio più recente di questo standard e risale al settembre 2006. Lo standard è organizzato in un gruppo di sei principi e dodici requisiti di accompagnamento. Ogni requisito contiene sottorequisiti la cui osservanza richiede l'implementazione di particolari processi, criteri o soluzioni tecnologiche. I criteri e i requisiti PCI DSS obbligano a:

-   Creare e gestire una rete protetta

    -   Requisito 1: installare e gestire una configurazione firewall per proteggere i dati sui titolari di carta.

    -   Requisito 2: non utilizzare i valori predefiniti forniti dal produttore per password del sistema e altri parametri di protezione.

-   Proteggere i dati sui titolari di carta

    -   Requisito 3: proteggere i dati sui titolari di carta presenti negli archivi.

    -   Requisito 4: crittografare la trasmissione dei dati sui titolari di carta sulle reti pubbliche e aperte.

-   Adottare un programma di gestione delle vulnerabilità

    -   Requisito 5: utilizzare e aggiornare regolarmente un software antivirus.

    -   Requisito 6: sviluppare e gestire sistemi e applicazioni sicuri.

-   Implementare forti misure di controllo dell'accesso

    -   Requisito 7: limitare l'accesso ai dati sui titolari di carta al personale che ne ha effettivamente bisogno.

    -   Requisito 8: assegnare un ID univoco a ogni persona dotata di accesso informatico.

    -   Requisito 9: limitare l'accesso fisico ai dati sui titolari di carta.

-   Monitorare e testare regolarmente le reti

    -   Requisito 10: registrare e monitorare tutti gli accessi alle risorse di rete e ai dati sui titolari di carta.

    -   Requisito 11: testare regolarmente i sistemi e i processi di protezione.

-   Adottare criteri di protezione delle informazioni

    -   Requisito 12: adottare criteri per la protezione delle informazioni.

I requisiti 9 e 12 non richiedono l'implementazione di soluzioni tecnologiche. Il requisito 9 indica di proteggere fisicamente i luoghi in cui vengono archiviati ed elaborati i dati sui titolari di carta. A tale scopo può rendersi necessaria l'implementazione di un sistema di protezione dell'accesso all'edificio, l'installazione e la gestione di un'apparecchiatura di sorveglianza e il controllo dell'identità di tutte le persone che lavorano negli uffici dell'organizzazione e dei visitatori. Il requisito 12 indica di creare dei criteri di protezione delle informazioni e di comunicarli ai dipendenti, ai fornitori e alle altre parti dell'organizzazione che lavorano con i dati sui titolari di carta.

#### Pianificazione della conformità allo standard PCI DSS

Creare da soli le soluzioni per la conformità allo standard PCI DSS non costituisce un'opzione né pratica, né economicamente conveniente. Nella pianificazione della conformità ai requisiti PCI DSS, è necessario considerare anche altre normative. Alcune di queste normative sono le seguenti:

-   Sarbanes-Oxley Act (SOX)

-   Gramm-Leach-Bliley Act (GLBA)

-   Health Insurance Portability and Accountability Act (HIPAA)

-   Direttiva sulla sicurezza dei dati dell'Unione Europea (EUDPD)

-   Standard ISO 17799:2005 Code of Practice for Information Security Management (ISO 17799)

**Nota**   Un'organizzazione multinazionale deve garantire l'osservanza di tutte le norme di legge vigenti in tutti i paesi in cui opera. A questo tipo di organizzazioni, Microsoft suggerisce di rivolgersi a un consulente legale esperto di tutte le leggi vigenti in tali paesi.

Per ulteriori informazioni su come pianificare le iniziative per la conformità a queste normative, vedere la [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true).

Le soluzioni di conformità allo standard PCI DSS create dall'organizzazione devono essere sviluppate tenendo presente quanto segue:

-   Le soluzioni attualmente in uso per adempiere ad altri requisiti normativi

-   I modi migliori per creare nuove soluzioni in grado di agevolare la conformità a tutti i requisiti normativi

Per raggiungere gli obiettivi di conformità con efficienza ed efficacia, Microsoft consiglia l'uso di un framework di controllo. L'uso di un framework di controllo permette all'organizzazione di eseguire il mapping tra le normative e gli standard applicabili e il framework. Così facendo, l'organizzazione può concentrarsi sulle iniziative di controllo IT mirate all'osservanza dei requisiti definiti nel framework, senza disperdersi tra le singole normative.

Se, successivamente, dovessero presentarsi nuovi standard e nuove normative, sarà possibile eseguire il mapping anche di questi ultimi e concentrare gli sforzi sulle parti del framework in cui si è verificato un cambiamento dei requisiti. Nel framework può essere eseguito il mapping di una vasta gamma di requisiti correlati al controllo IT, ad esempio alcuni requisiti specifici del settore quali i requisiti di protezione PCI, i criteri aziendali interni e così via.

I vantaggi che questo framework offre alle organizzazioni che desiderano raggiungere i loro obiettivi di conformità alle normative sono molteplici. L'approccio basato sull'uso del framework di controllo, infatti, consente di:

-   Combinare vari controlli IT per ottenere la conformità a più standard normativi, ad esempio gli standard PCI DSS ed EUDPD, ed evitare così l'uso di controlli distinti.

-   Adempiere alle nuove normative non appena queste vengono introdotte.

-   Assegnare priorità alle spese, scegliendo i controlli IT di maggiore efficacia.

-   Evitare sforzi duplicati per raggiungere gli obiettivi di conformità nelle diverse Business Unit dell'azienda.

-   Aggiornare con efficienza le normative grazie a modifiche incrementali dei controlli IT già implementati nell'organizzazione.

-   Stabilire una base comune su cui possano lavorare reparto IT e revisori.

Prima di pianificare le iniziative di conformità è necessario, ovviamente, studiare lo standard PCI DSS. Lo standard PCI DSS (in inglese) può essere scaricato dal sito <https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf>. Il PCI Security Standards Council, inoltre, ha elaborato un questionario di autovalutazione che consente alle organizzazioni di stabilire se sono effettivamente conformi allo standard PCI DSS. L'uso del questionario di autovalutazione agevola anche la pianificazione delle iniziative mirate alla conformità a questo standard. Il questionario di autovalutazione per lo standard PCI DSS (in inglese) può essere scaricato dal sito <https://www.pcisecuritystandards.org/pdfs/pci_saq_v1-0.pdf>.

Per ulteriori informazioni su come adempiere ai requisiti normativi utilizzando i controlli IT in un framework di controllo, vedere la *The* *Regulatory Compliance Planning Guide*.

#### Il processo di controllo dello standard PCI DSS

Il processo di controllo per la conformità allo standard PCI DSS è simile a quello indicato nella [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true). Tuttavia, per il controllo PCI DSS, esistono alcuni dettagli specifici.

Le revisioni per il controllo dello standard PCI DSS vengono eseguite da due tipi di organizzazioni esterne: le aziende QSA (Qualified Security Assessor) e le aziende ASV (Approved Scanning Vendor). Le aziende QSA si occupano della parte interna del controllo, mentre le ASV eseguono le analisi delle vulnerabilità di quegli ambienti dell'organizzazione che si interfacciano con Internet. Le aziende con certificazione QSA e ASV vengono sottoposte a revisione e approvazione da parte del PCI Data Security Council (PCI DSC) una volta all'anno.

Dopo aver eseguito il controllo di un'organizzazione, le aziende QSA sono tenute a redigere un report secondo le specifiche linee guida definite dal PCI DSC. Queste linee guida sono contenute in un documento con le procedure di controllo PCI (in inglese) che può essere scaricato dal sito <https://www.pcisecuritystandards.org/pdfs/pci_audit_procedures_v1-1.pdf>. Le linee guida spiegano come deve essere organizzato il report che la società QSA deve compilare dopo il controllo. Il report deve includere le informazioni sui contatti dell'organizzazione, la data di esecuzione del controllo, un riepilogo generale, una descrizione dell'ambito del lavoro e l'approccio scelto dalla società QSA per il controllo, i risultati delle analisi trimestrali e i risultati e le osservazioni finali. L'ultima sezione contiene il grosso delle informazioni sulla conformità dell'organizzazione allo standard PCI DSS. In questa sezione, l'azienda QSA riferisce sulla conformità dell'organizzazione a ognuno dei requisiti e dei sottorequisiti PCI utilizzando un particolare modello.

Prima di programmare i controlli PCI DSS per la propria organizzazione o, ancor meglio, durante la pianificazione della conformità allo standard PCI DSS, è necessario che il personale chiave dell'organizzazione studi le procedure di controllo PCI DSS. In questo modo sarà possibile capire chiaramente cosa verrà sottoposto a revisione dall'azienda QSA durante il controllo.

Anche le aziende ASV devono preparare un report con i risultati delle analisi delle vulnerabilità eseguite sugli ambienti dell'azienda che si interfacciano con Internet. Le linee guida per questo report sono contenute in un documento con le procedure di analisi PCI (in inglese) che può essere scaricato dal sito <https://www.pcisecuritystandards.org/pdfs/pci_scanning_procedures_v1-1.pdf>. Questo documento indica quali elementi dell'ambiente dell'organizzazione devono essere analizzati dall'azienda ASV e include una chiave che facilita la lettura e l'interpretazione del report.

Un'organizzazione che si occupa di commercio o fornitura di servizi deve osservare i requisiti di reporting sulla conformità di ogni singola azienda di carte di credito per assicurarsi che questa riconosca il suo stato di conformità. In altre parole, se un'organizzazione è un provider di servizi che gestisce dati sui titolari di carta associati a Visa e American Express, è tenuta a inviare i report di conformità a Visa e American Express.

Ogni azienda di carte di credito ha le sue regole e le sue procedure di conformità. Per ulteriori informazioni sugli specifici requisiti di conformità allo standard PCI DSS e sui programmi di supporto che ogni azienda offre a commercianti e provider di servizi, contattare le aziende di carte di credito per le quali si elaborano, trasmettono o archiviano dati sui titolari di carta.

[![](images/Bb821241.arrow_px_up(it-it,TechNet.10).gif)](#mainsection)[Top Of Page](#mainsection)

### Come adempiere ai requisiti dello standard PCI DSS

Questa sezione descrive dettagliatamente le soluzioni tecnologiche Microsoft da considerare nella pianificazione della conformità allo standard PCI DSS. Le soluzioni scelte dovrebbero essere inserite nelle attività quotidiane dell'organizzazione. Come indicato nella sezione Pianificazione della conformità allo standard PCI DSS, i criteri, le procedure e le soluzioni tecnologiche dell'organizzazione devono tener conto della conformità alle normative a tutti i livelli dell'azienda e la conformità allo standard PCI DSS deve essere valutata nei termini dell'impatto che può avere su ogni parte dell'azienda stessa.

Per una discussione dettagliata sulle considerazioni da fare per il mapping tra i controlli IT e le soluzioni tecnologiche, vedere la [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true).

#### Gestione dei documenti

Le soluzioni di gestione dei documenti combinano software e processi che facilitano la gestione delle informazioni non strutturate nell'organizzazione. Queste informazioni possono essere disponibili in vari formati digitali, tra cui documenti, immagini, file audio o video e file XML.

##### Requisiti PCI DSS adempiuti

L'implementazione di soluzioni di gestione dei documenti agevola la conformità allo standard PCI DSS in due modi. In primo luogo, l'uso di queste soluzioni per gestire i documenti che contengono dati sui titolari di carta possono promuovere l'osservanza dei requisiti PCI DSS relativi all'accesso ai dati e alla gestione e alla protezione delle informazioni. Nello specifico, queste soluzioni agevolano la conformità al requisito 7 e al sottorequisito 10.2.1. In secondo luogo, l'uso di sistemi di gestione dei documenti permette di gestire e pubblicare criteri quali quelli richiesti per adempiere alle Sezioni 3.6, 6.4, 9.2 e 12.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

##### Tecnologie disponibili

Microsoft offre una serie di tecnologie che, utilizzate in combinazione o singolarmente, permettono di creare i controlli IT per la gestione dei documenti. La progettazione di questi controlli deve essere finalizzata all'osservanza dei requisiti PCI DSS e di qualsiasi altro obbligo normativo applicabile all'organizzazione.

-   **Microsoft® Windows® Rights Management Services**. Windows Rights Management Services (RMS) è una piattaforma software che aiuta le applicazioni a proteggere le informazioni digitali da usi non autorizzati, sia online che offline, sia l'interno che all'esterno del firewall. RMS è la tecnologia di base delle funzioni Information Rights Management (IRM) di Microsoft Office e Windows SharePoint® Services. Per l'uso di queste funzioni, è richiesto un server RMS, disponibile in sede o tramite servizio di hosting.

    Con RMS è possibile integrare la strategia di protezione dell'organizzazione tutelando le informazioni con criteri di utilizzo permanenti che restano associati per sempre alle informazioni e le seguono ovunque. È possibile utilizzare applicazioni abilitate a RMS per gestire, controllare e verificare l'accesso ai documenti che contengono dati sui titolari di carta. Il client RMS è integrato nel sistema operativo Windows Vista™. Per le altre versioni di Windows, questo client è disponibile come download gratuito.
    Per ulteriori informazioni, vedere [Windows Rights Management Services](http://www.microsoft.com/rms) all'indirizzo <http://www.microsoft.com/rms>.

-   **Microsoft Office SharePoint Server**. SharePoint Server è un server di collaborazione e gestione dei contenuti che offre alle organizzazioni una piattaforma integrata per le esigenze di gestione documenti e portale. Fornisce il supporto per l'uso di applicazioni Web, intranet ed extranet in tutta l'azienda e offre a sviluppatori e personale IT la piattaforma e gli strumenti necessari per l'amministrazione dei server, l'estensibilità delle applicazioni e l'interoperabilità. SharePoint Server può essere utilizzato come repository centrale per i documenti che contengono dati sui titolari di carta e per quelli che descrivono criteri e processi. SharePoint Server 2007 è integrato in RMS, quindi i criteri di controllo di accesso possono essere applicati a tutte le copie dei contenuti scaricati da SharePoint Server 2007. Grazie a questa caratteristica, gli amministratori possono proteggere con IRM i download da una libreria di documenti. Se un utente cerca di scaricare un file dalla libreria, Microsoft Windows SharePoint Services verifica che tale utente disponga delle autorizzazioni richieste per il file e rilascia all'utente una licenza che gli consente di accedere al file con il livello di autorizzazione adeguato. A questo punto, Windows SharePoint Services scarica il file sul computer dell'utente in un formato crittografato e protetto dai diritti necessari.
    Per ulteriori informazioni, vedere il sito Web di [Microsoft SharePoint](http://go.microsoft.com/fwlink/?linkid=12632) con i prodotti e le tecnologie SharePoint all'indirizzo <http://go.microsoft.com/fwlink/?linkid=12632>.

-   **Microsoft Exchange Server**. Oggi, per la maggior parte delle aziende, la posta elettronica è uno strumento di comunicazione mission-critical. Il sempre maggiore affidamento alla posta elettronica ha aumentato il numero dei messaggi inviati e ricevuti, la quantità e la varietà del lavoro svolto dagli e-mail e i ritmi stessi del business. Exchange Server offre una piattaforma di messaggistica completa che permette di gestire lo scambio di informazioni nell'organizzazione nell'osservanza della conformità allo standard PCI DSS. Exchange Server 2007 include la messaggistica unificata, che consolida posta elettronica, posta vocale e fax in un'unica cartella Posta in arrivo. Inoltre, offre funzioni utili per applicare i criteri di conservazione, analizzare i messaggi in transito e adottare le azioni necessarie, registrare in modo flessibile il diario ed eseguire ricerche di testo elaborato in tutte le cassette postali implementate.
    Per ulteriori informazioni, vedere il sito Web di Microsoft Exchange Server all'indirizzo <http://www.microsoft.com/exchange/default.mspx>.

-   **Microsoft Office**. Office è la migliore suite di applicazioni di produttività per le aziende. La funzione IRM di Microsoft Office consente di controllare l'accesso a informazioni riservate quali i dati sui titolari di carta.

    Nello specifico, la funzione IRM di Office aiuta a:

    -   Impedire ai destinatari non autorizzati di inoltrare, copiare, modificare, stampare, inviare tramite fax o tagliare e incollare le informazioni protette per usi non consentiti.

    -   Impedire alle informazioni protette di essere copiate con la funzione STAMP di Windows.

    -   Mantenere lo stesso livello di protezione delle informazioni, indipendentemente dalla loro destinazione. Questa capacità è nota come *protezione persistente*.

    -   Offrire lo stesso livello di protezione agli allegati di posta elettronica, sempre che tali allegati siano file creati con altri programmi di Office, quali Microsoft Excel® o Microsoft Word.

    -   Proteggere le informazioni contenute nei messaggi di posta elettronica o nei documenti con una data di scadenza, per impedire che le informazioni possano essere visualizzate dopo il periodo di tempo specificato.

    -   Applicare i criteri aziendali che governano l'uso e la distribuzione delle informazioni all'interno e all'esterno dell'azienda.

#### Valutazione dei rischi

La valutazione dei rischi è il processo con cui l'organizzazione identifica i rischi per la sua attività e gli assegna una priorità. In genere, si utilizza un metodo sistematico per identificare le risorse del sistema di elaborazione delle informazioni, le minacce possibili per queste risorse e la vulnerabilità del sistema a tali minacce. Nel contesto della conformità alle normative, la valutazione dei rischi è il processo che valuta il livello di conformità e le inidoneità dell'organizzazione. Il primo passo della pianificazione della conformità allo standard PCI DSS deve sempre essere l'identificazione dei rischi per i dati sui titolari di carta e l'assegnazione delle priorità alle minacce che questi rischi rappresentano.

##### Requisiti PCI DSS adempiuti

La valutazione dei rischi può agevolare la conformità ai requisiti PCI DSS in molti modi. Consente di identificare le aree della rete in cui è necessario apportare degli aggiornamenti per raggiungere il livello di conformità richiesto. Anche dopo aver ottenuto la conformità iniziale, la valutazione dei rischi è molto importante per controllare il mantenimento della conformità nel tempo. L'uso della valutazione dei rischi per prevenire una serie di problemi potenziali può aiutare l'organizzazione ad adempiere a molti requisiti PCI DSS, tra cui i requisiti 1, 3, 4, 5, 6, 7, 8 e 11.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

##### Tecnologie disponibili

Microsoft offre una serie di tecnologie che, utilizzate in combinazione o singolarmente, permettono di creare i controlli IT per la valutazione dei rischi. La progettazione di questi controlli deve essere finalizzata all'osservanza dei requisiti PCI DSS e di qualsiasi altro obbligo normativo applicabile all'organizzazione.

<ul>
<li>
**Microsoft Baseline Security Analyzer (MBSA)**. Uno degli strumenti più validi per valutare i rischi per i dati sui titolari di carta è MBSA. MBSA è uno strumento di facile uso che permette di identificare i più comuni errori di configurazione della protezione in una serie di prodotti Microsoft, tra cui i sistemi operativi Microsoft Windows, Internet Information Services (IIS), SQL Server™, Microsoft Internet Explorer® e Microsoft Office. MBSA è anche in grado di rilevare gli aggiornamenti cumulativi, i service pack pubblicati in Microsoft Update e gli aggiornamenti della protezione mancanti. MBSA può essere eseguito dal prompt dei comandi o dalla sua GUI e può essere utilizzato con Microsoft Update e Microsoft Windows Server® Update Services. Considerata l'importanza di tenere sempre aggiornati i sistemi al fine di garantire la massima protezione dei dati sui titolari di carta, MBSA può rivelarsi uno strumento molto prezioso per la valutazione dei rischi dell'organizzazione.

</li>
Per ulteriori informazioni su MBSA, vedere Microsoft Baseline Security Analyzer (in inglese) all'indirizzo <http://www.microsoft.com/technet/security/tools/mbsahome.mspx>.

<li>
**Microsoft Systems Management Server**. Se l'organizzazione utilizza Microsoft Systems Management Server (SMS) per gestire i computer client e i server, è probabile che disponga già di alcuni degli strumenti necessari per valutare i rischi per i dati sui titolari di carta. Grazie a SMS, è possibile gestire in remoto le impostazioni di protezione dei computer con sistemi operativi Windows presenti sulle reti distribuite. È possibile sapere se sui computer della rete sono installati gli aggiornamenti software richiesti e tenere traccia dello stato di avanzamento degli aggiornamenti cumulativi su questi computer. Con SMS è possibile anche generare report che identificano l'inventario hardware e software completo, i dettagli di configurazione e lo stato dei computer della rete, nonché lo stato delle distribuzioni software e degli errori di distribuzione. Queste funzioni di SMS possono essere molto importanti ai fini della valutazione dei rischi per i dati sui titolari di carta dell'organizzazione.

</li>
Per ulteriori informazioni su SMS, vedere la home page di Microsoft Systems Management Server all'indirizzo <http://www.microsoft.com/smserver/default.mspx>.

<li>
**Microsoft System Center Operations Manager Audit Collection**. Operations Manager 2007 è in grado di estrarre e raccogliere con la massima sicurezza ed efficienza i registri di protezione dei sistemi operativi Windows, nonché di archiviare questi registri per le successive attività di analisi e reporting. I registri estratti vengono archiviati in un apposito database di raccolta controlli. Operations Manager provvede all'invio dei report da utilizzare per i dati di Audit Collection. Audit Collection può essere utilizzato per generare vari report di conformità, quali quelli necessari per i controlli di conformità al Sarbanes-Oxley Act. Audit Collection può essere utilizzato anche per l'analisi della protezione, ad esempio per rilevare le intrusioni o i tentativi di accesso non autorizzato.

</li>
Per ulteriori informazioni, vedere Audit Collection Services (in inglese) all'indirizzo [http://technet.microsoft.com/en-us/library/bb381258,aspx](http://technet.microsoft.com/en-us/library/bb381258.aspx).

<li>
**Windows Server Update Services**.** **Windows Server Update Services con Service Pack 1 consente a un'organizzazione di distribuire molti degli ultimi aggiornamenti dei prodotti Microsoft, pubblicati sul sito Microsoft Update. Windows Server Update Services è un componente aggiornato di Windows Server e offre un modo rapido ed efficace per tenere sempre aggiornati i sistemi. Con WSUS, è possibile disporre di un'infrastruttura di valutazione dei rischi costituita da:

-   **Microsoft Update**. Il sito Web di Microsoft a cui i componenti WSUS si connettono per gli aggiornamenti dei prodotti Microsoft.

-   **Server Windows Server Update Services**. Il componente server che viene installato su un computer dotato di sistema operativo Microsoft Windows 2000 Server con Service Pack 4 (SP4) o Windows Server 2003 all'interno del firewall aziendale. Il server Windows Server Update Services offre le funzioni di cui gli amministratori hanno bisogno per gestire e distribuire gli aggiornamenti con uno strumento basato sul Web, a cui è possibile accedere da Internet Explorer o da qualsiasi computer Windows della rete aziendale. Un server Windows Server Update Services, inoltre, può essere utilizzato come origine degli aggiornamenti per altri server dello stesso tipo.

-   **Aggiornamenti automatici**. Il componente client predefinito dei sistemi operativi Microsoft Windows Vista, Windows Server 2003, Windows XP e Windows 2000 con Service Pack 3. Aggiornamenti automatici permette ai computer client e ai server di ricevere gli aggiornamenti da Microsoft Update o da un server Windows Server Update Services.

</li>
Grazie a questi servizi, tutti gli ambienti host della rete possono disporre delle ultime correzioni rapide per la protezione fornite da Microsoft per i prodotti installati.

Per ulteriori informazioni, vedere la home page di Windows Server Update Services (in inglese) all'indirizzo <http://www.microsoft.com/windowsserversystem/updateservices/default.mspx>.

<li>
**Criteri di gruppo**. Criteri di gruppo è un'infrastruttura che consente al personale IT di implementare configurazioni specifiche per utenti e computer. Le impostazioni di Criteri di gruppo sono contenute negli oggetti Criteri di gruppo, collegati ai seguenti contenitori del servizio directory Microsoft Active Directory®: siti, domini o unità organizzative. Con Criteri di gruppo è possibile gestire da una posizione centrale i computer di una rete distribuita. Poiché Criteri di gruppo consente agli amministratori di distribuire un software in un sito, in un dominio o in una serie di unità organizzative, può essere uno strumento utile per identificare i rischi per l'ambiente IT dell'organizzazione.

</li>
Le impostazioni di Criteri di gruppo possono essere gestite con la Console Gestione Criteri di gruppo. Questa console è stata pensata per semplificare la gestione di Criteri di gruppo grazie a una posizione centrale da cui amministrare i principali aspetti di questa infrastruttura. La console soddisfa i principali requisiti di distribuzione di Criteri di gruppo, in quanto fornisce:

-   Un'interfaccia utente che facilita l'uso di Criteri di gruppo.

-   La capacità di eseguire il backup e il ripristino degli oggetti Criteri di gruppo.

-   La capacità di importare/esportare e copiare/incollare gli oggetti Criteri di gruppo e i filtri di Windows Management Instrumentation (WMI).

-   Un modo molto semplice di gestire la protezione di Criteri di gruppo.

-   La capacità di generare report HTML per le impostazioni degli oggetti Criteri di gruppo e i dati del Gruppo di criteri risultante.

-   La capacità di creare gli script delle operazioni degli oggetti Criteri di gruppo esposte dalla Console Gestione Criteri di gruppo (ma non quella di creare gli script delle impostazioni di un oggetto Criteri di gruppo).

Per ulteriori informazioni, vedere Windows Server 2003 Group Policy (in inglese) all'indirizzo [http://technet2,microsoft.com/windowsserver/en/technologies/featured/gp/default.mspx](http://technet2.microsoft.com/windowsserver/en/technologies/featured/gp/default.mspx) e Introducing the Group Policy Management Console (in inglese) all'indirizzo <http://www.microsoft.com/windowsserver2003/gpmc/gpmcintro.mspx>.

#### Gestione dei cambiamenti

La gestione dei cambiamenti è un processo strutturato con il quale l'organizzazione valuta le modifiche a un piano di progetto, a un'infrastruttura IT, alle distribuzioni software o agli altri processi o procedure dell'organizzazione. Un sistema di gestione dei cambiamenti può aiutare a definire il cambiamento, valutarne l'impatto, stabilire le azioni richieste per implementarlo e distribuire le informazioni necessarie nell'organizzazione. Inoltre, può aiutare a tenere traccia dei cambiamenti implementati nell'organizzazione. Grazie a questo sistema, l'ambiente IT sottoposto ai cambiamenti rimane sempre sotto controllo.

Ad esempio, è possibile creare un database che aiuti il personale a prendere decisioni migliori sui cambiamenti futuri grazie ai dati cronologici sulla riuscita o la mancata riuscita di cambiamenti simili effettuati nel passato. La gestione dei cambiamenti è anche un processo strutturato che comunica la presenza e lo stato dei cambiamenti a tutte le parti interessate. Il processo può produrre un sistema di inventario indicante le azioni che sono state intraprese e i casi in cui tali azioni hanno influito sullo stato delle risorse chiave, per facilitare la previsione e l'eliminazione dei problemi e semplificare la gestione delle risorse.

##### Requisiti PCI DSS adempiuti

La gestione dei cambiamenti è un fattore critico per la conformità allo standard PCI DSS come per qualsiasi altra iniziativa di conformità alle normative. Se l'organizzazione non sa quali cambiamenti ha apportato al suo ambiente IT, non può affermare con certezza che il suo ambiente sia protetto. La registrazione dei cambiamenti apportati a rete, sistemi, criteri e procedure aiuta l'organizzazione ad adempiere ai requisiti PCI DSS 6 e 11.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

##### Tecnologie disponibili

Microsoft offre diverse tecnologie che possono essere considerate nella progettazione delle soluzioni di gestione dei cambiamenti.

<li>
**Microsoft Office SharePoint Server**. Oltre a costituire un'opzione tecnologica per le soluzioni di gestione dei documenti, Microsoft Office SharePoint Server può essere anche un elemento chiave nel sistema di gestione dei cambiamenti di un'organizzazione. Le sue capacità di traccia delle versioni consentono di monitorare i cambiamenti nei criteri e nei documenti dei processi, gli aggiornamenti e le altre modifiche alle applicazioni, nonché le modifiche apportante nel tempo al software approvato.

Per ulteriori informazioni, vedere la sezione Gestione dei documenti e il sito Web di [Microsoft SharePoint](http://go.microsoft.com/fwlink/?linkid=12632) con i prodotti e le tecnologie SharePoint all'indirizzo <http://go.microsoft.com/fwlink/?linkid=12632>.

</li>
<li>
**Microsoft Systems Management Server**. L'uso di SMS permette non solo di gestire la valutazione dei rischi dell'organizzazione, ma anche di tenere traccia dei cambiamenti apportati ai sistemi informatici dell'organizzazione. Tra questi, le modifiche alle impostazioni di protezione o alle applicazioni installate sui computer client e sui server della rete. In più, la potente funzione di reporting predefinita di SMS consente di analizzare le modifiche apportate ai computer dell'organizzazione e capire se tali modifiche sono state eseguite nel rispetto dei requisiti di protezione stabiliti.

</li>
Per ulteriori informazioni su SMS, vedere la home page di Microsoft Systems Management Server all'indirizzo <http://www.microsoft.com/smserver/default.mspx>.

<li>
**Microsoft SMS 2003 Desired Configuration Monitoring 2.0**. Le capacità di SMS possono essere integrate con la funzione SMS 2003 Desired Configuration Monitoring (DCM). Questa funzione consente di automatizzare i controlli di gestione della configurazione per confrontare le impostazioni di configurazione desiderate o definite con quelle effettive. Per ottenere questo scopo, DCM permette all'utente di definire le impostazioni di configurazione desiderate per hardware, sistema operativo e applicazioni in più origini dati di configurazione. A questo punto, grazie al motore di controllo, DCM confronta le impostazioni desiderate con quelle effettive e genera un report sulla conformità della configurazione.

</li>
DCM può aiutare a ridurre il tempo di inattività non pianificato dei servizi, correlare i dati di configurazione e diminuire i costi dell'assistenza. Questa funzione offre un pratico strumento di modifica XML e una guida per la definizione delle voci di configurazione di hardware e software. Inoltre, con i suoi report di conformità estremamente dettagliati, aiuta a rilevare e risolvere gli errori di configurazione.

<li>
**Microsoft Desktop Optimization Pack per Software Assurance**. Microsoft Desktop Optimization Pack per Software Assurance è un servizio di sottoscrizione che riduce i costi di distribuzione delle applicazioni, consente di fornire le applicazioni come servizi e ottimizza la gestione e il controllo degli ambienti desktop dell'azienda. Questo pacchetto di ottimizzazione del desktop permette di migliorare i processi di gestione dei cambiamenti e i ripristini grazie a:

-   Miglioramento della gestione dei criteri di gruppo.

-   Riduzione del tempo di inattività.

-   Accesso su richiesta alle applicazioni, per gli utenti autorizzati.

</li>
Microsoft Desktop Optimization Pack è disponibile solo per i clienti con copertura Software Assurance per i loro desktop. Per ulteriori informazioni, vedere il documento su come ottimizzare il desktop Windows (in inglese) all'indirizzo <http://www.microsoft.com/windows/products/windowsvista/buyorupgrade/optimizeddesktop.mspx>.

</ul>
#### Protezione della rete

Le soluzioni di protezione della rete rappresentano un'ampia categoria di soluzioni specifiche per la protezione di tutti gli elementi di una rete aziendale, inclusi firewall, server, client, router, switch e punti di accesso. Pianificare e monitorare la protezione della rete aziendale è un elemento chiave per ottenere la conformità allo standard PCI DSS. Data la vasta gamma di soluzioni disponibili per risolvere il problema della protezione della rete, è probabile che un'organizzazione disponga già di molti degli elementi che fanno di una rete una rete protetta. Potrebbe sembrare più pratico ed economicamente conveniente partire dalle soluzioni di protezione già implementate piuttosto che cominciare da zero.

Tuttavia, è opportuno tenere presente che alcune delle tecnologie utilizzate potrebbero essere cambiate e che è possibile implementare nuove soluzioni attualmente escluse dalla strategia di protezione della rete. Con il suo materiale di assistenza e le sue soluzioni tecnologiche, Microsoft può essere di aiuto nell'implementazione di soluzioni di protezione della rete valide per ogni esigenza.

##### Requisiti PCI DSS adempiuti

Lo standard PCI DSS indica chiaramente che per ottenere la conformità è necessario implementare reti protette nell'intera organizzazione. Il criterio 1 sancisce che, per essere conforme, l'organizzazione deve creare e gestire una rete protetta. Il requisito 1 sancisce che l'organizzazione deve installare e gestire una configurazione firewall per proteggere i dati sui titolari di carta. Il requisito 2 sancisce che l'organizzazione deve cambiare i valori predefiniti forniti dal produttore per le password di sistema e gli altri parametri di protezione. Le soluzioni di protezione della rete aiutano anche ad adempiere ai requisiti 4 e 10 che indicano, rispettivamente, di crittografare la trasmissione dei dati sui titolari di carta sulla rete e di registrare e monitorare l'accesso alla rete.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

##### Tecnologie disponibili

Microsoft offre una vasta scelta di tecnologie utili per adempiere ai primi due requisiti PCI DSS.

-   **Microsoft Windows Firewall**. Windows XP Service Pack 2 (SP2) include Windows Firewall, che sostituisce Internet Connection Firewall (ICF). Windows Firewall è un firewall con stato, basato su host, che rimuove il traffico in ingresso non richiesto che non corrisponde o al traffico inviato come risposta a una richiesta del computer (traffico richiesto) o al traffico non richiesto che è stato specificato come consentito (traffico consentito). Windows Firewall offre un livello di protezione dagli utenti malintenzionati e dai programmi dannosi che utilizzano il traffico in ingresso non richiesto per attaccare i computer di una rete. Queste funzioni sono state migliorate in Windows Firewall con protezione avanzata su Windows Vista e Windows Server "Longhorn".

-   **Microsoft Internet Security and Acceleration Server**. Microsoft Internet Security and Acceleration (ISA) Server aiuta a proteggere la rete in molti modi. In primo luogo, può essere utilizzato per consentire agli utenti di accedere in remoto alle applicazioni aziendali tramite Internet. A tale scopo, è possibile configurare ISA Server in modo che pre-autentichi le richieste utente in ingresso, ispezioni tutto il traffico a livello di applicazione (incluso il traffico crittografato) e fornisca gli strumenti di pubblicazione automatizzati. In secondo luogo, se l'organizzazione ha delle filiali, ISA Server consente l'uso della compressione HTTP, l'inserimento di contenuti nella cache e capacità VPN (Virtual Private Network) per espandere la rete in modo facile e protetto. In terzo luogo, ISA Server permette di proteggere la rete dalle minacce Internet sia interne che esterne. Questa protezione è dovuta alla sua architettura proxy-firewall, alle sue capacità di ispezione dei contenuti, alle sue impostazioni granulari dei criteri e alle sue capacità di generazione avvisi e monitoraggio.

-   **Server and Domain Isolation con Internet Protocol security (IPsec) e i Criteri di gruppo di Active Directory**. La soluzione Server and Domain Isolation crea un livello di protezione end-to-end in grado di ridurre fortemente il rischio di attacchi dannosi e accessi non autorizzati alle risorse della rete. Basata su Windows IPsec e i Criteri di gruppo di Active Directory, questa soluzione consente di segmentare dinamicamente l'ambiente Windows in più reti logiche protette e isolate. Esistono molti modi per creare una rete isolata, con il vantaggio di isolare logicamente un intero dominio gestito o creare più reti virtuali protette di server, dati riservati e client specifici, limitando così l'accesso ai soli utenti autenticati e autorizzati o richiedendo l'uso della crittografia a specifici server della rete al fine di proteggere tutti i dati. Richiedendo la crittografia dei dati per il traffico scambiato tra specifici host di rete o subnet di rete, è possibile offrire maggiore garanzia ai partner aziendali e adempiere ai requisiti normativi che specificano di crittografare i dati che attraversano una rete.

-   **Configurazione guidata impostazioni di sicurezza di Windows Server 2003**. La Configurazione guidata impostazioni di sicurezza aiuta a proteggere la rete riducendo la superficie di attacco sui server con Windows Server 2003, Service Pack 1. Questa Configurazione guidata determina la funzionalità minima richiesta per i ruoli di un server e disabilita tutte le funzioni non necessarie. Nello specifico, Configurazione guidata impostazioni di sicurezza:

    -   Disabilita i servizi non necessari.

    -   Blocca le porte non utilizzate.

    -   Consente l'applicazione di limitazioni aggiuntive su indirizzi o protezione per le porte lasciate aperte.

    -   Impedisce le estensioni Web IIS, se applicabile.

    -   Riduce l'esposizione del protocollo in SMB (Server Message Block), LanMan e LDAP (Lightweight Directory Access Protocol).

    -   Definisce un criterio di controllo segnale/rumore.

-   **Connessione desktop remoto con Autenticazione server**. La connessione desktop remoto è un metodo molto valido per consentire agli utenti l'accesso ai computer client e ai server condivisi. Questa tecnologia permette di creare a costi contenuti dei computer condivisi per le attività di sviluppo e test. Questi computer possono anche avere la funzione di punto di accesso centrale per vari tipi di progetti e possono consentire l'accesso agli utenti esterni alla rete, isolando i rischi che questi rappresentano per la protezione della rete. Con l'aggiornamento client Connessione desktop remoto 6.0, inoltre, il personale IT può configurare l'autenticazione server. Grazie all'autenticazione server, è possibile impedire agli utenti di connettersi a un computer o a un server diverso da quello desiderato, con il rischio di esporre informazioni riservate. Microsoft ha introdotto questa funzione in Windows Vista e in Windows Server "Longhorn". Il client Connessione desktop remoto 6.0 può essere utilizzato sui computer con Windows Server 2003 con Service Pack 1 o Windows XP con Service Pack 2 (SP2). Il client consente la connessione ai server terminal legacy o ai desktop remoti, come nel passato, ma l'autenticazione server si verifica solo se il computer remoto esegue Windows Vista o Windows Server "Longhorn".

-   **Wi-Fi Protected Access 2**. Se l'organizzazione si avvale di una rete wireless, è opportuno considerare l'aggiornamento a punti di accesso, router wireless e altri dispositivi in grado di supportare la certificazione WPA2 (Wi-Fi Protected Access 2). La certificazione WPA2 può essere ottenuta tramite la Wi-Fi Alliance che attesta la compatibilità dei dispositivi wireless con lo standard IEEE 802.11i. Lo scopo della certificazione WPA2 è il supporto delle nuove funzioni di protezione obbligatorie dello standard IEEE 802.11i non ancora incluse nei prodotti che supportano il WPA. Ad esempio, il WPA2 richiede il supporto sia per la crittografia TKIP che per la crittografia AES. Il WPA2 è disponibile in due diverse modalità:

    -   WPA2-Enterprise utilizza l'autenticazione 802.1X ed è adatto alle reti con modalità di infrastruttura media o grande.

    -   WPA2-Personal utilizza l'autenticazione PSK ed è adatto alle reti con modalità di infrastruttura SOHO.

-   **Network Access Protection**. La piattaforma NAP (Network Access Protection) è stata pensata per Windows Server "Longhorn" e Windows Vista. I suoi componenti per l'applicazione dei criteri assicurano che i computer che si connettono alla rete o comunicano su una rete siano conformi ai requisiti definiti dagli amministratori per proteggere l'integrità del sistema. L'organizzazione può utilizzare una combinazione di componenti per la convalida dei criteri e la restrizione dell'accesso alla rete per controllare quest'ultimo o le comunicazioni. L'organizzazione può anche scegliere di limitare temporaneamente l'accesso dei computer non conformi ai requisiti a una rete ristretta. Con una configurazione appropriata, la rete ristretta può contenere le risorse necessarie per aggiornare i computer in modo che possano soddisfare i requisiti di integrità e godere dell'accesso illimitato alla rete e delle normali funzioni di comunicazione. La piattaforma NAP include un'API che permette a sviluppatori e fornitori di creare soluzioni complete per la convalida dei criteri di integrità, la restrizione dell'accesso alla rete e la conformità costante ai requisiti di integrità. Questa piattaforma offre i componenti per applicare l'accesso limitato per IPsec, connessioni di rete autenticate IEEE 802.1X, VPN e DHCP (Dynamic Host Configuration Protocol). Queste tecnologie possono essere utilizzate da sole o in combinazione. Grazie a queste capacità, la piattaforma NAP può costituire un potente strumento al servizio dell'integrità e della protezione della rete.

-   **Microsoft Virtual Server**. Microsoft Virtual Server 2005 R2 offre una piattaforma di virtualizzazione eseguibile sulla maggior parte dei principali sistemi operativi x86 in ambiente guest. È supportato da Microsoft come host per i sistemi operativi Windows Server e le applicazioni Windows Server System. La sua capacità di integrazione con una vasta gamma di strumenti di gestione di Microsoft e altri fornitori permette agli amministratori di gestire facilmente un ambiente Virtual Server 2005 R2 con gli strumenti già disponibili per la gestione dei server fisici. Poiché Microsoft Virtual Server consente di eseguire più sistemi operativi sullo stesso computer, agevola la conformità al requisito PCI DSS 2.2.1, che impone l'esecuzione di una sola funzione principale per server. Ad esempio, è possibile utilizzare Virtual Server per distribuire sullo stesso computer un server Web virtuale, un server di database virtuale e un server di file virtuale.

#### Controllo dell'host

Le soluzioni di controllo dell'host verificano i sistemi operativi di server e workstation. Queste soluzioni prevedono anche l'implementazione delle procedure consigliate di protezione a tutti i livelli del sistema operativo di ogni host, l'applicazione degli aggiornamenti e delle correzioni rapide più recenti e l'uso di metodi protetti per le operazioni di ogni giorno.

##### Requisiti PCI DSS adempiuti

Le soluzioni di controllo dell'host possono agevolare la conformità ai requisiti PCI DSS mantenendo sempre aggiornati e correttamente configurati i sistemi operativi. Nello specifico, il controllo dell'host aiuta ad adempiere ai requisiti PCI DSS 6 e 11.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

##### Tecnologie disponibili

Microsoft offre una serie di tecnologie che, utilizzate in combinazione o singolarmente, permettono di creare soluzioni di controllo dell'host. Come per le altre soluzioni tecnologiche, la progettazione di queste soluzioni deve essere finalizzata all'osservanza dei requisiti PCI DSS e di qualsiasi altro obbligo normativo applicabile all'organizzazione.

-   **Microsoft Baseline Security Analyzer (MBSA)**. Uno degli strumenti più validi per valutare i rischi per i dati sui titolari di carta è MBSA. MBSA è uno strumento di facile uso che permette di identificare i più comuni errori di configurazione della protezione in una serie di prodotti Microsoft, tra cui il sistema operativo Microsoft Windows, Internet Information Services, SQL Server, Internet Explorer e Microsoft Office. MBSA è anche in grado di rilevare gli aggiornamenti cumulativi, i service pack pubblicati in Microsoft Update e gli aggiornamenti della protezione mancanti. MBSA può essere eseguito dal prompt dei comandi o dalla sua GUI e può essere utilizzato con Microsoft Update e Windows Server Update Services. Considerata l'importanza di tenere sempre aggiornati i sistemi per garantire la massima protezione dei dati sui titolari di carta, MBSA può rivelarsi uno strumento molto prezioso per la valutazione dei rischi dell'organizzazione.

-   **Microsoft Windows Server Update Services**.** **Microsoft Windows Server Update Services (WSUS) con Service Pack 1 consente a un'organizzazione di distribuire molti degli ultimi aggiornamenti dei prodotti Microsoft, pubblicati sul sito Microsoft Update. WSUS è un componente di aggiornamento di Windows Server che offre un modo rapido e pratico per tenere i sistemi sempre aggiornati. Con WSUS, è possibile disporre di un'infrastruttura di gestione costituita da:

    -   **Microsoft Update**. Il sito Web di Microsoft a cui i componenti WSUS si connettono per gli aggiornamenti dei prodotti Microsoft.

    -   **Server Windows Server Update Services**. Il componente server che viene installato su un computer dotato di sistema operativo Microsoft Windows 2000 Server con Service Pack 4 (SP4) o Windows Server 2003 all'interno del firewall aziendale. Il server WSUS offre le funzioni di cui gli amministratori hanno bisogno per gestire e distribuire gli aggiornamenti con uno strumento basato sul Web, a cui è possibile accedere da Internet Explorer o da qualsiasi computer Windows della rete aziendale. Un server WSUS, inoltre, può essere utilizzato come origine degli aggiornamenti per altri server dello stesso tipo.

    -   **Aggiornamenti automatici**. Il componente client predefinito dei sistemi operativi Windows Vista, Windows Server 2003, Windows XP e Windows 2000 con Service Pack 3. Aggiornamenti automatici permette ai computer client e ai server di ricevere gli aggiornamenti da Microsoft Update o da un server con WSUS.

-   **Microsoft Systems Management Server**. Se l'organizzazione utilizza SMS per gestire i computer client e i server, è probabile che disponga già di alcuni degli strumenti necessari per valutare i rischi per i dati sui titolari di carta. Grazie a SMS, è possibile gestire in remoto le impostazioni di protezione dei computer con sistemi operativi Windows presenti sulle reti distribuite. È possibile sapere se sui computer della rete sono installati gli aggiornamenti software richiesti e tenere traccia dello stato di avanzamento degli aggiornamenti cumulativi su questi computer. Con SMS è possibile anche generare report che identificano l'inventario hardware e software completo, i dettagli di configurazione e lo stato dei computer della rete, nonché lo stato delle distribuzioni software e degli errori di distribuzione. Queste funzioni di SMS possono essere molto importanti ai fini della valutazione dei rischi per i dati sui titolari di carta dell'organizzazione.

-   **Microsoft Desktop Optimization Pack per Software Assurance**. Microsoft Desktop Optimization Pack per Software Assurance è un servizio di sottoscrizione che riduce i costi di distribuzione delle applicazioni, consente di fornire le applicazioni come servizi e ottimizza la gestione e il controllo degli ambienti desktop dell'azienda. Questo pacchetto di ottimizzazione del desktop rappresenta un'efficace soluzione di controllo dell'host che consente di:

    -   Semplificare e accelerare l'intero processo di gestione delle applicazioni, dalla pianificazione alla distribuzione, fino all'uso, alla manutenzione e alla migrazione del software.

    -   Migliorare la gestione delle risorse software dell'organizzazione.

    -   Accelerare e semplificare le distribuzioni e le migrazioni dei desktop.

#### Prevenzione del software dannoso

Le soluzioni di prevenzione del software dannoso sono fondamentali per la protezione dei dati sui titolari di carta nella rete. Impedendo l'invio di posta indesiderata e la diffusione di virus e spyware nei sistemi della rete, queste soluzioni assicurano che tali sistemi lavorino sempre al massimo della loro capacità e che i dati riservati non vengano involontariamente trasmessi a persone non autorizzate.

##### Requisiti PCI DSS adempiuti

Le soluzioni di prevenzione del software dannoso possono agevolare la conformità ai requisiti PCI DSS 5 e 6.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

##### Tecnologie disponibili

Microsoft offre una serie di tecnologie che, utilizzate in combinazione o singolarmente, permettono di prevenire il software dannoso. Queste tecnologie vanno considerate nel contesto di iniziative di più vasta portata sia per la conformità allo standard PCI DSS che per la conformità agli altri requisiti normativi.

-   **Microsoft Forefront™**. Forefront è una suite di prodotti specifici per settore per la protezione di sistemi operativi, server di applicazioni e perimetri di rete. Utilizzando Forefront in combinazione con l'infrastruttura IT già esistente, è possibile proteggere computer client e server da malware e altri attacchi dannosi provenienti sia dall'interno che dall'esterno dell'organizzazione.

-   **Strumento di rimozione malware**. Lo Strumento di rimozione malware controlla i computer che eseguono Windows XP, Windows 2000 e Windows Server 2003 per ricercare e rimuovere le infezioni causate dai più diffusi software dannosi. Al termine del processo di identificazione e rimozione, viene visualizzato un report nel quale vengono indicati gli eventuali software dannosi individuati e rimossi. Microsoft rilascia una versione aggiornata di questo strumento il secondo martedì di ogni mese e ogniqualvolta sia necessario per rispondere agli incidenti di protezione.

-   **Filtri di altri fornitori con Microsoft ISA Server**. Oltre a fornire soluzioni di protezione della rete, ISA Server aiuta a difendere l'organizzazione da attacchi tramite malware. A tale scopo, sono necessari filtri personalizzati o di altri fornitori che possano rimuovere il malware prima che raggiunga la rete aziendale.

    Per ulteriori informazioni, vedere Microsoft Internet Security & Acceleration Server all'indirizzo <http://www.microsoft.com/isaserver/default.mspx>.

#### Protezione delle applicazioni

Per ottenere la conformità ai requisiti PCI DSS, è necessario considerare le soluzioni di protezione delle applicazioni sotto due aspetti diversi. In primo luogo, è necessario richiedere che ogni nuova applicazione creata dagli sviluppatori dell'organizzazione sia conforme alle procedure di sviluppo di protezione. In secondo luogo, è necessario assicurarsi che vengano applicate le linee guida di protezione fornite con le applicazioni software acquistate da Microsoft o dagli altri fornitori.

#### Requisiti PCI DSS adempiuti

Lo sviluppo e la gestione di applicazioni protette, sia Web che basate su Windows, è un passo molto importante delle iniziative di conformità allo standard PCI DSS. In particolare, queste soluzioni tecnologiche agevolano la conformità al requisito 6.

Per il testo completo di questo requisito, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

#### Tecnologie disponibili

Microsoft offre assistenza e strumenti specifici per lo sviluppo di applicazioni protette. Inoltre, offre linee guida specifiche per l'uso sicuro dei principali prodotti server.

-   **Microsoft Visual Studio® 2005**. Visual Studio 2005 offre una serie di strumenti che aiutano gli sviluppatori a controllare le violazioni di protezione del codice nella fase di sviluppo di quest'ultimo:

    -   FxCop controlla il codice gestito alla ricerca di difetti, inclusi i difetti di protezione.

    -   PREfast è uno strumento di analisi statica per il codice C e C++. Grazie a questo strumento, gli sviluppatori sono in grado di rilevare una vasta gamma di problemi di protezione.

    -   Standard Annotation Language è un linguaggio che aiuta gli sviluppatori a identificare i bug di protezione non rilevabili dai compilatori di codice C o C++.

    -   Al momento di compilare codice non gestito scritto in C o C++, gli sviluppatori dovrebbero sempre eseguire la compilazione con la capacità di identificazione dei sovraccarichi dello stack /GS e collegare il codice con l'opzione /SafeESH.

    -   Gli sviluppatori RPC devono compilare il codice specificando il flag MIDL /robust.

-   **Microsoft Intelligent Application Gateway (IAG) 2007**. Nell'ambito di Microsoft Forefront Network Edge Security, IAG offre una VPN SSL (Secure Socket Layer), un firewall Web e la gestione della protezione degli endpoint per consentire funzioni di controllo dell'accesso, autorizzazione e ispezione dei contenuti per una vasta gamma di applicazioni di settore. La combinazione di queste tecnologie offre al personale che lavora in remoto o fuori ufficio un accesso flessibile e protetto da una varietà di dispositivi e postazioni tra cui chioschi, computer desktop e dispositivi mobili. IAG, inoltre, permette agli amministratori IT di applicare la conformità alle linee guida sull'uso delle informazioni e delle applicazioni per mezzo di un criterio di accesso remoto, personalizzato in base al dispositivo, all'utente, all'applicazione o ad altri criteri di business. I principali vantaggi includono:

    -   Una combinazione unica di accesso basato su VPN SSL, protezione integrata delle applicazioni e gestione della protezione degli endpoint.

    -   Un potente firewall per applicazioni Web in grado di tenere all'esterno il traffico dannoso e all'interno le informazioni riservate.

    -   La semplificazione della gestione dell'accesso protetto e della protezione delle risorse di business grazie a una piattaforma completa e facile da utilizzare.

    -   L'interoperabilità con l'infrastruttura di applicazioni Microsoft di base, i sistemi di livello aziendale di altri fornitori e gli strumenti personalizzati sviluppati internamente.

#### Linee guida

-   **Security Development Lifecycle**. Se l'organizzazione decide di sviluppare alcune delle sue soluzioni di gestione dei dati sui titolari di carta, dovrebbe considerare l'uso del processo Security Development Lifecycle creato da Microsoft per gli sviluppatori. Si tratta di un approccio completo allo sviluppo di applicazioni Web e desktop protette, da utilizzare nelle organizzazioni che elaborano e archiviano informazioni riservate quali i dati sui titolari di carta. Il processo Security Development Lifecycle inizia con la pianificazione di applicazioni protette, assicura che vengano adottate tecniche di codifica protette e include il test e la distribuzione sicuri delle applicazioni sviluppate.

-   **Le linee guida di protezione per i prodotti**. Microsoft offre linee guida di protezione per molti dei suoi prodotti software. Di particolare interesse per le organizzazioni di grandi e medie dimensioni sono le linee guida per Exchange Server, Systems Management Server ed SQL Server. Per informazioni sulle linee guida di protezione per questi prodotti, vedere la sezione relativa alla protezione delle applicazioni della [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true).

#### Messaggistica e collaborazione

Per osservare la conformità ai requisiti PCI DSS è necessario assicurarsi che il software di messaggistica e collaborazione utilizzato dall'organizzazione sia configurato e installato in modo protetto. Poiché le applicazioni di messaggistica e collaborazione sono diventate strumenti essenziali nel settore delle carte di pagamento, è fondamentale fare tutto il possibile per proteggere tutti i documenti e i messaggi e-mail che possono contenere dati sui titolari di carta.

#### Requisiti PCI DSS adempiuti

I comuni metodi di prevenzione delle violazioni di protezione dei messaggi includono i gateway di messaggistica, i server di messaggistica protetti e il filtraggio dei contenuti dei messaggi. Sia i gateway che il filtraggio instradano i messaggi a un'applicazione software specializzata. Questa applicazione può utilizzare una varietà di metodi per isolare specifiche stringhe di parole o di numeri, specifici schemi di parole o altri elementi, a seconda di come è stata progettata la soluzione. I messaggi che contengono queste parole o stringhe vengono messi in quarantena fino al controllo delle informazioni sospette oppure vengono semplicemente eliminate e cancellate. Questi metodi possono aiutare a proteggere i dati sui titolari di carta trasmessi tramite un messaggio e-mail o un documento in un ambiente di collaborazione. Tutte queste tecniche e soluzioni possono agevolare la conformità al requisito PCI DSS 4.

Per il testo completo di questo requisito, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

#### Tecnologie disponibili

Microsoft offre numerose soluzioni in grado di aiutare a proteggere il software di messaggistica e collaborazione. Ognuna di esse copre un diverso aspetto dell'organizzazione. La loro distribuzione deve essere organizzata in modo da lasciare il minor numero di vulnerabilità di protezione possibile una volta completata.

-   **Microsoft Exchange Server**. Come per la gestione dei documenti, Exchange può aiutare a definire potenti soluzioni di messaggistica nel pieno rispetto della protezione dei dati sui titolari di carta contenuti nei messaggi e-mail. Exchange Server 2007 include la messaggistica unificata, che consolida posta elettronica, posta vocale e fax in un'unica cartella Posta in arrivo. Inoltre, offre funzioni utili per applicare i criteri di conservazione, analizzare i messaggi in transito e adottare le azioni necessarie, registrare in modo flessibile il diario ed eseguire ricerche di testo elaborato in tutte le cassette postali implementate.
    Per ulteriori informazioni, vedere il sito Web di Microsoft Exchange Server all'indirizzo <http://www.microsoft.com/exchange/default.mspx>.

-   **Microsoft Forefront Security per Exchange Server**. Microsoft Forefront Security per Exchange Server aiuta a proteggere l'infrastruttura di posta elettronica da infezioni e tempi di inattività grazie a un approccio mirato all'uso di più livelli di difesa, all'ottimizzazione delle prestazioni e della disponibilità di Exchange Server e al controllo semplificato della gestione.

    -   **Protezione completa**. Microsoft Forefront Security per Exchange Server integra in un unica soluzione i motori di analisi delle aziende leader del settore della protezione e consente alle aziende di proteggere gli ambienti di messaggistica di Exchange da virus, worm e posta indesiderata.

    -   **Prestazioni ottimizzate**. Grazie alla perfetta integrazione con Exchange Server, le innovazioni dell'analisi e i controlli delle prestazioni, Forefront Security per Exchange Server consente di proteggere gli ambienti di messaggistica preservando il tempo di attività e ottimizzando le prestazioni del server.

    -   **Gestione semplificata.** Forefront Security per Exchange Server consente inoltre agli amministratori di gestire con facilità la configurazione e il funzionamento, gli aggiornamenti automatici delle firme del motore di analisi e il reporting a livello di server e di azienda.

-   **Microsoft Exchange Hosted Services**. Microsoft Exchange Hosted Services per la gestione e la protezione dei messaggi è composto da quattro diversi servizi che aiutano a tutelarsi dal malware proveniente dai messaggi e-mail, ottenere la conformità ai requisiti di conservazione, crittografare i dati per garantirne la riservatezza e preservare l'accesso alla posta elettronica durante e dopo le situazioni di emergenza. Questi servizi vengono distribuiti su Internet utilizzando un modello di "software come servizio", che aiuta a minimizzare il nuovo investimento, a liberare le risorse IT per farle concentrare su altre iniziative di generazione di valore e ad attenuare i rischi contenuti nei messaggi prima che raggiungano il firewall aziendale.

    Per ulteriori informazioni, vedere Microsoft Exchange Hosted Services (in inglese) all'indirizzo <http://www.microsoft.com/exchange/services/default.mspx>.

-   **Microsoft Office Information Right Management (IRM)**. Office è la migliore suite di applicazioni di produttività per le aziende. La funzione IRM di Microsoft Office consente di controllare l'accesso a informazioni riservate quali i dati sui titolari di carta.

    Nello specifico, la funzione IRM di Office aiuta a:

    -   Impedire ai destinatari non autorizzati di inoltrare, copiare, modificare, stampare, inviare tramite fax o tagliare e incollare informazioni protette per usi non consentiti.

    -   Impedire alle informazioni protette di essere copiate con la funzione STAMP di Windows.

    -   Mantenere lo stesso livello di protezione delle informazioni, indipendentemente dalla loro destinazione. Questa capacità è nota come protezione persistente.

    -   Offrire lo stesso livello di protezione agli allegati di posta elettronica, sempre che tali allegati siano file creati con altri programmi di Office, quali Excel o Word.

    -   Proteggere le informazioni contenute nei messaggi di posta elettronica o nei documenti con una data di scadenza, per impedire che le informazioni possano essere visualizzate dopo il periodo di tempo specificato.

    -   Applicare i criteri aziendali che governano l'uso e la distribuzione delle informazioni all'interno e all'esterno dell'azienda.

-   **Microsoft Windows SharePoint Services** **Information Rights Management (IRM)**. Come per le soluzioni di gestione dei documenti, SharePoint Services IRM può agevolare la conformità delle soluzioni di collaborazione ai requisiti PCI DSS. Questa tecnologia consente di creare un insieme persistente di controlli di accesso collegati non più a una specifica area della rete, ma ai contenuti. Questa capacità consente di controllare l'accesso anche ai file che non sono più soggetti al controllo diretto. IRM può essere utilizzato per i file ubicati nelle librerie di documenti e archiviati come allegati alle voci degli elenchi. Grazie a questa caratteristica, gli amministratori possono proteggere con IRM i download da una libreria di documenti. Se un utente cerca di scaricare un file dalla libreria, Windows SharePoint Services verifica che tale utente disponga delle autorizzazioni richieste per il file e rilascia all'utente una licenza che gli consente di accedere al file con il livello di autorizzazione adeguato. A questo punto, Windows SharePoint Services scarica il file sul computer dell'utente in un formato crittografato e protetto dai diritti necessari.

    Office IRM è basato sulla piattaforma Microsoft Windows Rights Management Services. Per abilitare questa funzione in Office, è necessario acquistare le licenze per il server RMS.

    Per ulteriori informazioni, vedere il sito Web di [Microsoft SharePoint](http://go.microsoft.com/fwlink/?linkid=12632) con i prodotti e le tecnologie SharePoint all'indirizzo <http://go.microsoft.com/fwlink/?linkid=12632>.

#### Classificazione e protezione dei dati

Le soluzioni di classificazione e protezione dei dati sono fondamentali per la conformità ai requisiti PCI DSS e la tutela dei dati sui titolari di carta. Queste soluzioni riguardano l'applicazione dei livelli di classificazione della protezione ai dati sui titolari di carta residenti nel sistema o in corso di trasmissione. Questa categoria di soluzioni riguarda anche la protezione dei dati in termini di riservatezza e integrità dei dati archiviati o trasmessi. I metodi di protezione maggiormente adottati dalle organizzazioni sono le soluzioni di crittografia.

#### Requisiti PCI DSS adempiuti

Le soluzioni di classificazione e protezione dei dati agevolano la conformità ai requisiti PCI DSS proteggendo i dati sui titolari di carta durante la loro permanenza in un database o mentre vengono trasmessi da un server all'altro o sulla rete, come succede quando un titolare di carta effettua un acquisto. L'uso di queste soluzioni agevola la conformità ai requisiti PCI DSS 3 e 7.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

#### Tecnologie disponibili

Microsoft offre una vasta gamma di tecnologie utili a classificare e proteggere i dati sui titolari di carta, sia mentre vengono trasmessi sulla rete, sia mentre vengono archiviati in un documento sul computer di un dipendente o in un database. Queste tecnologie includono:

-   **Crittografia unità BitLocker™**. La Crittografia unità BitLocker aiuta a proteggere i dati sui titolari di carta con le funzioni di crittografia delle unità e controllo dell'integrità dei componenti di tipo "early boot". La crittografia delle unità protegge i dati impedendo agli utenti non autorizzati di violare la protezione dei file e del sistema Windows su computer rubati o smarriti. Questa protezione viene ottenuta crittografando l'intero volume Windows. Con BitLocker, vengono crittografati tutti i file: file utente, file di sistema, file di scambio e file ibernazione. Il controllo dell'integrità dei componenti early boot assicura che la decrittografia dei dati venga eseguita solo se tali componenti non sono stati toccati e l'unità crittografata si trova sul computer originale. BitLocker è disponibile in Windows Vista Enterprise e Ultimate, nonché in Windows Server "Longhorn".

-   **Windows Encrypting File System (EFS).** EFS fornisce la tecnologia di crittografia di base utilizzata per archiviare i file crittografati nei volumi dei file system NTFS. Le cartelle e i file crittografati possono essere utilizzati allo stesso modo degli altri file e cartelle.

    La crittografia è trasparente per l'utente che ha crittografato il file. L'utente, pertanto, non deve decrittografare manualmente il file prima di poterlo utilizzare. Il file può essere aperto e modificato come un normale file.

-   **Microsoft Windows Rights Management Services**. Microsoft Windows Rights Management Services (RMS) è una piattaforma software che aiuta le applicazioni a proteggere i dati sui titolari di carta da usi non autorizzati, sia online che offline, sia l'interno che all'esterno del firewall.

    Con RMS, è possibile integrare la strategia di protezione dell'organizzazione proteggendo le informazioni con criteri di utilizzo permanenti che accompagnano sempre le informazioni, indipendentemente dalla loro destinazione. È possibile utilizzare applicazioni abilitate a RMS per gestire, controllare e verificare l'accesso ai documenti che contengono dati sui titolari di carta. Il client RMS è integrato nel sistema operativo Windows Vista. Per le altre versioni di Windows, questo client è disponibile come download gratuito.
    Per ulteriori informazioni, vedere [Windows Rights Management Services](http://www.microsoft.com/rms) all'indirizzo <http://www.microsoft.com/rms>.

-   **Crittografia di Microsoft SQL Server**. Quando i dati sui titolari di carta vengono archiviati in SQL Server, questo crittografa i dati utilizzando un'infrastruttura di gestione delle chiavi e una crittografia di tipo gerarchico. Ogni livello crittografa il livello immediatamente subordinato utilizzando una combinazione di certificati, chiavi asimmetriche e chiavi simmetriche. Esistono una chiave master per lo stesso SQL Server e una chiave distinta per ogni database presente nell'istanza di SQL Server. In questo modo, l'archivio dei dati sui titolari di carta dell'organizzazione è più protetto.

#### Gestione delle identità

La gestione delle identità è un altro elemento fondamentale per la conformità allo standard PCI DSS. Le soluzioni di gestione delle identità consentono di limitare il personale autorizzato ad accedere, elaborare e trasmettere i dati sui titolari di carta. L'organizzazione può utilizzare queste soluzioni per semplificare la gestione delle autorizzazioni e delle identità digitali di dipendenti, clienti e partner.

#### Requisiti PCI DSS adempiuti

L'uso delle soluzioni di gestione delle identità agevola la conformità al requisito PCI DSS 8, poiché permette di creare e assegnare un ID univoco a ogni persona dell'organizzazione che dispone dell'accesso a un computer. Queste soluzioni aiutano anche a limitare l'accesso ai dati sui titolari di carta in base all'ID univoco, come richiesto dal requisito PCI DSS 7.

Per il testo completo di questo requisito, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

#### Tecnologie disponibili

Microsoft offre numerose tecnologie in grado di aiutare la conformità ai requisiti di gestione delle identità.

-   **Microsoft Active Directory**. Active Directory supporta una serie di tecniche per il controllo del personale che può accedere ai dati sui titolari di carta sulla rete e all'esterno di questa. In primo luogo, Active Directory supporta l'autenticazione Kerberos, una delle tecniche di autenticazione predefinite di Windows. L'autenticazione Kerberos si basa su uno standard industriale che favorisce l'interoperabilità. Il controller di dominio Active Directory gestisce gli account utente e le informazioni di accesso per supportare il servizio Kerberos. In secondo luogo, Active Directory supporta l'autenticazione smart card. È possibile richiedere agli utenti remoti o agli amministratori dei sistemi contenenti dati sui titolari di carta l'uso di una smart card e di un PIN per accedere alla rete. In terzo luogo, Active Directory supporta il roaming delle credenziali, un servizio che permette agli utenti che devono utilizzare più computer di utilizzare le stesse credenziali per ognuno di essi. In quarto luogo, Active Directory consente all'organizzazione di personalizzare i fornitori di credenziali utilizzati per autenticare gli utenti. Queste funzioni permettono di ottenere un controllo granulare sulle modalità di concessione degli account Active Directory che possono accedere ai dati sui titolari di carta e sugli account a cui è stato fornito tale accesso.

-   **Microsoft Active Directory Federation Services**. Grazie ad Active Directory Federation Services (ADFS), è possibile creare soluzioni di gestione delle identità che si estendono oltre i tradizionali confini della foresta Active Directory. Utilizzando ADFS, l'organizzazione può estendere la sua infrastruttura Active Directory per fornire l'accesso alle risorse messe a disposizione su Internet dai partner trusted. I partner trusted possono includere terze parti esterne o altri reparti o filiali della stessa organizzazione.

<ul>
<li>
**Microsoft Identity Lifecycle Manager**. Microsoft Identity Lifecycle Manager (ILM) semplifica il processo di associazione e gestione dei record delle identità dei vari repository di dati e impedisce anomalie quali la presenza di record attivi per i dipendenti che non fanno più parte dell'organizzazione. ILM offre un framework di criteri per il controllo e la traccia dei dati relativi a identità e accesso, aiutando a gestire meglio la conformità. In più, con i suoi strumenti di self-help per gli utenti finali, contribuisce ad aumentare l'efficienza del reparto IT che può delegare a questi utenti molte attività, in piena sicurezza. Un'altra funzione chiave di ILM è una soluzione di gestione dei certificati basati su Windows che si integra con il sistema operativo Windows Server 2003 e con Active Directory per dare vita a una soluzione "chiavi in mano" di gestione del ciclo di vita end-to-end di smart card e certificati digitali per l'Autorità di certificazione di Windows Server 2003.

</li>
ILM consente di:

-   Sincronizzare le informazioni sulle identità in una varietà di archivi di identità eterogenei di tipo directory e non-directory. Ciò consente di automatizzare il processo di aggiornamento di queste informazioni su più piattaforme diverse mantenendo, al contempo, l'integrità e la proprietà dei dati in tutta l'azienda.

-   Eseguire il provisioning e il deprovisioning degli account utente e delle informazioni sulle identità, quali dati di distribuzione, account di posta elettronica e gruppi di protezione, su vari sistemi e piattaforme. È possibile creare rapidamente nuovi account per i dipendenti in base a eventi o modifiche negli archivi rilevanti come, ad esempio, il sistema di gestione delle risorse umane. È anche possibile eseguire immediatamente da questo tipo di sistemi il deprovisioning dei dipendenti che lasciano l'azienda.

-   Gestire certificati e smart card. ILM include una soluzione basata su flusso di lavoro e criteri che consente di gestire facilmente il ciclo di vita di certificati digitali e smart card. ILM si avvale dei servizi e dei servizi certificati di Active Directory per eseguire il provisioning dei certificati digitali e delle smart card, con un flusso di lavoro automatizzato che gestisce l'intero ciclo di vita delle credenziali basate sui certificati. ILM riduce notevolmente i costi associati a certificati digitali e smart card permettendo alle organizzazioni di ottimizzare la distribuzione, la gestione e la manutenzione dell'infrastruttura basata sui certificati. Inoltre, semplifica il provisioning, la configurazione e la gestione di certificati digitali e smart card aumentando allo stesso tempo il livello di protezione, grazie a una tecnologia di autenticazione robusta e multifattoriale.

Per ulteriori informazioni, vedere la home page di Microsoft Identity Lifecycle Manager (in inglese) all'indirizzo <http://www.microsoft.com/windowsserver/ilm2007/default.mspx>.

<li>
**Microsoft SQL Server**. SQL Server può essere utilizzato in combinazione con altre tecnologie per ottenere soluzioni di gestione delle identità. Utilizzare i database SQL Server per l'archiviazione delle informazioni su nomi utente e password e per il mapping tra certificati e account utente o altre soluzioni. Utilizzando SQL Server con Microsoft ILM, Active Directory, Criteri di gruppo e ACL è possibile limitare l'accesso degli utenti ai dati sui titolari di carta archiviati in altri database, documenti o directory.

</li>
Per ulteriori informazioni, vedere Microsoft SQL Server 2005 all'indirizzo <http://www.microsoft.com/sql/default.mspx>.

</ul>
#### Funzioni di supporto del sistema operativo

-   **Infrastruttura a chiave pubblica (PKI)**. L'infrastruttura a chiave pubblica è un sistema di certificati digitali, Autorità di certificazione (CA) e altre autorità di registrazione che verifica e autentica la validità di ogni parte implicata in una transazione elettronica mediante l'utilizzo della crittografia a chiave pubblica. Questa infrastruttura consente di applicare una robusta protezione ai dati sui titolari di carta che vengono scambiati su Internet, extranet, intranet e applicazioni.

#### Autenticazione, autorizzazione e controllo di accesso

L'autenticazione è il processo di identificazione degli utenti. Negli ambienti IT, l'autenticazione richiede in genere l'uso di un nome utente e di una password, ma può richiedere anche altri metodi per dimostrare l'identità, ad esempio smart card, analisi della retina, riconoscimento vocale o impronte digitali. L'autorizzazione deve stabilire se l'identità autenticata è autorizzata ad accedere alle risorse richieste. L'accesso può essere concesso o negato in base a una serie di criteri che vanno dall'indirizzo di rete del client all'ora del giorno o al tipo di browser utilizzato.

Nella pianificazione della strategia per l'autenticazione, l'autorizzazione e il controllo di accesso, è necessario integrare anche una strategia per concedere agli account utente le autorizzazioni per le risorse della rete. Per ulteriori informazioni, vedere [*Applicazione del principio del privilegio minimo agli account utente in Windows XP*](http://www.microsoft.com/technet/prodtechnol/winxppro/maintain/luawinxp.mspx).

#### Requisiti PCI DSS adempiuti

Autenticazione, autorizzazione e controllo di accesso sono elementi chiave della strategia di protezione dei dati sui titolari di carta, soprattutto in combinazione con le soluzioni di classificazione e protezione dei dati e di gestione delle identità. In questo contesto, le soluzioni di autenticazione, autorizzazione e controllo di accesso possono agevolare la conformità ai requisiti PCI DSS 6, 7 e 8.

Per il testo completo di ognuno di questi requisiti, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

#### Tecnologie disponibili

Microsoft offre diverse tecnologie che possono aiutare a creare e integrare le strategie di autenticazione, autorizzazione e controllo di accesso in una soluzione completa per la conformità allo standard PDI DSS.

-   **Microsoft Active Directory**. Il servizio Active Directory di Microsoft Windows 2000 Server, Windows Server 2003 e Windows Server "Longhorn" è dedicato principalmente all'autenticazione, all'autorizzazione e al controllo di accesso. Ad esempio, Active Directory supporta l'autenticazione Kerberos, una delle tecniche di autenticazione predefinite di Windows. L'autenticazione Kerberos si basa su uno standard industriale che favorisce l'interoperabilità. Il controller di dominio Active Directory gestisce gli account utente e le informazioni di accesso per supportare il servizio Kerberos. Inoltre, Active Directory supporta l'autenticazione smart card. È possibile richiedere agli utenti remoti o agli amministratori dei sistemi contenenti dati sui titolari di carta l'uso di una smart card e di un PIN per accedere alla rete. Active Directory supporta il roaming delle credenziali, un servizio che permette agli utenti che devono utilizzare più computer di utilizzare le stesse credenziali per ognuno di essi. Active Directory consente all'organizzazione di personalizzare i fornitori di credenziali utilizzati per autenticare gli utenti. In più, Active Directory permette di delegare le varie attività amministrative all'interno dell'azienda. Queste funzioni permettono di ottenere un controllo granulare sulle modalità di concessione degli account Active Directory che possono accedere ai dati sui titolari di carta e sugli account a cui è stato fornito tale accesso.

-   **Servizio di autenticazione Internet (IAS)**. IAS è l'implementazione Microsoft di un server e di un proxy RADIUS (Remote Authentication Dial-In User Service). In qualità di server RADIUS, IAS gestisce l'autenticazione centralizzata delle connessioni, l'autorizzazione e l'accounting per vari tipi di accesso alla rete, incluse le connessioni wireless e VPN. In qualità di proxy RADIUS, IAS inoltra i messaggi di autenticazione e accounting agli altri server RADIUS. Questa procedura consente a IAS di eseguire i passaggi di autenticazione delle connessioni remote prima che queste possano raggiungere la rete dell'organizzazione. Con le credenziali fornite dagli utenti per la connessione remota, è possibile autorizzare questi ultimi ad accedere solo alle risorse della rete di cui hanno bisogno per eseguire il proprio lavoro.

#### Funzioni di supporto del sistema operativo

-   **Uso degli elenchi di controllo di accesso (ACL) per concedere le autorizzazioni per le risorse**. Un ACL è un meccanismo utilizzato dai sistemi operativi successivi a Microsoft Windows NT per proteggere risorse quali file o cartelle. Gli ACL contengono diverse ACE, ovvero voci di controllo di accesso, che associano un'entità (costituita solitamente da un account utente o da un gruppo di account) a una regola che governa l'uso della risorsa. ACL e ACE permettono di concedere o negare diritti sulle risorse in base alle autorizzazioni che possono essere associate agli account utente. Ad esempio, è possibile creare un'ACE e applicarla all'ACL di un file per impedire a chiunque la lettura del file, a eccezione dell'amministratore. Questa tecnologia va utilizzata nell'ambito della soluzione generale di gestione delle identità, ma resta un ottimo metodo per limitare l'accesso ai dati sui titolari di carta alle sole persone che ne hanno bisogno per poter eseguire il proprio lavoro.

-   **Windows Firewall in Microsoft Windows Vista e Windows Server "Longhorn"**. Come già indicato, Windows Firewall su Windows Vista e Windows Server "Longhorn" può aiutare a proteggere sistemi e reti da attacchi dannosi. Inoltre, permette di controllare quali utenti, computer o gruppi possono accedere alle risorse di un computer o di un dominio. Utilizzando Windows Firewall con protezione avanzata è possibile creare regole per filtrare le connessioni di utenti, computer o gruppi Active Directory. Per creare questo tipo di regole, è necessario proteggere la connessione con IPsec utilizzando credenziali contenenti informazioni sugli account Active Directory, ad esempio Kerberos versione 5.

Per i collegamenti a informazioni concettuali e guide alla pianificazione di autenticazione, autorizzazione e controllo di accesso, vedere la sezione relativa a queste tre voci nella [*The Regulatory Compliance Planning Guide*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true).

#### Identificazione delle vulnerabilità

Le soluzioni di identificazione delle vulnerabilità offrono strumenti per il test delle vulnerabilità nei sistemi informativi. Il personale IT deve conoscere le vulnerabilità dell'ambiente IT per poterle correggere. L'identificazione delle vulnerabilità implica anche la capacità di ripristinare i dati perduti a causa di errori involontari degli utenti.

#### Requisiti PCI DSS adempiuti

Le soluzioni di vulnerabilità agevolano la conformità al requisito PCI DSS 11, che richiede l'esecuzione regolare di test dei sistemi e delle procedure di protezione.

Per il testo completo di questo requisito, vedere lo standard [*Payment Card Industry Data Security Standard,* *versione 1.1*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf).

#### Tecnologie disponibili

Microsoft offre una serie di soluzioni che facilitano la progettazione delle soluzioni di identificazione delle vulnerabilità necessarie per la conformità ai requisiti PCI DSS.

-   **Microsoft Baseline Security Analyzer (MBSA)**. Altrettanto importante della valutazione dei rischi nella progettazione dei controlli di protezione dei dati sui titolari di carta, MBSA consente di esaminare periodicamente le vulnerabilità che possono compromettere la protezione dei dati sui titolari di carta. MBSA permette di identificare i più comuni errori di configurazione della protezione in una serie di prodotti Microsoft, tra cui il sistema operativo Microsoft Windows, Internet Information Services, SQL Server, Internet Explorer e Microsoft Office. MBSA è anche in grado di rilevare gli aggiornamenti cumulativi, i service pack pubblicati in Microsoft Update e gli aggiornamenti della protezione mancanti. MBSA può essere eseguito dal prompt dei comandi o dalla sua GUI e può essere utilizzato con Microsoft Update e Windows Server Update Services. Considerata l'importanza di tenere sempre aggiornati i sistemi in uso per garantire la massima protezione dei dati sui titolari di carta, MBSA può rivelarsi uno strumento molto prezioso per capire se le installazioni dei prodotti hanno causato nel tempo alcune vulnerabilità per questi dati.

#### Monitoraggio, controllo e reporting

Le soluzioni di monitoraggio e reporting raccolgono e controllano i registri generati a seguito delle attività di autenticazione e accesso ai sistemi. È possibile progettare queste soluzioni in modo che raccolgano informazioni specifiche in base allo standard PCI DSS oppure in modo che utilizzino i registri predefiniti dei sistemi operativi e dei pacchetti software in uso.

Una sottocategoria delle attività di monitoraggio e reporting è la raccolta, l'analisi e la correlazione di tutti i dati registrati nell'organizzazione. Queste attività possono essere svolte per mezzo di una soluzione di tipo dashboard, che permette di analizzare meglio le varie informazioni raccolte. Questo tipo di soluzione permette al personale che gestisce l'IT di comprendere con maggiore chiarezza le correlazioni tra gli eventi.

#### Requisiti PCI DSS adempiuti

Le soluzioni di monitoraggio, controllo e reporting possono agevolare la conformità al requisito PCI DSS 10, che richiede di registrare e monitorare tutti gli accessi alle risorse di rete e ai dati sui titolari di carta.

#### Tecnologie disponibili

Microsoft offre numerose tecnologie che permettono di monitorare l'accesso alla rete e l'accesso ai dati sui titolari di carta.

-   **Microsoft System Center Operations Manager Audit Collection**. Operations Manager 2007 è in grado di estrarre e raccogliere con la massima sicurezza ed efficienza i registri di protezione dei sistemi operativi Windows, nonché di archiviare questi registri per le successive attività di analisi e reporting. I registri estratti vengono archiviati in un apposito database di raccolta controlli. Operations Manager provvede all'invio dei report da utilizzare per i dati di Audit Collection. Audit Collection può essere utilizzato per generare vari report di conformità, quali quelli necessari per i controlli di conformità al Sarbanes-Oxley Act. Audit Collection può essere utilizzato anche per l'analisi della protezione, ad esempio per rilevare le intrusioni o i tentativi di accesso non autorizzato.

-   **Infrastruttura di registrazione eventi di Microsoft Windows Vista**. Grazie ai miglioramenti apportati all'infrastruttura di registrazione eventi, il desktop di Windows Vista è ancora più facile da gestire e monitorare e offre informazioni ancora più utili per la risoluzione dei problemi. I rigidi standard adottati assicurano che gli eventi siano significativi, correggibili e ben documentati. Molti dei componenti che nelle versioni precedenti di Windows archiviavano i dati di registrazione in appositi file di testo possono ora aggiungere gli eventi nel registro eventi. Grazie all'inoltro degli eventi, gli amministratori possono gestire centralmente questi ultimi da un qualsiasi computer della rete. In questo modo possono identificare i problemi in modo proattivo e correlare i problemi che riguardano più computer. Il Visualizzatore eventi, poi, è stato completamente riprogettato e ora permette di creare visualizzazioni personalizzate, associare facilmente eventi e attività e, infine, visualizzare in remoto i registri di altri computer. Gli amministratori possono quindi utilizzare in modo più pratico il registro eventi per risolvere il problemi degli utenti.

-   **Microsoft SQL Server**. SQL Server Reporting Services è una soluzione completa, basata su server, che consente la creazione, la gestione e la consegna sia dei tradizionali report cartacei, sia dei report interattivi basati sul Web. Come parte integrante del framework di business intelligence di Microsoft, Reporting Services combina le funzionalità di gestione dei dati di SQL Server e Microsoft Windows Server con alcune famose e potenti applicazioni di Microsoft Office per distribuire in tempo reale le informazioni necessarie per le operazioni di routine e il processo decisionale. Questi servizi possono essere utilizzati per generare report di analisi dei dati sui titolari di carta e registrare le modifiche a questi ultimi. Oppure, possono essere utilizzati per monitorare con facilità i modelli di utilizzo della rete e il flusso delle informazioni.

#### Funzioni di supporto del sistema operativo

-   **Elenchi di controllo accesso di sistema (SACL) NTFS**. L'organizzazione può utilizzare i SACL NTFS per file e directory per tenere traccia delle modifiche apportate ai file e alle cartelle di un sistema. Una volta impostato un SACL su un file o una cartella, ogni volta che viene eseguita un'azione su uno di questi elementi, il SACL indica al sistema operativo Windows di registrare l'azione e l'utente che l'ha eseguita. I SACL non possono essere impostati sui sistemi formattati con il file system FAT, quindi è necessario utilizzare il file system NTFS su tutti i volumi che contengono dati sugli utenti e dati sui titolari di carta.

#### Gestione delle soluzioni tecnologiche PCI DSS

Per quanto non agevoli la conformità a specifici requisiti PCI DSS, l'uso di prodotti di gestione aiuta a tenere traccia dei controlli IT implementati a tal fine. Nella creazione di un framework di controlli IT, è sempre importante la capacità di gestire centralmente questi controlli riducendo al minimo i desk di amministrazione utilizzati.

#### Tecnologie disponibili

Microsoft offre due strumenti principali per la gestione del framework di controlli IT implementato per la conformità allo standard PCI DSS e agli altri requisiti normativi.

-   **Microsoft Forefront**. Microsoft Forefront è una suite di prodotti specifici per settore per la protezione di sistemi operativi client, server di applicazioni e perimetri di rete. Utilizzando Forefront in combinazione con l'infrastruttura IT già esistente, è possibile proteggere computer client e server da malware e altri attacchi dannosi, il tutto tramite la facile integrazione con server di applicazioni quali Exchange, SharePoint e server di Messaggistica immediata. Forefront può essere facilmente integrato con Active Directory e interagisce con questo servizio tramite ISA Server per supportare smart card, RADIUS e DHCP. In più, Forefront offre uno strumento di gestione centralizzato che consente l'uso di un'unica postazione di reporting e di un'unica postazione di applicazione delle misure di controllo dei criteri.

-   **Microsoft System Center**. La famiglia di prodotti Microsoft System Center ha lo scopo di dotare l'organizzazione di tutti gli strumenti necessari per automatizzare la gestione dei sistemi. System Center include tecnologie per l'automazione delle più comuni attività di gestione e strumenti che permettono al personale IT di rilevare, diagnosticare e correggere i problemi dell'ambiente informatico. Nello specifico, System Center offre prodotti in grado di svolgere le seguenti funzioni:

    -   Monitorare l'hardware e il software di un ambiente distribuito per rilevare i problemi e fornire gli strumenti necessari per risolverli.

    -   Automatizzare il processo di installazione, aggiornamento e correzione del software.

    -   Provvedere alle implementazioni dei processi standard di gestione dei sistemi.

    -   Gestire le attività di backup e ripristino dei dati del file server Windows.

    -   Soddisfare i requisiti di monitoraggio e configurazione delle organizzazioni di piccole dimensioni.

    -   Gestire le macchine virtuali. Il fatto che un hardware più veloce consenta l'esecuzione di più applicazioni sulla stessa macchina sta spingendo le organizzazioni a utilizzare sempre di più la virtualizzazione per isolare tali applicazioni.

    -   Ottenere installazioni appropriatamente dimensionate grazie a strumenti per la stima delle risorse richieste.

Questa sezione offre una descrizione delle soluzioni tecnologiche che un'organizzazione può utilizzare per ottenere e mantenere la conformità allo standard PCI DSS. Illustra i motivi per cui queste soluzioni sono importanti e offre i collegamenti alle soluzioni di assistenza e tecnologia Microsoft che agevolano la conformità alle normative.

L'implementazione di queste soluzioni non solo fornisce gli standard di protezione e conformità per l'ambiente IT, ma migliora i processi di business dell'organizzazione. Prima di implementare una delle soluzioni identificate, è necessario richiedere un parere ai propri revisori e consulenti legali in merito ai requisiti di conformità specifici per l'organizzazione e considerare attentamente l'impatto di queste soluzioni a tutti i livelli dell'organizzazione, non solo a livello di conformità. Microsoft offre informazioni e soluzioni per la conformità allo standard PCI DSS e agli altri obblighi normativi. Tuttavia, per ottenere informazioni complete su questo argomento importante e complesso, è consigliabile consultare anche altre fonti pubbliche.

[![](images/Bb821241.arrow_px_up(it-it,TechNet.10).gif)](#mainsection)[Top Of Page](#mainsection)

### Appendici

Questa sezione contiene le domande frequenti dei clienti sulle soluzioni tecnologiche Microsoft e sulle loro modalità di utilizzo ai fini della conformità ai requisiti PCI DSS. Inoltre, contiene una mappa delle soluzioni che possono aiutare le organizzazioni ad adempiere a questi requisiti.

#### Domande frequenti

**D: Perché è necessario occuparsi della conformità allo standard PCI DSS? Si tratta solo di un altro standard costoso e inutile?**

R: Ci sono tre buoni motivi per cui un'organizzazione dovrebbe intraprendere le iniziative adeguate per ottenere la conformità allo standard PCI DSS. Il primo è che alcune aziende di carte di credito, ad esempio Visa, prevedono ormai incentivi finanziari per chi osserva la conformità PCI e penalizzazioni per chi invece non lo fa. Il secondo è che la conformità aiuta a mitigare la responsabilità in caso di perdita dei dati. Il terzo è che, grazie a un'analisi approfondita e a una buona progettazione dei sistemi, il processo di conformità può costituire un aiuto reale per migliorare la registrazione dei dati sui clienti e, di conseguenza, aumentare la qualità dell'assistenza ai clienti e il livello di soddisfazione di questi ultimi.

**D: Microsoft non corre il rischio di sembrare troppo aggressiva nella vendita delle sue tecnologie per la conformità allo standard PCI DSS?**

R: Sapendo bene che la situazione di ogni organizzazione è unica, Microsoft ha creato questa guida con lo scopo di fornire informazioni il più possibile complete. Microsoft è in grado di sviluppare linee guida specifiche per i settori verticali. Per domande particolari, è possibile contattare direttamente i rappresentanti di vendita Microsoft. Come spiegato in precedenza, è possibile ottenere risultati di business migliori se si guarda al progetto di conformità anche come opportunità per migliorare il controllo e la gestione delle informazioni sui clienti.

**D: Questo documento descrive molte tecnologie utili per la conformità allo standard PCI DSS,** **ma poche soluzioni di conformità. Perché?**

R: Ogni situazione è unica, quindi non è possibile offrire una sola soluzione valida per tutti i contesti. Come spiegato nel riepilogo, però, Microsoft può fornire a ogni organizzazione informazioni più dettagliate.

**D: Cosa può fare Microsoft per aiutare un'organizzazione a ottenere la certificazione PCI DSS?**

R: Microsoft offre software e servizi in grado di aiutare le organizzazioni ad adempiere ai requisiti PCI DSS, ma non può garantire l'ottenimento della conformità da parte di queste aziende. In qualità di fornitore, Microsoft ha tutto l'interesse ad aiutare le organizzazioni ad adempiere a questi requisiti, tuttavia, ai fini della conformità, vanno valutate le organizzazioni, i loro revisori e le aziende di carte di credito con cui le organizzazioni lavorano.

**D: Il testo della Sezione 3.4.1 significa che le tecnologie di protezione di Microsoft non possono essere utilizzate?**

R: No. Il testo completo di questa sezione afferma quanto segue:

"Se viene utilizzata la crittografia dei dischi al posto della crittografia dei database a livello di file o di colonna, l'accesso logico deve essere gestito in modo indipendente dai meccanismi di controllo dell'accesso del sistema operativo nativo (ad esempio, evitando di utilizzare gli account del sistema locale o di Active Directory). Le chiavi di decrittografia non devono essere collegate agli account utente."

Le tecnologie di protezione dei dati di Microsoft non collegano le chiavi di decrittografia agli account utente. Ad esempio, la Crittografia unità BitLocker non associa mai queste chiavi (che possono essere costituite dai PIN o dalle password di ripristino) agli account utente di Active Directory. Anche Encrypting File System (EFS) non collega mai le chiavi di decrittografia agli account utente. L'organizzazione può revocare a una persona l'autorizzazione a decrittografare un documento senza dover modificare i privilegi di accesso. In alcune configurazioni, EFS tenta di ottimizzare l'esperienza utente inserendo automaticamente alcune chiavi di decrittografia nei profili di particolari utenti. Questo comportamento, tuttavia, può essere cambiato modificando la configurazione.

#### Requisiti PCI DSS e soluzioni tecnologiche associate

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Requisito</th>
<th style="border:1px solid black;" >Sezioni relative alle soluzioni tecnologiche</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Requisito 1</td>
<td style="border:1px solid black;"><a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_network_security">Protezione della rete</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Requisito 2</td>
<td style="border:1px solid black;"><a href="#_network_security">Protezione della rete</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Requisito 3</td>
<td style="border:1px solid black;"><a href="#_document_management">Gestione dei documenti</a>; <a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_data_classification_and_protection">Classificazione e protezione dei dati</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Requisito 4</td>
<td style="border:1px solid black;"><a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_messaging_and_collaboration">Messaggistica e collaborazione</a>; <a href="#_data_classification_and_protection">Classificazione e protezione dei dati</a>; <a href="#_network_security">Protezione della rete</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Requisito 5</td>
<td style="border:1px solid black;"><a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_malicious_software_prevention">Prevenzione del software dannoso</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Requisito 6</td>
<td style="border:1px solid black;"><a href="#_document_management">Gestione dei documenti</a>; <a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_change_management">Gestione dei cambiamenti</a>; <a href="#_host_control">Controllo dell'host</a>; <a href="#_malicious_software_prevention">Prevenzione del software dannoso</a>; <a href="#_application_security">Protezione delle applicazioni</a>; <a href="#_authentication,_authorization,_and_">Autenticazione, autorizzazione e controllo di accesso</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Requisito 7</td>
<td style="border:1px solid black;"><a href="#_document_management">Gestione dei documenti</a>; <a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_identity_management">Gestione delle identità</a>; <a href="#_authentication,_authorization,_and_">Autenticazione, autorizzazione e controllo di accesso</a>; <a href="#_data_classification_and_protection">Classificazione e protezione dei dati</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Requisito 8</td>
<td style="border:1px solid black;"><a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_authentication,_authorization,_and_">Autenticazione, autorizzazione e controllo di accesso</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Requisito 9</td>
<td style="border:1px solid black;"><a href="#_document_management">Gestione dei documenti</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Requisito 10</td>
<td style="border:1px solid black;"><a href="#_document_management">Gestione dei documenti</a>; <a href="#_change_management">Gestione dei cambiamenti</a>; <a href="#_monitoring,_auditing,_and_reporting">Monitoraggio, controllo e reporting</a>; <a href="#_network_security">Protezione della rete</a></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Requisito 11</td>
<td style="border:1px solid black;"><a href="#_risk_assessment">Valutazione dei rischi</a>; <a href="#_host_control">Controllo dell'host</a>; <a href="#_vulnerability_identification">Identificazione delle vulnerabilità</a></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Requisito 12</td>
<td style="border:1px solid black;"><a href="#_document_management">Gestione dei documenti</a></td>
</tr>
</tbody>
</table>
  
#### Altre risorse
  
[*The Payment Card Industry Data Security Standard,* *versione 1.1 (in inglese)*](https://www.pcisecuritystandards.org/pdfs/pci_dss_v1-1.pdf)
  
[*The Regulatory Compliance Planning Guide (in inglese)*](http://www.microsoft.com/technet/security/guidance/complianceandpolicies/compliance/rcguide/default.mspx?mfr=true)
  
[*The PCI DSS Self-Assessment Questionnaire (in inglese)*](https://www.pcisecuritystandards.org/pdfs/pci_saq_v1-0.pdf)
  
[*The PCI DSS QSA Audit Procedures (in inglese)*](https://www.pcisecuritystandards.org/pdfs/pci_audit_procedures_v1-1.pdf)
  
[*The PCI DSS ASV Scanning Procedures (in inglese)*](https://www.pcisecuritystandards.org/pdfs/pci_scanning_procedures_v1-1.pdf)** **
  
[*Applicazione del principio del privilegio minimo agli account utente in Windows XP*](http://www.microsoft.com/technet/prodtechnol/winxppro/maintain/luawinxp.mspx)* *
  
[*Best Practices for Delegating Active Directory Administration (in inglese)*](http://www.microsoft.com/downloads/details.aspx?familyid=631747a3-79e1-48fa-9730-dae7c0a1d6d3&displaylang=en)
  
[Download dell'Industry Center Banking (in inglese*)*](http://msdn2.microsoft.com/en-us/architecture/86e3451d-8219-46af-bf99-4a610e4bf1f4.aspx)
  
#### Commenti
  
Inviare quesiti e commenti su questa guida all'indirizzo <cisfdbk@microsoft.com>.
  
[![Top Of Page](images/Bb821241.arrow_px_up(it-it,TechNet.10).gif)](#mainsection)[Top Of Page](#mainsection)
