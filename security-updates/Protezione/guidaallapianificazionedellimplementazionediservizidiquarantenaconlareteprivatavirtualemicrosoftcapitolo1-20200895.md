---
TOCTitle: 'Guida alla pianificazione dell''implementazione di servizi di quarantena con la rete privata virtuale Microsoft - Capitolo 1'
Title: 'Guida alla pianificazione dell''implementazione di servizi di quarantena con la rete privata virtuale Microsoft - Capitolo 1'
ms:assetid: 'd7dd259f-77cb-4f30-be1b-1ba3ac08ee1f'
ms:contentKeyID: 20200895
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536296(v=TechNet.10)'
---

Guida alla pianificazione dell'implementazione di servizi di quarantena con la rete privata virtuale Microsoft
==============================================================================================================

### Capitolo 1 - Introduzione

Aggiornato: 24 maggio 2005

##### In questa pagina

[](#ebaa)[Riepilogo generale](#ebaa)
[](#eaaa)[Panoramica della Guida alla pianificazione](#eaaa)

### Riepilogo generale

La disponibilità diffusa di Internet ha determinato modifiche sostanziali al modo di operare di molte organizzazioni. Per mantenere un vantaggio sulla concorrenza, le organizzazioni richiedono sempre più ai propri dipendenti di connettersi alle reti aziendali da postazioni remote, ad esempio case, filiali, punti di accesso a Internet pubblici o sedi di clienti. Queste connessioni remote vengono in genere implementate con le tecnologie VPN (rete privata virtuale).

Le connessioni VPN consentono a partner e dipendenti di connettersi in modo protetto alle reti LAN aziendali tramite una rete pubblica. L'accesso remoto basato su tecnologie VPN offre molte nuove opportunità per le aziende, ad esempio applicazioni per l'amministrazione remota e ad alto livello di protezione. Un gran numero di utenti e gruppi aziendali utilizzano applicazioni di amministrazione e produttività che richiedono accessi remoti frequenti e affidabili alle reti LAN aziendali.

Benché la tecnologia VPN garantisca un accesso protetto basato sulla crittografia dei dati nel tunnel VPN, ciò non basta per evitare le intrusioni di software dannoso, ad esempio virus o worm introdotti dal computer di accesso remoto. Gli attacchi di virus o worm possono essere causati da computer infetti connessi alla rete LAN.

Poiché alcune organizzazioni, ad esempio quelle appartenenti al settore dei servizi finanziari, devono salvaguardare la propria reputazione in termini di transazioni protette, anche una minima violazione della protezione potrebbe comportare danni di immagine. Per questo motivo, le connessioni VPN devono essere sottoposte a severi processi di controllo e convalida dei requisiti di accesso.

Nel caso in cui il computer remoto non soddisfi i requisiti di protezione dell'organizzazione, l'accesso VPN è potenzialmente non protetto. La maggior parte delle implementazioni VPN non consente di verificare se su un computer remoto sono disponibili gli aggiornamenti di protezione o le impronte digitali dei virus più recenti prima della connessione alla rete aziendale. In molte organizzazioni, quindi, non è previsto che per un accesso remoto VPN di base vengano soddisfatti i relativi requisiti di protezione.

La connessione VPN in quarantena consente di risolvere questi problemi in quanto si basa su un meccanismo che prevede controlli di pre-connessione e post-connessione in tutti i computer connessi alla rete tramite protocolli VPN nonché l'isolamento di questi stessi computer finché non vengono soddisfatti i criteri di protezione richiesti. Tali controlli, eseguiti con script personalizzati, consentono di verificare versioni di Service Pack, aggiornamenti della protezione e se i programmi antivirus approvati vengono eseguiti in base ai file di definizione dei virus più recenti. Le organizzazioni possono verificare altri requisiti in questi script personalizzati.

Mediante la soluzione di connessione VPN in quarantena, tutti i computer connessi che soddisfano i criteri di accesso remoto specificati vengono collocati in una rete in quarantena e viene verificato che tali computer siano conformi ai criteri di protezione dell'organizzazione. Il server VPN di accesso remoto revoca le restrizioni di quarantena e consente l'accesso alle risorse di rete aziendali solo quando il computer di accesso remoto supera tutti i controlli di connessione.

In questa guida vengono illustrate le problematiche relative alla pianificazione e all'implementazione dei servizi di quarantena con VPN (Rete privata virtuale) tramite le nuove funzionalità disponibili in Microsoft® Windows Server™ 2003 con Service Pack 1 (SP1).

#### Problematiche per le aziende

Le organizzazioni devono affrontare diverse problematiche per garantire l'accesso remoto tramite connessioni VPN. Tali problematiche variano in base ai servizi forniti, al quadro normativo in cui si trova a operare l'azienda e all'ambiente di protezione. Tra le problematiche tipiche sono incluse quelle seguenti:

-   Definire un criterio di accesso VPN efficiente.

-   Ridurre le probabilità che computer infetti o non compatibili possano connettersi alla rete LAN aziendale.

-   Garantire la conformità ai requisiti legali relativi alla gestione delle informazioni personali e di protezione dei dati.

#### Vantaggi per le aziende

Le organizzazioni che implementano servizi di connessione VPN in quarantena efficienti possono ottenere considerevoli vantaggi. Tali vantaggi includono:

-   **Accesso protetto migliorato alle risorse aziendali**. La connessione VPN in quarantena migliora la protezione di accesso alla rete tramite una rigida conformità ai requisiti di aggiornamenti antivirus e della protezione.

-   **Amministrazione e manutenzione semplificate dei servizi**.** **Le organizzazioni possono uniformarsi agli standard delle tecnologie più sicure e aggiornate per l'implementazione VPN. Possono inoltre rimuovere le implementazioni VPN hardware, ad esempio i sistemi di computer di accesso remoto specializzati dell'infrastruttura di rete, semplificando in questo modo strumenti di supporto, documentazione e processi di connessione. Questa semplificazione consente di migliorare il supporto operativo quotidiano della soluzione di accesso VPN e di bilanciare i costi di gestione relativi all'implementazione di una soluzione di quarantena.

-   **Affidabilità e usabilità migliorate dell'accesso remoto**.** **I miglioramenti apportati ad affidabilità e usabilità favoriscono l'utilizzo del servizio VPN da parte dei dipendenti, fornendo maggiori garanzie per la protezione di risorse aziendali critiche e di attività importanti.

-   **Costo totale di proprietà ridotto**. Poiché i computer remoti devono essere conformi a rigidi criteri di affidabilità, vengono ridotti i costi complessivi di supporto e amministrazione. Questo risparmio deriva dalla riduzione delle chiamate di supporto e del tempo speso per bloccare gli attacchi di virus e worm.

-   **Protezione migliorata delle informazioni critiche per l'azienda**. Le informazioni sui clienti hanno un'importanza fondamentale per la maggior parte delle organizzazioni, in particolare per quelle che operano in ambienti regolamentati. Assicurando la maggiore protezione possibile a queste informazioni vengono garantiti i requisiti di conformità alle norme e viene salvaguardata la reputazione dell'organizzazione.

-   **Processi aziendali migliorati**. L'implementazione di una soluzione di connessione VPN in quarantena consente di migliorare la disponibilità dei processi e delle applicazioni aziendali per i responsabili di vendita esterni, i responsabili della clientela e i consulenti. Questa disponibilità migliorata garantisce tempi di decisione più rapidi e una maggiore flessibilità nella fornitura di prodotti e servizi.

Per ulteriori informazioni sui vantaggi sopra indicati, vedere il Capitolo 2 relativi ai metodi di connessione VPN in quarantena (rete privata virtuale).

#### Destinatari della guida

In questa guida sono incluse informazioni utili per coloro che, all'interno di organizzazioni di grandi dimensioni, si occupano di problemi relativi alla rigida tutela della privacy e per coloro che operano all'interno di un quadro normativo applicato con rigore. Tali informazioni sono valide per qualsiasi organizzazione che, indipendentemente dalle dimensioni, richiede un sistema efficace per la protezione dell'identità e il controllo dell'accesso ai dati.

Tra i destinatari della guida sono inclusi i responsabili di processi decisionali, gli architetti di impresa e gli amministratori responsabili della protezione aziendale incaricati di pianificare, distribuire o gestire collegamenti di accesso remoto e protezione di rete. Le informazioni fornite saranno utili anche ai consulenti coinvolti in operazioni di pianificazione, distribuzione o gestione di reti VPN basate su Microsoft Windows®.

#### Prerequisiti per i lettori

Ai fini di questa guida è necessario essere in possesso di competenze pratiche sui criteri e le tecnologie di gestione dell'accesso remoto. Per implementare le soluzioni disponibili nella guida, è necessario che i lettori abbiano esperienza e familiarità nelle seguenti aree e tecnologie:

-   Accesso remoto di Windows Server 2003

-   Servizio autenticazione Internet (IAS, Internet Authentication Service) o altre implementazioni di RADIUS (Remote Authentication Dial-in User Service)

-   Connection Manager e Connection Manager Administration Kit (CMAK)

-   Programmi di scripting o file batch

-   Servizi certificati e infrastruttura a chiave pubblica (PKI)

Nella guida vengono illustrati i quadranti Operatività e Supporto del modello di elaborazione di Microsoft Operations Framework (MOF). Vengono discusse anche le funzioni di gestione dei servizi (SMF, Service Management Function) Amministrazione della protezione e Gestione delle emergenze all'interno di MOF. Per ulteriori informazioni su MOF, visitare il sito Web [Microsoft Operations Framework](http://www.microsoft.com/mof) all'indirizzo www.microsoft.com/italy/technet/itsolutions/mo/mof/default.mspx.

[](#mainsection)[Inizio pagina](#mainsection)

### Panoramica della Guida alla pianificazione

La guida è composta dai seguenti capitoli:

**Capitolo 1: Introduzione**

In questo capitolo vengono fornite alcune informazioni di carattere generale, vengono illustrati i vantaggi e le problematiche delle aziende per la distribuzione VPN con un servizio di quarantena, viene indicato il tipo di utenti a cui si rivolge la guida, vengono elencati i prerequisiti per i lettori e viene fornita una panoramica dei capitoli e degli scenari di soluzione contenuti nella guida.

**Capitolo 2: Approcci alla connessione VPN in quarantena**

In questo capitolo vengono illustrati gli approcci per l'accesso alla connessione VPN in quarantena. Vengono inoltre esaminati gli elementi essenziali per l'accesso VPN in una soluzione per scenari con telelavoratori.

**Capitolo 3: Problemi e requisiti**

In questo capitolo viene presentato lo scenario di Woodgrove National Bank. Vengono quindi definiti il contesto operativo, i problemi aziendali, tecnici e di protezione e i requisiti della soluzione per gli scenari di connessione VPN in quarantena relativi alla Woodgrove National Bank. Nel capitolo viene inoltre illustrato uno scenario di soluzione per l'accesso VPN dei telelavoratori, di cui vengono esaminate le problematiche aziendali, tecniche e di protezione.

**Capitolo 4: Progettazione della soluzione**

In questo capitolo viene descritto in modo dettagliato come pianificare la soluzione per uno scenario di accesso VPN per telelavoratori. Vengono illustrati il concetto, i prerequisiti, l'architettura e il funzionamento della soluzione. Vengono infine descritte le modalità di estensione della soluzione.

Oltre a una valutazione generale dell'uso di VPN con i servizi di quarantena, nella guida vengono fornite informazioni sulle norme per l'implementazione di soluzioni di accesso remoto sicure, basate sullo scenario di Woodgrove National Bank introdotto in questa serie. In questo scenario viene illustrato come implementare un accesso VPN protetto per telelavoratori.

Lo scenario di Woodgrove National Bank è stato creato da Microsoft per illustrare alcune problematiche tipiche delle organizzazioni relative alla fornitura di servizi di quarantena per reti VPN e per mostrare le soluzioni offerte dalle tecnologie Microsoft. In questo scenario viene definito come:

-   Implementare un accesso remoto ad alto livello di protezione per il personale di vendita esterno che si trova raramente in ufficio.

-   Garantire continuità all'azienda in caso di fenomeni meteorologici eccezionali, in modo che i dipendenti possano continuare a essere produttivi da casa.

-   Garantire condizioni di lavoro flessibili in modo che i dipendenti possano scegliere di lavorare da casa.

-   Distribuire aggiornamenti software ai computer remoti in tempo utile.

##### Download

[![](images/Dd536296.icon_exe(it-it,TechNet.10).gif)Guida alla pianificazione dell'implementazione di servizi di quarantena con la rete privata virtuale Microsoft](http://go.microsoft.com/fwlink/?linkid=41308)

[](#mainsection)[Inizio pagina](#mainsection)
