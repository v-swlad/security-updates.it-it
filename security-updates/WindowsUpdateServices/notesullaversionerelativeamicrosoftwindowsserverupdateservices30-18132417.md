---
TOCTitle: 'Note sulla versione relative a Microsoft Windows Server Update Services 3.0'
Title: 'Note sulla versione relative a Microsoft Windows Server Update Services 3.0'
ms:assetid: '94d1385f-4872-4c29-8822-3a4ec5e45ae4'
ms:contentKeyID: 18132417
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc708491(v=WS.10)'
---

Note sulla versione relative a Microsoft Windows Server Update Services 3.0
===========================================================================

In queste note sulla versione si descrivono i problemi noti di Microsoft® Windows® Server Update Services (WSUS) 3.0 e vengono forniti consigli e requisiti per installare l'applicazione. Le note contengono le sezioni riportate di seguito:

-   Requisiti di sistema per l'installazione del server WSUS 3.0
-   Requisiti di configurazione per l'installazione del server WSUS 3.0
-   Requisiti di sistema per l'installazione della console remota di WSUS 3.0
-   Requisiti di configurazione per le console remote di WSUS 3.0
-   Requisiti di sistema per l'installazione del client
-   Requisiti software per l'installazione del server WSUS 3.0
-   Requisiti minimi di spazio su disco per l'installazione del server WSUS 3.0
-   Requisiti di aggiornamento per WSUS 3.0
-   Impostazione dei parametri della riga di comando
-   Problemi di configurazione e aggiornamento
-   Problemi noti
-   WSUS 3.0 su Windows Server® 2008
-   WSUS 3.0 in Windows Small Business Server 2003

| ![](images/Cc708491.note(WS.10).gif)Nota                                                                                                                                                                        |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| È possibile scaricare una copia di questo documento dall'[Area download Microsoft](http://go.microsoft.com/fwlink/?linkid=71220) all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=71220](http://go.microsoft.com/fwlink/?linkid=71220). |

Problema importante relativo alla configurazione: è necessario sovrascrivere la password del server proxy nella configurazione guidata
--------------------------------------------------------------------------------------------------------------------------------------

Quando si utilizza un server proxy che richiede l'autenticazione di nome e password, se durante la Configurazione guidata del server WSUS non viene sovrascritta la password del server proxy, potrebbe essere impossibile per il server WSUS sincronizzare gli aggiornamenti. Poiché la configurazione guidata viene avviata automaticamente alla fine dell'installazione, questo problema può causare errori di sincronizzazione dopo l'aggiornamento da una versione precedente di WSUS a WSUS 3.0.

Per evitare questo problema, annullare la configurazione guidata dopo l'aggiornamento oppure immettere di nuovo la password del proxy corretta durante la configurazione guidata. Per risolvere il problema nel momento in cui si verifica, passare ad **Origine aggiornamenti e server proxy** nella pagina **Opzioni**, immettere di nuovo la password proxy, quindi salvare l'impostazione.

Requisiti di sistema per l'installazione del server WSUS 3.0
------------------------------------------------------------

#### Il server WSUS 3.0 è supportato in Windows Server 2003 Service Pack 1 e Windows Server 2008

Il server WSUS 3.0 server è supportato in Windows Server 2003 Service Pack 1 e Windows Server 2008.

#### Windows 2000 Server non è supportato per i server WSUS 3.0

Microsoft Windows® 2000 Server non è un sistema operativo supportato per i server WSUS 3.0.

#### WSUS 3.0 non è supportato nei server che eseguono Servizi terminal

Anche se WSUS 3.0 può essere ancora eseguito sui server che utilizzano i Servizi terminal, questa operazione non è supportata né consigliata. WSUS 3.0 non verrà eseguito su un server su cui è in esecuzione Servizi terminal nelle configurazioni che utilizzano implementazioni remote di SQL Server. Dal momento che tutte le operazioni di personalizzazione remota, compresa l'installazione, su un server con licenza Servizi terminal viene eseguita come account di sistema e che l'account di sistema del server potrebbe non disporre delle autorizzazioni necessarie su SQL Server remoto, è probabile che l'installazione non venga eseguita correttamente.

Requisiti di configurazione per l'installazione del server WSUS 3.0
-------------------------------------------------------------------

#### IIS deve essere installato

Microsoft Windows Server Update Services 3.0 richiede Internet Information Services (IIS), il quale non viene installato per impostazione predefinita su Microsoft Windows Server 2003 o Windows Server 2008. Se si tenta di installare WSUS 3.0 senza IIS, verrà visualizzato un messaggio di errore del programma di installazione di Windows Server Update Services che indica l'assenza di IIS

#### Se IIS è in esecuzione in modalità isolamento IIS 5.0, non sarà possibile eseguire l'installazione

Se il server è stato aggiornato da Windows 2000 Server a Windows Server 2003, IIS potrebbe essere in esecuzione in modalità di compatibilità IIS 5.0. È possibile inoltre abilitare la modalità isolamento IIS 5.0 in Gestione IIS. In questo modo l'installazione avrà esito negativo. Prima di installare WSUS 3.0, sarà necessario disattivare la modalità isolamento IIS 5.0.

#### Se uno o più componenti di IIS sono installati in modalità di compatibilità a 32 bit su una piattaforma a 64 bit, l'installazione di WSUS 3.0 potrebbe avere esito negativo

Tutti i componenti IIS devono essere installati in modalità nativa su piattaforme a 64 bit. L'installazione potrebbe avere esito negativo se uno o più componenti di ISS sono in modalità di compatibilità a 32 bit.

#### I server proxy devono supportare entrambi i protocolli HTTP e HTTPS

Quando si configura il server WSUS principale, ovvero quello che ottiene gli aggiornamenti direttamente da Microsoft Update, ed è presente un server proxy tra il server WSUS e Internet, è necessario che il server proxy supporti entrambi i protocolli HTTP e HTTPS.

#### Se due o più siti Web sono già in esecuzione sulla porta 80, eliminarli tutti tranne uno prima di installare WSUS

Se sulla porta 80 risultano due o più siti Web in esecuzione (ad esempio Windows® SharePoint® Services), si consiglia di eliminarli tutti tranne uno prima di installare WSUS. In caso contrario potrebbe risultare impossibile eseguire l'aggiornamento automatico dei client del server.

#### Quando si installa WSUS 3.0, potrebbe essere necessario disattivare programmi antivirus

