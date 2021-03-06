---
TOCTitle: 'Implementazione dell''infrastruttura RADIUS per la protezione di reti LAN senza fili'
Title: 'Implementazione dell''infrastruttura RADIUS per la protezione di reti LAN senza fili'
ms:assetid: 'd914ca5c-e402-49a0-b883-795a61d1b264'
ms:contentKeyID: 20200849
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536250(v=TechNet.10)'
---

Costruire una rete wireless locale sicura con Windows Server 2003 Certificate Services
======================================================================================

### Implementazione dell'infrastruttura RADIUS per la protezione di reti LAN senza fili

##### In questa pagina

[](#elaa)[Argomenti del modulo](#elaa)
[](#ekaa)[Obiettivi](#ekaa)
[](#ejaa)[Ambito di applicazione](#ejaa)
[](#eiaa)[Utilizzo del modulo](#eiaa)
[](#ehaa)[Panoramica](#ehaa)
[](#egaa)[Foglio di lavoro per la pianificazione dell'infrastruttura RADIUS](#egaa)
[](#efaa)[Creazione dei propri server](#efaa)
[](#eeaa)[Installazione e configurazione del Servizio autenticazione Internet](#eeaa)
[](#edaa)[Configurazione del server IAS primario](#edaa)
[](#ecaa)[Configurazione del server IAS secondario](#ecaa)
[](#ebaa)[Riepilogo](#ebaa)
[](#eaaa)[Ulteriori informazioni](#eaaa)

### Argomenti del modulo

In questo modulo viene offerta una guida completa per la creazione di un'infrastruttura RADIUS (Remote Authentication Dial-In User Service) per la protezione di reti LAN senza fili (WLAN) basata sul Servizio autenticazione Internet (IAS, Internet Authentication Service) di Microsoft® Windows® Server™ 2003. Sono incluse informazioni sull'installazione e la configurazione dei server RADIUS, la preparazione del servizio directory Microsoft Active Directory® e la configurazione delle impostazioni del server IAS. In questo modo viene fornita l'infrastruttura RADIUS che verrà utilizzata da successivi moduli di questa guida per creare la soluzione completa *Securing Wireless LANs*.

[](#mainsection)[Inizio pagina](#mainsection)

### Obiettivi

Il modulo consente di:

-   Implementare un'infrastruttura RADIUS.

-   Installare e configurare server IAS.

-   Proteggere l'accesso alla rete.

[](#mainsection)[Inizio pagina](#mainsection)

### Ambito di applicazione

Questo modulo si applica ai seguenti prodotti e tecnologie:

-   Microsoft Windows Server 2003

-   Servizio autenticazione Internet Microsoft (IAS)

-   Microsoft Active Directory

[](#mainsection)[Inizio pagina](#mainsection)

### Utilizzo del modulo

Questo modulo offre la metodologia e illustra i passaggi necessari per la creazione di un'infrastruttura RADIUS adattabile che fornisca componenti di autenticazione e autorizzazione.

Per sfruttare al massimo il presente modulo:

-   Leggere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://www.microsoft.com/italy/technet/security/guidance/secmod171.mspx)" della *Guida alla pianificazione*. In tal modo sarà possibile comprendere i concetti generali di un'infrastruttura RADIUS.

-   Leggere "IAS Concepts" in Windows Server 2003 Deployment Kit alla pagina Web
    [http://www.microsoft.com/technet/prodtechnol/windowsserver2003/proddocs/deployguide/dnsbk\_ias\_tttg.asp](http://technet.microsoft.com/en-us/library/cc778118.aspx) (in inglese).

[](#mainsection)[Inizio pagina](#mainsection)

### Panoramica

La figura 1 mostra una panoramica del processo di creazione dell'infrastruttura RADIUS che sarà illustrato in modo dettagliato in questo modulo.

![](images/Dd536250.SGFG16201(it-it,TechNet.10).jpg "Diagramma del processo di creazione dell'infrastruttura RADIUS")

Figura 1
*Diagramma del processo di creazione dell'infrastruttura RADIUS*

Nell'elenco che segue viene offerta una descrizione generale delle sezioni principali di questo modulo:

-   **Foglio di lavoro per la pianificazione di IAS**: sono elencate le informazioni di configurazione utilizzate in questo modulo per installare e configurare il Servizio autenticazione Internet. È inclusa una tabella di informazioni che devono essere fornite dall'utente prima di iniziare l'implementazione del modulo.

-   **Creazione dei propri server**: vengono descritte le procedure di selezione e configurazione dell'hardware, l'installazione di Windows Server 2003 e l'installazione di componenti opzionali. Inoltre, vengono descritte la creazione di gruppi di protezione per la gestione di Active Directory e l'impostazione delle autorizzazioni necessarie per la delega delle attività di gestione. Nella sezione viene illustrata l'implementazione della protezione a livello di sistema operativo tramite l'applicazione di modelli di protezione. I modelli utilizzati sono tratti dalla *Windows Server 2003 Security Guide*, disponibile all'indirizzo Web: [http://go.microsoft.com/fwlink/?LinkId=14845](http://go.microsoft.com/fwlink/?linkid=14845). Inoltre, in questa sezione sono elencate alcune attività comuni per completare l'installazione di base dei server.

-   **Installazione e configurazione del Servizio autenticazione Internet**: vengono descritti i passaggi di preparazione, l'installazione del software e la configurazione del Servizio autenticazione Internet, incluse la creazione e la protezione delle directory dati IAS.

-   **Configurazione del server IAS primario**: viene descritto il processo di configurazione del server IAS primario che verrà utilizzato come modello di configurazione per ulteriori server IAS con ruoli simili nell'ambiente. Inoltre viene descritta la procedura di esportazione della configurazione IAS per l'utilizzo su altri server IAS.

-   **Configurazione del server IAS secondario**: viene descritta la procedura di configurazione del server IAS secondario che verrà unito al server IAS primario in una coppia di server RADIUS per la tolleranza di errore e il bilanciamento del carico. Viene descritta la procedura di importazione della configurazione IAS primaria per la distribuzione automatica.

-   **Configurazione dei server IAS filiale**: viene descritta la procedura di configurazione di un server IAS filiale facoltativo che può essere utilizzato come esempio per ambienti distribuiti. In questa sezione viene descritta la procedura di importazione della configurazione IAS primaria per la distribuzione automatica.

[](#mainsection)[Inizio pagina](#mainsection)

### Foglio di lavoro per la pianificazione dell'infrastruttura RADIUS

Nella tabella che segue vengono elencati i parametri di configurazione utilizzati in questa soluzione. Devono essere considerati come un elenco di controllo quando si prendono le decisioni relative alla pianificazione.

Molti dei parametri riportati in queste tabelle vengono impostati manualmente come parte della procedura documentata in questo modulo. Molti vengono impostati da uno script eseguito come parte di una procedura, oppure viene fatto riferimento al parametro da uno script, per completare un'altra configurazione o un'attività operativa.

**Nota:** gli script utilizzati nella Build Guide vengono descritti in modo più dettagliato nel file ToolsReadme.txt allegato agli script.

#### Elementi di configurazione definiti dagli utenti

Prima di iniziare la procedura di installazione, è necessario assicurarsi di avere a disposizione o aver deciso le impostazioni per tutti gli elementi inclusi nella tabella che segue. Nell'intero modulo vengono utilizzati negli esempi dei comandi i valori fittizi mostrati qui. È necessario sostituire tali valori fittizi con i valori adeguati alla propria organizzazione. I valori che è necessario sostituire sono indicati in corsivo.

**Tabella 1: Elementi di configurazione definiti dagli utenti**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Elemento di configurazione</th>
<th style="border:1px solid black;" >Impostazione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Nome DNS (Domain Name System) del dominio principale dell'insieme di strutture di Active Directory</td>
<td style="border:1px solid black;"><em>woodgrovebank.com</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nome di dominio NetBIOS (network basic input/output system)</td>
<td style="border:1px solid black;"><em>WOODGROVEBANK</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Nome server del server IAS primario</td>
<td style="border:1px solid black;"><em>HQ- IAS - 01</em></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nome server del server IAS secondario</td>
<td style="border:1px solid black;"><em>HQ - IAS - 02</em></td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Nome server del server IAS terziario</td>
<td style="border:1px solid black;"><em>BO - IAS - 03</em></td>
</tr>
</tbody>
</table>
  
#### Elementi di configurazione indicati dalla soluzione
  
Nel caso di un'installazione specifica non è necessario modificare le impostazioni specificate in questa tabella, a meno che non sia necessario utilizzare un'impostazione diversa da quella offerta dalla soluzione. La modifica dei parametri di progettazione forniti in questa tabella è perfettamente accettabile, a condizione di essere consapevoli del fatto che così facendo ci si discosta dalla soluzione testata. Prima di modificare eventuali valori qui indicati, assicurarsi di aver compreso a fondo le implicazioni della modifica che si intende apportare e le dipendenze che tale impostazione potrebbe avere nelle procedure di configurazione o negli script forniti.
  
**Tabella 2: Elementi di configurazione indicati dalla soluzione**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Elemento di configurazione</th>
<th style="border:1px solid black;" >Impostazione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">[Account] Nome completo del gruppo amministrativo che controlla la configurazione del Servizio autenticazione Internet</td>
<td style="border:1px solid black;">IAS Admins</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Nome precedente a Windows 2000 del gruppo amministrativo che controlla la configurazione del Servizio autenticazione Internet</td>
<td style="border:1px solid black;">IAS Admins</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Account] Nome completo del gruppo che rivede il registro IAS delle richieste di account e di autenticazione per motivi di sicurezza</td>
<td style="border:1px solid black;">IAS Security Auditors</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Account] Nome precedente a Windows 2000 del gruppo che rivede il registro IAS delle richieste di account e di autenticazione per motivi di sicurezza</td>
<td style="border:1px solid black;">IAS Security Auditors</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Script] Percorso per gli script di installazione</td>
<td style="border:1px solid black;">C:\MSSScripts</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Script] File batch per l'esportazione della configurazione IAS</td>
<td style="border:1px solid black;">IASExport.bat</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Script] File batch per l'importazione della configurazione IAS</td>
<td style="border:1px solid black;">IASImport.bat</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Script] File batch per l'esportazione della configurazione IAS client</td>
<td style="border:1px solid black;">IASClientExport.bat</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Script] File batch per l'importazione della configurazione IAS client</td>
<td style="border:1px solid black;">IASClientImport.bat</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Config] Percorso per i file di backup della configurazione</td>
<td style="border:1px solid black;">D:\IASConfig</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">[Registri richieste] Posizione dei file registro di autenticazione e delle richieste di controllo IAS</td>
<td style="border:1px solid black;">D:\IASLogs</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">[Registri richieste] Nome di condivisione dei registri di richieste RADIUS</td>
<td style="border:1px solid black;">IASLogs</td>
</tr>
</tbody>
</table>
  
#### Preparazione per il Servizio autenticazione Internet
  
La soluzione include due server IAS in posizione centrale configurati come server RADIUS per il controllo di accesso WLAN. Inoltre, la soluzione include un server IAS filiale facoltativo configurato come un server RADIUS, per ambienti che richiedono un'infrastruttura distribuita. Per ulteriori informazioni sulla posizione dei server IAS, consultare il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" della *Guida alla pianificazione*.
  
Prima dell'installazione del Servizio autenticazione Internet è necessario completare una serie di attività di preparazione, quali:
  
-   configurazione dell'hardware del server.
  
-   Installazione del software del sistema operativo del server.
  
-   Preparazione di Active Directory.
  
-   Esecuzione di alcune attività di consolidamento del server.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Creazione dei propri server
  
Nella sezione seguente vengono descritti i passaggi per la creazione dei propri server. Sebbene la creazione di ciascun server possa essere eseguita indipendentemente, è importante completare ogni passaggio per tutti i server.
  
#### Specifica dell'hardware del server
  
L'hardware del server per il Servizio autenticazione Internet deve essere selezionato dall'[Windows Server 2003 Hardware Compatibility List (HCL)](http://www.microsoft.com/whdc/hcl/default.mspx) (in inglese). La selezione dell'hardware del server dall'elenco di compatibilità hardware di Windows Server 2003 consente di evitare problemi di affidabilità e compatibilità, che potrebbero verificarsi nel caso di hardware non verificato o driver di periferica mal codificati. Per ulteriori informazioni sulla compatibilità hardware di Windows Server 2003 vedere il sito Web: <http://www.microsoft.com/whdc/hcl/default.mspx> (in inglese).
  
##### Specifiche hardware di server verificate
  
Le seguenti specifiche hardware sono state utilizzate per eseguire il test di questa soluzione in un ambiente di laboratorio. Queste specifiche hardware sono solo di riferimento e potrebbero non essere adeguate per tutti gli ambienti. Per ulteriori informazioni sui requisiti hardware del server IAS, vedere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" della *Guida alla pianificazione*.
  
**Tabella 3: Specifiche hardware di server verificate**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Risorsa</th>
<th style="border:1px solid black;" >Requisito</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">CPU</td>
<td style="border:1px solid black;">CPU doppia da 850 MHz o superiore</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Memoria</td>
<td style="border:1px solid black;">512 MB</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Interfacce di rete</td>
<td style="border:1px solid black;">2 x singole schede di interfaccia di rete (NIC, network interface card) unite per una maggiore adattabilità</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Archiviazione disco</td>
<td style="border:1px solid black;">-Controller RAID IDE (integrated device electronics) o SCSI (small computer system interface)<br />
-2 x 9 GB (SCSI o IDE) configurati come volume RAID 1 (unità C)<br />
-2 x 18 GB (SCSI o IDE) configurati come volume RAID 1 (unità D)<br />
-Archiviazione locale su supporti rimuovibili (CD-RW o nastro di backup) in assenza di una funzionalità di backup in rete<br />
-Unità disco floppy da 1.44 MB per il trasferimento dei dati</td>
</tr>
</tbody>
</table>
 

##### Preparazione dell'hardware

Completare tutte le configurazioni hardware in base alle indicazioni del fornitore hardware. Includere l'applicazione degli aggiornamenti più recenti del BIOS (basic input/output system) e dei firmware ricevuti dal proprio fornitore.

Utilizzando il software di gestione del controller del disco, fornito con l'hardware, creare i volumi RAID 1, come indicato nella tabella precedente.

#### Installazione di Windows Server 2003

Nella sezione seguente viene descritta in dettaglio l'installazione di Windows Server 2003 nei server IAS. Molte organizzazioni dispongono già di un processo automatico di installazione server. Tale processo automatico può essere utilizzato senza problemi per le build del server, purché sia possibile includere nella build i parametri indicati di seguito. Per informazioni sull'utilizzo di Windows Server 2003, Standard Edition, o Windows Server 2003, Enterprise Edition, vedere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" della *Guida alla pianificazione*.

Eseguire i passaggi indicati di seguito per installare Windows Server 2003 su uno dei server IAS.

-   **Per installare Windows Server 2003**

    1.  Avviare il sistema con il CD di Windows Server 2003 nell'unità CD-ROM. Assicurarsi che l'unità CD-ROM sia stata impostata come unità avviabile nelle impostazioni BIOS del server.

    2.  Creare una partizione nel volume primario, formattarla come file system NTFS (NTFS) e selezionare di installare Windows Server 2003 in tale partizione.

    3.  Selezionare le impostazioni internazionali appropriate.

    4.  Digitare il nome e le informazioni relative all'azienda per la quale verrà registrato Windows Server 2003.

    5.  Digitare una password sicura per l'account dell'amministratore locale (almeno 10 caratteri misti: maiuscole, minuscole, lettere, numeri e punteggiatura).

    6.  Digitare il nome del computer quando richiesto (sostituire questo valore con il nome che si è scelto):

        -   IAS Primario = H*Q - IAS - 01HQ- IAS - 0*1

        -   IAS secondario = H*Q - IAS - 02HQ - IAS - 0*2

        -   IAS filiale = BO - IAS - 03

    7.  Quando richiesto, scegliere l'opzione di unirsi a un dominio. Immettere il nome del dominio Active Directory a cui verranno aggiunti i server: *WOODGROVEBANK* (sostituire questo valore con il nome del dominio in cui si installa il server RADIUS). Quando richiesto, immettere le credenziali di un utente autorizzato ad aggiungere computer a questo dominio.

        **Nota:** nel caso di un dominio con più insiemi di strutture, i server IAS vengono solitamente installati nel dominio principale dell'insieme di strutture, per ottimizzare le operazioni del protocollo Kerberos. Sebbene non sia essenziale, questa soluzione si basa su tale configurazione.

    8.  Non installare componenti facoltativi.

        Dopo il riavvio al termine del processo di installazione principale:

    9.  Installare eventuali service pack correnti e aggiornamenti rapidi.

    10. Riassegnare all'unità CD-ROM/DVD la lettera R.

    11. Creare una partizione sul secondo volume del disco rigido, assegnare all'unità di questa partizione la lettera D e formattarla con NTFS.

    12. Attivare questa copia di Windows Server 2003.

##### Impostazioni di rete

I server IAS dispongono di una singola interfaccia di rete, ma può essere implementata unendo due schede di interfaccia fisiche (o NIC) per una maggiore adattabilità. L'interfaccia di rete deve essere configurata con un indirizzo IP (Internet Protocol) fisso e altri parametri di configurazione IP (gateway predefinito, impostazioni DNS e così via) adeguati per la propria organizzazione.

#### Verifica dell'installazione

È necessario verificare che l'installazione del sistema operativo sia stata completata correttamente e che i parametri configurati corrispondano ai risultati previsti.

-   **Per visualizzare la configurazione corrente del sistema**

    1.  Eseguire il comando:

        **systeminfo**

    2.  Verificare i seguenti elementi dell'output di systeminfo (altri dettagli dell'output sono stati omessi per maggiore concisione):
        ```

    3.  Se queste impostazioni non corrispondono a quelle previste, è necessario riconfigurare il server utilizzando il Pannello di controllo, oppure riavviare l'installazione.

##### Installazione di script di configurazione sui server

Assieme a questa soluzione vengono forniti script di supporto e file di configurazione, per semplificare alcuni aspetti della configurazione e del funzionamento di questa soluzione. È necessario installarli in ciascun server. Alcuni di questi script saranno richiesti dalle operazioni descritte nella *Guida operativa*, pertanto non dovranno essere eliminati al termine dell'installazione del server RADIUS.

-   **Per installare gli script di installazione in ciascun server**

    1.  Creare una cartella denominata C:\\MSSScripts.

    2.  Copiare gli script dal supporto di distribuzione alla cartella.

#### Controllo dei Service Pack e delle correzioni rapide di protezione

A questo punto è necessario ricontrollare l'elenco di service pack e correzioni rapide installate. Utilizzare uno strumento come Hfnetchk.exe per eseguire il controllo, ottenere le correzioni necessarie e, dopo una verifica adeguata, installarle nei server.

**Nota:** può essere necessario scaricare separatamente l'elenco corrente delle correzioni rapide in formato XML (Extensible Markup Language), per poter eseguire Hfnetchk.exe non in linea.

#### Installazione di software aggiuntivo

In questa sezione viene descritta l'installazione sui server IAS di eventuali programmi software aggiuntivi necessari.

##### CAPICOM

CAPICOM 2.0 è necessario sui server RADIUS per alcuni degli script di installazione e gestione forniti con questa soluzione. Le informazioni su dove trovare la versione più recente di CAPICOM si trovano nella sezione "[Ulteriori informazioni](http://www.microsoft.com/windows2000/techinfo/administration/management/pgremote.asp)", al termine del modulo.

Seguire le istruzioni del file eseguibile autoestraente, per installare e registrare la DLL (dynamic-link library) di CAPICOM.

##### Convalida della connettività di rete e di Active Directory

Il Servizio autenticazione Internet dipende molto dalla corretta configurazione di rete e dalla connettività di Active Directory. Si prenda, pertanto, in considerazione la possibilità di eseguire la diagnostica rete sul server prima di distribuire IAS.

È possibile eseguire Diagnostica rete tramite il comando **NETDIAG.EXE** degli Strumenti di supporto di Windows Server 2003. Gli Strumenti di supporto di Windows Server 2003 si trovano sul CD di Windows Server 2003. È possibile estrarli con il comando seguente:

**expand r:\\support\\tools\\support.cab -f:netdiag.exe c:\\mssscripts**

Al termine, eseguire NETDIAG.EXE utilizzando il seguente comando:

**C:\\mssscripts\\netdiag.exe**

Assicurarsi di controllare eventuali errori o avvisi ricevuti.

##### Verifica del livello di funzionalità del dominio

Il [modello preferito](http://www.microsoft.com/windows2000/techinfo/administration/management/pgremote.asp) per il controllo dell'accesso di rete consiste nello sfruttare l'impostazione **Controlla accesso tramite Criteri di accesso remoto** per gli account utente all'interno di Active Directory. L'impostazione **Controlla accesso tramite Criteri di accesso remoto** è disponibile solo se Active Directory è in esecuzione nella modalità nativa di Windows 2000 o versioni successive. Pertanto, è necessario controllare il livello di funzionalità del dominio prima della distribuzione di criteri di accesso remoto (RAP) in IAS.

È possibile controllare il livello di funzionalità del dominio visualizzando le proprietà del dominio all'interno dello strumento Domini e trust di Active Directory. Se il dominio di destinazione per IAS è configurato nella modalità mista di Windows 2000, rivolgersi agli amministratori di Active Directory appropriati per pianificare la migrazione alla modalità nativa.

Per ulteriori informazioni su questo argomento, vedere la sezione "[Ulteriori informazioni](http://www.microsoft.com/italy/technet/security/guidance/secmod171.mspx)" al termine del modulo.

##### Configurazione di gruppi di Active Directory

È necessario considerare il Servizio autenticazione Internet come parte dell'infrastruttura per la protezione della rete, pertanto le autorizzazioni alla configurazione del Servizio autenticazione Internet e ai file del registro devono essere rigorosamente controllate. Per soddisfare questo requisito viene utilizzata una combinazione di gruppi globali di Active Directory e gruppi locali di Windows Server 2003.

**Creazione di gruppi per l'amministrazione del Servizio autenticazione Internet**

Eseguire lo script riportato di seguito come amministratore di dominio, per creare gruppi di protezione per l'amministrazione del Servizio autenticazione Internet:

**Cscript //job:CreateIASGroups C:\\MSSScripts\\IAS\_Tools.wsf**

Questo script crea i seguenti gruppi di protezione come gruppi globali di dominio:

-   IAS Admins

-   IAS Security Auditors

Nel caso di un dominio con più insiemi di strutture, è necessario creare questi gruppi nello stesso dominio dei server IAS. Sebbene non sia essenziale (poiché vengono creati come gruppi globali), nel resto della guida verrà dato per scontato.

**Configurazione del gruppo di amministratori IAS**

IAS è un componente fondamentale del sistema operativo Windows Server 2003. Pertanto, è necessaria l'appartenenza al gruppo di protezione Administrators locale per eseguire attività di configurazione del Servizio autenticazione Internet.

Assicurarsi di aggiungere il gruppo globale IAS Admins di Active Directory al gruppo Administrators locale sui server IAS. Se il Servizio autenticazione Internet è installato su controller di dominio, il gruppo Administrators locale si trova nella cartella Builtin all'interno dello snap-in Utenti e computer di Active Directory.

**Avviso:** l'aggiunta di gruppi al gruppo Administrators locale nei controller di dominio di Active Directory può avere serie conseguenze per la protezione che devono essere prese attentamente in considerazione. Per ulteriori informazioni vedere la sezione dedicata alla collocazione del Servizio autenticazione Internet in controller di dominio nel modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" della *Guida alla pianificazione*.

È necessario popolare questi gruppi con gli account del personale amministrativo appropriato della propria organizzazione. Per una descrizione completa di come questi gruppi siano equiparabili ai ruoli amministrativi del Servizio autenticazione Internet, vedere la sezione relativa alla pianificazione delle autorizzazioni amministrative nel modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" della *Guida alla pianificazione*.

Per la procedura di installazione nel resto di questo documento è necessario utilizzare gli account con privilegi di IAS Admins.

##### Protezione di Windows Server 2003 per IAS

È necessario eseguire ulteriori passaggi per proteggere i server IAS da attacchi dannosi. I server IAS sono un componente fondamentale dell'infrastruttura di sicurezza, pertanto dovrebbero ricevere la stessa considerazione dei firewall e delle altre infrastrutture che forniscono accesso alla rete.

**Protezione fisica**

È necessario posizionare i server IAS in un luogo dove l'accesso fisico possa essere controllato rigorosamente. Questi server devono essere continuamente in linea, pertanto è necessario posizionarli in un luogo dotato delle strutture di una stanza per server (controllo della temperatura, filtraggio dell'aria, dispositivi antincendio e così via).

Per quanto possibile, la posizione dei server dovrebbe essere scelta in modo che sia il più possibile protetta da rischi esterni che potrebbero danneggiare il server. Ad esempio, incendi, inondazioni, terremoti e così via.

Di pari importanza sono il controllo dell'accesso fisico e la garanzia della protezione fisica dei backup, della documentazione e di altri dati di configurazione. Queste informazioni dovrebbero essere conservate in un luogo separato dai server.

##### Applicazione delle impostazioni di protezione del sistema ai server

I server IAS vengono protetti utilizzando il ruolo server IAS definito nella *Windows Server 2003 Security Guide*. Per ulteriori informazioni su questa guida, vedere la sezione "[Ulteriori informazioni](#xsltsection132121120120)" al termine del modulo. È possibile scaricare modelli dal seguente indirizzo: [http://go.microsoft.com/fwlink/?LinkId=14845](http://go.microsoft.com/fwlink/?linkid=14845)

Poiché i server IAS sono membri di un dominio, le impostazioni dei criteri di protezione vengono applicate utilizzando Criteri di gruppo basati sul dominio. È necessario creare un'adeguata struttura di unità organizzativa (UO) che conserverà gli oggetti computer del server IAS e una struttura di Oggetto Criteri di gruppo (GPO) per applicare le impostazioni di sicurezza. È necessario creare due GPO, se il Servizio autenticazione Internet viene eseguito su server dedicati:

-   Enterprise Client - Server membro di base

-   Enterprise Client - Servizio autenticazione Internet

Nella *Windows Server 2003 Security Guide* è incluso inoltre un modello per i controller di dominio che eseguono un blocco simile a quello del criterio di base per i server membri. È necessario applicare il modello di protezione Controller di dominio ai controller di dominio esistenti solo dopo aver letto la *Windows Server 2003 Security Guide* e aver eseguito un'attenta pianificazione.

Sebbene non sia richiesto, dopo aver letto il modulo "Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili" della *Guida alla pianificazione*, si può decidere di collocare il Servizio autenticazione Internet su controller di dominio. A causa dei seri problemi relativi al consolidamento dei controller di domino, in questo documento non vengono fornite istruzioni per l'applicazione di modelli Controller di dominio. Tuttavia, può essere necessario preparare qualunque combinazione richiesta da controller di dominio e server IAS con il modello IAS, per abilitare il Servizio autenticazione Internet dopo un blocco di controller di dominio. A questo scopo, è necessario creare un GPO aggiuntivo da applicare in una nuova sotto-UO posizionata al di sotto dell'unità organizzativa Controller di dominio:

-   Enterprise Client: IAS su Controller di dominio (contiene il criterio che estende il ruolo dei controller di dominio per consentire una funzionalità IAS)

È necessario seguire la procedura indicata di seguito, per importare il modello Enterprise Client: Server IAS in questo GPO.

La procedura che segue indica come è possibile creare le UO e i GPO per la propria azienda. I nomi di GPO e UO sono solo a scopo indicativo. È necessario adeguare la procedura ai propri standard di UO e GPO di dominio.

-   **Per creare le UO e i GPO dei server IAS**

    1.  Ottenere i seguenti modelli di protezione dalla *Windows Server 2003 Security Guide*:

        -   Enterprise Client - Dominio

        -   Enterprise Client - server membro di base

        -   Enterprise Client - Server IAS

        -   Enterprise Client - Controller di dominio

    2.  Accedere come membro del gruppo degli Amministratori di dominio o come utente che dispone di diritti per la creazione delle UO descritte di seguito. Inoltre, è necessario essere membri di Proprietari autori criteri di gruppo.

    3.  Aprire Microsoft Management Console (MMC) Utenti e computer di Active Directory.

    4.  Creare la seguente struttura dell'unità organizzativa:

        *woodgrovebank.com*

        -   **Server membri**

            -   **IAS**

        -   **Controller di dominio**

            -   **Controller di dominio con IAS**

            **Nota:** è necessario applicare il seguente criterio di dominio una sola volta per ciascun dominio. Se questo passaggio è stato completato nei moduli precedenti, adesso è possibile ignorarlo.

    5.  Aprire le proprietà del contenitore di dominio, nella scheda **Criterio gruppo** fare clic su **Nuovo** per creare un nuovo oggetto Criteri di gruppo e denominarlo **Criterio dominio**.

    6.  Modificare il GPO e selezionare la cartella Configurazione computer\\Impostazioni di Windows\\Impostazioni di protezione. Fare clic con il pulsante destro del mouse sulla cartella Impostazioni di protezione, quindi fare clic su **Importa**. Individuare il modello Enterprise Client - Domain.inf e selezionarlo come modello da importare.

    7.  Chiudere il GPO.

    8.  Ripetere i tre passaggi precedenti per la combinazione di unità operative, GPO e modelli di protezione mostrata nella tabella seguente.

        **Tabella 4: Oggetti Criteri di gruppo e posizione**

 
        <table style="border:1px solid black;">
        <colgroup>
        <col width="33%" />
        <col width="33%" />
        <col width="33%" />
        </colgroup>
        <thead>
        <tr class="header">
        <th style="border:1px solid black;" >Unità operativa</th>
        <th style="border:1px solid black;" >GPO</th>
        <th style="border:1px solid black;" >Modello di protezione</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td style="border:1px solid black;">Server membri</td>
        <td style="border:1px solid black;">Enterprise Client: Server membro di base</td>
        <td style="border:1px solid black;">Enterprise Client: Member Server Baseline.inf</td>
        </tr>
        <tr class="even">
        <td style="border:1px solid black;">IAS</td>
        <td style="border:1px solid black;">Enterprise Client: Servizio autenticazione Internet</td>
        <td style="border:1px solid black;">Enterprise Client: IAS Server.inf</td>
        </tr>
        <tr class="odd">
        <td style="border:1px solid black;">Controller di dominio con IAS</td>
        <td style="border:1px solid black;">Enterprise Client: IAS su Controller di dominio (facoltativo se IAS si trova su un controller di dominio)</td>
        <td style="border:1px solid black;">Enterprise Client: IAS Server.inf</td>
        </tr>
        </tbody>
        </table>
  
Dopo aver creato i GPO e importato i modelli, è necessario personalizzare le impostazioni nei GPO e applicarli ai computer del server IAS in base alla seguente procedura.
  
-   **Per personalizzare e applicare il GPO Enterprise Client: Servizio autenticazione Internet**
  
    1.  Da Utenti e computer di Active Directory modificare il GPO Enterprise Client -Servizio autenticazione Internet. In Configurazione computer\\Impostazioni di Windows\\Impostazioni di protezione\\Criteri locali\\Opzioni di protezione modificare gli elementi indicati di seguito in base agli standard di protezione della propria azienda:
  
        -   Account: rinomina account amministratore: *nuovo\_nome\_amministratore*
  
        -   Account: rinomina account guest: *nuovo\_nome\_guest*
  
        -   Accesso interattivo: testo del messaggio per gli utenti che tentano l'accesso: *testo\_di\_note\_legali*
  
        -   Accesso interattivo: titolo del messaggio per gli utenti che tentano l'accesso: *titolo\_note\_legali*
  
    2.  In Criteri locali\\Assegnazione diritti utente aggiungere i seguenti gruppi locali e di dominio ai diritti utente **Consenti accesso locale** :
  
        -   (locale) *Administrators*
  
        -   (locale) *Backup Operators*
  
        -   (dominio) IAS Security Auditors
  
    3.  Aprire le proprietà dei servizi elencati di seguito nella cartella Servizi sistema e fare clic su **Definisci questa impostazione nel modello**. Accettare le autorizzazioni predefinite facendo clic su **OK**. Impostare il valore di **Selezionare la modalità di avvio servizio** impostandola su **Automatico**.
  
        -   Archivi rimovibili
  
        -   **Copia replicata del volume
  
        -   Provider di copie replicate software Microsoft
  
        -   Utilità di pianificazione
  
        **Nota:** questi servizi sono disattivati nel modello di protezione dei server membro di base, ma i primi due sono necessari per consentire l'esecuzione di NTBackup.exe. Il servizio Utilità di pianificazione è richiesto da alcuni script operativi.
  
    4.  Spostare l'account del computer del server IAS nell'unità operativa IAS.
  
    5.  Sul server IAS, eseguire il comando indicato di seguito per applicare le impostazioni di GPO al computer:
  
        **gpupdate**
  
        **Nota:** la *Windows Server 2003 Security Guide* contiene una spiegazione più dettagliata di queste impostazioni di protezione. Per ulteriori dettagli su come ottenere la guida, vedere la sezione "[Ulteriori informazioni](http://support.microsoft.com/default.aspx?scid=kb;en-us;q254949)" alla fine del modulo.
  
<!-- -->
  
-   **Per personalizzare e applicare il GPO Enterprise Client: IAS su Controller di dominio**
  
    1.  Da Utenti e computer di Active Directory modificare il GPO Enterprise Client: IAS su Controller di dominio. In Configurazione computer\\Impostazioni di Windows\\Impostazioni di protezione\\Criteri locali\\Opzioni di protezione modificare gli elementi indicati di seguito in base agli standard di protezione della propria azienda:
  
        -   Account: rinomina account amministratore: *nuovo\_nome\_amministratore*
  
        -   Account: rinomina account guest: *nuovo\_nome\_guest*
  
        -   Accesso interattivo: testo del messaggio per gli utenti che tentano l'accesso: *testo\_di\_note\_legali*
  
        -   Accesso interattivo: titolo del messaggio per gli utenti che tentano l'accesso: *titolo\_note\_legali*
  
    2.  In Criteri locali\\Assegnazione diritti utente aggiungere i seguenti gruppi locali e di dominio ai diritti utente **Consenti accesso locale** :
  
        -   (locale) *Administrators*
  
        -   (locale) *Backup Operators*
  
        -   (dominio) IAS Security Auditors
  
    3.  Aprire le proprietà dei servizi elencati di seguito nella cartella Servizi sistema e fare clic su **Definisci questa impostazione nel modello**. Accettare le autorizzazioni predefinite facendo clic su **OK**. Impostare il valore di **Selezionare la modalità di avvio servizio** impostandola su **Automatico**.
  
        -   Archivi rimovibili
  
        -   **Copia replicata del volume
  
        -   Provider di copie replicate software Microsoft
  
        -   Utilità di pianificazione
  
        **Nota:** questi servizi sono disattivati nel modello di protezione dei server membro di base, ma i primi due sono necessari per consentire l'esecuzione di NTBackup.exe. Il servizio Utilità di pianificazione è richiesto da alcuni script operativi.
  
    4.  Spostare l'account del computer del server IAS nei controller di dominio con unità operativa IAS.
  
    5.  Sul server IAS, eseguire il comando indicato di seguito per applicare le impostazioni di GPO al computer:
  
        **gpupdate**
  
        **Nota:** la *Windows Server 2003 Security Guide* contiene una spiegazione più dettagliata di queste impostazioni di protezione. Per ulteriori dettagli su come ottenere la guida, vedere la sezione "[Ulteriori informazioni](http://www.microsoft.com/italy/technet/security/guidance/secmod171.mspx)" alla fine del modulo.
  
##### Verifica delle impostazioni di protezione
  
Per verificare la corretta applicazione delle impostazioni di protezione, procedere come indicato di seguito.
  
-   **Per verificare le impostazioni di protezione del server IAS**
  
    1.  Controllare la presenza di eventi con origine SceCli nel Registro eventi applicazioni. Dovrebbe essere visualizzato un evento con ID 1704 dopo il comando **gpupdate**. Il testo dell'evento dovrebbe essere il seguente:
  
        **Applicazione del criterio di protezione agli oggetti del criterio di gruppo riuscita.**
  
    2.  Riavviare il server, verificare che tutti i servizi previsti vengano avviati e che non vengano inseriti errori nel registro eventi di sistema.
  
    3.  Dovrebbe essere consentito l'accesso e dovrebbe essere visualizzato il testo della nota legale.
  
##### Configurazione della protezione di Servizi terminal
  
È necessario utilizzare Servizi terminal per la modifica pianificata dei segreti di RADIUS da utilizzare con i client RADIUS. La crittografia del traffico di Servizi terminal è utile per proteggere i segreti di RADIUS quando transitano in rete.
  
**Importante:** se viene utilizzato un altro metodo per impostare o modificare i segreti dei client RADIUS in rete (ad esempio, utilizzando lo snap-in MMC Servizio autenticazione Internet), assicurarsi di utilizzare IPSec (Internet Protocol Security) o un'altra tecnologia appropriata per proteggere le informazioni in transito. Per importanti informazioni sull'utilizzo di IPSsec nei controller di dominio, vedere: [http://support.microsoft.com/default.aspx?scid=kb;en-us;Q254949](http://support.microsoft.com/default.aspx?scid=kb;en-us;q254949) (in inglese).
  
Queste impostazioni devono essere configurate nel GPO Enterprise Client (IAS su Controller di dominio e nel GPO Enterprise Client) Servizio autenticazione Internet che si applicano ai server IAS.
  
**Tabella 5: Impostazioni da configurare in Configurazione computer\\Modelli amministrativi\\Componenti di Windows\\Servizi terminal**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Percorso</th>
<th style="border:1px solid black;" >Criterio</th>
<th style="border:1px solid black;" >Impostazione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Nega la disconnessione di un amministratore connesso alla sessione della console</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non consentire agli amministratori locali di personalizzare le autorizzazioni</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Imposta le regole per il controllo remoto delle sessioni utente di Servizi terminal</td>
<td style="border:1px solid black;">Nessun controllo remoto consentito</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Reindirizzamento dati client/server</td>
<td style="border:1px solid black;">Consenti reindirizzamento fuso orario</td>
<td style="border:1px solid black;">Disattivato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non consentire il reindirizzamento degli Appunti</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Consenti il reindirizzamento audio</td>
<td style="border:1px solid black;">Disattivato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non consentire il reindirizzamento della porta COM</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non consentire il reindirizzamento della stampante client</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non consentire il reindirizzamento della porta LPT</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non consentire il reindirizzamento delle unità</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Non impostare stampante predefinita del client come stampante predefinita per una sessione</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Crittografia e protezione</td>
<td style="border:1px solid black;">Imposta livello di crittografia connessione client</td>
<td style="border:1px solid black;">Alta</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Richiedi sempre password del client alla connessione</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Crittografia e protezione\Protezione RPC</td>
<td style="border:1px solid black;">Server protetto (Richiedi protezione)</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Sessioni</td>
<td style="border:1px solid black;">Imposta limite di tempo per le sessioni disconnesse</td>
<td style="border:1px solid black;">10 minuti</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Consenti la riconnessione solo dal client originale</td>
<td style="border:1px solid black;">Attivo</td>
</tr>
</tbody>
</table>
  
Ogni account di dominio o gruppo di protezione che richiede l'accesso dei Servizi terminal ai server IAS dovrà essere aggiunto al gruppo locale Utenti desktop remoto (a meno che non sia già membro del gruppo Administrators locale).
  
##### Restanti attività di configurazione di Windows
  
Sarà necessario eseguire ulteriori attività di configurazione, le quali potranno variare in base all'infrastruttura e agli standard della propria azienda. Ad esempio:
  
-   Attivazione dei backup o installazione di agenti di backup.
  
-   Configurazione del protocollo SNMP (Simple Network Management Protocol) del servizio Strumentazione gestione Windows (WMI).
  
-   Installazione di agenti di gestione, quali i componenti client Microsoft Operations Manager (MOM) o Microsoft Systems Management Server (SMS).
  
-   Installazione di software antivirus.
  
-   Installazione di agenti per il rilevamento delle intrusioni.
  
È necessario verificare questi elementi quando vengono installati.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Installazione e configurazione del Servizio autenticazione Internet
  
La soluzione include due server IAS in posizione centrale che funzionano da server RADIUS per l'autenticazione degli utenti e l'autorizzazione dell'accesso alla rete. Inoltre, la soluzione include un server IAS filiale facoltativo per gli ambienti che richiedono un'autenticazione degli utenti e un'autorizzazione dell'accesso alla rete distribuite. Per ulteriori informazioni sulla posizione dei server IAS, vedere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://www.microsoft.com/italy/technet/security/guidance/secmod171.mspx)" della *Guida alla pianificazione*.
  
Nella sezione seguente vengono descritti i passaggi per l'installazione del Servizio autenticazione Internet sui propri server. Sebbene l'installazione di ciascun server possa essere eseguita indipendentemente, è importante completare ogni passaggio dell'installazione per tutti i server. I passaggi per la configurazione del Servizio autenticazione Internet su ciascun server potranno essere leggermente diversi, in base al server che viene configurato.
  
#### Installazione dei componenti software IAS
  
Il Servizio autenticazione Internet viene installato tramite Windows Optional Components Manager (a cui si accede selezionando **Add-Remove Components** dal Pannello di controllo). Nella tabella che segue vengono descritti i componenti da installare. Il rientro indica la relazione tra i componenti come verranno visualizzati nella Optional Components Manager Wizard (ad esempio, **Enable network COM access** è un sottocomponente di Application Server). I componenti eliminati non vengono visualizzati in tabella.
  
**Tabella 6: Componenti IAS per l'installazione**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Componente facoltativo da installare</th>
<th style="border:1px solid black;" >Stato di installazione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Servizi di rete</td>
<td style="border:1px solid black;">Selezionato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Servizio autenticazione Internet</td>
<td style="border:1px solid black;">Selezionato</td>
</tr>
</tbody>
</table>
  
Notare che il supporto di installazione di Windows Server 2003 sarà necessario per completare l'installazione.
  
-   **Per installare i componenti IAS**
  
    -   Eseguire Optional Components Manager su tutti i server IAS utilizzando il comando indicato di seguito per automatizzare l'installazione del Servizio autenticazione Internet sul server:
  
        **sysocmgr /i:sysoc.inf /u:C:\\MSSScripts\\OC\_AddIAS.txt**
  
##### Registrazione di IAS in Active Directory
  
È necessario posizionare i server IAS all'interno del gruppo di protezione Server RAS (Servizio di accesso remoto) e IAS in ciascun dominio per il quale dovranno eseguire l'autenticazione. In tal modo si garantisce che i server IAS dispongano delle autorizzazioni adeguate per leggere le proprietà di accesso remoto degli account utente e computer.
  
I server possono essere posizionati manualmente in questo gruppo utilizzando lo snap-in MMC Utenti e computer di Active Directory o il comando di Netshell (**netsh**).
  
-   **Per registrare il Servizio autenticazione Internet sui server nel dominio predefinito utilizzando il comando netsh**
  
    1.  Accedere a ciascun server IAS con un account che dispone dei privilegi di Domain Admins per il dominio.
  
    2.  Accedere al prompt dei comandi.
  
    3.  Nel prompt dei comandi immettere:
  
        **netsh ras add registeredserver**
  
<!-- -->
  
-   **Per registrare il Servizio autenticazione Internet in domini diversi da quello predefinito utilizzando il comando netsh**
  
    1.  Accedere a ciascun server IAS con un account che dispone dei privilegi di Domain Admins per il dominio di destinazione.
  
    2.  Aprire un prompt dei comandi.
  
    3.  Nel prompt dei comandi digitare quanto segue e sostituire &lt;nomedominio&gt; con il nome del dominio in cui registrare il server IAS:
  
        **netsh ras add registeredserver domain = &lt;nomedominio&gt;**
  
    **Nota:** in alternativa è possibile aggiungere semplicemente l'oggetto computer del server IAS direttamente nel gruppo di protezione Server RAS e IAS.
  
##### Creazione e protezione delle directory dati IAS
  
È necessario creare directory di dati nelle unità dei server IAS per archiviare i dati di configurazione e del file di registro. Eseguire le procedure descritte di seguito da un prompt dei comandi su ciascun server IAS per creare e proteggere le directory dati IAS. In alternativa è possibile utilizzare lo script fornito, per automatizzare il passaggio.
  
-   **Per creare e proteggere le directory dati IAS**
  
    -   Eseguire i comandi indicati di seguito, sostituendo W*ODGROVEBAN*K con il nome NetBIOS del proprio dominio:
  
        **md D:\\IASConfig**
  
        **md D:\\IASLogs**
  
        **cacls D:\\IASConfig /G system:F administrators:F "Backup Operators":C**
  
        **cacls D:\\IASLogs /G system:F administrators:F "Backup Operators":C "W*OODGROVEBAN*K\\IAS Security Auditors":C**
  
Inoltre, è necessario condividere la directory D:\\IASLogs con IAS Security Auditors, in modo che sia possibile utilizzare in modalità remota i dati del Registro richieste di RADIUS.
  
-   **Per condividere in modo protetto la directory IAS log**
  
    -   Eseguire il comando indicato di seguito, sostituendo W*ODGROVEBAN*K con il nome NetBIOS del proprio dominio:
  
        **net share IASLogs=D:\\IASLogs /GRANT:"W*OODGROVEBAN*K\\IAS Security Auditors",CHANGE**
  
        È stato creato un file batch facoltativo contenente i comandi precedenti, ma sarà necessario modificarlo affinché includa il nome NetBIOS corretto del proprio dominio.
  
<!-- -->
  
-   **Per modificare ed eseguire il file batch per la creazione, la protezione e la condivisione delle directory dati IAS**
  
    1.  Utilizzare Blocco note per modificare il file C:\\MSSScripts\\IAS\_Data.BAT e sostituire W*OODGROVEBAN*K con il nome NetBIOS del proprio dominio.
  
    2.  Eseguire il file batch eseguendo il seguente comando da un prompt dei comandi:
  
        **C:\\MSSScripts\\IAS\_Data.BAT**
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Configurazione del server IAS primario
  
È necessario selezionare uno dei server IAS nel proprio ambiente come server primario. Questo server verrà configurato prima degli altri server in rete e funzionerà da modello per lo stato di configurazione IAS.
  
#### Configurazione della registrazione delle richieste di account e di autenticazione
  
Per impostazione predefinita il Servizio autenticazione Internet non registra le richieste di account e di autenticazione RADIUS. Se possibile, abilitare entrambi i tipi di registro richieste, per assicurare che gli eventi di protezione vengano registrati per essere analizzati in un secondo momento. Inoltre, la propria azienda può avere l'esigenza di utilizzare i dati di contabilità per scopi di fatturazione.
  
**Nota:** la registrazione delle richieste di RADIUS influenza le prestazioni del server, pertanto sono necessarie alcune procedure per assicurare che i registri non riempiano i dischi dei dati. Per ulteriori informazioni sulla pianificazione della capacità vedere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://www.microsoft.com/italy/technet/security/guidance/secmod171.mspx)" della *Guida alla pianificazione*, per i passaggi di archiviazione ed eliminazione dei file di registro vedere il modulo "[Gestione dell'infrastruttura di protezione RADIUS e LAN senza fili](http://technet.microsoft.com/it-it/library/dd536253)" della *Guida operativa*.
  
-   **Configurazione della registrazione di richiesta account e di autenticazione sui server IAS**
  
    1.  Utilizzando lo snap-in MMC Servizio autenticazione Internet, selezionare **Registrazione Accesso remoto**, quindi visualizzare le proprietà del metodo di registrazione **File locale**.
  
    2.  Selezionare le richieste di accounting (ad esempio, inizio e fine accounting) e le richieste di autenticazione (ad esempio, concessione di accesso o rifiuto di accesso).
  
        **Nota:** questa guida non abilita la registrazione di richieste di stato periodico. Tuttavia questo tipo di registrazione può essere necessario per tenere traccia delle informazioni sulla sessione di rete dell'utente. Per ulteriori informazioni vedere il modulo "[Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili](http://technet.microsoft.com/it-it/library/dd536258)" della *Guida alla pianificazione*.
  
    3.  Assicurarsi che la directory del file di registro sia D:\\IASLogs e che sia selezionato il formato file **Formato file compatibile con database**.
  
L'utilizzo del formato file **Formato file compatibile con database**consente l'importazione diretta in database quali Microsoft Access e Microsoft SQL Server™ 2000, per eseguire in futuro revisioni della protezione tramite query e report.
  
#### File di testo della configurazione del Servizio autenticazione Internet
  
È possibile utilizzare il comando **netsh** per esportare parti della configurazione del Servizio autenticazione Internet in file di testo. È possibile esportare individualmente le seguenti aree di configurazione:
  
-   Impostazioni del server
  
-   Configurazione di registrazione
  
-   Criteri di accesso remoto
  
-   Criteri di richiesta di connessione
  
-   client RADIUS
  
-   Configurazione completa
  
È possibile utilizzare questi file di testo per trasferire impostazioni di configurazione comuni in più server IAS, in modo da garantire una configurazione coerente e una maggiore velocità di distribuzione. Le seguenti sezioni di configurazione possono essere comuni a server con ruoli simili:
  
-   Configurazione server
  
-   Impostazioni di registrazione
  
-   Criteri di accesso remoto
  
-   Criteri di richiesta di connessione
  
È necessario eseguire la configurazione degli elementi precedenti solo sul server IAS primario, quindi utilizzare il comando **netsh** per esportare tali elementi in file di testo, i quali potranno essere importati in server IAS aggiuntivi con ruoli simili. In tal modo si assicura che i file di testo di configurazione per impostazioni di configurazione simili saranno sincronizzati in tutti i server.
  
Ciascun server IAS contiene informazioni di configurazione dei client RADIUS con segreti condivisi univoci per ciascun server. Pertanto, è necessario eseguire la configurazione e il backup di tali informazioni separatamente su ciascun server.
  
**Avviso:** l'utilizzo di **netsh** per eseguire un'immagine completa della memoria crea un file di testo di configurazione con informazioni relative a segreti condivisi di RADIUS potenzialmente riservate. Questa guida offre l'opportunità di distribuire impostazioni ed eseguire backup senza utilizzare un'immagine completa della memoria delle impostazioni IAS. Se si decide di utilizzare file di testo di configurazione dell'immagine completa della memoria, assicurarsi di gestirli allo stesso modo delle informazioni che potrebbero consentire a persone non autorizzate di accedere alla rete.
  
#### Esportazione della configurazione del server IAS primario
  
L'esportazione della configurazione del server IAS primario è necessaria per trasferire le impostazioni a server IAS aggiuntivi utilizzati in questa soluzione. Questi file di testo di backup verranno utilizzati in successive sezioni di questo modulo.
  
I file batch possono essere utilizzati per automatizzare l'esportazione delle aree comuni di configurazione IAS per il backup e per aiutare la distribuzione delle impostazioni IAS su più server IAS con lo stesso ruolo. Quando si creano file batch per la distribuzione delle impostazioni, assicurarsi di includere solo le impostazioni che possono essere trasferite attraverso server IAS:
  
-   Configurazione server
  
-   Impostazioni di registrazione
  
-   Criteri di accesso remoto
  
-   Criteri di richiesta di connessione
  
<!-- -->
  
-   **Per esportare la configurazione comune nel server IAS primario**
  
    -   Al prompt dei comandi digitare il comando seguente:
  
        **C:\\MSSScripts\\IASExport.bat**
  
Questo comando contiene una serie di comandi **netsh** che consentono di esportare le informazioni comuni relative alla configurazione in file di testo di configurazione nella directory D:\\IASConfig.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Configurazione del server IAS secondario
  
IAS sfrutta il comando **netsh** per copiare lo stato della configurazione da un server all'altro. In tal modo viene accelerata la distribuzione e si riducono le possibilità di errore durante una distribuzione multiserver. I file di testo della configurazione del server IAS primario precedentemente creati vengono utilizzati per caricare la configurazione sul server IAS secondario.
  
#### Caricamento del backup della configurazione dal server primario
  
Per caricare il file di testo della configurazione esportata dal server IAS primario ad altri server IAS, procedere come segue.
  
-   **Per caricare la configurazione comune dal server IAS primario ad altri server IAS**
  
    1.  Copiare tutti i file di configurazione dalla directory D:\\IASConfig sul server IAS primario alla directory D:\\IASConfig sugli altri server IAS.
  
    2.  Utilizzare il file batch riportato di seguito per caricare la configurazione dai file di testo di configurazione del server IAS primario:
  
        **C:\\MSSScripts\\IASImport.bat**
  
#### Configurazione di server IAS filiale facoltativi
  
IAS sfrutta il comando **netsh** per copiare lo stato di configurazione da un server all'altro. In tal modo viene accelerata la distribuzione e si riducono le possibilità di errore durante una distribuzione multiserver. I file di testo della configurazione del server IAS primario precedentemente creati vengono utilizzati per caricare la configurazione su server IAS filiale facoltativi, se necessario.
  
##### Caricamento del backup della configurazione dal server primario
  
Per caricare il file di testo della configurazione esportata dal server IAS primario ad altri server IAS, procedere come segue.
  
-   **Per caricare il backup della configurazione dal server IAS primario ad altri server IAS**
  
    1.  Copiare tutti i file di configurazione dalla directory D:\\IASConfig sul server IAS primario alla directory D:\\IASConfig sugli altri server IAS.
  
    2.  Utilizzare il file batch riportato di seguito per caricare la configurazione dai file di testo di configurazione del server IAS primario:
  
        **C:\\MSSScripts\\IASImport.bat**
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Riepilogo
  
A questo punto la situazione dovrebbe essere la seguente:
  
-   Un server IAS primario installato e configurato.
  
-   Un server IAS secondario installato e configurato.
  
-   Un server IAS filale facoltativo installato e configurato.
  
-   Gruppi amministrativi configurati utilizzati per la gestione dei server IAS.
  
A questo punto si è pronti per configurare impostazioni specifiche per WLAN. L'argomento è descritto nel modulo successivo di questa guida, "[Implementazione della protezione di reti LAN senza fili mediante lo standard 802.1X](http://technet.microsoft.com/it-it/library/dd536251.aspx)".
  
A questo punto è anche consigliabile leggere le parti rilevanti del modulo "[Gestione dell'infrastruttura di protezione RADIUS e LAN senza fili](http://technet.microsoft.com/it-it/library/dd536253)" della *Guida operativa*, che contiene informazioni fondamentali per mantenere funzionante l'infrastruttura RADIUS in modo protetto e affidabile.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Ulteriori informazioni
  
-   L'ultima versione di CAPICOM può essere scaricata dalla pagina Web [http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=860EE43A-A843-462F-ABB5-FF88EA5896F6](http://www.microsoft.com/downloads/details.aspx?displaylang=en&familyid=860ee43a-a843-462f-abb5-ff88ea5896f6) (in inglese).
  
-   Vedere "Managing Remote Access on a Per-Group Basis Using Windows 2000 Remote Access Policies" all'indirizzo <http://www.microsoft.com/windows2000/techinfo/administration/management/pgremote.asp> (in inglese).
  
-   La *Windows Server 2003 Security Guide* è disponibile all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=14845](http://go.microsoft.com/fwlink/?linkid=14845) (area download) oppure [http://go.microsoft.com/fwlink/?LinkId=14846](http://go.microsoft.com/fwlink/?linkid=14846) (in inglesse).
  
Per ulteriori informazioni sulle tecnologie WLAN e lo standard 802.1X, vedere
  
-   il white paper "Windows XP Wireless Deployment Technology and Component Overview," all'indirizzo <http://www.microsoft.com/windowsxp/pro/techinfo/administration/networking/default.asp> (in inglese).
  
[](#mainsection)[Inizio pagina](#mainsection)
