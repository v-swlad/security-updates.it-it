---
TOCTitle: 'Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X'
Title: 'Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X'
ms:assetid: '53aa011e-8fca-4c01-9c85-2f0a3b5649f0'
ms:contentKeyID: 20200858
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536259(v=TechNet.10)'
---

Pianifica la protezione di una LAN wireless con Windows Server 2003 Certificate Services
========================================================================================

### Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X

##### In questa pagina

[](#elaa)[Argomenti del modulo](#elaa)
[](#ekaa)[Obiettivi](#ekaa)
[](#ejaa)[Ambito di applicazione](#ejaa)
[](#eiaa)[Utilizzo del modulo](#eiaa)
[](#ehaa)[Utilizzo dello standard 802.1X e della crittografia per la protezione delle reti WLAN](#ehaa)
[](#egaa)[Certificati o password](#egaa)
[](#efaa)[Requisiti della soluzione](#efaa)
[](#eeaa)[Valutazione delle opzioni di protezione per reti WLAN](#eeaa)
[](#edaa)[Impostazioni software necessarie per le reti WLAN 802.1X](#edaa)
[](#ecaa)[Ulteriori considerazioni](#ecaa)
[](#ebaa)[Riepilogo](#ebaa)
[](#eaaa)[Ulteriori informazioni](#eaaa)

### Argomenti del modulo

L'obiettivo principale di questo modulo consiste nel descrivere l'architettura e la progettazione dei componenti della rete senza fili protetta mediante lo standard 802.1X delineata in questa soluzione. Nel modulo sono illustrate le scelte di progettazione necessarie per proteggere i componenti delle reti senza fili e i motivi alla base di tali scelte. Lo scopo secondario del modulo è quello di fornire il supporto necessario per poter determinare se la progettazione è adatta all'organizzazione.

[](#mainsection)[Inizio pagina](#mainsection)

### Obiettivi

Il modulo consente di:

-   Proteggere i dati trasmessi in una rete LAN senza fili (WLAN, Wireless LAN).

-   Scegliere credenziali basate su certificati o su password.

-   Comprendere le opzioni di protezione WLAN.

-   Configurare criteri di accesso su base IAS e criteri di gruppo del servizio di directory Active Directory® per i computer client.

[](#mainsection)[Inizio pagina](#mainsection)

### Ambito di applicazione

Questo modulo si applica ai seguenti prodotti e tecnologie:

-   Microsoft® Windows® Server™ 2003

-   Microsoft Internet Authentication Service (IAS)

-   Servizi certificati Microsoft

-   Microsoft Active Directory

[](#mainsection)[Inizio pagina](#mainsection)

### Utilizzo del modulo

In questo modulo viene descritta la metodologia di progettazione di una rete senza fili protetta mediante lo standard 802.1X. La metodologia proposta potrà quindi essere adattata alle esigenze specifiche dell'organizzazione. La presente guida fornisce il supporto necessario per determinare se la progettazione è adatta all'organizzazione.

Per sfruttare al massimo il presente modulo:

-   Leggere il modulo "[Architettura della soluzione di rete LAN senza fili protetta](http://technet.microsoft.com/it-it/library/dd536256)" per comprendere meglio le caratteristiche dello standard 802.1X con EAP-TLS (Extensible Authentication Protocol-Transport Layer Security).

-   Leggere il modulo "[Progettazione di un'infrastruttura a chiave pubblica](http://technet.microsoft.com/it-it/library/dd536257)" per una descrizione del processo di progettazione utilizzato per creare un'infrastruttura PKI.

-   Leggere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" per una descrizione dell'architettura e della progettazione del server IAS.

[](#mainsection)[Inizio pagina](#mainsection)

### Utilizzo dello standard 802.1X e della crittografia per la protezione delle reti WLAN

In seguito all'adozione di standard quali IEEE 802.11 e 802.11b, le reti WLAN stanno diventando sempre più diffuse. Questo tipo di rete consente agli utenti di spostarsi all'interno di un edificio o di un gruppo di edifici e, allo stesso tempo, avere la possibilità di collegarsi automaticamente alla rete mediante un punto di accesso senza fili (AP, Access Point).

Pur essendo estremamente pratiche, le reti WLAN presentano i seguenti rischi per la sicurezza:

-   Chiunque disponga di una scheda WLAN compatibile può ottenere l'accesso alla rete.

-   I segnali delle reti senza fili utilizzano le onde radio per inviare e ricevere informazioni. Chiunque si trovi nel raggio d'azione di un punto di accesso senza fili può individuare e ricevere tutti i dati inviati da e verso tale punto di accesso.

Per ovviare al primo rischio, è possibile configurare i punti di accesso senza fili IEEE 802.1X come client RADIUS (Remote Authentication Dial-In User Service) per inviare richieste di accesso e messaggi di accounting ai server RADIUS che eseguono il servizio IAS. Questo servizio esegue l'autenticazione degli utenti e dei dispositivi e controlla l'accesso alla rete mediante criteri di accesso remoto centralizzati.

Per far fronte al secondo rischio, è possibile proteggere i dati inviati tra i dispositivi senza fili e i punti di accesso senza fili utilizzando le funzionalità di crittografia WEP (Wired Equivalent Privacy) a 128 bit o WPA (Wi-Fi Protected Access) integrate nell'apparecchiatura di rete 802.11.

La crittografia WEP è caratterizzata dall'assenza di una gestione delle chiavi di crittografia e da imperfezioni della progettazione che nel tempo possono consentire a utenti malintenzionati di decifrare le chiavi di crittografia. Il servizio IAS consente di assegnare dinamicamente chiavi WEP avanzate ai computer client che eseguono Windows XP durante l'autenticazione basata su certificati. Le chiavi WEP inoltre possono essere aggiornate a intervalli regolari per ostacolare strumenti di attacco progettati in modo specifico per decifrare tali chiavi.

La funzionalità WPA è un sottoinsieme dello standard di protezione 802.11i di prossima uscita per sistemi WLAN basati su 802.11 e include caratteristiche di crittografia avanzate, progettate per risolvere alcuni problemi riscontrati in WEP. Poiché attualmente i prodotti abilitati per WPA non sono ancora ampiamente diffusi, la soluzione proposta è basata sulla crittografia WEP. Tuttavia, questa soluzione può essere estesa a WPA applicando solo alcune modifiche dell'hardware e un aggiornamento di Windows XP, disponibile per il download.

[](#mainsection)[Inizio pagina](#mainsection)

### Certificati o password

Lo standard 802.1X supporta l'utilizzo di diversi tipi di protocolli di autenticazione. In genere le organizzazioni scelgono metodi di autenticazione dei client WLAN basati su password o su credenziali legati ai certificati.

Come affermato in precedenza, la scelta del metodo di autenticazione richiesto per l'organizzazione può incidere in modo significativo sull'infrastruttura necessaria per la soluzione. Lo standard 802.1X si avvale di uno schema di autenticazione innestabile denominato EAP (Extensible Authentication Protocol).

Nella tabella che segue sono illustrati i tipi di EAP che possono essere utilizzati in un'infrastruttura Microsoft 802.1X e i relativi vantaggi e svantaggi.

**Tabella 1. Vantaggi e svantaggi dei tipi di EAP**

 
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
<th style="border:1px solid black;" >MD5</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Autenticazione reciproca</td>
<td style="border:1px solid black;">Autenticazione reciproca</td>
<td style="border:1px solid black;">Autenticazione reciproca</td>
<td style="border:1px solid black;">Autenticazione reciproca non supportata</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rotazione delle chiavi (reimpostazione delle chiavi)</td>
<td style="border:1px solid black;">Generazione delle chiavi durante l'autenticazione</td>
<td style="border:1px solid black;">Generazione delle chiavi durante l'autenticazione</td>
<td style="border:1px solid black;">Rotazione delle chiavi non supportata: vengono utilizzate chiavi statiche.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Livello della tecnologia di protezione</td>
<td style="border:1px solid black;">Autenticazione avanzata basata su password</td>
<td style="border:1px solid black;">Autenticazione avanzata</td>
<td style="border:1px solid black;">Tecnologia di protezione vulnerabile</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Protezione delle credenziali utente</td>
<td style="border:1px solid black;">Protezione mediante il tunnel TLS (Transport Layer Security)</td>
<td style="border:1px solid black;">Autenticazione basata su certificati</td>
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
<td style="border:1px solid black;">Qualsiasi tipo EAP approvato con tunnel TLS, incluse password basate su EAP-MSCHAPv2.</td>
<td style="border:1px solid black;">Solo certificati digitali</td>
<td style="border:1px solid black;">Solo password</td>
</tr>
</tbody>
</table>
  
Il tipo di EAP consigliato per l'autenticazione dei client basata su certificati è EAP-TLS, mentre quello consigliato per l'autenticazione dei client basata su password è EAP-MSCHAPv2 (Microsoft Challenge-Handshake Authentication Protocol versione 2) in PEAP (Protected Extensible Authentication Protocol), definito anche PEAP-EAP-MSCHAPv2.
  
L'autenticazione 802.1X basata su password è adatta a piccole organizzazioni che non dispongono di un'infrastruttura di certificazione e non si avvalgono dei certificati per altri scopi, ad esempio per l'utilizzo di Crittografia file system (EFS), delle reti private virtuali (VPN) e così via. In alternativa, l'autenticazione 802.1X basata su password può essere considerata una soluzione temporanea per ottenere il controllo dell'accesso alle WLAN 802.1X mentre si pianifica lo sviluppo di un'infrastruttura di certificazione.
  
Tuttavia, i costi legati all'acquisto di uno o più certificati server da terze parti affidabili devono essere valutati attentamente rispetto al valore apportato dall'infrastruttura di certificazione in un'organizzazione. Questa guida è stata sviluppata per agevolare l'individuazione di una soluzione di autenticazione dei client basata su certificati che si avvalga della funzionalità EAP-TLS senza comportare costi elevati e configurazioni complesse.
  
Per informazioni sul modo in cui implementare una soluzione 802.1X basata su password che utilizzi la funzionalità PEAP, consultare un partner Microsoft o rivolgersi al responsabile clienti Microsoft che potrà segnalare il partner o un esperto di Microsoft Consulting Services da contattare.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Requisiti della soluzione
  
È importante esaminare i requisiti relativi all'ambiente a cui fa riferimento questa soluzione prima di passare alla progettazione. In questa sezione i requisiti sono esaminati in modo dettagliato.
  
#### Requisiti dei computer client
  
La soluzione proposta è stata progettata e verificata utilizzando Windows XP Professional con Service Pack (SP) 1, poiché in questo sistema sono incluse le funzionalità 802.1X e WLAN richieste per sviluppare una soluzione con costi estremamente bassi e un livello di protezione ottimale.
  
Il processo di verifica della soluzione è stato svolto su anche computer client con Windows XP Professional e Windows XP Professional Tablet PC Edition. Entrambe le edizioni di Windows XP Professional includono la registrazione automatica dei certificati e il rinnovo dei certificati WLAN per computer e utente richiesti per l'autenticazione client EAP-TLS. Questa funzionalità è in grado di ridurre in modo significativo i costi normalmente associati ai certificati e allo standard 802.1X basato sui certificati.
  
I client 802.1X per Microsoft Windows 2000, Windows NT® versione 4.0 e Windows 9*x* sono forniti gratuitamente per i clienti che dispongono di un contratto di supporto. Tuttavia, la soluzione proposta non è stata verificata su questi tipi di client.
  
#### Infrastruttura server richiesta
  
Questa soluzione è basata su Servizi certificati di Windows Server 2003 e su Servizio di Autenticazione Internet (IAS) di Windows Server 2003. Alcune funzionalità di Servizi certificati e IAS sono state sviluppate esplicitamente per le reti WLAN basate sullo standard 802.1X. Alcune di queste funzionalità includono modelli di certificati modificabili e impostazioni di criteri di accesso remoto che consentono di configurare le impostazioni di implementazione semplificate necessarie per la tecnologia 802.1X.
  
La soluzione è stata progettata per un ambiente Windows Server 2003 e Windows 2000 Active Directory, anche se è stata verificata principalmente su controller di dominio Windows Server 2003. Sebbene non sia richiesto, è possibile combinare IAS con uno o più controller di dominio. Per una trattazione approfondita delle possibilità di combinazione, fare riferimento al modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" di questa guida.
  
#### Infrastruttura WLAN richiesta
  
In questa soluzione si presuppone l'utilizzo di un'infrastruttura WLAN progettata correttamente e perfettamente funzionante che supporti lo standard 802.1X e la crittografia WEP a partire da 128 bit. Si presuppone che l'infrastruttura LAN funzioni senza problemi e utilizzi solo i controlli di protezione essenziali. La migrazione a questa soluzione è molto simile per i due tipi di reti LAN 802.11 a chiave condivisa e a sistema aperto e può essere svolta senza problemi.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Valutazione delle opzioni di protezione per reti WLAN
  
I criteri di protezione relativi alle reti WLAN dell'organizzazione richiedono un'attenta pianificazione. Nella valutazione è consigliabile coinvolgere anche i responsabili incaricati dell'acquisto dell'hardware, della definizione dei criteri di protezione, dell'analisi di utilizzabilità della soluzione, della progettazione delle reti e delle operazioni di rete. Gli aspetti da prendere in considerazione includono i rischi che l'organizzazione deve affrontare e i controlli di protezione disponibili per limitare tali pericoli.
  
È inoltre importante definire i criteri di protezione delle reti WLAN e renderli disponibili e accessibili a tutti gli utenti della rete. In questa soluzione sono proposti controlli di protezione che consentono di ridurre i rischi associati alla moderna tecnologia WLAN ma che non possono arginare i rischi dovuti all'esecuzione di operazioni in rete non protette e all'utilizzo di punti di accesso senza fili inaffidabili da utenti interni all'organizzazione.
  
#### Scelta dell'autenticazione basata su utenti e/o computer
  
L'autenticazione basata su utente rappresenta una scelta naturale quando si prende in considerazione il metodo di identificazione per l'infrastruttura WLAN. Tuttavia, nella maggior parte dei casi è consigliabile implementare anche l'autenticazione basata su computer (o dispositivo) per ottenere una soluzione completa.
  
Alcune funzionalità di Windows XP Professional funzionano correttamente solo se è disponibile una connessione di rete attiva. L'autenticazione di computer mediante lo standard 802.1X garantisce che la connessione di rete venga stabilita durante la sequenza di avvio e prima che venga visualizzata la schermata di accesso iniziale di Windows.
  
**Tabella 2. Considerazioni relative all'autenticazione basata su computer**

 
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
<td style="border:1px solid black;">Gli agenti applicazione di gestione dei sistemi, come quelli inclusi in Microsoft Systems Management Server (SMS), spesso richiedono l'accesso alla rete senza l'intervento dell'utente.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Connessione desktop remoto</td>
<td style="border:1px solid black;">I computer sono accessibili da Connessione desktop remoto Windows quando nessun utente ha eseguito l'accesso a Windows.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Cartelle condivise</td>
<td style="border:1px solid black;">I file e le cartelle condivise di un computer sono disponibili anche se nessun utente ha eseguito l'accesso.</td>
</tr>
</tbody>
</table>
  
La strategia più efficace consiste nell'utilizzare l'autenticazione basata su utente quando è possibile e l'autenticazione basata su computer quando è necessario. La soluzione descritta in questa guida riproduce il comportamento predefinito del client 802.1X Windows XP Professional, ovvero è prevista l'autenticazione basata su computer quando nessun utente ha eseguito l'accesso, l'autenticazione basata su utente quando gli utenti accedono a Windows e di nuovo l'autenticazione basata su computer quando gli utenti si disconnettono. In questo modo l'accesso alla rete viene basato sulle credenziali dell'account utente per garantire l'affidabilità e allo stesso tempo è possibile garantire il corretto funzionamento delle funzionalità di Windows che richiedono l'accesso alla rete.
  
##### Convalida delle credenziali basate su certificati
  
La verifica della validità delle credenziali è particolarmente importante in una strategia di autenticazione WLAN basata su certificati. Individuando certificati client revocati è possibile impedire l'utilizzo di credenziali archiviate su computer smarriti o rubati. La convalida dei certificati server consente di impedire sofisticati attacchi di tipo man-in-the-middle.
  
Windows include un ampio supporto per la convalida dei certificati durante le operazioni basate sui certificati. Le funzionalità 802.1X di IAS e Windows XP Professional si avvalgono di questo supporto per garantire che i certificati utilizzati per la crittografia EAP-TLS siano validi e rappresentino un'identità di protezione attendibile.
  
**Tabella 3. Convalida IAS delle credenziali dei certificati client**

 
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
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della possibilità di creare una catena dal certificato a una fonte attendibile.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Verifica della conformità del certificato ai criteri di applicazione e utilizzo delle chiavi.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della proprietà del client mediante apposizione di una firma con chiave privata.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Verifica che il certificato non sia stato revocato.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
</tbody>
</table>
  
In Windows XP Professional vengono inoltre eseguiti, per impostazione predefinita, i seguenti controlli di convalida delle credenziali del server IAS.
  
**Tabella 4. Convalida di Windows XP delle credenziali dei certificati IAS**

 
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
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della possibilità di creare una catena dal certificato a una fonte attendibile.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Verifica della conformità del certificato ai criteri di applicazione e utilizzo delle chiavi.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Verifica della proprietà del server mediante apposizione di una firma con chiave privata.</td>
<td style="border:1px solid black;">Attivo</td>
<td style="border:1px solid black;">Invariato</td>
</tr>
</tbody>
</table>
  
Quando l'autenticazione in una WLAN viene eseguita mediante lo standard 802.1X, il computer client non può controllare le credenziali basate sui certificati del server per verificare se sono state revocate, poiché l'accesso alla rete non è disponibile durante l'autenticazione EAP-TLS. Per limitare questo rischio è tuttavia possibile attivare le seguenti opzioni aggiuntive di convalida delle credenziali.
  
**Tabella 5. Convalida avanzata di Windows XP delle credenziali dei certificati IAS**

 
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
<td style="border:1px solid black;">Selezione esplicita delle CA (Certification Authority, Autorità di certificazione) principali attendibili a cui è possibile concatenare il certificato server.</td>
<td style="border:1px solid black;">Non attivato</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
</tbody>
</table>
  
La verifica del nome del soggetto sui computer client richiede l'intervento dell'utente. Inoltre, è necessario implementare un processo di gestione per mantenere i valori delle stringhe costantemente aggiornati sui client WLAN attraverso i criteri di rete senza fili di Active Directory. Per questi motivi la soluzione proposta non prevede l'utilizzo di questa opzione. In un ambiente con livello di protezione alto, è consigliabile valutare i potenziali rischi derivanti dall'utilizzo di un certificato non autorizzato in server IAS inaffidabili con punti di accesso senza fili. Tali rischi devono essere valutati rispetto ai vantaggi in termini di utilizzabilità.
  
Le scelta esplicita delle autorità di certificazioni attendibili riduce il rischio di certificati server falsificati derivanti da CA alternative nell'archivio principale attendibile. Ciò richiede, tuttavia, un processo di gestione per garantire che le modifiche apportate all'autorità di certificazione attendibile principale siano estese alle impostazioni del client WLAN implementate attraverso i criteri di rete senza fili di Active Directory.
  
#### Identificazione dei requisiti di autorizzazione della rete
  
Uno degli obiettivi principali della progettazione di criteri di gestione dell'accesso di rete è quello di riuscire ad attenersi quanto più possibile ai criteri di protezione dell'organizzazione riducendo contemporaneamente i costi di gestione. Una rappresentazione centralizzata dei criteri di autorizzazione di rete, ad esempio i criteri di accesso remoto IAS, è particolarmente adatta a questo scopo.
  
**Nota:** in questa soluzione viene utilizzata l'amministrazione dell'autorizzazione di rete attraverso i criteri di accesso remoto IAS. Per ulteriori informazioni sulle considerazioni effettuate per la scelta di un modello di amministrazione dei criteri di accesso remoto, fare riferimento alle risorse indicate nella sezione "Ulteriori informazioni" alla fine di questo modulo.
  
La gestione flessibile e al contempo semplice dell'autorizzazione di rete deve costituire un obiettivo prioritario per un'organizzazione. Per ottenere una gestione semplificata è necessario ridurre al minimo il numero di criteri di accesso remoto pur garantendo che tutti i criteri di protezione dell'organizzazione siano rappresentati.
  
##### Definizione dei criteri di connessione
  
I criteri di accesso remoto possono convalidare numerose impostazioni di connessione prima di autorizzare la connessione, ad esempio:
  
-   Autorizzazione di accesso remoto
  
-   Appartenenza al gruppo
  
-   Tipo di connessione
  
-   Ora del giorno
  
-   Metodi di autenticazione
  
Possono inoltre essere utilizzate le seguenti condizioni avanzate:
  
-   Identità del server di accesso
  
-   Numero di telefono del client di accesso o indirizzo MAC (Media Access Control)
  
-   Se le proprietà delle chiamate in ingresso dell'account vengono ignorate
  
-   Se è consentito l'accesso non autenticato
  
Questa soluzione utilizza criteri di connessione IAS basati sul gruppo Active Directory e sul tipo di rete di origine piuttosto che sull'ora del giorno, sul metodo di autenticazione o su altre condizioni. In questo modo è possibile garantire che i criteri di accesso remoto vengano creati per un tipo specifico di accesso di rete (ad esempio senza fili, VPN, cablato o mediante connessione remota) e di raggruppamento di client, pur essendo abbastanza ampi da limitare il numero di criteri di accesso remoto richiesti.
  
##### Definizione delle restrizioni per le connessioni
  
Dopo l'autorizzazione di una connessione, è possibile utilizzare i criteri di accesso remoto per specificare eventuali restrizioni della connessione, che possono includere i seguenti aspetti:
  
-   Timeout di inattività
  
-   Durata massima della sessione
  
-   Livello di crittografia
  
-   Filtri di pacchetti IP
  
Possono inoltre essere applicate le seguenti restrizioni avanzate:
  
-   Indirizzo IP per le connessioni PPP (Point-to-Point Protocol)
  
-   Route statiche
  
Per determinare il numero di criteri di accesso remoto richiesti è necessario valutare quali siano i diversi tipi di utenti che devono poter accedere alle reti senza fili. Ad esempio, i dipendenti di molte organizzazioni richiedono l'accesso completo senza restrizioni all'intera rete aziendale. Diversamente, i consulenti e i partner commerciali possono richiedere l'accesso solo a determinate applicazioni in specifiche sottoreti.
  
I profili di restrizione delle connessioni sono specifici per ogni criterio di accesso remoto. Nel caso in cui siano richiesti più tipi di profili di restrizione delle connessioni, è necessario utilizzare più criteri di accesso remoto. La scelta del criterio di accesso remoto e, di conseguenza, del profilo di restrizione della connessione appropriato, è basata sui criteri di connessione.
  
Nella tabella che segue sono illustrati esempi di diversi tipi di utenti e delle restrizioni della connessione che possono essere applicati mediante il criterio di accesso remoto.
  
**Tabella 6. Esempi di restrizioni della connessione WLAN**

 
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
<td style="border:1px solid black;">Accesso non autenticato solo a segmenti della rete relativi a Internet per l'esplorazione del Web o accesso VPN all'organizzazione di origine</td>
</tr>
</tbody>
</table>
  
In questa soluzione è previsto il supporto solo per dipendenti autenticati. È quindi necessario solo un criterio di accesso remoto con un profilo di restrizione della connessione semplificato. Se l'organizzazione presenta requisiti aggiuntivi, ad esempio la necessità di supportare l'accesso guest alla rete senza fili, dovranno essere valutati altri criteri di accesso remoto. Per ulteriori informazioni sulla progettazione di tipi aggiuntivi di criteri di accesso remoto, consultare i riferimenti presenti nella sezione "Ulteriori informazioni" alla fine del modulo.
  
#### Scelta di una strategia di configurazione dei client
  
L'automazione delle impostazioni di configurazione dei computer client è un passo essenziale per riuscire a ridurre i costi legati all'implementazione di reti senza fili protette e le richieste di assistenza dovute all'errata configurazione delle impostazioni.
  
In Windows XP Professional sono disponibili funzionalità sofisticate che consentono di limitare i processi di configurazione e riconfigurazione da parte dell'utente finale per le impostazioni di protezione della rete senza fili e dello standard 802.1X. In Windows Server 2003 sono state aggiunte altre risorse che consentono alle organizzazioni di automatizzare la configurazione dei client mediante Active Directory e i criteri di rete senza fili. La soluzione descritta in questa guida si avvale dei criteri di rete senza fili di Windows Server 2003 per eseguire la configurazione automatica dei client di rete senza fili.
  
L'implementazione di tali impostazioni nei computer portatili può essere eseguita anche prima della distribuzione delle schede di rete WLAN. In alcuni casi le schede di rete senza fili possono essere installate da utenti finali, mentre le impostazioni della rete WLAN e dello standard 802.1X verranno applicate automaticamente da un criterio di gruppo precedentemente implementato. Il risultato finale sarà quindi una procedura semplice che consentirà agli utenti finali di stabilire una connessione alla rete WLAN 802.1X protetta.
  
#### Individuazione dei requisiti di crittografia del traffico
  
Per definire la strategia di protezione della privacy del traffico WLAN, è necessario valutare i pericoli in continua evoluzione legati alla crittografia WEP 802.11. Nonostante si utilizzi la gestione dinamica delle chiavi 802.1X e la crittografia WEP a 128 bit, è possibile che utenti malintenzionati sfruttino imperfezioni crittografiche in WEP per sferrare attacchi di tipo brute force, decifrare la chiave di crittografia WEP e accedere a informazioni riservate. Queste tecniche sono ampiamente diffuse e documentate. L'attacco viene sferrato da un utente malintenzionato che intercetta un volume consistente di traffico di rete e utilizza risorse di elaborazione estremamente veloci.
  
La strategia principale per ridurre i rischi legati alla manomissione della chiave WEP consiste nell'aggiornare le chiavi di sessione client secondo intervalli minori del tempo necessario per intercettare il traffico ed eseguire operazioni di tipo brute force. Questa soluzione può essere messa in opera mediante funzionalità di aggiornamento delle chiavi nei punti di accesso senza fili o impostando le opzioni RADIUS IAS affinché venga imposta la riautenticazione automatica dei client, che comporta l'aggiornamento della chiave WEP.
  
Nella soluzione illustrata in questa guida le opzioni RADIUS IAS vengono configurate in modo da imporre la riautenticazione del client Windows XP Professional ogni 10 minuti per garantire chiavi di sessioni WEP di breve durata. Questa scelta è stata basata sugli attacchi e gli scenari WEP relativi al traffico 802.11a conosciuti al momento della pubblicazione della presente guida.
  
La velocità effettiva massima per lo standard 802.11a è pari al 60% del valore teorico di 54 Mbps, ovvero 32 Mbps. Poiché WEP esegue la crittografia solo dei pacchetti di dati, che sono costituiti in media da 80 byte, il valore della velocità effettiva equivale a 4 Mbps (la crittografia 802.11 prevede circa 40 byte di sovraccarico per pacchetto di dati, incluso un messaggio di riconoscimento (ACK), determinando quindi un risultato di 50.000 pacchetti al secondo). Il traffico 802.11a protetto tramite la crittografia WEP viene considerato sicuro con un intervallo di riautenticazione di 10 minuti, in base agli attacchi conosciuti al momento del rilascio della guida. Questa logica è descritta in dettaglio nei seguenti punti:
  
-   Il sovraccarico di un pacchetto di dati unicast crittografato equivale a 24 byte di intestazione + 8 byte per la crittografia WEP + 4 byte FCS (Frame Check Sequence) + 14 byte per il messaggio di riconoscimento, ovvero 50 byte di sovraccarico per ogni pacchetto di dati inviato. Il sovraccarico di un pacchetto IP è di 20 byte.
  
-   Quindi 32 Mbps/70\*8 = 57.142 pacchetti al secondo
  
-   Per i pacchetti multicast, il messaggio di riconoscimento dei dati non è previsto, quindi:  
    32 Mbps/56\*8 = 71.428 pacchetti al secondo
  
L'utilizzo dell'autenticazione EAP-TLS garantisce inoltre che durante il processo di negoziazione TLS vengano generate chiavi di sessione WEP avanzate e che vengano trasportate senza problemi nella rete tra i componenti della soluzione.
  
Per stabilire la durata della chiave WEP è necessario valutare attentamente il valore dei dati gestiti e le capacità dei potenziali utenti malintenzionati. È inoltre necessario considerare il conseguente incremento del carico sui server IAS quando si sceglie di impostare la riautenticazione frequente dei client.
  
#### Scelta di una strategia di migrazione della rete WLAN
  
Se nell'organizzazione è già attiva una rete senza fili, è necessario scegliere una strategia di migrazione per ridurre al minimo i problemi per gli utenti e l'ambiente.
  
In seguito ad alcune indagini è emerso che molte organizzazioni utilizzano reti WLAN basate sulla tecnologia 802.11 senza alcuna opzione di autenticazione o crittografia. Questo tipo di strategia di protezione 802.11 è definito autenticazione a sistema aperto. Altre organizzazioni implementano soluzioni di crittografia e autenticazione di rete con chiave statica nei client e nei punti di accesso senza fili. Questo tipo di protezione di rete 802.11 è definito autenticazione con chiave condivisa.
  
I processi di migrazione dai modelli di protezione di rete a sistema aperto e con chiave condivisa alla protezione 802.1X sono molto simili. La differenza principale consiste nel fatto che la soluzione con chiave condivisa offre un certo grado di protezione, quindi la pianificazione della migrazione può essere meno urgente per alcune organizzazioni.
  
Il processo di migrazione in genere prevede tre passaggi:
  
1.  **Distribuzione dei certificati a computer e utenti**: questa operazione deve essere completata prima dell'implementazione di 802.1X per garantire che i certificati siano stati distribuiti ai computer portatili con accesso occasionale alla LAN.
  
2.  **Configurazione di criteri di accesso remoto senza fili sui server IAS**: la procedura per la configurazione di un criterio di accesso remoto senza fili è inclusa nella presente guida.
  
3.  **Implementazione delle configurazioni di rete senza fili nei computer client**: la nuova rete abilitata per 802.1X in genere richiede un nuovo identificatore del set di servizi (SSID) di rete e le impostazioni di rete possono essere configurate mediante i criteri di gruppo di Active Directory. I criteri di gruppo WLAN devono essere distribuiti prima della riconfigurazione dei punti di accesso senza fili per garantire che i computer mobili con accesso occasionale alla rete LAN ricevano la configurazione.
  
4.  **Configurazione dei punti di accesso senza fili affinché richiedano la protezione 802.1X**: questa operazione in genere viene eseguita per aree specifiche, ad esempio per un intero edificio o per un gruppo di edifici. È necessario definire procedure appropriate di ripristino nel caso di comportamenti imprevisti e selezionare il personale necessario per consentire all'help desk di gestire in modo adeguato il potenziale incremento delle chiamate.
  
Analogamente a tutte le strategie di migrazione, un'attenta valutazione è essenziale. In genere le fasi che comprendono la configurazione di computer client e punti di accesso senza fili possono causare problemi all'ambiente in uso se non vengono verificate in modo approfondito.
  
**Nota:** alcuni componenti hardware dei punti di accesso supportano la configurazione della comunicazione via radio tramite un adattatore compatibile 802.11b per la protezione preesistente e un altro adattatore radio 802.11b per 802.1X. Tuttavia, problemi legati alla separazione dei canali 802.11b rendono inappropriata questa strategia per la maggior parte delle organizzazioni.
  
È necessario contattare il fornitore delle apparecchiature WLAN per verificare che sia in grado di supportare l'aggiornamento a WPA dei punti di accesso senza fili e le schede di rete senza fili. Microsoft ha rilasciato un aggiornamento di Windows XP che consente di supportare la crittografia WPA. Inoltre, è consigliabile considerare la possibilità di aggiornare l'infrastruttura WLAN affinché supporti lo standard 802.11i, che probabilmente richiederà aggiornamenti dell'hardware.
  
La soluzione presa in esame presuppone l'installazione di un'infrastruttura di rete WLAN di preproduzione su cui possa essere configurato lo standard 802.1X. Nella guida non è descritta in modo dettagliato la progettazione di procedure di migrazione per reti WLAN di produzione mediante soluzioni di protezione proprietarie o a sistema aperto/chiave condivisa. Per informazioni dettagliate sulla migrazione da WLAN di produzione, consultare un partner Microsoft o rivolgersi al responsabile clienti Microsoft che potrà segnalare il partner o un esperto di Microsoft Consulting Services da contattare.
  
#### Progettazione dell'infrastruttura di rete senza fili
  
Una trattazione generale delle apparecchiature e della progettazione delle reti WLAN basate sullo standard 802.11 esula dagli argomenti trattati in questa guida. Nel capitolo dedicato alle reti WLAN di *Microsoft Windows Server 2003 Deployment Kit* (in inglese) sono fornite informazioni dettagliate su questo argomento.
  
In questa guida si è tentato di sviluppare una soluzione che possa funzionare con un'ampia gamma di prodotti distribuiti da vari fornitori di apparecchiature di rete. La pianificazione e le procedure di configurazione per specifici punti di accesso senza fili non rientrano nell'ambito di questa soluzione.
  
Tuttavia, quando si valutano le impostazioni di protezione e la gestione della protezione in relazione all'apparecchiatura 802.11, è necessario approfondire i seguenti argomenti mediante le risorse fornite dal produttore dell'hardware:
  
-   **Nome SSID e password predefinita**: questo argomento include la modifica del SSID predefinito per tutti i punti di accesso e la scelta di configurare o meno i punti di accesso per la trasmissione dei SSID.
  
-   **Modifica della password predefinita della console e delle stringhe SNMP (Simple Network Management Protocol)**: questo argomento include la modifica delle password di gestione predefinite e delle stringhe di accesso nei punti di accesso senza fili e la loro conservazione nel tempo.
  
-   **Amministrazione protetta dei punti di accesso senza fili**: in questo contesto viene esaminato l'utilizzo di comunicazioni protette quando si amministrano i punti di accesso senza fili usufruendo di protocolli quali SSH (Secure Shell) o HTTP (Hypertext Transfer Protocol) con SSL o TLS.
  
-   **Impostazioni del client RADIUS**: questo argomento include la configurazione dei punti di accesso affinché utilizzino i server RADIUS per l'autenticazione e la gestione degli account. Gli argomenti relativi alla configurazione dei punti di accesso per un server RADIUS principale o secondario, all'utilizzo di segreti RADIUS avanzati e all'attributo autenticatore del messaggio sono trattati nel modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" di questa guida. Nel modulo "[Implementazione dell'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536251)" della *Guida all'implementazione* sono incluse istruzioni relative all'utilizzo di uno script per generare segreti RADIUS avanzati.
  
-   **Commutazione e filtraggio del traffico di una VLAN (Virtual Local Area Network)**: nell'ambito di questo argomento viene esaminato l'utilizzo di reti VLAN per limitare l'accesso a varie tipologie di utenti in diversi scenari. Il server IAS può fornire valori RADIUS basati sul criterio di accesso remoto che consentono di selezionare automaticamente le VLAN appropriate durante la connessione client. Per ulteriori informazioni sulle opzioni IAS relative alla specifica di VLAN per i punti di accesso senza fili, consultare i riferimenti indicati nella sezione "Ulteriori informazioni" alla fine di questo modulo.
  
-   **Strategie per limitare l'utilizzo improprio di trasmissioni radio LAN senza fili all'esterno dei limiti dell'edificio**: questo argomento include considerazioni di protezione, ad esempio evitare di posizionare i punti di accesso su muri esterni o su finestre. È inoltre indicato di ridurre la capacità di trasmissione dei punti di accesso quando la copertura può essere limitata all'area necessaria e di evitare la copertura di aree superflue quali i parcheggi.
  
-   **Rilevamento di punti di accesso senza fili inaffidabili**: questo argomento include la ricerca continua di punti di accesso inaffidabili nella rete aziendale mediante strumenti di gestione WLAN (Wide Local Area Network) basati su Windows XP e Windows CE, ad esempio NetStumbler o AirMagnet.
  
Per ulteriori informazioni su questi argomenti e sulla configurazione di punti di accesso senza fili, consultare la documentazione specifica del fornitore o richiedere l'intervento di un esperto dell'apparecchiatura in questione.
  
#### Considerazioni sui criteri di gruppo di reti senza fili
  
È consigliabile consultare l'amministratore dei criteri di gruppo Active Directory per determinare la strategia più adatta per applicare i criteri di gruppo di reti senza fili ai computer client. Gli aspetti da valutare riguardano i criteri di applicazione degli oggetti Criteri di gruppo, la loro posizione in Active Directory e altri fattori. Nella tabella che segue sono elencati alcuni oggetti Criteri di gruppo da prendere in considerazione e le impostazioni selezionate in questa soluzione.
  
**Tabella 7. Pianificazione dei criteri di rete senza fili**

 
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
<td style="border:1px solid black;">Filtraggio dei gruppi basato su Active Directory per includere solo computer selezionati.</td>
<td style="border:1px solid black;">Gruppo globale di computer per i criteri di rete senza fili</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Numero di oggetti Criteri gruppo richiesti</td>
<td style="border:1px solid black;">Un solo criterio di rete senza fili.</td>
<td style="border:1px solid black;">Criteri di rete senza fili</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Posizione oggetto Criteri di gruppo</td>
<td style="border:1px solid black;">Creato e applicato dall'oggetto di dominio.</td>
<td style="border:1px solid black;"><em>ForestRootDomain</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Numero di profili WLAN configurati nel criterio</td>
<td style="border:1px solid black;">Un solo profilo WLAN configurato per le organizzazioni che implementano lo standard 802.1X.</td>
<td style="border:1px solid black;">L'oggetto Criteri di gruppo contiene un profilo WLAN per gli ambienti in cui le reti WLAN non sono state utilizzate per scopi di produzione.<br />
È possibile aggiungere altri profili WLAN per rispondere alle esigenze di una migrazione graduale da una WLAN di produzione precedente.</td>
</tr>
</tbody>
</table>
 

Questa soluzione utilizza una strategia semplificata di gestione dei criteri di rete senza fili basata sulla creazione di un singolo oggetto Criteri di gruppi e sulla sua applicazione all'oggetto di dominio. È tuttavia possibile definire standard di gestione dei criteri di gruppo specifici per l'organizzazione e applicare i criteri di rete senza fili in modo appropriato.

**Nota:** in molti casi le organizzazioni concorderanno sull'esigenza di creare un solo oggetto Criteri di gruppo dei criteri di rete senza fili, ma sceglieranno di crearlo e applicarlo in una posizione diversa dall'oggetto di dominio.

[](#mainsection)[Inizio pagina](#mainsection)

### Impostazioni software necessarie per le reti WLAN 802.1X

Per garantire un livello di protezione adeguato delle WLAN 802.1X, è necessario configurare due principali componenti software:

-   Criteri di accesso alla rete su base IAS

-   Criteri di gruppo su base Active Directory per computer client

I criteri di accesso alla rete su base IAS costituiscono il nucleo centrale di una soluzione di gestione dell'accesso. Le impostazioni relative ai criteri di protezione delle reti WLAN vengono implementate in modo automatico in ogni server RADIUS su base IAS. In questi criteri sono incluse impostazioni relative ai seguenti elementi:

-   Criteri di accesso remoto

-   Criteri richiesta di connessione

I criteri di accesso remoto definiscono l'accesso alle reti attraverso i punti di accesso senza fili. I criteri richiesta di connessione determinano la gestione delle richieste RADIUS da vari punti di accesso senza fili configurati come clienti RADIUS.

I criteri di gruppo basati su Active Directory per computer client contengono tutte le impostazioni che verranno implementate nei client Windows XP. Questi criteri di gruppo influiscono sul modo in cui i client interagiscono con i punti di accesso senza fili, il server RADIUS e le altre reti senza fili.

#### Configurazione dei criteri di accesso remoto

La creazione di criteri di accesso remoto sui server IAS è necessaria per poter applicare la strategia di accesso alle reti senza fili dell'organizzazione. Il processo di creazione e configurazione dei criteri di accesso remoto comprende la definizione di tre tipi di impostazioni per ogni criterio:

-   Condizioni del criterio

-   Autorizzazioni del criterio

-   Profilo del criterio

In questa soluzione viene utilizzato un singolo criterio di accesso remoto che garantisce accesso senza restrizioni alla rete senza fili per i dipendenti. Nella tabella che segue sono descritte in dettaglio le condizioni del criterio di accesso remoto scelte per questa soluzione.

**Tabella 8. Condizioni del criterio di accesso remoto**

 
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
<td style="border:1px solid black;">Tipo - porta - NAS</td>
<td style="border:1px solid black;">Senza fili - Altro<br />
oppure<br />
&quot;Senza fili - IEEE 802.11&quot;</td>
<td style="border:1px solid black;">Identifica le richieste in ingresso come provenienti dall'hardware dei punti di accesso senza fili.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Gruppo - Windows</td>
<td style="border:1px solid black;">Criterio di accesso remoto: appartenenza al gruppo di protezione Wireless Access.</td>
<td style="border:1px solid black;">Gruppo di protezione universale basato su Active Directory che contiene gruppi globali nidificati per utenti e computer che avranno accesso alla rete WLAN.</td>
</tr>
</tbody>
</table>
  
L'autorizzazione del criterio di accesso remoto adottato in questa soluzione è impostata su **Concedi** e gli account utente sono configurati con l'impostazione **Controlla accesso tramite Criteri di accesso remoto**.
  
Nella tabella che segue sono descritte in dettaglio le opzioni del profilo del criterio di accesso remoto utilizzate in questa soluzione. Potrebbero essere necessarie impostazioni aggiuntive per rispondere a esigenze specifiche dell'ambiente.
  
**Tabella 9. Opzioni del profilo del criterio di accesso remoto**

 
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
<td style="border:1px solid black;">10</td>
<td style="border:1px solid black;">Questa impostazione impone ai computer client di eseguire una nuova autenticazione ogni 10 minuti. Rappresenta una soluzione ideale per garantire che le chiavi WEP vengano aggiornate.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Autenticazione: metodi EAP</td>
<td style="border:1px solid black;">Smart card o altro certificato</td>
<td style="border:1px solid black;">Questa impostazione seleziona EAP-TLS come tipo EAP per il profilo senza fili.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Attributo RADIUS Ignore<strong>-</strong>User<strong>-</strong>Dial-in-Properties</td>
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
  
#### Configurazione dei criteri richiesta di connessione
  
È necessario scegliere il modo in cui il servizio IAS gestirà le richieste RADIUS quando viene utilizzato come server RADIUS e proxy RADIUS. La scelta del ruolo RADIUS per il servizio IAS è illustrata nel modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" di questa guida.
  
Indipendentemente dal ruolo scelto per il server IAS, è necessario configurare i seguenti componenti dei criteri richiesta di connessione per poter ottenere accesso alla rete senza fili:
  
-   Condizioni del criterio
  
-   Profilo del criterio
  
Nella soluzione proposta IAS viene utilizzato come server RADIUS e, quindi, le richieste di connessione vengono gestite localmente dai singoli server. Le impostazioni riportate nella tabella che segue illustrano le condizioni dei criteri configurate nel criterio richiesta di connessione adottato per questa soluzione.
  
**Nota:** le impostazioni del criterio richiesta di connessione in questa soluzione utilizzano i valori predefiniti per l'installazionedel servizio IAS di Windows Server 2003.
  
**Tabella 10. Condizioni del criterio richiesta di connessione**

 
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
<td style="border:1px solid black;">&quot;Restrizioni data e ora&quot;</td>
<td style="border:1px solid black;">&quot;Lun 00:00 - 24:00,<br />
Mar 00:00 - 24:00,<br />
Gio 00:00 - 24:00,<br />
Ven 00:00 - 24:00,<br />
Sab 00:00 - 24:00,<br />
Dom 00:00- 4:00&quot;</td>
<td style="border:1px solid black;">Questa condizione del criterio richiesta di connessione predefinito garantisce che le richieste di connessione ricevute in qualsiasi orario siano conformi al criterio.</td>
</tr>
</tbody>
</table>
  
Nella tabella che segue sono illustrate le impostazioni del profilo utilizzate nel criterio richiesta di connessione scelto per questa soluzione.
  
**Tabella 11. Impostazioni del profilo relativo al criterio richiesta di connessione**

 
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
<td style="border:1px solid black;">Questa impostazione garantisce che le richieste vengano autenticate direttamente sulla base di Active Directory.</td>
</tr>
</tbody>
</table>
  
#### Configurazione dei criteri di gruppo per i computer client
  
È necessario eseguire un'attenta pianificazione prima di utilizzare criteri di gruppo basati su Active Directory per configurare le impostazioni della rete WLAN e le impostazioni di protezione dello standard 802.1X nei client mediante i criteri di rete senza fili (IEEE 802.11). In questa sezione sono descritte in dettaglio alcune impostazioni scelte per questa soluzione e le motivazioni di tale scelta. I criteri di rete senza fili (IEEE 802.11) sono disponibili nell'oggetto \\Configurazione computer\\Impostazioni di Windows\\Impostazioni di protezione\\Criteri di accesso senza fili (IEEE 802.11) nell'Editor oggetti Criteri di gruppo.
  
##### Configurazione delle impostazioni delle reti senza fili
  
La configurazione delle impostazioni WLAN viene eseguita modificando le proprietà degli oggetti Criteri di gruppo WLAN nel criterio di gruppo specifico e include impostazioni relative alle seguenti aree:
  
-   Impostazioni generali
  
-   Reti preferite
  
-   Proprietà di rete
  
Nella tabella che segue sono illustrate le impostazioni generali del criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 12. Impostazioni generali dei criteri di rete senza fili**

 
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
<td style="border:1px solid black;">Nome</td>
<td style="border:1px solid black;">Configurazione senza fili del computer client</td>
<td style="border:1px solid black;">Questo valore può essere modificato in base agli standard di denominazione dell'organizzazione.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rete a cui accedere</td>
<td style="border:1px solid black;">La rete disponibile (di preferenza con punto di accesso)</td>
<td style="border:1px solid black;">Questa impostazione scoraggia i computer client dall'eseguire connessioni di rete ad-hoc con altri computer configurati con lo stesso SSID utilizzato per la rete 802.1X. Tuttavia, la possibilità di stabilire connessioni di rete ad-hoc consente ai dipendenti di utilizzare reti ad-hoc quando è necessario, ad esempio da casa, e per questo si è scelto di consentirne l'uso.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Connetti automaticamente alle reti non preferite</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">In Windows XP Professional agli utenti viene fornita automaticamente una notifica delle reti senza fili disponibili senza tuttavia stabilire direttamente la connessione. In questo modo è possibile ottenere un equilibrio ottimale tra protezione e utilizzabilità.</td>
</tr>
</tbody>
</table>
  
È necessario creare una voce per la nuova WLAN 802.1X nella scheda **Reti preferite** del criterio di rete senza fili. Dopo aver specificato una rete preferita, è necessario modificare i valori predefiniti delle proprietà della rete.
  
Nella tabella che segue sono descritte in dettaglio le impostazioni delle proprietà di rete relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili adottato per questa soluzione.
  
**Tabella 13. Impostazioni delle proprietà di rete dei criteri di rete senza fili**

 
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
<td style="border:1px solid black;">Nome</td>
<td style="border:1px solid black;">MSSWLAN</td>
<td style="border:1px solid black;">Modificare questo valore in modo conforme agli standard di denominazione dell'organizzazione. È necessario, tuttavia, scegliere un nome diverso da qualsiasi WLAN di produzione esistente.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Chiave rete senza fili (WEP) - Crittografia dati (WEP abilitato)</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">La crittografia è essenziale per proteggere la riservatezza del traffico di rete senza fili nelle reti 802.11. Se nell'organizzazione sono supportate reti 802.11, è necessario garantire che siano protette mediante la crittografia WEP o di altro tipo.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Chiave rete senza fili (WEP) - Autenticazione di rete (modalità condivisa)</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">La protezione 802.11 con chiave condivisa rappresenta una strategia di protezione basata su chiavi WEP statiche. In questa soluzione lo standard 802.1X viene utilizzato per fornire chiavi di sessione WEP dinamiche e, quindi, questa opzione è deselezionata.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Chiave rete senza fili (WEP) - Chiave fornita automaticamente</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">In questa soluzione lo standard 802.1X viene utilizzato per fornire chiavi di sessione WEP dinamiche allo scopo di eseguire la crittografia del traffico.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Rete computer a computer (ad hoc). I punti di accesso senza fili non sono utilizzati</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">In questa soluzione è stata scelta la modalità di infrastruttura WLAN 802.11 con punti di accesso senza fili configurati per lo standard 802.1X.</td>
</tr>
</tbody>
</table>
  
##### Configurazione delle impostazioni 802.1X nei computer client
  
La configurazione delle impostazioni relative allo standard 802.1X viene eseguita mediante criteri di rete senza fili e include impostazioni relative alle seguenti aree:
  
-   Parametri 802.1X
  
-   Tipo di EAP
  
-   Convalida delle credenziali
  
-   Procedura di autenticazione basata su computer
  
Nella tabella che segue sono descritte in dettaglio le impostazioni 802.1X relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 14. Impostazioni 802.1X dei criteri di rete senza fili**

 
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
<td style="border:1px solid black;">Attiva</td>
<td style="border:1px solid black;">Questa opzione consente al computer client di accedere alle reti protette mediante lo standard 802.1X</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Messaggio di avvio EAPOL</td>
<td style="border:1px solid black;">Trasmissione</td>
<td style="border:1px solid black;">Questo messaggio indica al client di avviare il processo di autenticazione.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Parametri (secondi) - Avvio massimo</td>
<td style="border:1px solid black;">3</td>
<td style="border:1px solid black;">Questo valore determina il numero di messaggi di avvio consecutivi EAPOL (EAP over LAN) che il client trasmetterà quando non riceve risposta. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Parametri (secondi) - Periodo di sospensione</td>
<td style="border:1px solid black;">60</td>
<td style="border:1px solid black;">Questo valore determina l'intervallo di tempo che trascorrerà prima che il client tenti di nuovo un processo di autenticazione 802.1X non riuscito. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Parametri (secondi) - Periodo di avvio</td>
<td style="border:1px solid black;">60</td>
<td style="border:1px solid black;">Questo valore determina l'intervallo di tempo che deve trascorrere tra i messaggi di avvio EAPOL per eseguire di nuovo l'invio. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Periodo di autenticazione</td>
<td style="border:1px solid black;">30</td>
<td style="border:1px solid black;">Questo valore determina l'intervallo di tempo che deve intercorrere tra i messaggi di richiesta 802.1X rinviati quando non si riceve una risposta. L'impostazione predefinita di questo valore non deve essere modificata se non espressamente richiesto.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Tipo di EAP</td>
<td style="border:1px solid black;">Smart card o altro certificato</td>
<td style="border:1px solid black;">Questa opzione specifica EAP-TLS come tipo di EAP.</td>
</tr>
</tbody>
</table>
  
Nella tabella che segue sono descritte in dettaglio le impostazioni EAP relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 15. Impostazioni EAP dei criteri di rete senza fili**

 
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
<td style="border:1px solid black;">Utilizza un certificato su questo computer.</td>
<td style="border:1px solid black;">Questa opzione specifica l'uso di certificati su base software e chiavi private anziché di credenziali smart card.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Utilizza un certificato su questo computer - Utilizza selezione certificati semplice (opzione consigliata)</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">Con questa opzione la scelta del certificato corretto verrà basata automaticamente sulle proprietà dei certificati. L'opzione può essere disattivata per consentire la selezione manuale del certificato corretto durante la risoluzione dei problemi.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Convalida certificato server</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">Questa opzione consente di determinare se il certificato presentato al client durante l'autenticazione EAP-TLS è compreso nell'intervallo di date valide specificato.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Convalida certificato server - Connetti ai server seguenti</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">Questa opzione consente di controllare il suffisso del nome completo di dominio (FQDN) nel campo soggetto del certificato server. Se questa opzione è attivata, nei computer client verrà visualizzata una finestra di testo in cui si richiede l'approvazione del server IAS come attendibile. In questo caso è necessario valutare il rapporto tra utilizzabilità e protezione per scegliere se attivare l'opzione.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Convalida certificato server - Connetti ai server seguenti - Valore</td>
<td style="border:1px solid black;">Vuota</td>
<td style="border:1px solid black;">Questo valore specifica il suffisso del nome completo di dominio che deve corrispondere alle informazioni del soggetto nel certificato presentato al client durante l'autenticazione EAP-TLS.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Autorità di certificazione principali attendibili</td>
<td style="border:1px solid black;">CAsocietà selezionata</td>
<td style="border:1px solid black;">Questa opzione consente agli amministratori di specificare le CA principali attendibili a cui è possibile concatenare le credenziali dei certificati server 802.1X. Per questa opzione è necessario selezionare le proprie CA principali attendibili.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Utilizza un nome utente diverso per la connessione</td>
<td style="border:1px solid black;">Deselezionata</td>
<td style="border:1px solid black;">Questa opzione consente agli utenti di specificare un nome utente diverso da quello contenuto nel certificato presentato durante l'autenticazione EAP-TLS.</td>
</tr>
</tbody>
</table>
  
Nella tabella che segue sono descritte in dettaglio le impostazioni di autenticazione client relative alla nuova rete abilitata per lo standard 802.1X nel criterio di rete senza fili scelto per questa soluzione.
  
**Tabella 16. Opzioni di autenticazione del computer 802.1X**

 
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
<td style="border:1px solid black;">Questa impostazione stabilisce se il computer può eseguire l'accesso come Guest se non è disponibile alcuna credenziale. Si tratta di una soluzione utile per reti WLAN pubbliche o per utenti esterni all'organizzazione.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Autentica come computer se le informazioni sono disponibili</td>
<td style="border:1px solid black;">Selezionata</td>
<td style="border:1px solid black;">Questa impostazione è essenziale per garantire che l'autenticazione del computer venga eseguita quando gli utenti non sono collegati al computer.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Autenticazione basata su computer</td>
<td style="border:1px solid black;">Con riautenticazione utente</td>
<td style="border:1px solid black;">Questa opzione predefinita consente di garantire che vengano utilizzate le credenziali utente quando possibile. Tuttavia, quando gli utenti non sono connessi al computer, verranno utilizzate le credenziali computer per garantire che la connessione alla rete sia sempre disponibile.</td>
</tr>
</tbody>
</table>
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Ulteriori considerazioni
  
In questa sezione sono trattati brevemente altri argomenti da prendere in considerazione che non rientrano nell'ambito di questa soluzione ma possono influire sull'ambiente in uso.
  
#### Supporto di profili comuni e utenti mobili
  
Per garantire il funzionamento dei componenti 802.1X di Windows su base EAP-TLS, è necessario che i certificati e le chiavi private siano disponibili nell'archivio certificati sui computer client. In molte organizzazioni, gli utenti senza fili utilizzano computer portatili o Tablet PC in viaggio, avendo così sempre a disposizione i certificati e le chiavi private.
  
Tuttavia, se la strategia IT adottata prevede la possibilità condividere computer tra più utenti, è consigliabile valutare l'implementazione di profili mobili. I profili mobili consentono di garantire che le chiavi private e i certificati siano sempre disponibili per poter essere utilizzati nell'ambito dello standard 802.1X.
  
I criteri di rete senza fili inoltre consentono di configurare i computer che eseguono Windows XP affinché eseguano l'autenticazione esclusivamente di computer. Sebbene questa configurazione non sia implementata nella soluzione, può risultare utile in alcune organizzazioni.
  
#### Supporto di client senza connessioni alla rete LAN cablata
  
Sebbene sia inusuale per le grandi organizzazioni, in alcuni ambienti potrebbe non essere stata implementata la struttura LAN cablata necessaria per unire i computer client a un dominio e, quindi, distribuire i certificati e i criteri di gruppo. Senza i certificati dei computer e degli utenti e una configurazione appropriata della WLAN dei client, gli utenti non saranno in grado di accedere alla rete WLAN basata sullo standard 802.1X.
  
Se si utilizza questo tipo di ambiente, è opportuno considerare una strategia in cui gli utenti forniscono credenziali basate su password mediante il protocollo PEAP-MSCHAPv2 al server RADIUS per la connessione a una rete VLAN controllata mediante le pagine Web di registrazione di Servizi certificati. In questo modo gli utenti possono eseguire la registrazione e installare certificati per ottenere accesso completo alla rete WLAN aziendale mediante l'autenticazione EAP-TLS. Una strategia di questo tipo non rientra nell'ambito della soluzione proposta e richiederebbe un criterio di accesso remoto aggiuntivo sui server IAS, oltre a una progettazione specifica della rete VLAN.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Riepilogo
  
In questo modulo è stato esaminato il processo di progettazione della protezione delle reti WLAN mediante lo standard 802.1X, che include l'individuazione dei requisiti, la valutazione delle opzioni di protezione, lo sviluppo di una strategia e considerazioni di altro tipo. Dopo aver definito la progettazione in base alle opzioni descritte in questo modulo, sarà possibile implementare la protezione delle reti WLAN basata sullo standard 802.1X nell'ambiente in uso.
  
Le considerazioni sulla progettazione illustrate in questo modulo verranno utilizzate nella *Guida all'implementazione* e nella *Guida operativa* per implementare la protezione delle reti WLAN sulla base dello standard 802.1X.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Ulteriori informazioni
  
Per ulteriori informazioni sulla protezione delle reti senza fili, vedere quanto riportato di seguito:
  
-   Il sito Web del supporto tecnico di Windows Server 2003, disponibile all'indirizzo:  
    <http://technet.microsoft.com/en-us/windowsserver/bb512923.aspx> (in inglese).
  
    La documentazione del prodotto include una panoramica delle funzionalità di IAS, istruzioni essenziali per la configurazione e procedure consigliate per la distribuzione.
  
-   Il capitolo relativo al supporto degli utenti mobili nel *Microsoft Windows Server 2003 Resource Kit*, disponibile all'indirizzo:  
    <http://www.microsoft.com/windowsserver2003/techinfo/reskit/resourcekit.mspx> (in inglese).
  
    In questo capitolo del *Resource Kit* sono incluse informazioni tecniche su IAS più dettagliate di quelle contenute nella documentazione del prodotto, che possono essere utilizzate come riferimento per approfondire argomenti specifici.
  
-   Il capitolo relativo alla distribuzione di una LAN senza fili del *Microsoft Windows Server 2003 Deployment Kit*, disponibile all'indirizzo:  
    <http://www.microsoft.com/windowsserver2003/techinfo/reskit/deploykit.mspx> (in inglese).
  
    Questo capitolo del *Deployment Kit* contiene una guida alla distribuzione per l'utilizzo del servizio IAS in vari scenari che non rientrano nell'ambito della presente guida alla protezione delle reti senza fili, ma che influiscono sulle scelte di progettazione.
  
-   Per una trattazione completa delle reti WLAN 802.1X, dei problemi di protezione delle reti WLAN e degli standard correlati, vedere: [http://www.drizzle.com/~aboba/IEEE/](http://www.drizzle.com/~aboba/ieee/) (in inglese).
  
-   Per ulteriori informazioni sulle soluzioni WLAN e sul settore specifico, visitare il sito Web Wi-Fi Alliance disponibile all'indirizzo:  
    [http://www.wi-fialliance.org](http://www.wi-fialliance.org/) (in inglese).
  
-   Per informazioni sulle reti WLAN, incluse informazioni di carattere generale, ricerche di mercato, white paper e programmi di formazione, visitare il sito Web dell'associazione WLANA (Wireless LAN Association), disponibile all'indirizzo: <http://www.wlana.org/learning_center.html> (in inglese).
  
-   Per informazioni su EAP-TLS, EAPOL, EAP-RADIUS, RADIUS e altri standard Internet utilizzati con 802.1X, visitare il sito Web IETF (Internet Engineering Task Force), disponibile all'indirizzo: <http://www.ietf.org/> (in inglese).
  
-   Gli standard WLAN specifici includono: 802.11, 802.11b, 802.11a, 802.1X, 802.11i e altri. Per informazioni su questo argomento, visitare l'area relativa agli standard senza fili del sito Web IEEE (Institute of Electrical and Electronics Engineers), disponibile all'indirizzo:  
    <http://standards.ieee.org/wireless/> (in inglese).
  
Per ulteriori informazioni sulle tecnologie WLAN 802.1X, vedere:
  
-   Il white paper "Windows XP Wireless Deployment Technology and Component Overview" nel sito Web Microsoft disponibile all'indirizzo:  
    <http://technet.microsoft.com/en-us/library/bb457015.aspx> (in inglese).
  
#### Elementi di configurazione definiti dall'utente
  
Prima di iniziare la procedura di impostazione, è necessario verificare di aver individuato o scelto le impostazioni per tutti gli elementi riportati nella tabella che segue.
  
**Tabella 17. Elementi di configurazione definiti dall'utente**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Elemento di configurazione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Nome variabile</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Nome di dominio DNS per la radice di strutture Active Directory</td>
<td style="border:1px solid black;">woodgrovebank.com</td>
<td style="border:1px solid black;"><em>ForestRootDomain</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nome NetBIOS del dominio</td>
<td style="border:1px solid black;">WOODGROVE</td>
<td style="border:1px solid black;"><em>NBDomainName</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Nome del server IAS primario</td>
<td style="border:1px solid black;">HQIAS - 01</td>
<td style="border:1px solid black;"><em>PrimaryIAShostname</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nome del server IAS secondario</td>
<td style="border:1px solid black;">HQ - IAS - 02</td>
<td style="border:1px solid black;"><em>SecondaryIAShostname</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Nome del server IAS opzionale delle filiali</td>
<td style="border:1px solid black;">BO - IAS - 03</td>
<td style="border:1px solid black;"><em>TertiaryIAShostname</em></td>
</tr>
</tbody>
</table>
  
#### Elementi di configurazione prescritti nella soluzione
  
Le impostazioni specificate in questa tabella non devono essere modificate se non se ne ha una particolare necessità.
  
**Tabella 18. Elementi di configurazione richiesti dalla soluzione**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Elemento di configurazione</th>
<th style="border:1px solid black;" >Impostazione</th>
<th style="border:1px solid black;" >Nome variabile</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo globale di Microsoft Active Directory in cui sono inclusi gli utenti che richiedono certificati di autenticazione 802.1X</td>
<td style="border:1px solid black;">Registrazione automatica certificato utente di autenticazione client</td>
<td style="border:1px solid black;"><em>EnrollUserCertGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Nome precedente a Windows 2000 per il gruppo globale di Active Directory in cui sono inclusi gli utenti che richiedono certificati di autenticazione 802.1X</td>
<td style="border:1px solid black;">Registrazione automatica certificato utente di autenticazione client</td>
<td style="border:1px solid black;"><em>EnrollUserCertNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi i computer che richiedono certificati di autenticazione 802.1X</td>
<td style="border:1px solid black;">Registrazione automatica certificato computer di autenticazione client</td>
<td style="border:1px solid black;"><em>EnrollComputerCertGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Nome precedente a Windows 2000 per il gruppo globale di Active Directory in cui sono inclusi i computer che richiedono certificati di autenticazione 802.1X</td>
<td style="border:1px solid black;">Registrazione automatica certificato computer di autenticazione client</td>
<td style="border:1px solid black;"><em>EnrollComputerCertNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi server IAS che richiedono certificati di autenticazione 802.1X</td>
<td style="border:1px solid black;">Registrazione automatica certificato di autenticazione server RAS e IAS</td>
<td style="border:1px solid black;"><em>EnrollIASCertGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Nome precedente a Windows 2000 per il gruppo globale di Active Directory in cui sono inclusi server IAS che richiedono certificati di autenticazione 802.1X</td>
<td style="border:1px solid black;">Registrazione automatica certificato di autenticazione server RAS e IAS</td>
<td style="border:1px solid black;"><em>EnrollIASCertNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi gli utenti a cui è concesso l'accesso alla rete senza fili</td>
<td style="border:1px solid black;">Criteri di accesso remoto - Utenti senza fili</td>
<td style="border:1px solid black;"><em>WLANUsersGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Nome precedente a Windows 2000 per il gruppo globale di Active Directory in cui sono inclusi gli utenti a cui è concesso l'accesso alla rete senza fili</td>
<td style="border:1px solid black;">Criteri di accesso remoto - Utenti senza fili</td>
<td style="border:1px solid black;"><em>WLANUsersNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi i computer a cui è concesso l'accesso alla rete senza fili</td>
<td style="border:1px solid black;">Criteri di accesso remoto - Computer senza fili</td>
<td style="border:1px solid black;"><em>WLANComputersGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi i computer a cui è concesso l'accesso alla rete senza fili</td>
<td style="border:1px solid black;">Criteri di accesso remoto - Computer senza fili</td>
<td style="border:1px solid black;"><em>WLANComputersNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo universale di Active Directory in cui sono inclusi il gruppo Utenti senza fili e il gruppo Computer senza fili</td>
<td style="border:1px solid black;">Criteri di accesso remoto - Accesso senza fili</td>
<td style="border:1px solid black;"><em>WLANAccessGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Gruppo universale di Active Directory in cui sono inclusi il gruppo Utenti senza fili e il gruppo Computer senza fili</td>
<td style="border:1px solid black;">Criteri di accesso remoto - Accesso senza fili</td>
<td style="border:1px solid black;"><em>WLANAccessNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi i computer che richiedono la configurazione di proprietà di rete senza fili</td>
<td style="border:1px solid black;">Criteri di rete senza fili - Computer</td>
<td style="border:1px solid black;"><em>WLANConfigPolicyGroup</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Gruppo globale di Active Directory in cui sono inclusi i computer che richiedono la configurazione di proprietà di rete senza fili</td>
<td style="border:1px solid black;">Criteri di rete senza fili - Computer</td>
<td style="border:1px solid black;"><em>WLANConfigPolicyNTGroup</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Certificati] Modello di certificato utilizzato per generare certificati per l'autenticazione client di utenti</td>
<td style="border:1px solid black;">Autenticazione client - Utenti</td>
<td style="border:1px solid black;"><em>UserClientAuthTemplate</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Certificati] Modello di certificato utilizzato per generare certificati per l'autenticazione client di computer</td>
<td style="border:1px solid black;">Autenticazione client - Computer</td>
<td style="border:1px solid black;"><em>ComputerClientAuthTemplate</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Certificati] Modello di certificato utilizzato per generare certificati per l'autenticazione server eseguita da IAS</td>
<td style="border:1px solid black;">Autenticazione server RAS e IAS</td>
<td style="border:1px solid black;"><em>IASServerCertificate</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Scripts] Percorso degli script di installazione</td>
<td style="border:1px solid black;">C:\MSSScripts</td>
<td style="border:1px solid black;"><em>ScriptPath</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Config] Percorso dei file di backup della configurazione</td>
<td style="border:1px solid black;">D:\IASConfig</td>
<td style="border:1px solid black;"><em>ConfigPath</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Config] Percorso dei file di configurazione del client RADIUS</td>
<td style="border:1px solid black;">D:\ClientIAS</td>
<td style="border:1px solid black;"><em>IASClientPath</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Request Logs] Percorso dei registri delle richieste di autenticazione e controllo IAS</td>
<td style="border:1px solid black;">D:\IASLogs</td>
<td style="border:1px solid black;"><em>IASRequestLogLocation</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Criteri di accesso remoto] Nome criterio</td>
<td style="border:1px solid black;">Consenti accesso senza fili</td>
<td style="border:1px solid black;"><em>IASRAPName</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Criteri di gruppo] Nome dell'oggetto Criteri di gruppo di Active Directory</td>
<td style="border:1px solid black;">Criterio di rete senza fili</td>
<td style="border:1px solid black;"><em>GPONameForWLAN</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Criterio di gruppo] Criterio di rete senza fili nell'oggetto Criteri di gruppo</td>
<td style="border:1px solid black;">Configurazione senza fili del computer client</td>
<td style="border:1px solid black;"><em>ClientWLANPolicy</em></td>
</tr>
</tbody>
</table>
  
[](#mainsection)[Inizio pagina](#mainsection)
