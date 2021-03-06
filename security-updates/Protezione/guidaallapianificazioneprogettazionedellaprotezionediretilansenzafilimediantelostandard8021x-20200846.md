---
TOCTitle: 'Guida alla pianificazione - Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X'
Title: 'Guida alla pianificazione - Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X'
ms:assetid: '8a71cd83-527b-488c-b979-2ea182f129be'
ms:contentKeyID: 20200846
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536247(v=TechNet.10)'
---

Capitolo 6: Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X
=============================================================================================

Pubblicato: 11 ottobre 2004|Aggiornato: 24/11/2004

##### In questa pagina

[](#ehaa)[Introduzione](#ehaa)
[](#egaa)[Utilizzo dello standard 802.1X e della crittografia per la protezione delle reti WLAN](#egaa)
[](#efaa)[Certificati o password](#efaa)
[](#eeaa)[Requisiti della soluzione](#eeaa)
[](#edaa)[Valutazione delle opzioni di protezione per reti WLAN](#edaa)
[](#ecaa)[Impostazioni software necessarie per le reti WLAN 802.1X](#ecaa)
[](#ebaa)[Considerazioni aggiuntive](#ebaa)
[](#eaaa)[Riepilogo](#eaaa)

### Introduzione

Il presente capitolo descrive l'architettura e la progettazione dei componenti della rete senza fili protetta mediante lo standard 802.1X per la soluzione di reti LAN senza fili (WLAN). Nel capitolo sono illustrate le scelte di progettazione necessarie per proteggere i componenti delle reti senza fili e i motivi alla base di tali scelte.

Un importante obiettivo del capitolo è aiutare a valutare l'adeguatezza della progettazione per le esigenze specifiche della propria azienda. In presenza di scelte progettuali alternative, oltre all'opzione utilizzata in questa soluzione vengono forniti altri metodi rilevanti. Alcuni argomenti sono più approfonditi di altri per consentire la comprensione delle implicazioni di una determinata procedura senza la necessità di consultare altri documenti.

#### Prima di iniziare

Prima di leggere questo capitolo, è necessario conoscere i concetti relativi a tecnologia LAN senza fili (WLAN) basata sullo standard 802.11, controllo degli accessi alla rete mediante 802.1X, RADIUS (Remote Authentication Dial-in User Service), Servizio autenticazione Internet (IAS) di Microsoft® e  opzioni di distribuzione WLAN mediante Microsoft Windows® XP Professional. Per approfondire questi argomenti, leggere i riferimenti elencati nella sezione “Ulteriori informazioni” di questo capitolo. M*icrosoft Windows Server*™ *2003 Resource Kit* e *Microsoft Windows Server 2003 Deployment Kit* contengono molte informazioni utili.

#### Panoramica dei capitoli

Il diagramma di flusso riportato di seguito illustra la struttura del capitolo.

![](images/Dd536247.06fig6-1(it-it,TechNet.10).gif "Figura 6.1 Pianificazione della protezione WLAN mediante lo standard 802.1X")

**Figura 6.1 Pianificazione della protezione WLAN mediante lo standard 802.1X**

In questo capitolo sono trattati sei argomenti principali:

1.  **Utilizzo dello standard 802.1X e della crittografia per la protezione delle reti WLAN** Le reti WLAN presentano due vulnerabilità principali che possono essere sfruttate da chiunque disponga di una scheda di rete WLAN compatibile. Questo capitolo spiega come:

    -   Abilitare un accesso sicuro alla rete configurando dei punti di accesso senza fili IEEE (Institute of Electrical and Electronics Engineers) 802.1X come client RADIUS per l'invio di richieste di accesso e messaggi di accounting a server RADIUS. Questi server RADIUS (che eseguono IAS) controllano l'accesso alla rete tramite criteri di accesso remoto centralizzati.

    -   Proteggere dati trasmessi tra dispositivi senza fili e punti di accesso senza fili tramite le funzionalità di crittografia WPA (Wi-Fi Protected Access) e WEP (Wired Equivalent Privacy) a 128 bit e quelle di integrità incorporate nell'apparecchiatura di rete 802.11X. La protezione dei dati impedisce l'intercettazione e l'utilizzazione di dati trasmessi via radio.

2.  **Certificati o password** Microsoft offre il supporto nativo di diversi tipi di protocolli di autenticazione compatibili con lo standard 802.1X. Le forme di autenticazione più comuni sono le password e i certificati digitali. Il metodo di autenticazione scelto può incidere in modo significativo sull'infrastruttura necessaria per la soluzione. Lo scopo di questo capitolo è agevolare le imprese nella scelta del metodo più appropriato.

3.  **Descrizione dei** **prerequisiti della soluzione** Prima iniziare la progettazione, è importante comprendere i prerequisiti della soluzione necessari per l'ambiente in uso, tra cui i requisiti per computer client, infrastruttura server e sistemi WLAN. In questa sezione i requisiti sono esaminati in modo dettagliato.

4.  **Valutazione delle opzioni di protezione per reti WLAN** La pianificazione delle opzioni di protezione è complessa e dovrebbe coinvolgere i responsabili dell'acquisto dell'hardware, della definizione dei criteri di protezione, dell'analisi di utilizzabilità della soluzione, della progettazione delle reti e delle operazioni di rete. Questi esperti dovrebbero prendere in considerazione gli argomenti illustrati nel presente capitolo:

    -   Identificazione dei requisiti di autorizzazione della rete

    -   Scelta di una strategia di configurazione dei client

    -   Individuazione dei requisiti di crittografia del traffico

    -   Progettazione di un'infrastruttura di rete senza fili

    -   Considerazioni sui criteri di gruppo di reti senza fili

5.  **Impostazioni software necessarie per le reti WLAN 802.1X** Per ottenere un adeguato livello di protezione della rete WLAN basata sullo standard 802.1X, è necessario configurare i criteri di accesso alla rete mediante IAS e un oggetto Criteri di gruppo (GPO, Group Policy Object) del servizio directory Active Directory® per i computer client. Questa sezione illustra come effettuare questa operazione.

6.  **Valutazione dei fattori aggiuntivi** In questa sezione, sono brevemente trattati altri argomenti da prendere in considerazione che non rientrano nell'ambito di questa soluzione ma possono influire sull'ambiente in uso. Tra questi fattori sono inclusi:

    -   Supporto di profili comuni e utenti mobili

    -   Supporto di client senza connessioni alla rete LAN cablata

[](#mainsection)[Inizio pagina](#mainsection)

### Utilizzo dello standard 802.1X e della crittografia per la protezione delle reti WLAN

In seguito all'adozione di standard quali IEEE 802.11 e 802.11b, le reti WLAN stanno diventando sempre più diffuse. Questo tipo di rete consente agli utenti di spostarsi all'interno di un edificio o di un gruppo di edifici e, allo stesso tempo, collegarsi automaticamente alla rete mediante un punto di accesso senza fili (AP, Access Point).

Pur essendo estremamente pratiche, le reti WLAN presentano i seguenti rischi per la sicurezza:

-   Chiunque disponga di una scheda WLAN compatibile può ottenere l'accesso alla rete.

-   I segnali delle reti senza fili utilizzano le onde radio per inviare e ricevere informazioni. Chiunque si trovi nel raggio d'azione di un punto di accesso senza fili può individuare e ricevere tutti i dati inviati da e verso tale punto di accesso.

Per ovviare al primo rischio, è possibile configurare i punti di accesso senza fili IEEE 802.1X come client RADIUS per inviare richieste di accesso e messaggi di accounting ai server RADIUS che eseguono il servizio IAS. Il servizio IAS esegue l'autenticazione degli utenti e dei dispositivi e controlla l'accesso alla rete mediante criteri di accesso remoto centralizzati.

Per far fronte al secondo rischio, è possibile proteggere i dati inviati tra i dispositivi senza fili e i punti di accesso senza fili utilizzando le funzionalità di crittografia WEP a 128 bit o WPA integrate nell'apparecchiatura di rete 802.11.

La crittografia WEP statica è caratterizzata dall'assenza di una gestione delle chiavi di crittografia nativa e da gravi difetti di progettazione che nel tempo possono consentire a utenti malintenzionati di decifrare le chiavi di crittografia. Il servizio IAS consente di assegnare dinamicamente chiavi WEP avanzate ai computer client che eseguono Windows XP durante l'autenticazione basata su certificati. Le chiavi WEP, inoltre, possono essere rigenerate a intervalli regolari per ostacolare strumenti di attacco progettati in modo specifico per decifrare tali chiavi.

La funzionalità WPA è un sottoinsieme dello standard di protezione 802.11i (prossimamente disponibile) per sistemi WLAN basati su 802.11 e include caratteristiche di crittografia avanzate, progettate per risolvere alcuni problemi comuni al WEP statico. La soluzione presentata in questa guida può essere utilizzata con la crittografia WPA mediante hardware compatibile con WPA e un aggiornamento del client Windows XP.

[](#mainsection)[Inizio pagina](#mainsection)

### Certificati o password

Microsoft offre il supporto nativo di diversi tipi di protocolli di autenticazione compatibili con lo standard 802.1X. In genere, le aziende scelgono metodi di autenticazione dei client WLAN basati su password o su credenziali legate ai certificati.

Come affermato in precedenza, la scelta del metodo di autenticazione può incidere in modo significativo sull'infrastruttura necessaria per la soluzione. Lo standard 802.1X si avvale di uno schema di autenticazione denominato EAP (Extensible Authentication Protocol) che consente di “innestare” diversi tipi di autenticazione.

Nella tabella seguente, sono illustrati i tipi di EAP che possono essere utilizzati in un'infrastruttura Microsoft 802.1X e i relativi vantaggi e svantaggi.

**Tabella 6.1. Vantaggi e svantaggi dei tipi di EAP**

 
<table style="border:1px solid black;">
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Funzionalità</th>
<th style="border:1px solid black;" >PEAP</th>
<th style="border:1px solid black;" >EAP-TLS</th>
<th style="border:1px solid black;" >EAP-MD5</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Autenticazione reciproca</td>
<td style="border:1px solid black;">Autenticazione reciproca</td>
<td style="border:1px solid black;">Autenticazione reciproca</td>
<td style="border:1px solid black;">Solo autenticazione client</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rigenerazione programmata e generazione dinamica delle chiavi</td>
<td style="border:1px solid black;">Generazione delle chiavi durante l'autenticazione e rigenerazione delle chiavi a intervalli prestabiliti</td>
<td style="border:1px solid black;">Generazione delle chiavi durante l'autenticazione e rigenerazione delle chiavi a intervalli prestabiliti</td>
<td style="border:1px solid black;">Nessuna rigenerazione o generazione dinamica delle chiavi: vengono utilizzate chiavi statiche</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Livello della tecnologia di protezione</td>
<td style="border:1px solid black;">Utilizzo di autenticazione tramite password complesse o certificati digitali</td>
<td style="border:1px solid black;">Autenticazione avanzata</td>
<td style="border:1px solid black;">Tecnologia di protezione vulnerabile</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Protezione delle credenziali utente</td>
<td style="border:1px solid black;">Protezione mediante il tunnel TLS (Transport Layer Security)</td>
<td style="border:1px solid black;">Autenticazione basata su certificati protetta dal tunnel TLS (Transport Layer Security)</td>
<td style="border:1px solid black;">Vulnerabile ad attacchi del dizionario</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Semplicità di implementazione</td>
<td style="border:1px solid black;">Ampiamente supportata e inclusa a livello nativo nei client Windows</td>
<td style="border:1px solid black;">Richiesta un'infrastruttura a chiave pubblica (PKI) Ampiamente supportata e inclusa a livello nativo nei client Windows</td>
<td style="border:1px solid black;">Semplice, ma sconsigliata per le reti senza fili</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Flessibilità delle credenziali</td>
<td style="border:1px solid black;">Qualsiasi tipo di EAP approvato con tunnel TLS, incluso il metodo basato su password EAP-MSCHAPv2.</td>
<td style="border:1px solid black;">Solo certificati digitali</td>
<td style="border:1px solid black;">Solo password</td>
</tr>
</tbody>
</table>
  
Il tipo di EAP consigliato per l'autenticazione dei client basata su certificati è EAP-TLS, mentre quello consigliato per l'autenticazione dei client basata su password è EAP-MSCHAPv2 in PEAP (Protected Extensible Authentication Protocol), definito anche PEAP–EAP–MSCHAPv2.
  
L'autenticazione 802.1X basata su password che utilizza PEAP e MSCHAPv2 è una soluzione affidabile a costi ridotti. È adatta per le imprese che non dispongono di un'infrastruttura di certificazione e non necessitano di certificati per altri scopi, come ad esempio l’uso di EFS (Encrypting File System) o una rete privata virtuale (VPN). Effettuare la migrazione dall'autenticazione 802.1X basata su password a quella basata su certificati è un'operazione semplice. Pertanto, in un secondo tempo l'azienda può facilmente passare da un metodo di autenticazione all'altro.
  
Tenere presente che anche per una soluzione basata su password tramite PEAP, è necessario un certificato su ciascun server RADIUS. È opportuno valutare i costi legati all'acquisto di certificati presso un'autorità di certificazione commerciale rispetto al valore che un'infrastruttura di certificazione propria può apportare all'azienda.
  
Questa soluzione utilizza un'autenticazione dei client basata su certificati poiché offre un livello di protezione maggiore. Tale metodo di autenticazione si basa sul protocollo EAP-TLS (Extensible Authentication Protocol-Transport Layer Security).
  
Per informazioni sulla distribuzione di una soluzione 802.1X basata su password che utilizzi le funzionalità PEAP e MSCHAPv2, consultare la relativa sezione nel capitolo 2 "Scelta di una strategia di rete senza fili protetta" e il riferimento alla fine di questo capitolo della guida alla soluzione correlata, *Protezione delle reti LAN senza fili con PEAP e password*.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Requisiti della soluzione
  
Prima di iniziare la progettazione, è importante comprendere i prerequisiti della soluzione necessari per l'ambiente in uso. In questa sezione i requisiti sono esaminati in modo dettagliato.
  
#### Requisiti dei computer client
  
La soluzione proposta è stata progettata e verificata utilizzando Windows XP Professional con Service Pack (SP) 1, poiché in questo sistema sono incluse le funzionalità 802.1X e WLAN richieste per sviluppare una soluzione con costi estremamente bassi e facilmente gestibile.
  
Il processo di verifica della soluzione è stato svolto anche su computer client con Windows XP Professional e Windows XP Tablet PC Edition. Entrambe le edizioni di Windows XP includono la registrazione automatica dei certificati e il rinnovo dei certificati WLAN per computer e utente richiesti per l'autenticazione client EAP-TLS. Questa funzionalità è in grado di ridurre in modo significativo i costi normalmente associati ai certificati e alla soluzione 802.1X basata sui certificati.
  
Inoltre, Microsoft fornisce i client 802.1X per Windows 2000 (disponibili per il download gratuito) e Windows 9*x* e Microsoft Windows NT® 4.0 (gratuiti per i clienti che dispongono di un contratto di supporto). Tuttavia, la soluzione proposta non è stata verificata su questi tipi di client.
  
#### Infrastruttura server richiesta
  
Questa soluzione dipende dai componenti IAS e dai Servizi certificati di Windows Server 2003. Alcune funzionalità di Servizi certificati e IAS sono state sviluppate esplicitamente per le reti WLAN basate sullo standard 802.1X. Alcune delle funzionalità utilizzate in questa soluzione includono modelli di certificati modificabili e impostazioni di criteri di accesso remoto che consentono di configurare le impostazioni di distribuzione semplificate necessarie per la tecnologia 802.1X.
  
La soluzione è stata progettata per ambienti Windows Server 2003 e Windows 2000 Active Directory, anche se è stata collaudata solo su controller di dominio Windows Server 2003. È possibile installare l'IAS sui controller di dominio in uso. Per una trattazione approfondita delle possibilità di combinazione relative a questa opzione, consultare il Capitolo 5 "Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili".
  
#### Infrastruttura WLAN richiesta
  
In questa soluzione, si presuppone l'utilizzo di un'infrastruttura WLAN progettata correttamente e perfettamente funzionante. Questa guida non contiene istruzioni sulla progettazione di reti senza fili, quali la disposizione dei punti di accesso senza fili e la selezione del canale. Se l'azienda non è dotata di un'infrastruttura WLAN, prima di iniziare la distribuzione dei componenti di protezione WLAN, è necessario assicurarsi che il personale disponga delle competenze tecniche necessarie per l'allestimento di tale sistema.
  
L'hardware di rete deve supportare lo standard 802.1X e la crittografia WEP a 128 bit. In questa guida, si presuppone che l'infrastruttura WLAN funzioni correttamente e che non siano attivati i controlli della protezione o che siano abilitati solo quelli della protezione di base 802.11. La migrazione a questa soluzione da reti WLAN 802.11 a chiave condivisa (WEP statico) o a sistema aperto (non protette) è molto simile e può essere svolta senza grossi problemi.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Valutazione delle opzioni di protezione per reti WLAN
  
I criteri di protezione relativi alle reti WLAN dell'organizzazione richiedono un'attenta pianificazione. Nella valutazione, è consigliabile coinvolgere anche i responsabili incaricati dell'acquisto dell'hardware, della definizione dei criteri di protezione, dell'analisi di utilizzabilità della soluzione, della progettazione delle reti e delle operazioni di rete. La valutazione dei criteri di protezione realizzata da queste persone dovrebbe comprendere anche l'analisi dei rischi inerenti e la scelta dei controlli della protezione necessari per ridurli.
  
È inoltre importante definire i criteri di protezione delle reti WLAN e renderli disponibili e accessibili a tutti gli utenti della rete. Questa soluzione fornisce i controlli della protezione per ridurre i rischi associati alla moderna tecnologia di rete WLAN. Tuttavia, la soluzione non può attenuare i rischi degli utenti di un'azienda che eseguono attività di rete improvvisate e non protette e distribuiscono punti di accesso senza fili inaffidabili.
  
#### Scelta dell'autenticazione basata su utenti e computer
  
L'autenticazione basata su utente rappresenta una scelta naturale quando si prende in considerazione il metodo di identificazione per l'infrastruttura WLAN. Tuttavia, nella maggior parte dei casi, è consigliabile implementare anche l'autenticazione basata su computer (o dispositivo) per ottenere una soluzione completa per la propria WLAN.
  
Alcune funzionalità di Windows XP Professional funzionano correttamente solo se è disponibile una connessione di rete attiva. L'autenticazione di computer mediante lo standard 802.1X garantisce che la connessione di rete WLAN venga stabilita durante la sequenza di avvio prima che venga visualizzata la schermata di accesso iniziale di Windows. Dopo la disconnessione dell'utente, il computer esegue una nuova autenticazione per la rete WLAN al fine di assicurare una connessione costante alla rete.
  
**Tabella 6.2. Motivi per l'uso dell'autenticazione basata su computer**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Funzionalità</th>
<th style="border:1px solid black;" >Scenario che richiede l'autenticazione basata su computer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Criteri di gruppo per computer Active Directory</td>
<td style="border:1px solid black;">I criteri di gruppo basati su computer vengono applicati durante l'avvio del computer e a intervalli programmati, anche se nessun utente accede a Windows.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Script di accesso alla rete</td>
<td style="border:1px solid black;">Gli script di accesso alla rete vengono eseguiti durante l'accesso iniziale dell'utente.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Agenti di gestione dei sistemi</td>
<td style="border:1px solid black;">Gli agenti di gestione dei sistemi, come quelli inclusi in Microsoft Systems Management Server (SMS), spesso richiedono l'accesso alla rete senza l'intervento dell'utente.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Connessione desktop remoto</td>
<td style="border:1px solid black;">È possibile accedere ai computer da Connessione desktop remoto Windows quando nessun utente è connesso al computer.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Cartelle condivise</td>
<td style="border:1px solid black;">Le cartelle e i file condivisi di un computer sono disponibili anche se nessun utente ha eseguito l'accesso.</td>
</tr>
</tbody>
</table>
  
La strategia più efficace consiste nell'utilizzare l'autenticazione basata su utente quando è possibile e l'autenticazione basata su computer quando è necessario. Questa soluzione riproduce il comportamento predefinito del client 802.1X Windows XP Professional, ovvero è prevista l'autenticazione basata su computer quando nessun utente ha eseguito l'accesso, l'autenticazione basata su utente quando gli utenti accedono a Windows e di nuovo l'autenticazione basata su computer quando gli utenti si disconnettono. In questo modo, l'autenticazione nella rete utilizza le credenziali dell'account utente per garantire l'affidabilità e allo stesso tempo è possibile garantire il corretto funzionamento delle funzionalità di Windows quando nessun utente è connesso.
  
##### Convalida delle credenziali basate su certificati
  
In una strategia di autenticazione WLAN basata su certificati, è importante verificare la validità delle credenziali. Controllando i certificati revocati, è possibile impedire l'utilizzo di certificati client archiviati su computer smarriti o rubati. Forzando i client a verificare i certificati del server, è possibile impedire sofisticati attacchi di tipo “man-in-the-middle” eseguiti mediante server RADIUS e punti di accesso inaffidabili.
  
Windows include un ampio supporto per la convalida dei certificati durante le operazioni basate sui certificati. Le funzionalità 802.1X di Windows XP Professional e di IAS si avvalgono di questo supporto per garantire che i certificati utilizzati per la crittografia EAP-TLS siano validi e rappresentino un'identità di protezione attendibile.
  
**Tabella 6.3. Convalida IAS delle credenziali dei certificati client**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Convalida IAS delle credenziali dei certificati client</th>
<th style="border:1px solid black;" >Comportamento predefinito</th>
<th style="border:1px solid black;" >Impostazioni utilizzate nella soluzione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Verifica della validità del certificato rispetto alle date indicate.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della possibilità di creare una catena dal certificato a una fonte attendibile.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Verifica della conformità del certificato ai criteri di applicazione e utilizzo delle chiavi.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della proprietà del client mediante apposizione di una firma con chiave privata.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Verifica che il certificato non sia stato revocato.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
</tbody>
</table>
  
In Windows XP Professional vengono inoltre eseguiti, per impostazione predefinita, i seguenti controlli di convalida delle credenziali del server IAS.
  
**Tabella 6.4. Convalida di Windows XP delle credenziali dei certificati IAS**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Convalida di Windows XP delle credenziali dei certificati server</th>
<th style="border:1px solid black;" >Comportamento predefinito</th>
<th style="border:1px solid black;" >Impostazioni utilizzate nella soluzione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Verifica della validità del certificato rispetto alle date indicate.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della possibilità di creare una catena dal certificato a una fonte attendibile.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Verifica della conformità del certificato ai criteri di applicazione e utilizzo delle chiavi.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della proprietà del server mediante apposizione di una firma con chiave privata.</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
</tbody>
</table>
  
Durante l'autenticazione dell'utente nella rete WLAN, il computer client non può eseguire un controllo delle revoche completo del certificato server, poiché l'accesso alla rete è disponibile solo al termine di un'autenticazione riuscita.
  
Per una maggiore affidabilità del controllo di validità, è possibile attivare opzioni aggiuntive di convalida delle credenziali (eseguite dal client).
  
**Tabella 6.5. Convalida avanzata di Windows XP delle credenziali dei certificati IAS**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Convalida di Windows XP delle credenziali dei certificati server</th>
<th style="border:1px solid black;" >Comportamento predefinito</th>
<th style="border:1px solid black;" >Impostazioni utilizzate nella soluzione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Il soggetto certificato corrisponde a un valore stringa DNS (Domain Name System) configurabile nel client.</td>
<td style="border:1px solid black;">Non attivato</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Selezione esplicita delle CA (Certification Authority, Autorità di certificazione) principali attendibili che possono essere concatenate dal certificato server.</td>
<td style="border:1px solid black;">Non attivato</td>
<td style="border:1px solid black;">Attivato</td>
</tr>
</tbody>
</table>
  
La verifica del nome del soggetto sui computer client richiede l'intervento dell'utente. È inoltre necessario implementare un processo di gestione per mantenere aggiornati i nomi di soggetto certificato server sui client della rete WLAN utilizzando le impostazioni degli oggetti Criteri di gruppo delle reti senza fili. Per questi motivi la soluzione proposta non prevede l'utilizzo di questa opzione. In un ambiente con un alto livello di protezione, prima di decidere se impostare questo livello superiore di convalida, è opportuno considerare i pericoli derivanti da server IAS inaffidabili con punti di accesso senza fili.
  
Le scelta esplicita delle autorità di certificazioni attendibili riduce il rischio di certificati server falsificati derivanti da CA alternative nell'archivio principale attendibile. Ciò richiede, tuttavia, un processo di gestione aggiuntivo per assicurare che le modifiche apportate all'autorità di certificazione attendibile principale siano estese alle impostazioni del client WLAN. Queste impostazioni possono essere distribuite utilizzando le impostazioni degli oggetti Criteri di gruppo delle reti senza fili.
  
#### Identificazione dei requisiti di autorizzazione della rete
  
Uno degli obiettivi principali della progettazione di criteri di gestione dell'accesso di rete è quello di riuscire ad attenersi quanto più possibile ai criteri di protezione dell'azienda riducendo contemporaneamente i costi di gestione. Una rappresentazione centralizzata dei criteri di autorizzazione di rete, ad esempio i criteri di accesso remoto IAS, è particolarmente adatta a questo scopo.
  
**Nota:** in questa soluzione, viene utilizzata l'amministrazione dell'autorizzazione di rete attraverso i criteri di accesso remoto IAS. Per ulteriori informazioni sulle considerazioni effettuate per la scelta di un modello di amministrazione dei criteri di accesso remoto, fare riferimento alle risorse indicate nella sezione "Ulteriori informazioni" alla fine di questo capitolo.
  
La gestione flessibile e al contempo semplice dell'autorizzazione di rete deve costituire un obiettivo prioritario per un'organizzazione. Per ottenere una gestione semplificata è necessario ridurre al minimo il numero di criteri di accesso remoto pur garantendo che tutti i criteri di protezione dell'organizzazione siano rappresentati.
  
##### Definizione dei criteri di connessione
  
I criteri di accesso remoto IAS possono consentire o rifiutare le richieste di connessione. Un criterio contiene una serie di criteri che vengono confrontati ad ogni tentativo di connessione. Il primo criterio trovato che corrisponde a una determinata connessione viene usato per consentire o rifiutare l'accesso. Di seguito sono riportati i principali attributi di connessione che possono essere confrontati con un criterio:
  
-   Appartenenza al gruppo
  
-   Tipo di connessione
  
-   Ora del giorno
  
-   Metodi di autenticazione
  
Inoltre, è possibile specificare molti altri criteri di filtri avanzati, come riportato di seguito:
  
-   Identità del server di accesso
  
-   Numero di telefono del client di accesso o indirizzo MAC (Media Access Control)
  
-   Se le proprietà delle chiamate in ingresso dell'account vengono ignorate
  
-   Se è consentito l'accesso non autenticato
  
Questa soluzione utilizza criteri di connessione IAS basati sul gruppo di protezione di dominio e sul tipo di rete di origine piuttosto che sull'ora del giorno, sul metodo di autenticazione o su altre condizioni. In questo modo, è possibile garantire che i criteri di accesso remoto vengano creati per un tipo specifico di accesso di rete (ad esempio senza fili, VPN, cablato o mediante connessione remota) e di raggruppamento di client, pur essendo abbastanza ampi da limitare il numero di criteri richiesti.
  
**Nota:** questa soluzione utilizza gruppi di protezione personalizzati (Criteri di accesso remoto - Utenti senza fili e Criteri di accesso remoto - Computer senza fili) per limitare gli utenti e i computer autorizzati ad accedere alla rete WLAN. Se si desidera che tutti i computer e gli utenti del dominio abbiano accesso alla rete WLAN, è possibile aggiungere i gruppi Utenti dominio e Computer del dominio a questi gruppi di protezione personalizzati per semplificare l'amministrazione.
  
##### Definizione delle restrizioni per le connessioni
  
Dopo l'autorizzazione di una connessione, è possibile utilizzare i criteri di accesso remoto per specificare eventuali restrizioni della connessione e altri attributi da applicare a tale connessione, tra cui:
  
-   Timeout di inattività
  
-   Durata massima della sessione
  
-   Livello di crittografia
  
-   Filtri di pacchetti IP
  
È inoltre possibile applicare alla connessione gli attributi riportati di seguito:
  
-   Indirizzo IP per le connessioni PPP (Point-to-Point Protocol)
  
-   Route statiche
  
Uno dei fattori principali che determina il numero di criteri di accesso remoto di cui necessita l'azienda è il numero di diversi tipi di utenti che devono accedere alla rete senza fili. Ad esempio, i dipendenti di molte aziende richiedono l'accesso completo senza restrizioni all'intera rete aziendale. Diversamente, i consulenti e i partner commerciali possono richiedere l'accesso solo a determinate applicazioni in specifiche sottoreti.
  
I profili di restrizione delle connessioni sono specifici per ogni criterio di accesso remoto. Nel caso in cui siano richiesti più tipi di profili di restrizione delle connessioni, è necessario utilizzare più criteri di accesso remoto.
  
La tabella che segue illustra degli esempi di vari tipi di utenti e alcune delle restrizioni della connessione che possono essere applicate tramite i criteri di accesso remoto.
  
**Tabella 6.6. Esempi di restrizioni della connessione WLAN**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Tipo di gruppo utente</th>
<th style="border:1px solid black;" >Esempio di restrizione della connessione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Dipendenti</td>
<td style="border:1px solid black;">Accesso autenticato senza restrizioni alla rete aziendale</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Consulenti e partner commerciali</td>
<td style="border:1px solid black;">Accesso autenticato limitato a reti e applicazioni specifiche</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Visitatori</td>
<td style="border:1px solid black;">Accesso non autenticato solo a segmenti della rete relativi a Internet per l'esplorazione del Web o l'accesso VPN all'organizzazione di origine</td>
</tr>
</tbody>
</table>
  
In questa soluzione è previsto il supporto solo per dipendenti autenticati. È quindi necessario solo un criterio di accesso remoto con un profilo di restrizione della connessione semplificato. Se l'azienda presenta ulteriori esigenze, ad esempio la necessità di supportare utenti con un accesso limitato alla rete senza fili, è necessario aggiungere criteri di accesso remoto. Per ulteriori informazioni sulla progettazione di tipi aggiuntivi di criteri di accesso remoto, consultare i riferimenti presenti nella sezione "Ulteriori informazioni" alla fine del capitolo.
  
#### Scelta di una strategia di configurazione dei client
  
L'automazione delle impostazioni di configurazione dei computer client è un passo essenziale per riuscire a ridurre i costi legati alla distribuzione di reti senza fili protette e le richieste di assistenza dovute all'errata configurazione delle impostazioni.
  
In Windows XP Professional, sono disponibili funzionalità sofisticate che consentono di limitare i processi di configurazione e riconfigurazione manuale delle impostazioni di protezione della rete senza fili e dello standard 802.1X sui client WLAN. Windows Server 2003 consente di automatizzare completamente la configurazione dei client tramite  le impostazioni dei criteri di rete senza fili in Criteri di gruppo. La soluzione descritta in questa guida si avvale dei criteri di rete senza fili di Windows Server 2003 per eseguire la configurazione automatica di tutti i client di rete senza fili.
  
È possibile distribuire  queste impostazioni degli oggetti Criteri di gruppo anche prima di distribuire le schede di interfaccia di rete (NIC) WLAN. In questo modo, gli utenti finali possono effettuare un'installazione semplificata delle schede di interfaccia di rete senza fili e, usando le impostazioni WLAN distribuite tramite un oggetto Criteri di gruppo, collegarsi automaticamente alla rete WLAN 802.1X protetta.
  
#### Individuazione dei requisiti di crittografia del traffico
  
Per definire la strategia di protezione del traffico della rete WLAN, è necessario valutare i pericoli in continua evoluzione legati alla crittografia WEP 802.11. Come è stato illustrato in precedenza, è possibile che utenti malintenzionati sfruttino imperfezioni crittografiche in WEP per sferrare attacchi per decifrare la chiave di crittografia WEP. Per effettuare questo tipo di attacco, un intruso deve acquisire parecchi milioni di pacchetti crittografati con la stessa chiave.
  
La migliore strategia per ridurre i rischi legati alla protezione di una rete WLAN basata su WEP è assicurare l'aggiornamento periodico delle chiavi usate per la crittografia del traffico di rete. La frequenza dell'aggiornamento deve essere tale da impedire al pirata informatico di acquisire una quantità di traffico sufficiente ad eseguire l'attacco. Questa soluzione può essere eseguita impostando le opzioni RADIUS IAS in modo da imporre la riautenticazione automatica del client, che comporta l'aggiornamento della chiave WEP.
  
Nella soluzione illustrata in questa guida, le opzioni RADIUS IAS vengono configurate in modo da imporre la riautenticazione del client Windows XP ogni 10 minuti per garantire chiavi di sessioni WEP di breve durata. Questa scelta è stata basata su situazioni e strumenti di attacco WEP noti al momento della stesura di questa guida. La crittografia WEP di base include difetti, quali il sequencing inadeguato del vettore di inizializzazione che può essere sfruttato da un pirata informatico per violare più rapidamente le chiavi. È consigliabile verificare che i punti di accesso siano in grado di generare vettori di inizializzazione meno prevedibili e quindi più affidabili.
  
**Importante:** un timeout di una sessione di 10 minuti potrebbe essere troppo breve per molti scenari. I timeout brevi pongono un carico elevato sui server IAS. Inoltre, i timeout brevi aumentano la possibilità di rendere il server IAS temporaneamente non disponibile, causando la disconnessione dei client dalla rete WLAN. Per queste ragioni, è possibile utilizzare un timeout più lungo di 60 minuti senza compromettere in modo significativo la protezione della rete WLAN.
  
L'utilizzo dell'autenticazione EAP-TLS garantisce che durante il processo di negoziazione TLS vengano generate chiavi di sessione WEP univoche e che vengano trasportate senza problemi nella rete tra i componenti della soluzione. A differenza del WEP statico, le chiavi di crittografia non vengono mai riutilizzate o condivise tra i client.
  
#### Scelta di una strategia di migrazione della rete WLAN
  
Se nell'organizzazione è già attiva una rete senza fili, è necessario scegliere una strategia di migrazione per ridurre al minimo i problemi per gli utenti e l'ambiente.
  
In seguito ad alcune indagini, è emerso che molte aziende utilizzano reti WLAN basate sulla tecnologia 802.11 senza alcuna opzione di autenticazione o protezione dei dati. Questo tipo di strategia di protezione 802.11 è definito autenticazione a *sistema aperto*. Altre aziende implementano soluzioni di crittografia e autenticazione di rete con chiave statica. Questo tipo di protezione di rete 802.11 è definito autenticazione con *chiave condivisa*.
  
I processi di migrazione dai modelli di protezione di rete a sistema aperto e con chiave condivisa alla protezione 802.1X sono molto simili. La differenza principale consiste nel fatto che la soluzione con chiave condivisa offre un certo grado di protezione, quindi la pianificazione della migrazione può essere meno urgente per alcune organizzazioni.
  
La migrazione da una di queste strategie di autenticazione a un modello di protezione basato sullo standard 802.1X include le seguenti operazioni:
  
1.  **Distribuzione di certificati a utenti e computer** - Questa operazione deve essere completata prima dell'implementazione di 802.1X per garantire che i certificati vengano distribuiti ai computer portatili che accedono alla LAN solo di tanto in tanto.
  
2.  **Configurazione di criteri di accesso remoto alla rete senza fili sui server IAS** - Viene illustrata la procedura per la configurazione di un criterio di accesso remoto senza fili.
  
3.  **Implementazione delle configurazioni di rete senza fili nei computer client** - La nuova rete abilitata per 802.1X in genere richiede un nuovo identificatore del set di servizi (SSID) di rete. È possibile distribuire le impostazioni di rete per questo SSID mediante i criteri di gruppo di Active Directory. I criteri di gruppo WLAN devono essere distribuiti prima della riconfigurazione dei punti di accesso senza fili per garantire che i computer portatili che si collegano alla rete WLAN con poca frequenza ricevano impostazioni degli oggetti Criteri di gruppo WLAN.
  
4.  **Configurazione dei punti di accesso senza fili affinché richiedano la protezione 802.1X** - Questa operazione in genere viene eseguita per aree specifiche, ad esempio per un intero edificio o per un gruppo di edifici. È necessario definire procedure appropriate di ripristino nel caso di comportamenti imprevisti e selezionare il personale necessario per consentire all'help desk di gestire in modo adeguato le chiamate.
  
Analogamente a tutte le strategie di migrazione, un'attenta valutazione è essenziale. Una configurazione sbagliata di computer client e punti di accesso senza fili può causare problemi all'ambiente in uso. Prima della distribuzione, è necessario eseguire test completi delle modifiche previste.
  
**Nota:** alcuni punti di accesso senza fili supportano la configurazione della comunicazione via radio tramite un adattatore compatibile 802.11 per la protezione WEP statica e un altro adattatore radio 802.11 per 802.1X. Tuttavia, problemi legati alla separazione dei canali 802.11 rendono inappropriata questa strategia per molte aziende.
  
È necessario contattare il fornitore delle apparecchiature WLAN per verificare che sia in grado di supportare l'aggiornamento a WPA dei punti di accesso senza fili e delle schede di interfaccia di rete senza fili. Microsoft ha rilasciato un aggiornamento di Windows XP che consente di supportare la crittografia WPA (incluso in SP2). È consigliabile pianificare l'aggiornamento dell'infrastruttura WLAN affinché supporti lo standard 802.11i, che probabilmente richiederà aggiornamenti dell'hardware su punti di accesso senza fili e schede di interfaccia di rete senza fili.
  
Nella guida non è descritta in modo dettagliato la progettazione di procedure di migrazione per reti WLAN di produzione mediante soluzioni di protezione proprietarie o a sistema aperto/chiave condivisa. Per informazioni dettagliate sulla migrazione da WLAN di produzione, consultare un partner Microsoft o rivolgersi al responsabile clienti Microsoft che potrà segnalare il partner o un esperto di Microsoft Consulting Services da contattare.
  
#### Progettazione dell'infrastruttura di rete senza fili
  
Una trattazione generale delle apparecchiature e della progettazione delle reti WLAN basate sullo standard 802.11 esula dagli argomenti trattati in questa guida. Nel capitolo dedicato alle reti WLAN di *Microsoft Windows Server 2003 Deployment Kit* (in inglese), sono fornite informazioni generali su questo argomento.
  
In questa guida, si è tentato di sviluppare una soluzione che possa funzionare con un'ampia gamma di prodotti distribuiti da vari fornitori di apparecchiature di rete. La pianificazione e le procedure di configurazione per specifici punti di accesso senza fili non rientrano nell'ambito di questa soluzione.
  
Tuttavia, quando si valutano le impostazioni di protezione e la gestione della protezione in relazione all'apparecchiatura 802.11, è necessario approfondire i seguenti argomenti mediante le risorse fornite dal produttore dell'hardware:
  
-   **Nome SSID e password predefinita** - Questo argomento include la modifica dell'SSID predefinito per tutti i punti di accesso e la scelta di configurare o meno i punti di accesso per la trasmissione degli SSID.
  
-   **Modifica della password predefinita della console e delle stringhe SNMP (Simple Network Management Protocol)** - Questo argomento include la modifica delle password di gestione predefinite e delle stringhe di accesso nei punti di accesso senza fili e la loro conservazione nel tempo.
  
-   **Amministrazione protetta dei punti di accesso senza fili** - In questo contesto viene esaminato l'utilizzo di comunicazioni protette quando si amministrano i punti di accesso senza fili usufruendo di protocolli quali SSH (Secure Shell) o HTTP (Hypertext Transfer Protocol) con SSL o TLS.
  
-   **Impostazioni del client RADIUS** - Questo argomento include la configurazione dei punti di accesso affinché utilizzino i server RADIUS per l'autenticazione e la gestione degli account. Gli argomenti relativi alla configurazione dei punti di accesso per un server RADIUS principale o secondario, all'utilizzo di segreti RADIUS avanzati e all'attributo autenticatore del messaggio sono trattati nel capitolo 5 "Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili" e nel capitolo 9 "Implementazione dell'infrastruttura per la protezione di reti LAN senza fili", che include istruzioni relative all'utilizzo di uno script per generare segreti RADIUS avanzati.
  
-   **Commutazione e filtraggio del traffico di una VLAN (Virtual Local Area Network)** - Nell'ambito di questo argomento, viene esaminato l'utilizzo di reti VLAN per limitare l'accesso a varie tipologie di utenti in diversi scenari. Il server IAS può fornire valori RADIUS basati sul criterio di accesso remoto che consentono di selezionare automaticamente le VLAN appropriate durante la connessione client. Per ulteriori informazioni sulle opzioni IAS relative alla specifica di VLAN per i punti di accesso senza fili, consultare i riferimenti indicati nella sezione "Ulteriori informazioni" alla fine di questo capitolo.
  
-   **Strategie per limitare l'utilizzo improprio di trasmissioni radio LAN senza fili all'esterno dei limiti dell'edificio** - Questo argomento include considerazioni di protezione, ad esempio evitare di posizionare i punti di accesso su muri esterni o su finestre. È inoltre indicato di ridurre la capacità di trasmissione dei punti di accesso quando la copertura può essere limitata all'area necessaria e di evitare la copertura di aree superflue quali i parcheggi.
  
-   **Rilevamento di punti di accesso senza fili inaffidabili** - Questo argomento include la ricerca continua di punti di accesso inaffidabili nella rete aziendale mediante strumenti di gestione WLAN basati su Windows XP e Windows CE, ad esempio NetStumbler o AirMagnet.
  
Per ulteriori informazioni su questi argomenti e sulla configurazione di punti di accesso senza fili, consultare la documentazione specifica del fornitore o richiedere l'intervento di un esperto dell'apparecchiatura in questione. Alcuni di questi temi sono discussi nella sezione "802.11 Wireless Network Technical Reference" della *documentazione tecnica su Windows Server 2003* nella sezione "Ulteriori informazioni" alla fine di questo capitolo.
  
#### Considerazioni sui criteri di gruppo di reti senza fili
  
È consigliabile consultare gli amministratori dell'oggetto Criteri di gruppo del dominio per determinare la strategia più adatta per applicare i criteri di gruppo di reti senza fili ai computer client. Nella tabella che segue sono elencati gli elementi chiave da scegliere per l'ambiente in uso e le impostazioni selezionate in questa soluzione.
  
**Tabella 6.7. Pianificazione dei criteri di rete senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Considerazione sui criteri di rete senza fili</th>
<th style="border:1px solid black;" >Strategia da adottare</th>
<th style="border:1px solid black;" >Dettagli sulla soluzione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Criteri di applicazione dei criteri di gruppo</td>
<td style="border:1px solid black;">Filtraggio dei gruppi di protezione di Active Directory per includere solo computer selezionati.</td>
<td style="border:1px solid black;">Criteri di rete senza fili - Gruppo globale di computer</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Numero di oggetti Criteri gruppo richiesti</td>
<td style="border:1px solid black;">Un solo criterio di rete senza fili.</td>
<td style="border:1px solid black;">L'oggetto Criteri di gruppo utilizzato in questa soluzione è denominato “Criteri di rete senza fili”.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Posizione oggetto Criteri di gruppo</td>
<td style="border:1px solid black;">Creato e applicato dall'oggetto di dominio.</td>
<td style="border:1px solid black;">woodgrovebank.com.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Numero di profili WLAN configurati nel criterio</td>
<td style="border:1px solid black;">Un solo profilo WLAN configurato per le organizzazioni che implementano lo standard 802.1X.</td>
<td style="border:1px solid black;">L'oggetto Criteri di gruppo contiene un profilo WLAN per gli ambienti in cui le reti WLAN non sono state utilizzate per scopi di produzione.
È possibile aggiungere altri profili WLAN per rispondere alle esigenze di una migrazione graduale da una WLAN di produzione precedente.</td>
</tr>
</tbody>
</table>
 

**Nota:** questa soluzione concede a un gruppo di protezione personalizzato (Criteri di rete senza fili - Computer) l'autorizzazione per l'applicazione dei criteri nell'oggetto Criteri di gruppo "Criteri di rete senza fili". L'appartenenza a questo gruppo determina quindi quali computer ricevono le impostazioni degli oggetti Criteri di gruppo WLAN. Per consentire a tutti i computer di ricevere le impostazioni di configurazione della rete WLAN, è possibile semplificare l’amministrazione aggiungendo il gruppo Computer del dominio o quello Utenti autenticati a questo gruppo. Tuttavia, tenere presente che questa procedura applica le impostazioni dei criteri a tutti i server e i client nel dominio (Computer del dominio) o nell'insieme di strutture (Utenti autenticati).

Questa soluzione utilizza una semplice strategia di gestione dei criteri di rete senza fili basata sulla creazione di un singolo oggetto Criteri di gruppi collegato all'oggetto di dominio. Ciò significa che qualsiasi computer nel dominio che è anche membro del gruppo "Criteri di rete senza fili - Computer" riceve le impostazioni dei criteri. Può essere utile valutare la possibilità di definire standard di gestione dei criteri di gruppo più sofisticati e applicare di conseguenza i criteri di rete senza fili. La maggior parte delle aziende necessiteranno un solo oggetto Criteri di gruppo dei criteri di rete senza fili (anche se possono scegliere di collegarlo a una posizione diversa dall'oggetto di dominio).

[](#mainsection)[Inizio pagina](#mainsection)

### Impostazioni software necessarie per le reti WLAN 802.1X

Per garantire un livello di protezione adeguato delle reti WLAN 802.1X, è necessario configurare due principali componenti software:

-   Criteri di accesso alla rete su base IAS

-   Criteri di gruppo di Active Directory per computer client

I criteri di accesso alla rete su base IAS costituiscono il nucleo centrale di una soluzione di gestione dell'accesso alla rete. Le impostazioni relative ai criteri di protezione delle reti WLAN vengono implementate in modo automatico in ogni server RADIUS su base IAS. In questi criteri sono incluse impostazioni relative ai seguenti elementi:

-   Criteri di accesso remoto

-   Criteri richiesta di connessione

I criteri di accesso remoto definiscono l'accesso alle reti attraverso i punti di accesso senza fili. I criteri richiesta di connessione determinano la gestione delle richieste RADIUS da vari punti di accesso senza fili configurati come clienti RADIUS.

I criteri di gruppo di Active Directory per computer client contengono tutte le impostazioni che verranno implementate nei client Windows XP. Questi criteri di gruppo influiscono sul modo in cui i client interagiscono con i punti di accesso senza fili, il server RADIUS e le altre reti senza fili.

#### Configurazione dei criteri di accesso remoto

La creazione di criteri di accesso remoto sui server IAS è necessaria per poter applicare la strategia di accesso alle reti senza fili dell'organizzazione. Il processo di creazione e configurazione dei criteri di accesso remoto comprende la definizione di tre tipi di impostazioni per ogni criterio:

-   Condizioni del criterio

-   Autorizzazioni del criterio

-   Profilo del criterio

In questa soluzione, viene utilizzato un singolo criterio di accesso remoto che garantisce accesso senza restrizioni alla rete senza fili per i dipendenti. Nella tabella che segue sono descritte in dettaglio le condizioni del criterio di accesso remoto per questa soluzione.

**Tabella 6.8. Condizioni del criterio di accesso remoto**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Condizione del criterio</th>
<th style="border:1px solid black;" >Condizione corrispondente</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Tipo - Porta - NAS</td>
<td style="border:1px solid black;">Senza fili - Altro
oppure
Senza fili - IEEE 802.11</td>
<td style="border:1px solid black;">Identifica le richieste in ingresso come provenienti dall'hardware dei punti di accesso senza fili.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Windows - Gruppo</td>
<td style="border:1px solid black;">Appartenenza al gruppo di protezione Criteri di accesso remoto - Accesso senza fili</td>
<td style="border:1px solid black;">Gruppo di protezione universale di dominio che contiene gruppi globali nidificati per utenti e computer che avranno accesso alla rete WLAN.</td>
</tr>
</tbody>
</table>
  
L'autorizzazione del criterio di accesso remoto adottato in questa soluzione è impostata su **Concedi** e gli account utente sono configurati con l'impostazione **Controlla accesso tramite Criteri di accesso remoto**.
  
Nella tabella che segue sono descritte in dettaglio le opzioni del profilo del criterio di accesso remoto utilizzate in questa soluzione. Potrebbero essere necessarie impostazioni aggiuntive per rispondere a esigenze specifiche dell'ambiente.
  
**Tabella 6.9. Opzioni del profilo del criterio di accesso remoto**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione profilo</th>
<th style="border:1px solid black;" >Impostazione profilo</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Limitazioni chiamate in ingresso - Limite massimo di minuti per la connessione del client (timeout sessione)</td>
<td style="border:1px solid black;">10 minuti</td>
<td style="border:1px solid black;">Questa impostazione impone ai computer client l'esecuzione di una nuova autenticazione e la creazione di chiavi di crittografia ogni 10 minuti.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Autenticazione - Metodi EAP</td>
<td style="border:1px solid black;">Smart card o altro certificato</td>
<td style="border:1px solid black;">Questa impostazione seleziona EAP-TLS come tipo EAP per il profilo senza fili.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Attributo RADIUS Ignore-User-Dial-in-Properties</td>
<td style="border:1px solid black;">Attributo impostato su True</td>
<td style="border:1px solid black;">Questo attributo garantisce che le impostazioni relative alle chiamate in ingresso, ad esempio l'opzione di richiamata, degli account utente Active Directory non vengano inviate ai punti di accesso senza fili. Questa soluzione è necessaria per evitare problemi relativi ad alcuni prodotti di accesso alla rete.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Attributo RADIUS Termination-Action</td>
<td style="border:1px solid black;">Attributo impostato su RADIUS Request</td>
<td style="border:1px solid black;">Questo attributo garantisce che la connessione dei client non venga interrotta dai punti di accesso senza fili durante la riautenticazione.</td>
</tr>
</tbody>
</table>
  
**Importante:** un timeout di una sessione di 10 minuti potrebbe essere troppo breve per molti scenari. I timeout brevi pongono un carico elevato sui server IAS. Inoltre, i timeout brevi aumentano la possibilità di rendere il server IAS temporaneamente non disponibile, causando la disconnessione dei client dalla rete WLAN molto prima. Per queste ragioni, è possibile utilizzare un timeout più lungo di 60 minuti senza compromettere in modo significativo la protezione della rete WLAN.
  
#### Configurazione dei criteri richiesta di connessione
  
È necessario scegliere il modo in cui il servizio IAS gestirà le richieste RADIUS quando viene utilizzato come server RADIUS e proxy RADIUS. La scelta del ruolo RADIUS per il servizio IAS è illustrata nel capitolo 5, "Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili".
  
Indipendentemente dal ruolo scelto per il server IAS, è necessario configurare i seguenti componenti dei criteri richiesta di connessione per poter ottenere accesso alla rete senza fili:
  
-   Condizioni del criterio
  
-   Profilo del criterio
  
Nella soluzione proposta, IAS viene utilizzato come server RADIUS e, quindi, le richieste di connessione vengono gestite localmente dai singoli server. Le impostazioni riportate nella tabella che segue illustrano le condizioni dei criteri configurate nel criterio richiesta di connessione adottato per questa soluzione.
  
**Nota:** le impostazioni del criterio richiesta di connessione in questa soluzione utilizzano i valori predefiniti per l'installazione del servizio IAS di Windows Server 2003.
  
**Tabella 6.10. Condizioni del criterio richiesta di connessione**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Condizione del criterio</th>
<th style="border:1px solid black;" >Condizione corrispondente</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Restrizioni data e ora</td>
<td style="border:1px solid black;">&quot;Dom 00:00-24:00; Lun 00:00-24:00; Mar 00:00-24:00; Mer 00:00-24:00; Gio 00:00-24:00;<br />
Ven 00:00-24:00;<br />
Sab 00:00-24:00&quot;</td>
<td style="border:1px solid black;">Questa condizione del criterio richiesta di connessione predefinito garantisce che le richieste di connessione ricevute in qualsiasi orario siano conformi al criterio.</td>
</tr>
</tbody>
</table>
  
Nella tabella che segue sono illustrate le impostazioni del profilo utilizzate nel criterio richiesta di connessione scelto per questa soluzione.
  
**Tabella 6.11. Impostazioni del profilo relativo al criterio richiesta di connessione**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione profilo</th>
<th style="border:1px solid black;" >Impostazione profilo</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Autenticazione</td>
<td style="border:1px solid black;">Autentica le richieste su questo server</td>
<td style="border:1px solid black;">Questa impostazione garantisce che le richieste vengano autenticate direttamente sulla base di Active Directory, invece di venire inoltrate ad altri server RADIUS.</td>
</tr>
</tbody>
</table>
  
#### Configurazione dei criteri di gruppo per i computer client
  
È necessario eseguire un'attenta pianificazione prima di utilizzare criteri di gruppo di Active Directory per configurare le impostazioni della rete WLAN e quelle di protezione dello standard 802.1X nei computer client mediante i criteri di rete senza fili (IEEE 802.11). Questa sezione descrive una serie di impostazioni presenti in questa soluzione e i motivi per includerli. I criteri di rete senza fili (IEEE 802.11) sono disponibili nell'oggetto \\Configurazione computer\\Impostazioni di Windows\\Impostazioni di protezione\\Criteri di accesso senza fili (IEEE 802.11) nell'Editor oggetti Criteri di gruppo.
  
##### Configurazione delle impostazioni delle reti senza fili
  
La configurazione delle impostazioni WLAN viene eseguita modificando le proprietà degli oggetti Criteri di gruppo WLAN nel criterio di gruppo specifico. Sono inclusi i diversi tipi di impostazioni:
  
-   Impostazioni generali
  
-   Reti preferite
  
-   Proprietà di rete
  
Nella tabella che segue sono illustrate le impostazioni generali del criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 6.12. Impostazioni generali dei criteri di rete senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Name</td>
<td style="border:1px solid black;">Configurazione senza fili del computer client</td>
<td style="border:1px solid black;">Questo valore può essere modificato in base agli standard di denominazione dell'azienda.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rete a cui accedere</td>
<td style="border:1px solid black;">La rete disponibile (di preferenza con punto di accesso)</td>
<td style="border:1px solid black;">Questa impostazione impedisce che computer client si colleghino ad altri computer configurati con lo stesso SSID utilizzato per la rete 802.1X. Tuttavia, la possibilità di stabilire connessioni di rete ad hoc consente ai dipendenti di utilizzare altre reti quando è necessario, ad esempio da casa, e per questo si è scelto di consentirne l'uso.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Connetti automaticamente alle reti non preferite</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">In Windows XP Professional agli utenti viene fornita automaticamente una notifica delle reti senza fili disponibili senza tuttavia stabilire direttamente la connessione. Notificando gli utenti senza collegarli automaticamente è possibile ottenere un equilibrio ottimale tra protezione e utilizzabilità.</td>
</tr>
</tbody>
</table>
  
È necessario creare una voce per la rete WLAN SSID 802.1X nella scheda **Reti preferite** del criterio di rete senza fili. Dopo aver specificato una rete preferita, è necessario modificare i valori predefiniti delle proprietà della rete.
  
Nella tabella che segue sono descritte in dettaglio le impostazioni delle proprietà di rete relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili adottato per questa soluzione.
  
**Tabella 6.13. Impostazioni delle proprietà dei criteri di rete senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Name</td>
<td style="border:1px solid black;">MSSWLAN</td>
<td style="border:1px solid black;">Modificare questo valore in modo conforme agli standard di denominazione dell'azienda. È necessario, tuttavia, scegliere un nome diverso da qualsiasi WLAN di produzione esistente.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Chiave rete senza fili (WEP) - Crittografia dati (WEP abilitato)</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">La crittografia è essenziale per proteggere la riservatezza del traffico di rete senza fili nelle reti 802.11. Se nell'azienda sono supportate reti 802.11, assicurarsi che siano protette mediante la crittografia WEP o di altro tipo.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Chiave rete senza fili (WEP) - Autenticazione di rete (modalità condivisa)</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">La protezione 802.11 con chiave condivisa rappresenta una strategia di protezione basata su chiavi WEP statiche. In questa soluzione, lo standard 802.1X viene utilizzato per fornire autenticazione RADIUS sulla base di Active Directory e, quindi, questa opzione è deselezionata.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Chiave rete senza fili (WEP) - Chiave fornita automaticamente</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">Quando questa impostazione è abilitata, lo standard 802.1X viene utilizzato per fornire automaticamente chiavi di sessione WEP dinamiche allo scopo di eseguire la crittografia del traffico di rete.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Rete computer a computer (ad hoc). I punti di accesso senza fili non sono utilizzati.</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">L'impostazione in questa soluzione utilizza la modalità di infrastruttura WLAN 802.11 con punti di accesso senza fili configurati per lo standard 802.1X e non per connessioni di rete ad hoc Point-to-Point.</td>
</tr>
</tbody>
</table>
  
##### Configurazione delle impostazioni 802.1X nei computer client
  
La configurazione delle impostazioni relative allo standard 802.1X viene eseguita mediante criteri di rete senza fili e include i seguenti tipi di impostazioni:
  
-   Parametri 802.1X
  
-   Tipo di EAP
  
-   Convalida delle credenziali
  
-   Procedura di autenticazione basata su computer
  
Nella tabella che segue sono descritte in dettaglio le impostazioni 802.1X relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 6.14. Impostazioni 802.1X dei criteri di rete senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Abilita controllo accesso alla rete mediante IEEE 802.1X</td>
<td style="border:1px solid black;">Attivato</td>
<td style="border:1px solid black;">Questa opzione consente al computer client di accedere alle reti protette mediante lo standard 802.1X.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Messaggio di avvio EAPOL</td>
<td style="border:1px solid black;">Trasmissione</td>
<td style="border:1px solid black;">Questo messaggio indica al client di avviare il processo di autenticazione.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Parametri (secondi) - Avvio massimo</td>
<td style="border:1px solid black;">3</td>
<td style="border:1px solid black;">Questo valore determina il numero di messaggi di avvio consecutivi EAPOL (EAP over LAN) che il client trasmette quando non riceve risposta. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Parametri (secondi) - Periodo di sospensione</td>
<td style="border:1px solid black;">60</td>
<td style="border:1px solid black;">Questo valore determina l'intervallo di tempo che trascorrerà prima che il client tenti di nuovo un processo di autenticazione 802.1X non riuscito. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Parametri (secondi) - Periodo di avvio</td>
<td style="border:1px solid black;">60</td>
<td style="border:1px solid black;">Questo valore determina l'intervallo di tempo che deve trascorrere prima del reinvio dei messaggi di avvio EAPOL. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Periodo di autenticazione</td>
<td style="border:1px solid black;">30</td>
<td style="border:1px solid black;">Questo valore determina l'intervallo di tempo che deve trascorrere prima del reinvio di messaggi di richiesta 802.1X quando non si riceve una risposta. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Tipo di EAP</td>
<td style="border:1px solid black;">Smart card o altro certificato</td>
<td style="border:1px solid black;">Questa opzione specifica EAP-TLS come tipo di EAP.</td>
</tr>
</tbody>
</table>
  
Di seguito sono descritte in dettaglio le impostazioni EAP relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili per questa soluzione.
  
**Tabella 6.15. Impostazioni EAP dei criteri di rete senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Per la connessione</td>
<td style="border:1px solid black;">Utilizza un certificato su questo computer</td>
<td style="border:1px solid black;">Questa opzione specifica l'uso di certificati su base software e chiavi private anziché di credenziali smart card.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Utilizza un certificato su questo computer - Utilizza selezione certificati semplice (opzione consigliata)</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">Con questa opzione attivata, la scelta del certificato corretto verrà basata automaticamente sulle proprietà dei certificati. L'opzione può essere disattivata per consentire la selezione manuale del certificato corretto durante la risoluzione dei problemi.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Convalida certificato server</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">Con questa opzione attivata, viene stabilito se il certificato presentato al client durante l'autenticazione EAP-TLS è valido (se il certificato contiene il nome DNS corretto del server IAS e se il certificato per l'autenticazione server non è scaduto ed è collegato a una CA principale nell'archivio certificati del client).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Convalida certificato server - Connetti ai server seguenti</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">Quando è attivata, questa opzione consente di controllare il suffisso del nome completo di dominio (FQDN) nel campo soggetto del certificato server. Se questa opzione è attivata, nei computer client verrà visualizzata una finestra di testo in cui si richiede l'approvazione del server IAS come attendibile. In questo caso è necessario valutare il rapporto tra utilizzabilità e protezione per scegliere se attivare l'opzione.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Convalida certificato server - Connetti ai server seguenti - Valore</td>
<td style="border:1px solid black;">Vuota</td>
<td style="border:1px solid black;">Questo valore specifica il suffisso del nome completo di dominio che deve corrispondere alle informazioni del soggetto nel certificato presentato al client durante l'autenticazione EAP-TLS.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Autorità di certificazione principali attendibili</td>
<td style="border:1px solid black;">CAsocietà selezionata</td>
<td style="border:1px solid black;">Questa opzione consente agli amministratori di specificare le CA principali attendibili a cui è possibile concatenare le credenziali dei certificati server 802.1X. Per questa opzione, è necessario selezionare le proprie CA principali attendibili.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Utilizza un nome utente diverso per la connessione</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">Quando è attivata, questa opzione consente agli utenti di specificare un nome utente diverso da quello contenuto nel certificato presentato durante l'autenticazione EAP-TLS. L'opzione è disattivata per questa soluzione.</td>
</tr>
</tbody>
</table>
  
Nella tabella che segue sono descritte in dettaglio le impostazioni di autenticazione del computer relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 6.16. Opzioni di autenticazione del computer 802.1X**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Commento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Autentica come Guest se le informazioni sull'utente o sul computer non sono disponibili</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">Quando è attivata, questa impostazione stabilisce se il computer può eseguire l'accesso come Guest se non è disponibile alcuna credenziale. Si tratta di una soluzione utile per reti WLAN pubbliche o per utenti esterni all'organizzazione.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Autentica come computer se le informazioni sono disponibili</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">È essenziale attivare questa impostazione per garantire che l'autenticazione del computer venga eseguita quando gli utenti non sono collegati interattivamente al computer.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Autenticazione basata su computer</td>
<td style="border:1px solid black;">Con riautenticazione utente</td>
<td style="border:1px solid black;">Questa opzione predefinita consente di garantire che vengano utilizzate le credenziali utente quando possibile. Tuttavia, quando gli utenti non sono connessi al computer, verranno utilizzate le credenziali computer per garantire che la connessione alla rete sia sempre disponibile.</td>
</tr>
</tbody>
</table>
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Considerazioni aggiuntive
  
In questa sezione sono trattati brevemente altri argomenti da prendere in considerazione che non rientrano nell'ambito di questa soluzione ma possono influire sull'ambiente in uso.
  
#### Supporto di profili comuni e utenti mobili
  
Per garantire il funzionamento dei componenti 802.1X di Windows su base EAP-TLS, è necessario che le informazioni su certificati e chiavi private siano disponibili nell'archivio certificati sui computer client. In molte aziende, gli utenti senza fili utilizzano computer portatili o Tablet PC in viaggio per avere sempre a disposizione le informazioni su certificati e chiavi private.
  
Tuttavia, se la strategia WLAN adottata prevede la possibilità di condividere computer tra più utenti, è consigliabile valutare l'implementazione di profili mobili. I profili mobili consentono di garantire che le informazioni sulle chiavi private e i certificati siano sempre disponibili per poter essere utilizzati nell'ambiente basato sullo standard 802.1X.
  
In alternativa, i criteri di rete senza fili consentono di configurare i computer che eseguono Windows XP affinché eseguano l'autenticazione esclusivamente di computer. Sebbene questa configurazione non sia implementata nella soluzione, può risultare utile in alcune organizzazioni.
  
#### Supporto di client senza connessioni alla rete LAN cablata
  
Sebbene sia inusuale per le grandi organizzazioni, in alcuni ambienti potrebbe non essere stata implementata l'infrastruttura LAN cablata necessaria per unire i computer client a un dominio e, quindi, distribuire i certificati e i criteri di gruppo. Senza i certificati dei computer e degli utenti e una configurazione appropriata della WLAN dei client, gli utenti non saranno in grado di accedere alla rete WLAN basata sullo standard 802.1X. Questo problema si verifica anche quando un'azienda dispone di una rete cablata che richiede sempre l'autenticazione 802.1X.
  
Se si utilizza questo tipo di ambiente, è opportuno considerare una strategia in cui gli utenti forniscono credenziali basate su password mediante il protocollo PEAP-MSCHAPv2 al server RADIUS per la connessione a una rete VLAN controllata mediante le pagine Web di registrazione di Servizi certificati. In questo modo, gli utenti possono eseguire la registrazione e installare certificati per ottenere l'accesso completo alla rete WLAN aziendale mediante l'autenticazione EAP-TLS. Una strategia di questo tipo non rientra nell'ambito della soluzione proposta e richiederebbe un criterio di accesso remoto aggiuntivo sui server IAS, oltre a una progettazione specifica della rete VLAN.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Riepilogo
  
Questo capitolo descrive il processo di progettazione della protezione delle reti WLAN mediante lo standard 802.1X, che include l'individuazione dei requisiti WLAN, la valutazione delle opzioni di protezione, lo sviluppo di una strategia e considerazioni di altro tipo. Dopo aver definito la progettazione in base alle opzioni descritte in questo capitolo, sarà possibile distribuire la protezione delle reti WLAN basata sullo standard 802.1X nell'ambiente in uso.
  
La progettazione descritta nel presente capitolo verrà utilizzata nella Guida alla creazione e nella Guida operativa più avanti per l'implementazione dell'infrastruttura della protezione delle reti WLAN sulla base dello standard 802.1X.
  
#### Ulteriori informazioni
  
Per ulteriori informazioni sulla protezione delle reti senza fili, vedere quanto riportato di seguito:
  
-   Il sito Web dedicato alla [documentazione del prodotto Windows Server 2003](http://www.microsoft.com/windowsserver2003/proddoc/default.mspx) all'indirizzo http://www.microsoft.com/windowsserver2003/proddoc/default.mspx.
  
    La documentazione del prodotto include una panoramica delle funzionalità di IAS, istruzioni essenziali per la configurazione e procedure consigliate per la distribuzione.
  
-   La soluzione Microsoft [*Protezione delle reti LAN senza fili con PEAP e password*](http://technet.microsoft.com/it-it/library/dd547490.aspx) è disponibile all'indirizzo http://technet.microsoft.com/it-it/library/dd547490.aspx *.*
  
-   Il capitolo “[IAS Technical Reference](http://technet.microsoft.com/en-us/library/cc759100.aspx)” della *documentazione tecnica su Microsoft Windows Server 2003* è disponibile all'indirizzo http://technet.microsoft.com/en-us/library/cc759100.aspx (in inglese).
  
    In questo capitolo del Resource Kit sono incluse informazioni tecniche su IAS più dettagliate di quelle contenute nella documentazione del prodotto, che possono essere utilizzate come riferimento per approfondire argomenti specifici.
  
-   La [*documentazione tecnica su Windows Server 2003*](http://www.microsoft.com/windows/reskits/default.asp) e il [*Microsoft Windows Server 2003 Deployment Kit*](http://www.microsoft.com/windows/reskits/default.asp) sono disponibili all'indirizzo http://www.microsoft.com/windows/reskits/default.asp (in inglese).
  
-   Il capitolo “Deploying a Wireless LAN” della guida in inglese *Deploying Network Services* che fa parte del [*Microsoft Windows Server 2003 Deployment Kit*](http://www.microsoft.com/windowsserver2003/techinfo/reskit/deploykit.mspx) è disponibile all'indirizzo http://www.microsoft.com/windowsserver2003/techinfo/reskit/deploykit.mspx (in inglese).
  
    Questo capitolo del Deployment Kit contiene una guida alla distribuzione per l'utilizzo del servizio IAS in vari scenari che non rientrano nell'ambito della presente guida alla protezione delle reti senza fili, ma che influiscono sulle scelte di progettazione.
  
-   Per una trattazione completa delle reti WLAN 802.1X, dei problemi di protezione delle reti WLAN e degli standard correlati, vedere [la pagina Web non ufficiale della protezione basata sullo standard 802.11](http://www.drizzle.com/~aboba/ieee/) all'indirizzo http://www.drizzle.com/~aboba/IEEE/ (in inglese).
  
-   Per informazioni sulle soluzioni WLAN e informazioni sul settore, visitare il sito Web di Wi-Fi alliance all'indirizzo [http://www.wi-fialliance.org](http://www.wi-fialliance.org/) (in inglese).
  
-   Per informazioni sulle reti WLAN, comprese le informazioni di background, ricerche di mercato, white paper e programmi di formazione, visitare il [centro formazione di Wireless LAN Association (WLANA) all'indirizzo http://www.wlana.org/learning\_center.html](http://www.wlana.org/learning_center.html) (in inglese).
  
-   Per informazioni su EAP–TLS, EAPOL, EAP–RADIUS, RADIUS e altri standard Internet utilizzati con 802.1X, visitare il sito Web di IETF [(The Internet Engineering Task Force)](http://www.ietf.org/) all'indirizzo: http://www.ietf.org/.
  
-   Per informazioni sugli standard WLAN specifici che includono 802.11, 802.11a, 802.11b, 802.1X, 802.11i, consultare l'[area relativa agli standard senza fili del sito Web di IEEE](http://standards.ieee.org/wireless/) all'indirizzo http://standards.ieee.org/wireless/ (in inglese).
  
-   La [802.11 Wireless Technical Reference](http://technet.microsoft.com/en-us/library/cc737818.aspx) è disponibile all'indirizzo http://technet.microsoft.com/en-us/library/cc737818.aspx (in inglese).
  
[](#mainsection)[Inizio pagina](#mainsection)