Quando si installa WSUS 3.0 potrebbe essere necessario disattivare programmi antivirus prima di eseguire l'installazione correttamente. Dopo aver disattivato i programmi antivirus e prima di avviare l'installazione di WSUS, riavviare il computer. Il riavvio del computer impedisce che i file vengano bloccati quando il processo di installazione ha bisogno di accedere ad essi. Al termine dell'installazione, assicurarsi di riattivare il programma antivirus. Visitare il sito Web del produttore del programma antivirus per informazioni sulle procedure corrette relative alla disattivazione e riattivazione del programma antivirus e sulla versione.

| ![](images/Cc708491.Caution(WS.10).gif)Attenzione                                                                                                                                                                                                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Questa soluzione alternativa potrebbe rendere il computer o la rete in uso più vulnerabile agli attacchi da parte di utenti malintenzionati o di software dannoso, ad esempio virus. Non è consigliabile questa soluzione alternativa ma tali informazioni vengono fornite in modo che sia possibile implementarla a propria discrezione. Utilizzare questa soluzione alternativa a proprio rischio e pericolo. |

| ![](images/Cc708491.note(WS.10).gif)Nota                                                                                                                                                                                                                              |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Un programma antivirus è progettato per aumentare la protezione del computer in uso dai virus. Non si devono scaricare o aprire file provenienti da origini non attendibili, visitare siti Web non attendibili o aprire allegati di posta elettronica quando il programma antivirus è disattivato. |

#### In SQL Server deve essere attivata l'opzione relativa ai trigger nidificati

Questa opzione è attivata per impostazione predefinita ma può essere disattivata da un amministratore di SQL Server.

Se si desidera utilizzare un database di SQL Server come archivio dati di Windows Server Update Services, l'amministratore di SQL Server dovrà verificare che l'opzione relativa ai trigger nidificati venga attivata nel server prima che l'amministratore di WSUS 3.0 installi WSUS 3.0 e specifichi il database durante l'installazione.

Durante l'installazione di WSUS 3.0 viene infatti attivata l'opzione RECURSIVE\_TRIGGERS che è un'opzione specifica del database, ma non l'opzione relativa ai trigger nidificati che è un'opzione globale del server.

Per verificare se l'opzione relativa ai trigger nidificati è attivata, utilizzare la stored procedure seguente:

**sp\_configure 'nested triggers'**

Per attivare l'opzione relativa ai trigger nidificati, eseguire la stored procedure seguente da un file batch nel computer che esegue SQL Server:

**sp\_configure 'nested triggers', 1**

**GO**

**RECONFIGURE**

**GO**

Se non si dispone di SQL Server Management Studio nel server potrebbe essere possibile eseguire script di SQL dalla riga di comando. È possibile scaricare l'utilità Query della riga di comando di Microsoft SQL Server 2005 nell'[Area download Microsoft](http://go.microsoft.com/fwlink/?linkid=70728) all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70728. Per iniziare, eseguire **sqlcmd**.

Per eseguire gli script SQL su Windows Internal Database, è necessario inoltre scaricare SQL Native Client dalla stessa pagina di download.

#### Limiti e requisiti di SQL remoto

WSUS 3.0 offre supporto per l'esecuzione del software di database in un computer distinto dal computer contenente il resto dell'applicazione WSUS 3.0. Esistono alcuni requisiti per configurare un'installazione di SQL remota

-   Non è possibile utilizzare un server configurato come controller di dominio sul lato back-end della coppia SQL remota.
-   È necessario che il Terminal Server non sia in esecuzione sul computer che sarà il server front-end di un'installazione SQL remota.
-   È necessario utilizzare almeno Microsoft SQL Server 2005 Service Pack 1 (disponibile nell'[Area download Microsoft all'indirizzo](http://go.microsoft.com/fwlink/?linkid=66143)http://go.microsoft.com/fwlink/?LinkId=66143) per il software di database nel computer back-end, se su tale computer è in esecuzione Windows Server 2003, oltre a SQL Server 2005 Service Pack 2, se sul computer è in esecuzione Windows Server® 2008.
-   Entrambi i computer front-end e back-end devono far parte di un dominio Active Directory; se si trovano su domini diversi, è necessario stabilire un criterio di trust interdominio prima di eseguire l'installazione di WSUS.
-   Se WSUS 2.0 è stato già installato in una configurazione SQL remota e si desidera eseguire l'aggiornamento a WSUS 3.0, è consigliabile disinstallare WSUS 2.0 (mediante **Installazione applicazioni** nel Pannello di controllo) nel computer back-end, accertandosi che il database esistente rimanga intatto. Sarà quindi necessario installare SQL Server 2005 SP1 o SP2 e aggiornare il database esistente. Infine, installare WSUS 3.0 sul computer front-end.

#### Non è possibile installare WSUS quando sono già installate alcune versioni non definitive di Internet Explorer 7 oltre a Servizi terminal

L'installazione di WSUS avrà esito negativo in presenza di determinate versioni non definitive di Internet Explorer 7 insieme a Servizi terminal.

Requisiti di sistema per l'installazione della console remota di WSUS 3.0
-------------------------------------------------------------------------

È possibile installare la console remota di WSUS 3.0 sulle piattaforme riportate di seguito:

-   Windows Server 2008
-   Windows Vista®
-   Windows Server 2003 SP1
-   Windows XP SP2

Requisiti di configurazione per la console remote di WSUS 3.0
-------------------------------------------------------------

#### È consigliabile utilizzare una connessione a banda larga tra una console di amministrazione remota e un server WSUS 3.0

È possibile che si verifichino problemi di prestazioni durante la connessione al server WSUS 3.0 con una console di amministrazione remota su una connessione WAN a banda stretta. Si può limitare il numero di aggiornamenti e di computer visualizzati filtrando le relative visualizzazioni di aggiornamenti e computer, ma è consigliabile utilizzare una connessione a banda larga tra la console di amministrazione remota e i server WSUS 3.0. In caso di problemi di prestazioni con la console remota, connettersi al server utilizzando Terminal Server per la gestione remota.

Requisiti di sistema per l'installazione del client
---------------------------------------------------

Aggiornamenti automatici è il componente client di WSUS. È possibile utilizzarlo con WSUS su qualsiasi sistema operativo scelto tra i seguenti:

-   Microsoft Windows Vista
-   Windows Server 2008
-   Microsoft Windows Server 2003 (qualsiasi edizione)
-   Microsoft Windows XP Professional SP2
-   Microsoft Windows 2000 Professional SP4, Windows 2000 Server SP4 o Windows 2000 Advanced Server con SP4

Requisiti software per l'installazione del server WSUS 3.0
----------------------------------------------------------

Nella tabella che segue viene illustrato il software necessario per le piattaforme Windows Server 2003 SP1. Le informazioni sul software necessario per Windows Server 2008 sono disponibili nella sezione relativa a WSUS 3.0 su Windows Server 2008.

Prima di eseguire il programma di installazione di WSUS 3.0, accertarsi che il server di WSUS 3.0 soddisfi questo elenco di requisiti. Se uno di questi aggiornamenti richiede il riavvio del computer al termine dell'installazione, sarà necessario eseguire il riavvio prima dell'installazione di WSUS 3.0.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Requisito</th>
<th style="border:1px solid black;" >Dettagli</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Internet Information Services (IIS)</td>
<td style="border:1px solid black;">Eseguire l'installazione dal sistema operativo.
Vedere il Problema 1: IIS deve essere installato.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft .NET Framework versione 2.0 Redistributable Package (x86)</td>
<td style="border:1px solid black;">Vedere Microsoft .NET Framework versione 2.0 Redistributable Package (x86)Microsoft .NET Framework versione 2.0 Redistributable Package (x86) all'indirizzo <a href="http://go.microsoft.com/fwlink/?linkid=68935">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=68935. Per piattaforme a 64 bit, vedere Microsoft .NET Framework versione 2.0 Redistributable Package (x64) nell'<a href="http://go.microsoft.com/fwlink/?linkid=70637">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70637.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Management Console 3.0 per Windows Server 2003</td>
<td style="border:1px solid black;">Si tratta di un prerequisito per l'utilizzo dell'interfaccia utente di WSUS 3.0. Vedere Microsoft Management Console 3.0 per Windows Server 2003 (KB907265) nell'<a href="http://go.microsoft.com/fwlink/?linkid=70412">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70412. Per piattaforme a 64 bit, vedere Microsoft Management Console 3.0 per Windows Server 2003 x64 Edition (KB907265) nell'<a href="http://go.microsoft.com/fwlink/?linkid=70638">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70638.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft Report Viewer</td>
<td style="border:1px solid black;">Si tratta di un prerequisito per l'utilizzo dell'interfaccia utente di WSUS 3.0. Vedere Microsoft Report Viewer Redistributable 2005 nell'<a href="http://go.microsoft.com/fwlink/?linkid=70410">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70410.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">SQL Server 2005 (facoltativo)</td>
<td style="border:1px solid black;">Se non risulta già installata una versione compatibile di SQL Server, WSUS 3.0 installerà Windows Internal Database. Se si intende utilizzare un database SQL Server completo, è necessario utilizzare almeno SQL Server 2005 SP1 (disponibile nell'<a href="http://go.microsoft.com/fwlink/?linkid=66143">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=66143) su Windows Server 2003 oppure SQL Server 2005 SP2 (disponibile nell'<a href="http://go.microsoft.com/fwlink/?linkid=84823">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=84823) su Windows Server 2008.</td>
</tr>
</tbody>
</table>
  
| ![](images/Cc708491.note(WS.10).gif)Nota                                                                                                                                                                                                                                                                               |  
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Se WSUS 2.0 è stato installato in precedenza e utilizza SQL Server 2000, SQL Server Desktop Engine 2000 o qualsiasi database di SQL Server precedente a SQL Server 2005 SP1 (o SQL Server 2005 SP2 su Windows Server 2008), il programma di installazione di WSUS 3.0 installerà Windows® Internal Database ed eseguirà la migrazione del database. |
  
Requisiti minimi di spazio su disco per l'installazione del server WSUS 3.0  
---------------------------------------------------------------------------
  
Per installare Windows Server Update Services, sono necessari i requisiti minimi di spazio su disco seguenti:
  
-   1 GB nella partizione di sistema  
-   2 GB per il volume in cui verranno archiviati i file del database  
-   20 GB per il volume in cui verranno archiviati i contenuti
  
| ![](images/Cc708491.Important(WS.10).gif)Importante                         |  
|----------------------------------------------------------------------------------------------------------|  
| Non è possibile installare WSUS 3.0 in unità compresse. Verificare che l'unità scelta non sia compressa. |
  
Requisiti di aggiornamento per WSUS 3.0  
---------------------------------------
  
#### Verificare che l'installazione di WSUS proceda in modo corretto ed eseguire un backup del database WSUS prima di eseguire l'aggiornamento
  
Quando si esegue l'aggiornamento a WSUS 3.0 da una versione precedente, accertarsi che l'installazione corrente venga eseguita in modo corretto ed eseguire un backup del database WSUS prima dell'aggiornamento.
  
1.  Analizzare gli errori più recenti nei registri eventi, eventuali problemi di sincronizzazione tra i server downstream e upstream o problemi con client che non inviano informazioni per i rapporti. Risolvere gli eventuali problemi prima di procedere.  
2.  È possibile eseguire DBCC CHECKDB per verificare che il database WSUS sia indicizzato in modo corretto. Per ulteriori informazioni su CHECKDB, vedere [DBCC CHECKDB](http://go.microsoft.com/fwlink/?linkid=86948), all'indirizzo http://go.microsoft.com/fwlink/?LinkId=86948.  
3.  Eseguire il backup del database WSUS.
  
#### Software Update Services 1.0 deve essere disinstallato
  
L'installazione di WSUS 3.0 non verrà eseguita correttamente se Software Update Services 1.0 è installato nello stesso computer. È necessario disinstallare Software Update Services 1.0 prima di installare WSUS 3.0.
  
#### L'aggiornamento da una versione beta di WSUS 3.0 alla versione RTM di WSUS 3.0 non è supportato, è tuttavia consentito l'aggiornamento dalla versione RC alla RTM
  
Se si dispone di una versione beta di WSUS 3.0 già installata, sarà necessario disinstallarla ed eliminare il database prima di installare la versione RTM di WSUS 3.0. È possibile eseguire l'aggiornamento alla versione RTM solo dalla versione RC.
  
#### Non è possibile eseguire l'aggiornamento da WSUS 2.0 a WSUS 3.0 in un sistema operativo a 64 bit
  
WSUS 2.0 non è supportato nei sistemi operativi a 64 bit. Non è possibile eseguire l'aggiornamento da WSUS 2.0 a WSUS 3.0 in sistemi a 64 bit
  
Impostazione dei parametri della riga di comando  
------------------------------------------------
  
È possibile eseguire installazioni automatiche di WSUS 3.0 utilizzando i parametri della riga di comando di WSUS. Nella tabella seguente vengono riportati i parametri della riga di comando per WSUS 3.0.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Opzione</th>
<th style="border:1px solid black;" >Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"><strong>/q</strong></td>
<td style="border:1px solid black;">Esegue l'installazione invisibile.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/u</strong></td>
<td style="border:1px solid black;">Disinstalla il prodotto. Viene disinstallata anche l'istanza di Windows Internal Database, se installata.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/p</strong></td>
<td style="border:1px solid black;">Consente solo il controllo dei prerequisiti. Non viene installato il prodotto, ma viene esaminato il sistema e vengono segnalati eventuali prerequisiti mancanti.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>/?, /h</strong></td>
<td style="border:1px solid black;">Visualizza i parametri della riga di comando e le relative descrizioni.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>/g</strong></td>
<td style="border:1px solid black;">Esegue l'aggiornamento dalla versione 2.0 di WSUS. L'unico parametro valido con questa opzione è /q (installazione invisibile). L'unica proprietà valida con questa opzione è DEFAULT_WEBSITE.</td>
</tr>
</tbody>
</table>
  
Nella tabella seguente vengono indicate le proprietà della riga di comando per WSUS 3.0.
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Proprietà</th>
<th style="border:1px solid black;" >Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">CONTENT_LOCAL</td>
<td style="border:1px solid black;">0=contenuto ospitato localmente, 1=contenuto ospitato su Microsoft Update</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CONTENT_DIR</td>
<td style="border:1px solid black;">Percorso della directory contenuto. Il valore predefinito è <em>WSUSInstallationDrive</em><strong>\WSUS\WSUSContent</strong>, dove <em>WSUSInstallationDrive</em> è l'unità locale con lo spazio libero più grande.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">WYUKON_DATA_DIR</td>
<td style="border:1px solid black;">Percorso della directory di dati Windows Internal Database.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">SQLINSTANCE_NAME</td>
<td style="border:1px solid black;">Il nome deve essere indicato nel formato <em>NomeServer</em>\<em>NomeIstanzaSQL</em>. Se l'istanza del database si trova nel computer locale, utilizzare la variabile di ambiente %COMPUTERNAME%. Se non è già disponibile un'istanza esistente, il valore predefinito è %COMPUTERNAME%\WSUS.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DEFAULT_WEBSITE</td>
<td style="border:1px solid black;">0=porta 8530, 1=porta 80</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">PREREQ_CHECK_LOG</td>
<td style="border:1px solid black;">Percorso e nome del file registro</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">CONSOLE_INSTALL</td>
<td style="border:1px solid black;">0=installa il server WSUS, 1=installa solo la console</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">ENABLE_INVENTORY</td>
<td style="border:1px solid black;">0=non installa, 1=installa funzionalità inventario</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DELETE_DATABASE</td>
<td style="border:1px solid black;">0=mantieni database, 1=rimuovi i file del database</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">DELETE_CONTENT</td>
<td style="border:1px solid black;">0=mantieni contenuto, 1=rimuovi file di contenuto</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">DELETE_LOGS</td>
<td style="border:1px solid black;">0=mantiene i file di registro, 1=rimuove i file di registro (si utilizza con il commutatore di installazione /u).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">CREATE_DATABASE</td>
<td style="border:1px solid black;">0=usa database corrente, 1=crea database</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">PROGRESS_WINDOW_HANDLE</td>
<td style="border:1px solid black;">Handle della finestra per restituire i messaggi di stato MSI</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">MU_ROLLUP</td>
<td style="border:1px solid black;">1=partecipa al programma Analisi utilizzo Microsoft Update, 0=non partecipa</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">FRONTEND_SETUP</td>
<td style="border:1px solid black;">1=non scrive il precorso del contenuto nel database, 0=scrive il percorso del contenuto nel database (per NLB)</td>
</tr>
</tbody>
</table>
  
#### Esempio di sintassi
  
```  
WSUSSetup.exe /q DEFAULT\_WEBSITE=0 (install in quiet mode using port 8530) WSUSSetup.exe /q /u (uninstall WSUS)  
```  
| ![](images/Cc708491.Important(WS.10).gif)Importante                                                                                                                                                 |  
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
| Se si installa WSUS 3.0 in modalità non interattiva (/q) e il computer non dispone di tutti i prerequisiti installati, l'installazione genererà un file denominato WSUSPreReqCheck.xml che verrà salvato nella directory %TEMP%. |
  
Problemi di installazione  
-------------------------
  
#### IIS viene riavviato durante l'installazione di WSUS 3.0
  
Il programma di installazione di WSUS 3.0 riavvia IIS senza notifica, il che potrebbe influire negativamente sui siti Web esistenti nell'ambito dell'organizzazione. Se IIS non è in esecuzione, verrà avviato dal programma di installazione di WSUS 3.0.
  
#### Se sono aperte delle connessioni a un database di WSUS esistente, l'installazione potrebbe avere esito negativo
  
Se si sta eseguendo l'aggiornamento a WSUS 3.0 da un'installazione esistente e risultano ancora aperte delle connessioni al database di WSUS esistente, ad esempio se è aperto SQL Server Management Studio, l'installazione potrebbe avere esito negativo. Chiudere tutte le connessioni e reinstallare WSUS 3.0.
  
#### Nel programma di installazione di WSUS viene indicata una directory errata per i file di database
  
Nella pagina **Inizio installazione** del programma di installazione di Windows Server Update Services 3.0 viene erroneamente indicato come percorso del database la directory padre di quest'ultimo. Ad esempio, se il percorso predefinito è %systemdrive%\\WSUS\\UpdateServicesDbFiles, verrà erroneamente indicato il percorso %systemdrive%\\WSUS.
  
#### Se WSUS è installato su un computer che dispone dei supporti lingua MUI (Multilingual User Interface) con una lingua predefinita diversa dall'inglese, la Guida verrà visualizzata nella lingua predefinita e non in inglese
  
Se si utilizza un computer che dispone di supporti lingua MUI con una lingua predefinita diversa dall'inglese, sarà comunque possibile installare WSUS se le impostazioni internazionali dell'utente corrente sono in inglese. L'interfaccia utente verrà visualizzata in inglese ma è necessario utilizzare una soluzione alternativa per visualizzare la Guida in inglese. Copiare il file .chm della Guida in inglese (*WSUSInstallDir*\\documentation\\mui\\0409\\WSUS30Help.chm) nella directory di documentazione principale (*WSUSInstallDir*\\documentation\\WSUS30Help.chm). A questo punto la Guida verrà visualizzata correttamente in tutte le lingue.
  
Problemi di aggiornamento  
-------------------------
  
#### Se si esegue l'aggiornamento da WSUS 3.0 RC a WSUS 3.0 RTM, il certificato SSL non verrà assegnato al sito Web WSUS
  
Il sito Web di WSUS verrà eliminato e creato di nuovo durante l'aggiornamento da WSUS 3.0 RC a WSUS 3.0 RTM. Di conseguenza, il certificato SSL non sarà più assegnato al sito Web di WSUS. Sarà necessario quindi riassegnare il certificato al termine dell'aggiornamento.
  
#### Ripristino dopo l'esito negativo di un aggiornamento
  
Se si esegue l'aggiornamento da WSUS 2.0 a WSUS 3.0 e l'aggiornamento non viene eseguito correttamente per un qualsiasi motivo, sarà necessario reinstallare WSUS 2.0 e ripristinarne il database utilizzando la copia di backup.
  
#### Non è possibile eseguire l'aggiornamento da WSUS 2.0 a WSUS 3.0 se è presente un database di WSUS 3.0 da un'installazione precedente
  
Se in precedenza è stato installato WSUS 3.0 e poi reinstallato WSUS 2.0 sarà necessario eliminare il database di WSUS 3.0 nel computer prima di tentare di reinstallare WSUS 3.0.
  
#### Se si modifica il nome del computer prima di eseguire l'aggiornamento a WSUS 3.0, quest'ultimo potrebbe avere esito negativo
  
Se si modifica il nome del computer dopo l'installazione di WSUS 2.0 e prima di eseguire l'aggiornamento a WSUS 3.0, quest'ultimo può avere esito negativo.
  
Utilizzare lo script seguente per rimuovere e aggiungere nuovamente i gruppi ASPNET e Amministratori WSUS. Eseguire quindi nuovamente l'aggiornamento.
  
Sarà necessario sostituire *&lt;DBLocation&gt;* con la cartella in cui è installato il database e *&lt;ContentDirectory&gt;* con la cartella di archiviazione locale.
  
```  
sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @asplogin varchar(200) SELECT @asplogin=name from sysusers WHERE name like '%ASPNET' EXEC sp\_revokedbaccess @asplogin" sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @wsusadminslogin varchar(200) SELECT @wsusadminslogin=name from sysusers WHERE name like '%WSUS Administrators' EXEC sp\_revokedbaccess @wsusadminslogin"   sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @asplogin varchar(200) SELECT @asplogin=HOST\_NAME()+'\\ASPNET' EXEC sp\_grantlogin @asplogin EXEC sp\_grantdbaccess @asplogin EXEC sp\_addrolemember webService,@asplogin" sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "USE SUSDB DECLARE @wsusadminslogin varchar(200) SELECT @wsusadminslogin=HOST\_NAME()+'\\WSUS Administrators' EXEC sp\_grantlogin @wsusadminslogin EXEC sp\_grantdbaccess @wsusadminslogin EXEC sp\_addrolemember webService,@wsusadminslogin"   sqlcmd.exe -S *&lt;DBLocation&gt;* -E -Q "backup database SUSDB to disk=N'*&lt;ContentDirectory&gt;*\\SUSDB.Dat' with init"  
```
  
#### Durante l'installazione potrebbe essere sovrascritto un backup di database precedente
  
Il programma di installazione di WSUS 3.0 aggiunge il database alla directory specificata durante il processo. Per impostazione predefinita, si tratta di *%systemdrive%*\\WSUS\\UpdateServicesDbFiles. Se in tale directory è presente un backup di database precedente, quest'ultimo verrà sovrascritto dal nuovo database. È consigliabile che gli amministratori eseguano il backup dei file di database prima di applicare aggiornamenti al computer in cui si trova il database.
  
#### Se è stata eseguita la migrazione da MSDE a SQL Server 2000 o SQL Server 2005 su WSUS 2.0, sarà necessario modificare un valore di registro
  
Se è stato installato WSUS 2.0 ed è stata eseguita la migrazione da SQL Server 2000 o SQL Server 2005, sarà necessario modificare il valore di **HKLM\\SOFTWARE\\Microsoft\\Update Services\\Server\\Setup\\WmsdeInstalled** da 1 a 0. Se non si provvede prima di eseguire l'aggiornamento a WSUS 3.0, l'aggiornamento avrà esito negativo.
  
#### Se l'installazione di WSUS 2.0 viene avviata e poi annullata, la chiave del Registro di sistema di WSUS verrà eliminata
  
Se l'installazione di WSUS 2.0 viene avviata e poi annullata, la chiave del Registro di sistema di WSUS verrà eliminata. Ciò può causare problemi se WSUS 3.0 è già installato. Lo stesso problema si verifica se si avvia la disinstallazione di WSUS 2.0 e quindi si annulla l'operazione per tentare quindi di eseguire l'aggiornamento da WSUS 2.0 a WSUS 3.0.
  
#### Se si disinstalla WSUS 3.0 e si mantengono tuttavia i file di registro, potrebbero verificarsi problemi di autorizzazione dopo la reinstallazione
  
Quando si disinstalla WSUS 3.0, è possibile mantenere i file di registro dell'installazione. Quando si reinstalla WSUS 3.0, i file di registro precedenti perdono le rispettive autorizzazioni (in genere solo Amministratori WSUS). Sarà pertanto necessario ripristinare le autorizzazioni per tali file di registro.
  
#### Se Windows SharePoint Services viene installato dopo WSUS 3.0 RC, sarà possibile eseguire l'aggiornamento a WSUS 3.0 RTM con una procedura alternativa
  
Se si è installato WSUS 3.0 RC prima di Windows SharePoint Services in un computer, è possibile eseguire l'aggiornamento a WSUS 3.0 RTM solo scegliendo l'installazione sulla porta personalizzata (porta 8530). Per eseguire questa installazione dalla riga di comando, aprire una shell di comando e digitare il comando seguente: **WSUSSetup /q / g/ DEFAULT\_WEBSITE=0**. Per eseguire questa installazione mediante l'interfaccia utente, digitare **WSUSSetup /g DEFAULT\_WEBSITE=0**.
  
Se WSUS è installato su un computer in cui sono installati i supporti lingua MUI, la Guida verrà visualizzata nella lingua predefinita invece che nella lingua dell'utente corrente
  
#### Se i client di WSUS 2.0 contengono aggiornamenti con stato Non applicabile, gli aggiornamenti verranno visualizzati come "Sconosciuto" per un breve periodo di tempo dopo l'aggiornamento a WSUS 3.0
  
Se un server WSUS 2.0 contiene dei client con aggiornamenti non applicabili, gli aggiornamenti verranno visualizzati con stato Sconosciuto per un breve periodo di tempo dopo l'aggiornamento del server a WSUS 3.0. Lo stato dell'aggiornamento torna su Non applicabile alla successiva analisi del client.
  
Problemi noti  
-------------
  
#### Risoluzione di più errori di download o di ripetuti problemi di sincronizzazione client
  
Se i client di WSUS 3.0 segnalano più errori di download oppure se i client non eseguono correttamente la sincronizzazione con il server di WSUS 3.0 per un periodo di tempo prolungato, è possibile che la cache di download del client sia danneggiata. Per risolvere il problema è possibile provare a eliminare la cache di download del client dal file system.
  
Per eliminare la cache di download del client:
  
1.  Eliminare tutti i file e le sottodirectory in questo percorso del computer client: **%windir%\\SoftwareDistribution\\Download**  
2.  Tentare di installare l'aggiornamento sincronizzando di nuovo il computer client con WSUS 3.0. Questo tentativo di installazione potrebbe non avere esito positivo e potrebbe essere visualizzato un messaggio di errore analogo al seguente: **WU\_E\_DM\_NOTDOWNLOADED, "Impossibile scaricare l'aggiornamento".**  
3.  Dopo questo errore, il computer client riavvia automaticamente il download e sarà possibile procedere con l'installazione.
  
#### Se la sincronizzazione ha esito negativo, ripetere l'operazione
  
Se la sincronizzazione ha esito negativo, il primo passo verso la risoluzione del problema dovrà essere il tentativo di sincronizzare di nuovo il server. Se le sincronizzazioni successive hanno esito negativo, utilizzare le informazioni relative alla risoluzione dei problemi riportate nella [WSUS 3.0 Operations Guide all'indirizzo](http://go.microsoft.com/fwlink/?linkid=81072) all'indirizzo http://go.microsoft.com/fwlink/?LinkId=81072 (le informazioni potrebbero essere in lingua inglese).
  
#### La modifica della configurazione di WSUS 3.0 direttamente dal database non è supportata
  
I dati di configurazione di Windows Server Update Services vengono archiviati in un database di SQL Server. Tali dati non possono tuttavia essere modificati direttamente dal database. Non tentare di modificare la configurazione di WSUS 3.0 accedendo direttamente al database. È necessario modificare la configurazione di WSUS 3.0 utilizzando la console WSUS 3.0 o chiamando le API di WSUS 3.0.
  
#### Problemi di download non segnalati tempestivamente se le quote disco sono attivate
  
Se le quote disco sono attivate e la quota è stata raggiunta, problemi di download dell'aggiornamento nel server di WSUS potrebbero non essere segnalati tempestivamente. Per evitare questo problema, disattivare le quote disco o aumentare la quota.
  
#### Se WSUS 3.0 viene distribuito mediante SSL, i computer client potrebbero riportare un errore con codice 0x8024400a
  
Nei computer client possono a volte verificarsi errori con codice "0x8024400a" quando comunicano con un server di WSUS 3.0 utilizzando SSL. Per un aggiornamento che consente di risolvere questo problema, vedere [KB 905422](http://go.microsoft.com/fwlink/?linkid=70593) all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70593 (le informazioni potrebbero essere in lingua inglese).
  
#### L'account di dominio WSUS Administrators non verrà eliminato quando si disinstalla WSUS
  
Il gruppo WSUS Administrators viene creato come un account di dominio, non come un account locale, nei controller di dominio in modo che tutte le installazioni che utilizzano tale account di dominio vengono disattivate qualora l'account venisse eliminato al momento della disinstallazione di WSUS. Di conseguenza, disinstallando WSUS, l'account di dominio WSUS Administrators non verrà eliminato.
  
#### Se un server figlio viene trasformato in server padre, gli aggiornamenti del sito di catalogo devono essere reimportati
  
Quando si innalza un server downstream a server upstream, è necessario anche reimportare tutti gli aggiornamenti del sito di catalogo. In caso contrario, il sito non sarà in grado di sincronizzare le nuove revisioni dell'aggiornamento del sito di catalogo nell'ambito del server.
  
#### Se si utilizza IIS con SSL, l'accesso non crittografato è ancora possibile a meno che non sia selezionata l'opzione "Richiedi canale protetto"
  
Se si configura IIS per l'utilizzo di SSL installando un certificato, sarà ancora possibile accedere al sito mediante un protocollo HTTP non crittografato a meno che non sia selezionata l'opzione "Richiedi canale protetto". Per ulteriori informazioni, vedere l'articolo relativo all'[attivazione della crittografia](http://go.microsoft.com/fwlink/?linkid=70601) all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70601 (le informazioni potrebbero essere in lingua inglese).
  
#### L'importazione del sito del catalogo potrebbe non essere eseguita correttamente senza le autorizzazioni di lettura/scrittura per la cartella %windir%\\TEMP
  
Quando si esegue un'importazione del sito del catalogo, se l'account Servizio di rete non dispone di autorizzazioni di lettura/scrittura per la cartella %windir%\\TEMP, l'importazione potrebbe non essere eseguita correttamente e potrebbe essere visualizzato un messaggio di errore analogo al seguente: "Impossibile elaborare la richiesta. ---&gt; Impossibile trovare il file 'C:\\WINDOWS\\TEMP\\*NomeFiletemporaneo*.dll'."
  
#### Le prestazioni possono essere lente durante la sincronizzazione tra WSUS 3.0 e un server di replica figlio che esegue WSUS 2.0
  
Se si installa WSUS 3.0 su un server padre e si tenta di sincronizzare un server di replica figlio che esegue WSUS 2.0 potrebbero verificarsi problemi di prestazioni. Per risolvere questo problema, vedere l'articolo [KB 910847](http://go.microsoft.com/fwlink/?linkid=70669) all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70669 (le informazioni potrebbero essere in lingua inglese).
  
#### Se il server di posta non è attivo o non è raggiungibile, la funzionalità di notifica di posta elettronica non funzionerà e l'utente non riceverà alcuna segnalazione del problema
  
Se il server di posta elettronica della rete non è in linea, non verranno inviate notifiche di posta elettronica senza alcuna segnalazione. Tuttavia verrà scritto l'evento 10052 (HealthCoreEmailNotificationRed) nel registro eventi.
  
#### Impostazioni modificate in un server padre non vengono trasferite immediatamente al server figlio
  
Quando la configurazione del server padre viene modificata, potrebbe essere necessario attendere qualche minuto prima che tali modifiche alla configurazione diventino effettive. Se viene modificata un'impostazione nel server padre, ad esempio la selezione di una nuova lingua, e viene immediatamente avviata una sincronizzazione nel server figlio, la modifica non sarà effettiva. Verrà invece trasferita al server figlio alla successiva sincronizzazione pianificata. Il tempo di attesa aumenta in base al numero di aggiornamenti presenti nel server padre.
  
#### La disinstallazione di WSUS 3.0 non rimuove l'istanza del database
  
Se WSUS 3.0 viene disinstallato, l'istanza del database verrà mantenuta. L'istanza potrebbe essere condivisa da più applicazioni, le quali potrebbero smettere di funzionare se essa venisse rimossa.
  
Se è necessario disinstallare Windows Internal Database, sarà possibile utilizzare i comandi seguenti:
  
(su piattaforme a 32 bit)
  
```  
msiexec /x {CEB5780F-1A70-44A9-850F-DE6C4F6AA8FB} callerid=ocsetup.exe  
```  
(su piattaforme a 64 bit)
  
```  
msiexec /x {BDD79957-5801-4A2D-B09E-852E7FA64D01} callerid=ocsetup.exe  
```  
Se si desidera disinstallare Windows Internal Database Service Pack 2 da Windows Server 2008, è possibile procedere mediante Gestione server.
  
Tuttavia, la rimozione dell'applicazione potrebbe non riguardare la rimozione di file con estensione mdb e ldb predefiniti. Ciò causerà l'esito negativo di una successiva installazione di WSUS 3.0. Questi file possono essere eliminati dalla directory %windir%\\SYSMSI\\SSEE.
  
#### Se un server figlio modifica il server padre, gli aggiornamenti con stato "Sconosciuto" vengono riportati come "Non applicabile"
  
Se un serve figlio inizia la sincronizzazione da un server padre differente, gli aggiornamenti con stato "Sconosciuto" verranno riportati nel nuovo server padre come "Non applicabile". Questo stato è temporaneo e verrà corretto alla successiva segnalazione dello stato da parte del server figlio, dopo la sincronizzazione con i client.
  
#### Se un server di replica WSUS 3.0 gestisce più di un computer con lo stesso nome, la segnalazione rollup non avrà esito positivo
  
Se un server di replica WSUS 3.0 gestisce più di un computer con lo stesso nome, la segnalazione rollup non avrà esito positivo. Di conseguenza, i rapporti disponibili nel server di WSUS principali saranno incompleti. Questo problema viene risolto eliminando tutte tranne una delle voci di computer duplicata nel server di replica.
  
#### Se Pulizia guidata server scade in un server quando eseguita su più server da una console remota, la connessione a tutti i server andrà perduta
  
È possibile eseguire la Pulizia guidata server su più server da una singola console remota. Tuttavia, se la procedura di pulizia scade in uno dei server, la console perde le sue connessioni a tutti i server. Nessun dato andrà perduto ma l'amministratore dovrà reimpostare la connessione remota a tutti i server.
  
#### Pulizia server elimina i file dopo trenta giorni, non dopo tre mesi
  
Il testo in alcune parti di Pulizia server non è esatto. Viene indicato: "Eliminare gli aggiornamenti scaduti e non approvati per tre mesi oppure le precedenti revisioni di aggiornamenti non approvate per 3 mesi". La quantità di tempo esatta è trenta giorni, non tre mesi.
  
#### L'avvio e l'immediata interruzione della connessione in rapida successione determinano la visualizzazione di un messaggio di errore (senza che si sia tuttavia verificato alcun problema) nella Configurazione guidata
  
Quando si configura WSUS, viene richiesto di connettersi al server padre (Microsoft Update oppure il server padre nella Intranet) allo scopo di trasferire informazioni di base sul server. Se si fa clic su **Avvia connessione** e immediatamente dopo su **Interrompi connessione**, verrà visualizzato il messaggio di errore inesatto "Nessun errore di sincronizzazione".
  
#### Sono ora disponibili i client WSUS su Windows Vista RTM per la ricerca degli aggiornamenti in Microsoft Update
  
Nelle versioni precedenti di WSUS, i client su Windows Vista RTM erano in grado di recuperare gli aggiornamenti solo dal server di WSUS. Con WSUS 3.0 RTM, i client Vista sono ora in grado di scaricare gli aggiornamenti anche da Microsoft Updates. È possibile indirizzare i client Vista a Microsoft Update accedendo a Windows Update nel Pannello di controllo e facendo clic sul collegamento ipertestuale **Controlla aggiornamenti in linea da Microsoft Update**. Se l'opzione di Criteri di gruppo **Rimuovi accesso per l'utilizzo delle funzionalità di Windows Update** è attiva, in Windows Update non verrà visualizzato il collegamento.
  
WSUS 3.0 su Windows Server 2008  
-------------------------------
  
#### Versioni supportate
  
WSUS 3.0 supporta Windows Server 2008 nelle versioni a 32 bit e a 64 bit.
  
#### Requisiti
  
###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Requisito</th>
<th style="border:1px solid black;" >Dettagli</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Internet Information Services (IIS)</td>
<td style="border:1px solid black;">Eseguire l'installazione dal sistema operativo. Verificare che i componenti seguenti siano attivati:
Autenticazione di Windows
Contenuto statico
ASP.NET
Management Compatibility di IIS 6.0
Compatibilità metabase di IIS</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft .NET Framework versione 2.0 Redistributable Package (x86)</td>
<td style="border:1px solid black;">Non necessario in Windows Server 2008, già installato come componente del sistema operativo.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Microsoft Management Console 3.0</td>
<td style="border:1px solid black;">Non necessario in Windows Server 2008, già installato come componente del sistema operativo.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Microsoft Report Viewer</td>
<td style="border:1px solid black;">Si tratta di un prerequisito per l'utilizzo dell'interfaccia utente di WSUS. Vedere Microsoft Report Viewer nell'<a href="http://go.microsoft.com/fwlink/?linkid=70410">Area download Microsoft</a> all'indirizzo http://go.microsoft.com/fwlink/?LinkId=70410.</td>
</tr>
</tbody>
</table>
  
#### Problema 1: Il file di configurazione di IIS 7.0 deve essere aggiornato prima di eseguire WSUS 3.0
  
Prima di eseguire WSUS 3.0, è necessario aggiornare il file di configurazione di IIS in Windows Server 2008. È necessario eseguire le operazioni seguenti:
  
1. Aprire il file di configurazione di IIS: %WINDIR%\\system32\\inetsrv\\applicationhost.config
  
2. Nel tag &lt;System.webServer&gt;&lt;modules&gt; rimuovere &lt;add name="CustomErrorMode"&gt;, se presente.
  
3. Nel tag &lt;System.webServer&gt;&lt;modules&gt; aggiungere &lt;remove name="CustomErrorMode"&gt;.
  
Il tag risultante dovrebbe essere analogo al seguente:
  
```  
 &lt;System.webServer&gt; &lt;modules&gt; &lt;remove name="CustomErrorMode"&gt; &lt;/modules&gt; &lt;/System.webServer&gt;  
```
  
#### Problema 2: Per installare WSUS 3.0 sulla porta personalizzata di Windows Server 2008 Beta 3, è necessario creare in anticipo il sito Web
  
Per installare WSUS 3.0 su Windows Server 2008 Beta 3 e configurare WSUS in modo che utilizzi la porta personalizzata 8530, è necessario creare un sito Web denominato "WSUS Administration" sulla porta 8530 prima di avviare il programma di installazione di WSUS.
  
WSUS 3.0 in Windows Small Business Server 2003  
----------------------------------------------
  
#### Problema 1: Se la radice virtuale IIS è limitata ad alcuni indirizzi IP o nomi di dominio, il server di WSUS 3.0 non sarà in grado di aggiornarsi
  
È possibile che in alcune installazioni di Windows Small Business Server il sito Web IIS predefinito sia configurato in base all'impostazione "Limitazioni sull'indirizzo IP e sul nome di dominio". In questo caso, il client di Windows Update nel server potrebbe non essere in grado di aggiornarsi.
  
#### Problema 2: Problemi di integrazione relativi all'installazione di WSUS 3.0 in Small Business Server
  
-   Se in Windows Small Business Server 2003 viene utilizzato un server proxy ISA per l'accesso a Internet, sarà necessario digitare le informazioni seguenti nell'interfaccia utente **Impostazioni**: impostazioni del server proxy, nome del server proxy e porta.  
-   Se ISA utilizza l'Autenticazione Windows, le credenziali del server proxy dovranno essere digitate nella forma "DOMINIO\\utente". L'utente deve appartenere al gruppo degli utenti di Internet.
  
#### Problema 3: Se alla rete in uso è stata aggiunta una sottorete senza utilizzare le procedure guidate di Windows SBS, sarà necessario attenersi alla procedura seguente
  
Il processo di installazione del server di WSUS installa due directory principali virtuali IIS nel server: SelfUpdate e ClientWebService. Il programma di installazione colloca inoltre alcuni file nella home directory del sito Web predefinito, sulla porta 80, che consente ai computer client di eseguire automaticamente l'aggiornamento attraverso il sito Web predefinito. Per impostazione predefinita, il sito Web predefinito è configurato in modo da negare l'accesso a tutti gli indirizzi IP diversi da localhost o da sottoreti specifiche associate al server. Di conseguenza, i computer client che non sono in host locali o in quelle sottoreti specifiche non possono eseguire l'aggiornamento automatico. Se alla rete in uso è stata aggiunta una sottorete senza utilizzare le procedure guidate di Microsoft Windows Small Business Server 2003 (Windows SBS), sarà necessario attenersi alla procedura seguente.
  
1.  In Gestione server, espandere **Gestione avanzata**, **Internet Information Services**, **Siti Web** e **Sito Web predefinito**, fare clic con il pulsante destro del mouse sulla directory virtuale **Selfupdate** e quindi fare clic su **Proprietà**.  
2.  Fare clic su **Protezione directory**.  
3.  In **Limitazioni sugli indirizzi IP e sui nomi di dominio** fare clic su **Modifica** e quindi su **Accesso concesso**.  
4.  Fare clic su **OK**, fare clic con il pulsante destro del mouse sulla directory virtuale **ClientWebService** e quindi fare clic su **Proprietà**.  
5.  Fare clic su **Protezione directory**.  
6.  In **Limitazioni sugli indirizzi IP e sui nomi di dominio** fare clic su **Modifica** e quindi su **Accesso concesso**.
  
#### Copyright
  
Le informazioni eventualmente disponibili relative a un prodotto software possono fare riferimento a una versione preliminare del prodotto stesso il quale può essere soggetto a modifiche sostanziali prima della commercializzazione. Tali informazioni sono riservate e di proprietà di Microsoft Corporation. Vengono divulgate a seguito di un accordo di non divulgazione tra il destinatario e Microsoft. I dati vengono forniti a solo scopo informativo e Microsoft non rilascia alcuna garanzia, esplicita o implicita, relativamente a tali informazioni. Le informazioni contenute nel presente documento, inclusi gli URL o altri riferimenti a siti Web, sono soggette a modifiche senza preavviso. I rischi correlati all'uso o derivanti dall'uso di tali informazioni sono interamente a carico dell'utente. Se non specificato diversamente, ogni riferimento a società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, località ed eventi utilizzati negli esempi è puramente causale e ha il solo scopo di illustrare l'uso del prodotto Microsoft. Il rispetto di tutte le applicabili leggi in materia di copyright è esclusivamente a carico dell'utente. Fermi restando tutti i diritti coperti da copyright, nessuna parte di questo documento potrà comunque essere riprodotta o inserita in un sistema di riproduzione o trasmessa in qualsiasi forma e con qualsiasi mezzo (in formato elettronico, meccanico, su fotocopia, come registrazione o altro) per qualsiasi scopo, senza il permesso scritto di Microsoft Corporation.
  
Microsoft può essere titolare di brevetti, domande di brevetto, marchi, copyright o altri diritti di proprietà intellettuale relativi all'oggetto del presente documento. Salvo quanto espressamente previsto in un contratto scritto di licenza Microsoft, la consegna del presente documento non implica la concessione di alcuna licenza su tali brevetti, marchi, copyright o altra proprietà intellettuale.
  
© 2007 Microsoft Corporation. Tutti i diritti riservati.
  
Microsoft, SQL Server, Windows e Windows Server sono marchi o marchi registrati di Microsoft Corporation negli Stati Uniti e/o negli altri paesi.
  
Altri nomi di prodotti e società citati nel presente documento possono essere marchi dei rispettivi proprietari.
