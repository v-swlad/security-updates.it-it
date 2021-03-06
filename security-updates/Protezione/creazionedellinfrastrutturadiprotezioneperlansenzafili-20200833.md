---
TOCTitle: 'Creazione dell''infrastruttura di protezione per LAN senza fili'
Title: 'Creazione dell''infrastruttura di protezione per LAN senza fili'
ms:assetid: '50862132-b26b-4541-b517-1fe7b26b7dd6'
ms:contentKeyID: 20200833
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536234(v=TechNet.10)'
---

Protezione delle reti LAN senza fili con PEAP e password
========================================================

### Capitolo 5: Creazione dell'infrastruttura di protezione per LAN senza fili

Aggiornato: 2 aprile 2004

##### In questa pagina

[](#ekaa)[Cenni preliminari](#ekaa)
[](#ejaa)[Prima di iniziare](#ejaa)
[](#eiaa)[Operazioni preliminari per l'implementazione](#eiaa)
[](#ehaa)[Verifica preparazione per l'installazione](#ehaa)
[](#egaa)[Installazione di IAS](#egaa)
[](#efaa)[Registrazione di IAS in Active Directory](#efaa)
[](#eeaa)[Configurazione del server IAS primario](#eeaa)
[](#edaa)[Distribuzione delle impostazioni a più server IAS](#edaa)
[](#ecaa)[Configurazione dei punti di accesso senza fili](#ecaa)
[](#ebaa)[Riepilogo](#ebaa)
[](#eaaa)[Riferimenti](#eaaa)

### Cenni preliminari

In questo capitolo viene descritto come installare e configurare Servizio autenticazione Internet (IAS, Internet Authentication Service) per fornire servizi RADIUS (Remote Access Dial-In User Service) a una rete locale senza fili (WLAN) e come configurare i punti di accesso senza fili affinché utilizzino i servizi RADIUS offerti da IAS.

Di seguito sono riportati gli argomenti principali trattati nel capitolo:

-   Operazioni preliminari per l'installazione di IAS

-   Configurazione del primo server IAS

-   Replica delle impostazioni in altri server IAS

-   Aggiunta di punti di accesso senza fili come client RADIUS di IAS

-   Configurazione di punti di accesso senza fili

Le procedure incluse nel presente capitolo sono meno automatizzate rispetto alle procedure riportate nei capitoli precedenti. Benché IAS sia configurabile a livello di programmazione, molte impostazioni non possono essere configurate mediante l'utilizzo di Windows® Scripting Host o degli strumenti disponibili dalla riga di comando. Per i non sviluppatori il codice compilato delle applicazioni è in genere meno accessibile rispetto agli script. Pertanto, le procedure per le quali non è stato possibile creare lo script sono state completate mediante l'utilizzo di passaggi manuali. Se si intende automatizzare la configurazione di IAS mediante l'utilizzo dell'interfaccia Oggetti dati server, fare riferimento al sito MSDN® all'indirizzo [http://msdn.microsoft.com](http://msdn.microsoft.com/). Per individuare l'esatta posizione delle informazioni sull'argomento, vedere i riferimenti riportati nella parte finale del capitolo.

Il fatto che le procedure di configurazione riportate nel presente capitolo siano in gran parte manuali presenta diversi aspetti positivi. Innanzitutto, l'interfaccia di amministrazione IAS è facile da utilizzare ed è spesso supportata da procedure di configurazione guidate. Inoltre, le procedure di configurazione vengono in genere eseguite solo su un server e quindi replicate negli altri server IAS mediante l'utilizzo di comandi semplici. Infine, l'esecuzione manuale delle procedure consente di acquisire ulteriori informazioni sull'installazione e la configurazione di IAS. Quest'ultimo aspetto è più rilevante che per altri componenti della soluzione. IAS è l'hub su cui si basa il resto della soluzione, pertanto può essere vantaggioso acquisire competenze relative all'amministrazione e alla configurazione.

[](#mainsection)[Inizio pagina](#mainsection)

### Prima di iniziare

Prima di implementare le istruzioni incluse nel capitolo, è necessario leggere ed eseguire le procedure riportate nel capitolo 3 "Predisposizione dell'ambiente" e nel capitolo 4 "Creazione dell'autorità di certificazione della rete". È inoltre necessario leggere il capitolo 2 "Pianificazione dell'implementazione della protezione di reti LAN senza fili" e acquisire informazioni sull'architettura e sulla progettazione della soluzione.

Inoltre, potrebbe risultare utile la conoscenza dei seguenti argomenti:

-   IAS e RADIUS

-   Concetti sulla rete WLAN

[](#mainsection)[Inizio pagina](#mainsection)

### Operazioni preliminari per l'implementazione

#### Autorizzazioni necessarie

Per eseguire le procedure incluse nel presente capitolo, è necessario accedere con un account che sia membro del gruppo Administrators per il dominio in cui si esegue l'installazione dei server IAS.

**Nota:** se non si esegue l'installazione del server IAS su controller di dominio, ai fini dell'installazione e della configurazione sarà semplicemente necessario essere membri del gruppo Administrators locale di ogni server IAS. Inoltre, è necessario disporre delle autorizzazioni necessarie per modificare l'appartenenza al gruppo Server RAS e IAS per il dominio in cui si esegue l'installazione.

#### Strumenti necessari

Di seguito sono indicati gli strumenti necessari per eseguire le procedure riportate nel capitolo.

**Tabella 5.1: Strumenti necessari**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Strumento</th>
<th style="border:1px solid black;" >Descrizione</th>
<th style="border:1px solid black;" >Origine</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">MSS Secure WLAN Scripts</td>
<td style="border:1px solid black;">Set di script e strumenti forniti con la soluzione.</td>
<td style="border:1px solid black;">Descritto nel capitolo 3 &quot;Predisposizione dell'ambiente&quot;.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>Servizio di Autenticazione Internet</strong></td>
<td style="border:1px solid black;">Strumento di MMC (Microsoft® Management Console) utilizzato per la gestione delle impostazioni e dei criteri di IAS.</td>
<td style="border:1px solid black;">Fornito con Windows Server™ 2003.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>Utenti e computer di Active Directory</strong></td>
<td style="border:1px solid black;">Strumento di MMC utilizzato per la gestione di utenti, gruppi, computer e altri oggetti Active Directory del servizio directory Microsoft Active Directory®.</td>
<td style="border:1px solid black;">Fornito con Windows Server 2003.</td>
</tr>
</tbody>
</table>
  
#### Parametri IAS
  
Nella seguente tabella sono riportati i parametri principali utilizzati per l'installazione e la configurazione del server IAS.
  
**Tabella 5.2: Parametri di configurazione del server IAS**

 
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
<td style="border:1px solid black;"><strong>Registrazione di IAS nel registro eventi di Windows</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Richieste di autenticazione rifiutate</td>
<td style="border:1px solid black;">Abilitato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Richieste di autenticazione riuscite</td>
<td style="border:1px solid black;">Abilitato</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>Registrazione RADIUS di IAS</strong></td>
<td style="border:1px solid black;">Disabilitato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>Criteri di accesso remoto</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nome dei criteri di accesso remoto</td>
<td style="border:1px solid black;">Consenti accesso LAN senza fili</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Gruppo di protezione per concedere l'accesso a</td>
<td style="border:1px solid black;">Accesso LAN senza fili</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Tipo di EAP utilizzato</td>
<td style="border:1px solid black;">PEAP (Protected Extensible Authentication Protocol)</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Tipo di EAP PEAP utilizzato</td>
<td style="border:1px solid black;">EAP MS-CHAP v2</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Riconnessione rapida</td>
<td style="border:1px solid black;">Abilitato</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>Profilo dei criteri di accesso remoto</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Durata connessione client (timeout sessione)</td>
<td style="border:1px solid black;">60 minuti
Può essere ridotta a 15 minuti per le reti WLAN 802.11a/g a 54 Mbps</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Attributi RADIUS</td>
<td style="border:1px solid black;">Ignore-User-Dialin-Properties = &quot;True&quot;
Termination Action = &quot;RADIUS-Request&quot;</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>Criterio richiesta di connessione</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Nome criterio</td>
<td style="border:1px solid black;">Utilizza autenticazione Windows per tutti gli utenti</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Condizioni del criterio</td>
<td style="border:1px solid black;">Day-and-Time-Restrictions = All times</td>
</tr>
</tbody>
</table>
  
**Importante:** queste impostazioni sono state utilizzate nel testing interno della soluzione e determinano i comportamenti documentati. Anche se molte impostazioni possono essere configurate su valori differenti, è consigliabile eseguire dei cambiamenti solo quando si è perfettamente consapevoli dello scopo di ogni impostazione specifica e delle conseguenze causate da eventuali modifiche.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Verifica preparazione per l'installazione
  
IAS si basa su una corretta configurazione e connettività di Active Directory e della rete. Per la corretta installazione e gestione di IAS sono richiesti diversi strumenti.
  
#### Convalida dell'ambiente IAS
  
Prima di installare IAS sul server, è necessario eseguire una serie di controlli per verificare se è possibile contattare un controller di dominio e per accertarsi che tutti gli strumenti richiesti siano stati installati in base alle procedure descritte nel capitolo 3, "Predisposizione dell'ambiente". Nella seguente procedura viene utilizzato uno script che consente di eseguire i controlli automaticamente.
  
**Per controllare l'ambiente IAS**
  
1.  Aprire la shell dei comandi utilizzando il collegamento **MSS WLAN Tools** sul server in cui si intende installare IAS.
  
2.  Eseguire il comando:
  
    **MSSSetup CheckIASEnvironment**
  
3.  Lo script conferma il nome del dominio a cui appartiene il server. Scegliere **OK** per accettare.
  
4.  Dopo aver completato l'operazione, verrà visualizzata una finestra di dialogo in cui viene indicato se i controlli sono stati completati o meno. Scegliere **OK** per chiudere la finestra di dialogo.
  
5.  Se tutti i controlli sono stati completati, passare alla procedura successiva. In caso contrario, consultare il registro del programma di installazione (**%systemroot%\\debug\\MSSWLAN-Setup.log**) per individuare la causa dell'errore e correggere il problema prima di eseguire nuovamente lo script.
  
#### Verifica delle impostazioni di DHCP
  
Il protocollo DHCP (Dynamic Host Configuration Protocol) viene utilizzato per assegnare automaticamente gli indirizzi IP ai client WLAN. Verificare che gli ambiti DHCP assegnati ai siti dispongano di un numero di indirizzi IP sufficiente a coprire il numero massimo di client WLAN che possono essere attivi in ogni sito. Se l'ambito è condiviso con client cablati, le sue dimensioni devono essere tali da contenere entrambi i gruppi di client.
  
Nelle organizzazioni con un gran numero di client WLAN o con client WLAN che vengono spostati regolarmente da un sito all'altro è necessario configurare ambiti separati. Se si dispone di ambiti separati, è possibile specificare per i client tempi di lease molto brevi (ad esempio, 8 ore o meno) evitando che nei client WLAN transitori gli indirizzi IP disponibili si esauriscano rapidamente. A questo scopo, posizionare i client WLAN su una subnet separata dal resto della rete del sito e configurare un router o uno switch di livello 3 per connettere le subnet.
  
Per ambienti relativamente statici o di dimensioni ridotte, la condivisione di una subnet IP e di un singolo ambito DHCP tra client WLAN e cablati è del tutto accettabile.
  
Per ulteriori informazioni, vedere il capitolo "Deploying a Wireless LAN" di *Windows Server 2003 Deployment Kit* (in inglese). I riferimenti a questo argomento sono indicati nella parte finale del capitolo.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Installazione di IAS
  
In questa sezione viene descritto come installare IAS sul server.
  
#### Installazione dei componenti software di IAS
  
È possibile installare i componenti software di IAS mediante l'utilizzo dello script fornito con questa guida. Lo script utilizza Windows Optional Components Installation Manager per l'installazione di IAS e crea tutti i file di configurazione richiesti in fase di esecuzione.
  
**Per installare IAS**
  
1.  Aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Eseguire il seguente comando per installare i componenti software di IAS:
  
    **MSSSetup InstallIAS**
  
3.  Lo script, quindi, crea il file dei parametri dell'installazione. Al termine, viene richiesto di continuare l'installazione. Per completare l'installazione è necessario disporre del CD di installazione di Windows Server 2003 o del percorso di rete contenente l'origine dell'installazione di Windows. Scegliere **OK** per continuare o **Annulla** per interrompere l'installazione prima che venga completata.
  
    **Nota:** se si sceglie di annullare l'installazione, il file dei parametri dei componenti facoltativi di IAS (OC\_IAS.txt) verrà lasciato nella cartella di lavoro corrente. Se si decide di non accettare le impostazioni predefinite della soluzione, è possibile modificare e utilizzare il file nell'installazione personalizzata.
  
4.  Al termine dell'installazione, verrà visualizzato un messaggio di conferma. Scegliere **OK**.
  
#### Verifica dell'installazione
  
Per verificare l'installazione, fare clic su **Start,** quindi scegliere **Tutti i programmi,** **Strumenti di amministrazione** e infine **Servizio di Autenticazione Internet**. IAS dovrebbe risultare installato e in esecuzione sul server.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Registrazione di IAS in Active Directory
  
Ogni server IAS deve essere registrato in Active Directory. La registrazione implica l'aggiunta dell'account computer del server IAS al gruppo di protezione Server RAS e IAS che consente ai server IAS di disporre dell'autorizzazione per la lettura delle proprietà di accesso remoto degli account di computer e utenti in Active Directory.
  
Per registrare i server è possibile:
  
-   Aggiungere i server al gruppo manualmente (mediante l'utilizzo di **Utenti e computer di Active Directory**).
  
-   Scegliere la voce **Registra con Active Directory** dal menu **Azione** della MMC **Servizio di Autenticazione Internet (IAS, Internet Authentication Service)**.
  
-   Utilizzare il comando **Netsh**.
  
L'ultimo metodo, che prevede l'utilizzo del comando **Netsh**, è stato aggiunto agli altri perché presenta uno script semplice e consente la registrazione del server in altri domini.
  
**Per registrare il server IAS nel dominio predefinito**
  
1.  Accedere al server IAS e aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Eseguire il comando:
  
    **netsh ras add registeredserver**
  
Se sono disponibili più domini, attenersi alla seguente procedura per tutti i domini che presentano utenti o computer che verranno autenticati dal server IAS. Se i server IAS, ad esempio, vengono installati nel dominio A e sono presenti utenti della rete WLAN nel dominio B, sarà necessario registrare i server IAS sia nel dominio B sia nel dominio A. Per eseguire questa operazione, occorre disporre dell'autorizzazione per modificare l'appartenenza al gruppo Server RAS e IAS nel dominio di destinazione.
  
**Per registrare il server IAS in domini diversi dal dominio predefinito**
  
1.  Dal prompt dei comandi eseguire il comando sottostante, immettendo al posto di *DomainName* il nome del dominio in cui deve essere registrato il server IAS:
  
    **netsh ras add registeredserver domain =** *DomainName*
  
    **Nota:** in alternativa, è possibile aggiungere l'oggetto computer del server IAS direttamente al gruppo di protezione Server RAS e IAS nel dominio di destinazione mediante l'utilizzo di **Utenti e computer di Active Directory**.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Configurazione del server IAS primario
  
Nella presente sezione viene descritta la procedura per la configurazione del primo server IAS. I server IAS successivi verranno configurati eseguendo la replica delle impostazioni del server come descritto nelle procedure riportate più avanti nel capitolo.
  
#### Registrazione automatica dei certificati server IAS
  
Nel capitolo 4, "Creazione dell'autorità di certificazione della rete", sono indicate le procedure per l'installazione degli oggetti Criteri di gruppo che consentono ai membri del gruppo Server RAS e IAS di registrare i certificati del computer automaticamente. La registrazione del server IAS in Active Directory comporta l'aggiunta al gruppo dell'account del server. Tuttavia, per fare in modo che l'appartenenza al gruppo venga aggiunta al token di accesso del computer e garantisca la corretta registrazione dei certificati, sarà necessario riavviare il server.
  
**Nota:** come per gli utenti, l'appartenenza al gruppo nel token della sessione di accesso non viene modificata finché i computer non vengono nuovamente connessi al dominio. Nei computer la modifica sarà effettiva all'avvio.
  
Prima di passare alla procedura successiva è necessario riavviare il server.
  
**Avviso:** prima di riavviare il server, accertarsi che non siano in esecuzione altre operazioni. Se il server è un controller di dominio, accertarsi che sia disponibile un altro controller di dominio prima di riavviarlo. Inoltre, è necessario evitare di riavviare il server durante operazioni critiche del sistema quali il backup del server.
  
##### Verifica della distribuzione dei certificati server IAS
  
Dopo aver riavviato il server, verificare che il certificato server IAS sia stato registrato.
  
**Per verificare il certificato di autenticazione del server IAS**
  
1.  Aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Eseguire il seguente comando per aprire la MMC **Certificati**:
  
    **ComputerCerts.msc**
  
3.  Nella struttura della console fare doppio clic su **Certificati (computer locale)**, quindi fare doppio clic su **Personale**. Fare clic su **Certificati**.
  
4.  Verrà visualizzato almeno un certificato con il nome del server nella colonna **Rilasciato a** nonché il nome dell'autorità di certificazione nella colonna **Rilasciato da**. Scorrere l'elenco verso destra per visualizzare la colonna **Modello di certificato**. Nella colonna verrà visualizzato il valore **Computer** per il certificato.
  
    **Nota:** se si tratta del primo server IAS e viene installato sullo stesso server della CA, in entrambe le colonne verrà visualizzato un altro certificato con il nome della CA corrispondente al certificato della CA autofirmato.
  
5.  Se il certificato richiesto non viene visualizzato nello snap-in **MMC** Certificati, selezionare **Certificati (computer locale)** dalla struttura della console (nel riquadro sinistro), quindi scegliere **Tutte le attività** dal menu **Azione** e infine **Registra automaticamente certificati**. Aggiornare la visualizzazione della MMC **Certificati**.
  
#### Configurazione del primo server IAS
  
Anche se il set dei punti di accesso senza fili installati sui server è in genere diverso per ogni server, la configurazione dei server IAS sarà pressoché identica in questa soluzione. Per mantenere la configurazione sincronizzata tra i server e ridurre le risorse per la gestione di più server, la maggior parte delle attività di configurazione verrà eseguita sul primo server IAS installato, quindi le impostazioni del server verranno replicate negli altri server IAS dell'organizzazione.
  
Durante le procedure incluse nella presente sezione, sul primo server IAS verranno configurati i seguenti tipi di impostazioni:
  
-   Registrazione delle richieste
  
-   Criteri di accesso remoto
  
-   Impostazioni delle richieste di connessione
  
In seguito, le impostazioni verranno replicate negli altri server IAS. È inoltre necessario aggiungere al server IAS una voce di un client RADIUS per ogni punto di accesso senza fili fornito dal server IAS (argomento trattato nella sezione "Configurazione di punti di accesso senza fili" più avanti nel capitolo).
  
##### Configurazione della registrazione nei registri eventi di Windows
  
IAS include nel registro di sistema di Windows gli eventi più importanti a livello di sistema, ad esempio l'avvio e l'arresto del servizio nonché gli errori di configurazione e del servizio. Facoltativamente, è possibile registrare anche i tentativi di autenticazione riusciti e rifiutati.
  
**Per abilitare la registrazione IAS delle richieste di autenticazione**
  
1.  Aprire la MMC **Servizio di Autenticazione Internet**. A questo scopo, fare clic su **Start,** quindi scegliere **Tutti i programmi,** **Strumenti di amministrazione** e infine **Servizio di Autenticazione Internet**.
  
2.  Fare clic con il pulsante destro del mouse su **Servizio di Autenticazione Internet (locale)** e quindi scegliere **Proprietà**.
  
3.  Verificare che **Richieste di autenticazione rifiutate** e **Richieste di autenticazione riuscite** siano entrambe abilitate.
  
4.  Scegliere **OK**.
  
##### Configurazione della registrazione delle richieste di autenticazione e di accounting nei registri RADIUS
  
IAS è anche in grado di registrare informazioni di autenticazione e accounting nei registri RADIUS. In IAS i registri RADIUS non vengono creati per impostazione predefinita e la registrazione RADIUS non è abilitata nella soluzione al fine di ridurre i sovraccarichi di gestione.
  
Se per scopi di accounting e controllo della protezione è richiesta la registrazione RADIUS, è possibile abilitare entrambi i tipi di registri delle richieste. In IAS la scrittura dei registri viene eseguita su file di testo o in un database SQL. Questi registri possono essere utilizzati come input nei sistemi di controllo per tenere traccia di potenziali violazioni della protezione. Più raramente, i registri di accounting vengono utilizzati dalle organizzazioni per scopi di fatturazione benché questo tipo di impiego è in genere limitato ai provider di servizi Internet commerciali e ad altri servizi di rete. Se si intende implementare la registrazione RADIUS o si desidera semplicemente acquisire ulteriori informazioni sull'argomento, vedere i riferimenti nella parte finale del capitolo.
  
**Nota:** non è consigliabile abilitare la registrazione di autenticazione e accounting RADIUS a meno che non si presentino esigenze particolari. Oltre a una riduzione delle prestazioni del server, è richiesta una manutenzione regolare dei file del registro per evitare che possano occupare tutto lo spazio disponibile sui dischi del server.
  
##### Creazione di un criterio di accesso remoto IAS per reti WLAN
  
Eseguire la seguente procedura per creare un criterio di accesso remoto nel server IAS.
  
**Per creare un criterio di accesso remoto in IAS**
  
1.  Aprire la MMC **Servizio di Autenticazione Internet**. A questo scopo, fare clic su **Start,** quindi scegliere **Tutti i programmi,** **Strumenti di amministrazione** e infine **Servizio di Autenticazione Internet**.
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Criteri di accesso remoto**, quindi scegliere **Nuovi Criteri di accesso remoto**. Scegliere **Avanti** per continuare.
  
3.  Selezionare **Criterio tipico per scenari comuni** per configurare il criterio e denominarlo **Consenti accesso LAN senza fili**. Scegliere **Avanti**.
  
4.  Selezionare **Senza fili** come metodo di accesso.
  
5.  Selezionare l'opzione **Gruppo** per **Concedi accesso in base a** e immettere (o cercare) il gruppo di protezione Accesso LAN senza fili. Scegliere **Avanti** per continuare.
  
6.  Selezionare **PEAP (Protected EAP)** dall'elenco dei tipi di EAP.
  
7.  Scegliere il pulsante **Configura...**. Nel campo **Certificato emesso** verrà visualizzato il certificato server IAS emesso precedentemente (in caso contrario, selezionarlo dall'elenco dei certificati disponibili). Nell'elenco **Tipi di EAP** verrà visualizzato **Password protetta (EAP MSCHAPv2)**. Selezionare la casella di controllo **Abilitariconnessione rapida**.
  
    **Importante:** se si utilizzano client Pocket PC 2003 Wireless, sarà necessario selezionare la casella di controllo **Abilita riconnessione rapida** a meno che non sia disponibile una versione di Pocket PC che supporti questa opzione (vedere il riferimento all'articolo della Knowledge Base nella parte finale del capitolo). Se si abilita la riconnessione rapida, i client Pocket PC non saranno in grado di riconnettersi alla rete allo scadere dell'autenticazione iniziale.
  
8.  Scegliere **OK**, quindi **Avanti.** Scegliere **Fine** per completare la procedura.
  
    **Importante:** il nuovo criterio **ConsentiaccessoLANsenza fili** può coesistere con gli altri criteri di accesso remoto creati o con i criteri di accesso remoto predefiniti. Tuttavia, è necessario verificare che nessun altro criterio di accesso remoto predefinito venga eliminato o elencato sotto (livello di priorità inferiore) il criterio **Consenti accesso LAN senza fili** nella cartella **Criteri di accesso remoto** di IAS.
  
##### Modifica delle impostazioni del profilo dei Criteri di accesso WLAN
  
Benché la **Creazione guidata nuovo criterio di accesso remoto** (come utilizzata nella procedura precedente) consenta di creare criteri di accesso remoto validi, le due impostazioni seguenti devono essere configurate manualmente. La prima impostazione aggiunge l'attributo RADIUS **Ignore-User-Dialin-Properties**. L'attributo indica a IAS di ignorare l'impostazione relativa all'autorizzazione di accesso remoto specificata nella scheda **Chiamate in ingresso** dell'oggetto utente Active Directory. Inoltre, impedisce a IAS di inviare le informazioni nelle risposte RADIUS ai punti di accesso senza fili in quanto potrebbero causare problemi di compatibilità.
  
La seconda categoria, oltre a terminare la connessione client dopo un periodo di timeout specificato, consente al server IAS di forzare la riautenticazione del client. Queste impostazioni sono particolarmente importanti quando si utilizza una protezione dati WEP (Wired Equivalent Privacy) dinamica (predefinita per questa soluzione). Il timeout della sessione controlla la frequenza in base alla quale vengono generate le nuovi chiavi di crittografia dei dati della rete.
  
**Nota:** l'accesso WPA (Wi-Fi Protected Access) include un meccanismo per la generazione di nuove chiavi per ogni pacchetto trasmesso. Le considerazioni seguenti non sono applicabili alle reti WLAN di tipo WPA.
  
Il valore di timeout della sessione rappresenta un compromesso tra affidabilità e protezione. Un periodo di timeout di 60 minuti garantisce una protezione adeguata nella maggior parte delle circostanze e in particolare nelle reti 802.11b a 11 Mbps. In genere, i client senza fili non riusciranno mai a trasmettere in 60 minuti una quantità di dati tale da consentire il recupero di una chiave WEP dinamica da parte di un utente malintenzionato. Le reti WLAN più veloci 802.11a o 802.11g che utilizzano velocità standard a 54 Mbps, consentono la trasmissione di una maggiore quantità di dati in un determinato periodo di tempo, pertanto per questo tipo di reti è necessario impostare un timeout di 15 minuti. Tuttavia, l'utilizzo di un valore più basso può comportare una riduzione dell'affidabilità delle reti WLAN e aumentare il carico sui server IAS.
  
Per informazioni più dettagliate sull'impostazione del timeout di una sessione client, è consigliabile consultare la sezione "Opzioni di protezione per il WEP dinamico" del capitolo 2 "Pianificazione dell'implementazione della protezione di reti LAN senza fili".
  
È necessario configurare il timeout di una sessione client e l'attributo **Termination-Action** di RADIUS sul valore richiesto dal server IAS per forzare la riautenticazione del client in base all'intervallo richiesto. Per ulteriori informazioni sulle impostazioni dei criteri di accesso remoto, vedere la sezione "Criteri RADIUS" del capitolo 2 "Pianificazione dell'implementazione della protezione di reti LAN senza fili".
  
**Per modificare le impostazioni del profilo dei criteri di accesso senza fili**
  
1.  Nella MMC **Servizio di Autenticazione Internet** fare clic con il pulsante destro del mouse sul criterio **Consenti accesso LAN senza fili** e scegliere **Proprietà**. Quindi scegliere **Modifica profilo**.
  
2.  Fare clic sulla scheda **Limitazioni chiamate in ingresso**, quindi selezionare l'opzione **Durata connessione client (timeout sessione)** e immettere **60** (minuti) se si utilizza una rete WLAN 802.11b (11 Mbps) o **15** (minuti) per una rete WLAN 802.11a o g (54 Mbps) di velocità superiore.
  
    **Nota:** se si utilizza una protezione WPA per la rete WLAN anziché un WEP dinamico, sarà necessario impostare il valore su 8 ore. Tale impostazione consente ai client di disporre di credenziali valide aggiornate per un periodo di tempo ragionevole evitando, allo stesso tempo, connessioni client eccessivamente prolungate dopo la disabilitazione dell'account. Tuttavia, negli ambienti con protezione molto alta in cui è necessario ridurre al minimo il ritardo tra la disabilitazione di un account e l'esclusione del client dalla rete, questo valore può essere impostato su 1 ora.
  
3.  Fare clic sulla scheda **Avanzate**, quindi aggiungere l'attributo **Ignore-User-Dialin-Properties** e impostarlo su **True.** Quindi aggiungere l'attributo **Termination-Action** e impostarlo su **RADIUS Request**.
  
##### Verifica del criterio di richiesta di connessione per reti WLAN
  
Il criterio di richiesta di connessione IAS predefinito è configurato in modo tale da consentire a IAS di autenticare utenti e computer direttamente mediante un confronto con Active Directory. Eseguire i seguenti passaggi per verificare la configurazione del criterio di richiesta di connessione predefinito.
  
**Per verificare la configurazione del criterio di richiesta di connessione predefinito**
  
1.  Aprire la MMC **Servizio di Autenticazione Internet**, quindi accedere alla cartella **Elaborazione richiesta connessione\\Criteri richiesta di connessione** e fare clic con il pulsante destro del mouse sul criterio di richiesta di connessione **Utilizza autenticazione Windows per tutti gli utenti.** Quindi scegliere **Proprietà**.
  
2.  Verificare che le condizioni del criterio contengano **Date-And-Time-Restrictions matches"Sun 00:00-24:00; Mon 00:00-24:00; Tue 00:00-24:00; Wed 00:00-24:00; Thu 00:00-24:00; Fri 00:00-24:00; Sat 00:00-24:00".**
  
3.  Scegliere il pulsante **Modifica profilo** e accertarsi che nella scheda **Autenticazione** sia selezionata l'opzione **Autentica le richieste su questo server**.
  
4.  Verificare che nella scheda **Attributi** non sia specificata alcuna regola.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Distribuzione delle impostazioni a più server IAS
  
Dopo aver completato la configurazione del server IAS primario, è possibile eseguirne una replica in altri server IAS.
  
Per eseguire l'installazione e la registrazione di IAS in Active Directory, attenersi alle procedure precedentemente descritte nelle relative sezioni del presente capitolo. È inoltre necessario eseguire la procedura di "Verifica della distribuzione dei certificati server IAS" per accertarsi che nei nuovi server sia stata completata la registrazione dei certificati. Al termine, è possibile esportare le impostazioni di IAS dal primo server per importarle in altri server, come descritto nelle procedure incluse nella seguente sezione.
  
**Importante:** è possibile replicare le impostazioni solo in altri server IAS Windows Server 2003. Se si utilizzano le seguenti procedure, non sarà possibile replicare le impostazioni di Windows Server 2003 nelle versioni Windows 2000 di IAS.
  
#### Replica delle impostazioni dal primo server IAS
  
È possibile utilizzare il comando **Netsh** per esportare parti della configurazione di IAS in file di testo. Gli script utilizzati nelle seguenti procedure utilizzano il file Netsh.exe per esportare le impostazioni e importarle nei server IAS.
  
Le seguenti categorie di impostazioni IAS possono essere esportate e importate separatamente nei server IAS:
  
-   Impostazioni del server
  
-   Configurazione di registrazione
  
-   Criteri di accesso remoto
  
-   Criteri richiesta di connessione
  
-   Client RADIUS
  
-   Configurazione completa (include tutte le categorie sopra riportate)
  
Le impostazioni esportate vengono memorizzate in file di testo, tuttavia i dati sono codificati. È possibile utilizzare questi file di testo per trasferire impostazioni di configurazione comuni in più server IAS, in modo da garantire una configurazione coerente e una maggiore velocità di distribuzione.
  
La maggior parte delle categorie di configurazione avrà un ruolo simile nei server IAS ad eccezione, in genere, della categoria dei client RADIUS. In questa soluzione, nei server IAS verranno autenticati solo i client WLAN. Se si decide di utilizzare uno o più server IAS in modo diverso, ad esempio per l'autenticazione di client di accesso remoto, sarà necessario configurare e replicare le impostazioni dei server utilizzati in modo indipendente o eseguire la configurazione manualmente. In caso contrario, è possibile che le impostazioni dei criteri e di altre configurazioni vengano sovrascritte o vadano perse.
  
Gli elementi riportati di seguito devono essere configurati solo sul primo server IAS (come descritto nella sezione precedente relativa alla configurazione di IAS).
  
-   Configurazione server
  
-   Impostazioni di registrazione
  
-   Criteri di accesso remoto
  
-   Criteri di richiesta di connessione
  
L'utilizzo delle procedure incluse nella presente sezione consentirà di esportare le impostazioni e di replicarle in altri server IAS.
  
**Suggerimento:** per semplificare la registrazione delle modifiche apportate alla configurazione di IAS, è consigliabile includere un numero di versione nel nome del criterio di accesso remoto. Ogni volta che vengono modificate le impostazioni di IAS, è necessario aggiornare il nome e includere un nuovo numero di versione. Ciò consente di rilevare più facilmente le modifiche nei diversi server IAS e di verificare che in ognuno di essi vengano utilizzate le stesse impostazioni.
  
Designare il primo server IAS come "master". Quindi utilizzare le procedure seguenti per replicare le impostazioni di questo server negli altri server IAS dell'organizzazione. La replica delle impostazioni dei client RADIUS viene descritta in modo dettagliato nella sezione "Replica della configurazione di client RADIUS in altri server IAS" più avanti nel capitolo.
  
**Nota:** la designazione "Master" non comporta alcuna conseguenza sostanziale in IAS. In pratica, viene impiegata solo per indicare il server che verrà utilizzato per apportare le modifiche iniziali alla configurazione prima che vengano replicate negli altri server IAS.
  
##### Esportazione delle impostazioni dal server IAS master
  
Questa procedura consente il salvataggio delle impostazioni del server IAS corrente su file del disco.
  
**Per esportare la configurazione IAS su file del disco**
  
1.  Accedere al server IAS primario e aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Se richiesto, identificare una cartella per memorizzare i file di output o inserire un disco floppy formattato nell'unità del server.
  
3.  Eseguire il seguente comando per esportare la configurazione IAS:
  
    **MSSTools ExportIASSettings** \[**/path:***CartellaOutput*\]
  
    *CartellaOutput* è un parametro facoltativo utilizzato per specificare la cartella in cui verranno scritti i file esportati. Il percorso deve essere racchiuso tra virgolette se contiene spazi incorporati. La cartella, se specificata, deve essere disponibile altrimenti i file vengono scritti nella directory corrente.
  
4.  Di seguito sono riportati i file creati dallo script:
  
    -   IAS\_Server\_Settings.txt
  
    -   IAS\_Logging.txt
  
    -   IAS\_Rem\_Access\_Policies.txt
  
    -   IAS\_Con\_Request\_Policies.txt
  
5.  Archiviare i file per importarli in altri server.
  
##### Importazione delle impostazioni in altri server IAS
  
In questa procedura vengono utilizzati i file delle impostazioni esportati nella procedura precedente per configurare altri server IAS con le stesse impostazioni. La procedura non prevede l'importazione dei client RADIUS che verrà trattata in una sezione successiva.
  
**Avviso:** quando si importano le impostazioni di IAS in un server IAS, verranno sovrascritte tutte le impostazioni di IAS esistenti sul server, ad eccezione delle informazioni dei client RADIUS. Se per i server vengono create impostazioni differenti, ad esempio criteri di accesso remoto diversi per supportare i client VPN, non occorre utilizzare questa procedura per importare nei server le impostazioni della rete WLAN di IAS. In questo caso, è necessario configurare le impostazioni manualmente facendo riferimento alle procedure descritte nella sezione "Configurazione del server IAS primario" già trattata nel presente capitolo.
  
**Per importare la configurazione IAS da file su disco**
  
1.  Accedere al server IAS di destinazione e aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Identificare la cartella contenente i file di configurazione precedentemente esportati dal server IAS master.
  
3.  Eseguire il seguente comando per importare la configurazione di IAS:
  
    **MSSTools ImportIASSettings** \[**/path:***CartellaIntput*\]
  
    *CartellaInput* è un parametro facoltativo utilizzato per specificare la cartella in cui lo script cercherà i file delle impostazioni da importare. Il percorso deve essere racchiuso tra virgolette se contiene spazi incorporati. Se non viene specificata alcuna cartella, i file verranno immessi nella directory corrente.
  
Per verificare se l'importazione delle impostazioni è stata eseguita in modo corretto, è sufficiente aprire la MMC **Servizio di Autenticazione Internet** e controllare le impostazioni dei criteri di accesso remoto e richiesta di connessione.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Configurazione dei punti di accesso senza fili
  
Nella presente sezione viene descritto come aggiungere punti di accesso senza fili come client RADIUS dei server IAS.
  
#### Aggiunta di punti di accesso come client RADIUS di un server IAS
  
L'aggiunta di punti di accesso senza fili come client RADIUS di un server IAS deve essere eseguita prima che a tali punti venga consentito l'utilizzo dei servizi di autenticazione e accounting RADIUS. Per ulteriori informazioni sulla modalità di assegnazione dei punti di accesso senza fili a diversi server IAS, vedere le procedure incluse nel capitolo 2, "Pianificazione dell'implementazione della protezione di reti LAN senza fili".
  
I punti di accesso senza fili assegnati a una posizione specifica verranno in genere configurati per utilizzare un server IAS nella stessa posizione come server RADIUS primario e un altro server IAS nella stessa posizione o in una posizione diversa come server RADIUS secondario. I termini "primario" e "secondario" in questo caso non si riferiscono ad alcuna relazione gerarchica né a una differenza nella configurazione tra i server IAS. Questi termini sono importanti solo per i punti di accesso senza fili, ognuno dei quali dispone di un server RADIUS primario e secondario (o di backup) designato. Prima di configurare i punti di accesso senza fili, è necessario decidere il server IAS primario e il server RADIUS secondario per ogni punto di accesso senza fili.
  
Nelle seguenti procedure vengono fornite le istruzioni per aggiungere client RADIUS a due server IAS. Durante la prima procedura viene generato un segreto RADIUS per il punto di accesso senza fili. Questo segreto, o chiave, verrà utilizzato da IAS e dal punto di accesso per l'autenticazione reciproca. I dettagli del client e il rispettivo segreto vengono registrati in un file. Questo file viene utilizzato nella seconda procedura per importare il client nel secondo server IAS.
  
**Importante:** per aggiungere lo stesso client a due server IAS non è necessario utilizzare la prima procedura. Se si decide di utilizzarla ugualmente, per le voci client di ogni server verrà configurato un segreto RADIUS differente e il punto di accesso senza fili non sarà in grado di autenticare entrambi i server.
  
##### Aggiunta di punti di accesso al primo server IAS
  
Nella presente sezione viene descritto come aggiungere punti di accesso senza fili al primo server IAS. Per automatizzare la generazione di segreti RADIUS casuali avanzati e aggiungere il client al server IAS viene fornito uno script. Mediante lo script viene creato anche un file (per impostazione predefinita Clients.txt) in cui vengono registrati i dettagli relativi a ogni punto di accesso aggiunto. Nel file vengono registrati il nome, l'indirizzo IP e il segreto RADIUS generato per ogni punto di accesso senza fili. Queste informazioni sono richieste per la configurazione del secondo server IAS e dei punti di accesso senza fili.
  
Se si preferisce aggiungere i client manualmente, per generare i segreti per i punti di accesso senza fili è consigliabile attenersi alla procedura "Generazione di voci client per punti di accesso senza fili" più avanti nel presente capitolo.
  
**Importante:** i client RADIUS vengono aggiunti al server IAS come client "RADIUS Standard". Benché si tratti di una scelta appropriata per la maggior parte dei punti di accesso senza fili, per alcuni di essi potrebbe essere necessario configurare sul server IAS attributi specifici del produttore. Tali attributi possono essere configurati selezionando una periferica specifica del fornitore nelle proprietà dei client RADIUS mediante la MMC **Servizio di Autenticazione Internet** oppure (se la periferica non è inclusa nell'elenco) specificando gli attributi del produttore nel criterio di accesso remoto di IAS. Per ulteriori informazioni sulla configurazione degli attributi specifici del produttore in IAS, vedere i riferimenti riportati nella parte finale del capitolo.
  
Inoltre, per ulteriori informazioni sui requisiti degli attributi specifici del produttore per i server RADIUS, fare riferimento alla documentazione relativa ai punti di accesso senza fili.
  
**Per aggiungere un client RADIUS al primo server IAS**
  
1.  Accedere al server IAS in cui si desidera aggiungere i punti di accesso senza fili e aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Se nella directory corrente è incluso un file di output di client RADIUS o se nel parametro di percorso viene specificato un file esistente, la nuova voce client verrà aggiunta al file. Per evitare che ciò avvenga, rimuovere il file esistente o specificare un nome di file diverso nel comando.
  
3.  Eseguire il seguente comando per aggiungere un punto di accesso senza fili al server IAS:
  
    **MSSTools AddRADIUSClient** \[**/path:***FileOutput.txt*\]
  
    **Nota:** il parametro *path* è facoltativo. È possibile specificare il nome del file (insieme a un percorso di cartella facoltativo) in cui verrà archiviato l'output del comando. Il percorso deve essere racchiuso tra virgolette se contiene spazi incorporati. Se non viene specificato alcun parametro di percorso, l'output del comando verrà salvato nel file Clients.txt nella directory corrente.
  
4.  Quando richiesto, specificare un nome per il punto di accesso senza fili. È necessario immettere nella MMC **Servizio di Autenticazione Internet** un riferimento descrittivo che non deve necessariamente corrispondere al nome assegnato al punto di accesso durante la configurazione. Utilizzare un nome DNS (Domain Name System) o una stringa qualsiasi.
  
5.  Immettere l'indirizzo IP del punto di accesso senza fili in formato decimale separato da punti, ad esempio 10.20.1.153.
  
6.  Verrà automaticamente generata una password per il client. Questa password è una stringa crittografica generata in maniera casuale ed è formata da 23 caratteri stampabili utilizzati dal server IAS e dal punto di accesso senza fili per l'autenticazione reciproca. Queste impostazioni vengono utilizzate per aggiungere il client RADIUS al server IAS. Inoltre, al file di output (per impostazione predefinita Clients.txt) nella directory corrente vengono aggiunti anche il nome, l'indirizzo IP e il segreto. Il file di output è un file di testo delimitato da virgola con un client RADIUS per ogni riga che può essere facilmente utilizzato negli script o importato e modificato mediante l'utilizzo di applicazioni quali Microsoft Excel.
  
7.  Ripetere i passaggi da 3 a 6 per tutti gli altri punti di accesso senza fili che si desidera aggiungere al server IAS.
  
In seguito, il file di output verrà utilizzato come riferimento durante l'impostazione dei segreti RADIUS per i punti di accesso senza fili. Per ulteriori informazioni, vedere la sezione "Configurazione dei punti di accesso senza fili" più avanti nel capitolo.
  
**Importante:** non lasciare il file di output dei client RADIUS sul server in quanto contiene i segreti dei client RADIUS in formato non crittografato. Dopo aver aggiunto i punti di accesso senza fili, spostare il file su un disco floppy o su un altro supporto rimovibile e conservarlo in un luogo sicuro.
  
Nella procedura "Aggiunta di un client RADIUS al primo server IAS" sopra riportata viene utilizzato uno strumento di esempio incluso nella soluzione (AddRADIUSClient.exe*)*. Questo strumento è una semplice applicazione di Visual Basic.NET che utilizza l'interfaccia Oggetti dati server per la configurazione dei server IAS e consente di scrivere lo script per aggiungere i client al server IAS.
  
Lo strumento non è supportato da Microsoft e non è stato sottoposto a test accurati. Tuttavia, il codice sorgente dell'applicazione è incluso nel caso in cui siano richieste eventuali verifiche o modifiche prima dell'utilizzo.
  
**Nota:** a differenza della maggior parte degli script utilizzati nelle procedure di installazione, questo script non registra informazioni sullo stato nel file di registro MSSWLAN-setup.log. In questo modo i segreti dei client RADIUS non vengono archiviati nel file e vengono scongiurati eventuali rischi per la protezione. Tuttavia, le informazioni sullo stato vengono visualizzate sullo schermo.
  
###### Esecuzione script dell'aggiunta dei punti di accesso al server IAS (procedura alternativa)
  
Se non si desidera aggiungere i punti di accesso senza fili al server IAS in modo interattivo mediante l'utilizzo della procedura precedente, è sufficiente generare i file di output delle voci dei client RADIUS per ogni punto di accesso senza fili senza aggiungerli al server IAS. In questo caso, per importare le voci dei client RADIUS sia nel primo che nel secondo server IAS, è possibile utilizzare la procedura "Importazione dei client RADIUS nel secondo server IAS" descritta più avanti nella presente sezione. Poiché è possibile creare lo script dell'intera operazione, è consigliabile aggiungere i client RADIUS tramite script se si prevede di eseguire l'aggiunta di un gran numero di punti di accesso senza fili.
  
**Importante:** questa procedura rappresenta un metodo alternativo che consente di aggiungere i client mediante la creazione di script anziché in modo interattivo. Se si è scelto di seguire la procedura precedente "Aggiunta di un client RADIUS al primo server IAS", non sarà necessario attenersi alla seguente procedura.
  
Utilizzare la seguente procedura per generare segreti RADIUS avanzati. Lo script, come nella procedura precedente, utilizza una funzione CryptoAPI che consente di generare un valore del tutto casuale per ogni segreto RADIUS. In questo modo i valori saranno sufficientemente sicuri da scongiurare eventuali attacchi del dizionario o di identificazione della password.
  
**Per generare file di voci client per i punti di accesso senza fili**
  
1.  Aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Eseguire il comando sottostante. Immettere un nome descrittivo per il punto di accesso senza fili al posto del parametro *NomeClient* e l'indirizzo IP del punto di accesso senza fili al posto di *IndirizzoIP*. (È possibile specificare un percorso e un nome di file alternativi per indicare la posizione in cui verrà salvato l'output. Se non viene specificato alcun parametro di percorso, l'output verrà salvato nel file Clients.txt nella cartella di lavoro corrente). Se il file di output è già esistente, il nuovo valore verrà aggiunto al file. In caso contrario, il file verrà creato.
  
    **MSSTools GenRADIUSPwd /client:***NomeClient***/IP:***IndirizzoIP* \[**/path:***percorso\\nomefile*\]
  
    I parametri "client" e "path" possono includere spazi. Se uno dei due parametri contiene uno spazio, sarà necessario racchiuderlo tra virgolette. Anche se il comando può essere visualizzato su più righe, è necessario che venga immesso su una singola riga.
  
3.  Ripetere il passaggio 2 per tutti i punti di accesso senza fili per i quali è necessario generare segreti RADIUS. Ogni voce client verrà aggiunta al file di output (per impostazione predefinita Clients.txt). Il file di output è un file di testo delimitato da virgola con un client RADIUS per ogni riga che può essere facilmente utilizzato negli script o importato e modificato mediante l'utilizzo di applicazioni quali Microsoft Excel.
  
    **Avviso:** non lasciare il file di output sul server in quanto contiene i segreti dei client RADIUS in testo normale. Dopo aver aggiunto i punti di accesso senza fili, spostare il file su un disco floppy o su un altro supporto rimovibile e conservarlo in un luogo sicuro.
  
    **Nota:** a differenza della maggior parte degli script utilizzati nelle procedure di installazione, questo script non registra informazioni sullo stato nel file di registro MSSWLAN-setup.log. In questo modo i segreti dei client RADIUS non vengono archiviati nel file e vengono scongiurati eventuali rischi per la protezione. Tuttavia, le informazioni sullo stato vengono visualizzate sullo schermo.
  
##### Importazione dei punti di accesso nel secondo server IAS
  
Dopo aver aggiunto i punti di accesso senza fili al primo server IAS, è necessario aggiungerli a un secondo server prima di configurarli per l'utilizzo di RADIUS.
  
**Per importare i client RADIUS nel secondo server IAS**
  
1.  Copiare il file di output dei client creato nelle procedure precedenti (per motivi di protezione rimuovere il file dal primo server IAS in cui non ne è più richiesta la presenza).
  
2.  Aprire e visualizzare il file in Blocco note o Microsoft Excel per verificare se contiene le voci corrette. (Questa operazione è importante perché il file potrebbe contenere voci vecchie lasciate in seguito a una precedente esecuzione della procedura). Rimuovere tutte le voci client non necessarie.
  
3.  Eseguire il comando seguente per importare i client nel secondo server IAS:
  
    **MSSTools AddSecRADIUSClients** \[**/path:***FileInput.txt*\]
  
    **Nota:** il parametro *path* è facoltativo. È possibile utilizzare un parametro di percorso diverso per leggere l'input appartenente a un file o a una cartella differente. Il percorso deve essere racchiuso tra virgolette se contiene spazi incorporati. Se non viene specificato alcun parametro, il comando eseguirà la ricerca e la lettura dell'input dal file Clients.txt nella directory corrente.
  
4.  Lo script, oltre a rifiutare tutte le voci client non valide incluse nel file, consentirà di visualizzare il numero di voci valide e non valide.
  
5.  Aprire la MMC **Servizio di Autenticazione Internet** ed esaminare il contenuto della cartella **Client RADIUS** per verificare se l'aggiunta dei client è stata eseguita in modo corretto.
  
    **Nota:** a differenza della maggior parte degli script utilizzati durante l'installazione e la configurazione della soluzione, questo script non registra informazioni sullo stato nel file MSSWLAN-setup.log. In questo modo i segreti dei client RADIUS non vengono archiviati nel file e vengono scongiurati eventuali rischi per la protezione. Tuttavia, le informazioni sullo stato vengono visualizzate sullo schermo.
  
#### Configurazione dei punti di accesso senza fili
  
Dopo aver aggiunto al server IAS le voci dei client RADIUS per i punti di accesso senza fili, è possibile configurare i punti di accesso senza fili. È necessario aggiungere gli indirizzi IP dei server IAS e i segreti dei client RADIUS che verranno utilizzati da ogni punto di accesso per comunicare in modo protetto con i server IAS. Ogni punto di accesso senza fili verrà configurato con un server IAS primario e uno secondario (o di backup). È necessario eseguire le procedure incluse nella presente sezione per i punti di accesso senza fili in ogni sito dell'organizzazione. Per ulteriori informazioni sulla modalità di assegnazione dei punti di accesso senza fili ai server IAS, fare riferimento al capitolo 2 "Pianificazione dell'implementazione della protezione di reti LAN senza fili".
  
La procedura per configurare i punti di accesso senza fili varia in base alla marca e al modello della periferica. Tuttavia, i fornitori dei punti di accesso senza fili in genere forniscono istruzioni dettagliate per la configurazione delle proprie periferiche. A seconda del fornitore, è possibile che le istruzioni siano disponibili anche in linea.
  
Prima di configurare le impostazioni di protezione per i punti di accesso senza fili, è necessario configurare le impostazioni di rete di base. Di seguito sono riportate solo alcune delle impostazioni previste:
  
-   Indirizzo IP e subnet mask del punto di accesso senza fili
  
-   Gateway predefinito
  
-   Nome descrittivo del punto di accesso senza fili
  
-   Nome rete senza fili (SSID)
  
L'elenco include molti altri parametri che interessano la distribuzione di più punti di accesso senza fili come le impostazioni che controllano la corretta copertura radio per il sito, ad esempio il canale radio 802.11, la velocità di trasmissione, la potenza di trasmissione e così via. Poiché si tratta di parametri che non vengono trattati nella presente guida, è consigliabile utilizzare la documentazione di riferimento del fornitore o consultare un provider di servizi di rete per configurarli in modo corretto. Per ulteriori informazioni sulla distribuzione dei punti di accesso senza fili, vedere i riferimenti riportati nella parte finale del capitolo.
  
In base alle indicazioni fornite nel presente capitolo si presume che gli elementi specificati siano stati impostati in modo corretto e che pertanto sia possibile connettersi al punto di accesso senza fili da un client WLAN mediante una connessione non autenticata. Questo aspetto deve essere verificato prima di configurare i parametri di autenticazione e protezione indicati nelle sezioni seguenti.
  
##### Abilitazione dell'autenticazione per reti WLAN protette sui punti di accesso
  
È necessario configurare ogni punto di accesso senza fili con un server RADIUS primario e uno secondario. Il punto di accesso senza fili in genere utilizza il server primario per tutte le richieste di autenticazione e passa al server secondario in caso di indisponibilità del server primario. Come indicato nel capitolo 2, "Pianificazione dell'implementazione della protezione di reti LAN senza fili", è importante pianificare l'assegnazione dei punti di accesso senza fili e decidere accuratamente il server primario e quello secondario. Per riepilogare:
  
-   In un sito con due o più server IAS è necessario bilanciare i punti di accesso senza fili sui server disponibili in modo tale che circa la metà utilizzi il server 1 come primario e il server 2 come secondario e che quelli restanti utilizzino il server 2 come primario e il server 1 come secondario.
  
-   Nei siti in cui è disponibile un singolo server IAS, tale server verrà sempre utilizzato come server primario. È quindi necessario configurare un server remoto (nel sito con connettività più affidabile) come server secondario.
  
-   Nei siti in cui non è disponibile alcun server IAS, è necessario bilanciare i punti di accesso senza fili tra i server remoti utilizzando il server con connettività a resilienza più elevata e latenza inferiore. In pratica, i server devono trovarsi in siti diversi a meno che non sia disponibile una connettività WAN resiliente.
  
Nella seguente tabella vengono indicate le impostazioni necessarie per la configurazione dei punti di accesso senza fili. Anche se i nomi e le descrizioni delle impostazioni possono variare a seconda del fornitore, la documentazione relativa ai punti di accesso senza fili consente di determinare le impostazioni corrispondenti agli elementi inclusi nella tabella.
  
**Tabella 5.3: Configurazione punti di accesso senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Elemento</th>
<th style="border:1px solid black;" >Impostazione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"><strong>Parametri di autenticazione</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Modalità di autenticazione</td>
<td style="border:1px solid black;">Autenticazione 802.1X</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Riautenticazione</td>
<td style="border:1px solid black;">Abilita</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Reimpostazione chiavi rapida/dinamica</td>
<td style="border:1px solid black;">Abilita</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Timeout aggiornamento chiavi</td>
<td style="border:1px solid black;">60 minuti</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>Parametri di crittografia (impostazioni in genere collegate alla crittografia WEP statica)</strong></td>
<td style="border:1px solid black;">(I parametri di crittografia possono essere disabilitati o sottoposti a overriding quando è abilitata la reimpostazione rapida delle chiavi)</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Abilita crittografia</td>
<td style="border:1px solid black;">Abilita</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Rifiuta non crittografati</td>
<td style="border:1px solid black;">Abilita</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>Autenticazione RADIUS</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Abilita autenticazione RADIUS</td>
<td style="border:1px solid black;">Abilita</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Server autenticazione RADIUS primario</td>
<td style="border:1px solid black;">Indirizzo IP server IAS primario</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Porta server RADIUS primario</td>
<td style="border:1px solid black;">1812 (predefinita)</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Server autenticazione RADIUS secondario</td>
<td style="border:1px solid black;">Indirizzo IP server IAS secondario</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Porta server RADIUS secondario</td>
<td style="border:1px solid black;">1812 (predefinita)</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Segreto condiviso autenticazione RADIUS</td>
<td style="border:1px solid black;"><strong>XXXXXX</strong> (sostituire con il segreto generato)</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Numero massimo tentativi</td>
<td style="border:1px solid black;">5</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Timeout tentativi</td>
<td style="border:1px solid black;">5 secondi</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>Accounting RADIUS</strong></td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Abilita accounting RADIUS</td>
<td style="border:1px solid black;">Abilita</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Server accounting RADIUS primario</td>
<td style="border:1px solid black;">Indirizzo IP server IAS primario</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Porta server RADIUS primario</td>
<td style="border:1px solid black;">1813 (predefinita)</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Server accounting RADIUS secondario</td>
<td style="border:1px solid black;">Indirizzo IP server IAS secondario</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Porta server RADIUS secondario</td>
<td style="border:1px solid black;">1813 (predefinita)</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Segreto condiviso accounting RADIUS</td>
<td style="border:1px solid black;"><strong>XXXXXX</strong> (sostituire con il segreto generato)</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Numero massimo tentativi</td>
<td style="border:1px solid black;">5</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Timeout tentativi</td>
<td style="border:1px solid black;">5 secondi</td>
</tr>
</tbody>
</table>
  
**Importante:** l'opzione **Timeout aggiornamento chiavi** è impostata su 60 minuti per l'utilizzo con WEP dinamico. Il valore **Timeout sessione** impostato nel criterio di accesso remoto IAS è uguale o inferiore al valore dell'opzione. Per ulteriori informazioni, vedere la sezione precedente "Modifica delle impostazioni del profilo dei Criteri di accesso WLAN". Poiché l'impostazione con il valore più basso assume la precedenza, sarà sufficiente modificare l'impostazione nel server IAS. Se si utilizza la protezione WPA, sarà necessario aumentare il valore dell'impostazione nel punto di accesso a 8 ore. Per ulteriori informazioni, vedere la documentazione del fornitore.
  
Per aggiungere punti di accesso senza fili al server IAS, utilizzare gli stessi segreti RADIUS generati mediante la procedura "Aggiunta di un client RADIUS al primo server IAS". Anche se non è stato ancora configurato un server IAS secondario per il backup del server primario, è tuttavia possibile aggiungere l'indirizzo IP del server al punto di accesso senza fili (per evitare di doverlo riconfigurare in seguito). La configurazione di server IAS aggiuntivi verrà trattata in una sezione successiva del presente capitolo.
  
In base al modello hardware dei punti di accesso senza fili, è possibile che per i server RADIUS di autenticazione e accounting non siano presenti voci configurabili separate. Se esistono voci configurabili separate, sarà necessario impostarle entrambe sullo stesso server a meno che non vi sia un motivo particolare per procedere in modo diverso.
  
I valori di timeout e numero massimo di tentativi di RADIUS indicati nella tabella in genere sono predefiniti ma non obbligatori.
  
**Nota:** se si utilizzano punti di accesso senza fili senza alcuna protezione attivata o solo con WEP statico, sarà necessario pianificare la migrazione a una rete WLAN basata su 802.1X. Per ulteriori informazioni sulla migrazione da una rete senza fili esistente, vedere la sezione "Migrazione da una rete WLAN esistente" del capitolo 2 "Pianificazione dell'implementazione della protezione di reti LAN senza fili".
  
##### Impostazioni aggiuntive per la protezione dei punti di accesso senza fili
  
Oltre ad abilitare i parametri 802.1X, è necessario configurare una protezione più elevata per i punti di accesso senza fili. La maggior parte dell'hardware di rete viene fornito con protocolli di gestione non protetti e password di amministratore impostate su valori predefiniti noti che comportano rischi per la protezione. Anche se la tabella sottostante non è completa, è necessario configurare le impostazioni indicate. Per informazioni attendibili sull'argomento, è consigliabile consultare la documentazione del fornitore. Quando si scelgono le password e i nomi di comunità per il protocollo SNMP, è necessario utilizzare valori complessi che includano lettere maiuscole e minuscole, numeri e segni di punteggiatura. Evitare di ricorrere a informazioni facilmente identificabili quali nomi di dominio, nomi di società e indirizzi di siti.
  
**Tabella 5.4: Configurazione protezione punti di accesso senza fili**

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Elemento</th>
<th style="border:1px solid black;" >Impostazione consigliata</th>
<th style="border:1px solid black;" >Note</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;"><strong>Generale</strong></td>
<td style="border:1px solid black;"><br />
</td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Password amministratore</td>
<td style="border:1px solid black;">XXXXXX</td>
<td style="border:1px solid black;">Impostare una password complessa.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Altre password di gestione</td>
<td style="border:1px solid black;">XXXXXX</td>
<td style="border:1px solid black;">In alcune periferiche vengono utilizzate diverse password di gestione per ottenere un accesso protetto mediante l'utilizzo di protocolli di gestione differenti. Verificare che tutti i valori predefiniti vengano sostituiti con valori in grado di assicurare maggiore protezione.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;"><strong>Protocolli di gestione</strong></td>
<td style="border:1px solid black;"><br />
</td>
<td style="border:1px solid black;"><br />
</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Console seriale</td>
<td style="border:1px solid black;">Abilita</td>
<td style="border:1px solid black;">Se non sono disponibili protocolli crittografati, questo è il metodo più sicuro per configurare i punti di accesso senza fili benché siano richieste connessioni fisiche via cavo seriale tra i punti di accesso senza fili e il terminale e non possa essere utilizzato in remoto.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Telnet</td>
<td style="border:1px solid black;">Disabilita</td>
<td style="border:1px solid black;">Tutte le trasmissioni Telnet sono in testo normale, pertanto le password e i segreti dei client RADIUS saranno visibili sulla rete. Se è possibile garantire la protezione del traffico Telnet mediante l'utilizzo di criteri IPsec o SSH, Telnet può essere abilitato e utilizzato in modo sicuro.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">HTTP</td>
<td style="border:1px solid black;">Disabilita</td>
<td style="border:1px solid black;">La gestione HTTP in genere è in testo normale e presenta gli stessi punti deboli del protocollo Telnet non crittografato. Se disponibile, è consigliabile l'utilizzo di HTTPS.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">HTTPS (SSL o TLS)</td>
<td style="border:1px solid black;">Abilita</td>
<td style="border:1px solid black;">Per la configurazione di chiavi e certificati per HTTPS, seguire le istruzioni del fornitore.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"><strong>Comunità SNMP</strong></td>
<td style="border:1px solid black;"><br />
</td>
<td style="border:1px solid black;">SNMP è il protocollo predefinito per la gestione della rete. Utilizzare SNMP v3 con password di protezione per ottenere il livello di protezione più elevato. Spesso viene utilizzato dagli strumenti di configurazione GUI e dai sistemi per la gestione della rete. Tuttavia, se non viene impiegato può essere disabilitato.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Nome comunità 1</td>
<td style="border:1px solid black;">XXXXXX</td>
<td style="border:1px solid black;">In genere, il valore predefinito è &quot;pubblico&quot; e va sostituito con un valore complesso.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Nome comunità 2</td>
<td style="border:1px solid black;">Disabilitato</td>
<td style="border:1px solid black;">I nomi di comunità non necessari devono essere disabilitati o impostati su valori complessi.</td>
</tr>
</tbody>
</table>
  
Non è necessario disabilitare la trasmissione SSID (nome rete WLAN) perché potrebbe impedire la connessione di Windows XP alla rete corretta. Anche se la disabilitazione della trasmissione SSID rappresenta una misura di protezione spesso consigliata, garantisce pochi vantaggi pratici se viene utilizzato un metodo di autenticazione 802.1X protetto. Anche se la trasmissione SSID dal punto di accesso viene disabilitata, è relativamente facile per un utente malintenzionato determinare l'SSID mediante l'acquisizione di pacchetti di connessione client. Se si intende proteggere l'identità della rete WLAN durante la trasmissione, è possibile assegnare un nome generico all'SSID non attribuibile all'organizzazione.
  
#### Replica della configurazione di client RADIUS in altri server IAS
  
In genere, i punti di accesso senza fili di un sito specifico vengono gestiti dal server IAS dello stesso sito. Il server IAS del sito A, ad esempio, soddisfa le richieste dei punti di accesso senza fili del sito A, mentre il server del sito B soddisfa le richieste dei punti di accesso senza fili del sito B e così via. Tuttavia, altre impostazioni server, ad esempio i criteri di accesso remoto, spesso sono comuni a molti server IAS. Per questo motivo, l'importazione e l'esportazione delle informazioni dei client RADIUS viene gestita separatamente mediante le procedure descritte nella presente sezione.
  
Anche se la replica delle informazioni dei client RADIUS è richiesta solo in pochi scenari, questa operazione può risultare utile in molte circostanze, ad esempio quando si dispone di due server IAS nello stesso sito che fungono da server RADIUS primario e secondario per tutti i punti di accesso senza fili appartenenti al sito.
  
**Per esportare le impostazioni dei client RADIUS in un file**
  
1.  Accedere al server IAS di origine e aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Se richiesto, identificare una cartella per memorizzare il file di output o inserire un disco floppy formattato nell'unità del server.
  
3.  Eseguire il seguente comando per esportare la configurazione dei client RADIUS:
  
    **MSSTools ExportIASClients** \[**/path:***CartellaOutput*\]
  
    *CartellaOutput* è un parametro facoltativo utilizzato per specificare la cartella in cui verrà scritto il file di output. Se il parametro non viene specificato, il file di output verrà scritto nella directory corrente. Se il parametro viene specificato, la cartella deve essere disponibile.
  
4.  Lo script crea il file IAS\_Clients.txt.
  
    **Avviso:** è necessario rimuovere il file dal server e memorizzarlo in un luogo sicuro in quanto contiene i segreti RADIUS di tutti i punti di accesso senza fili configurati sul server. Dopo aver esportato le impostazioni dei client RADIUS, è possibile importarle in altri server. Questa operazione viene in genere eseguita per la creazione di un server secondario per un gruppo specifico di punti di accesso senza fili.
  
**Per importare le impostazioni dei client RADIUS da un file:**
  
1.  Accedere al server IAS di destinazione e aprire una shell comandi utilizzando il collegamento **MSS WLAN Tools**.
  
2.  Identificare la cartella o il disco floppy in cui è memorizzato il file dei segreti RADIUS esportato IAS\_Clients.txt.
  
3.  Eseguire il seguente comando per importare la configurazione dei client RADIUS:
  
    **MSSTools ImportIASClients** \[**/path:***CartellaInput*\]
  
    *CartellaInput* è un parametro facoltativo utilizzato per specificare la cartella in cui verrà letto il file. Se specificata, la cartella deve essere disponibile. Se non viene specificata alcuna cartella, si presume che il file sia incluso nella directory corrente.
  
    **Avviso:** se è stata eseguita una copia del file IAS\_Clients.txt nel server di destinazione, è necessario che tale copia venga rimossa dal server e memorizzata in un luogo sicuro in quanto contiene i segreti RADIUS di tutti i punti di accesso senza fili configurati sul server.
  
    L'importazione delle informazioni dei client RADIUS non è un processo di tipo aggiuntivo. Le impostazioni importate dai client RADIUS sovrascriveranno le voci client esistenti sul server.
  
Per eseguire l'importazione dei client RADIUS con un metodo più flessibile, è possibile utilizzare lo strumento AddRADIUSClient.exe fornito con la soluzione. Questo strumento consente di creare lo script per aggiungere i client RADIUS nei diversi server in modo selettivo.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Riepilogo
  
Nel presente capitolo vengono descritte le procedure seguenti:
  
-   Come installare e configurare il primo server IAS.
  
-   Come installare server IAS aggiuntivi e replicare la configurazione del primo server.
  
-   Come aggiungere punti di accesso senza fili al server IAS come client RADIUS.
  
-   Come configurare punti di accesso senza fili per l'utilizzo dei server IAS e come modificare le impostazioni predefinite per aumentare la protezione.
  
A questo punto è possibile configurare i client WLAN. Per ulteriori informazioni sull'esecuzione di questa procedura, vedere il capitolo 6 "Configurazione dei client delle reti LAN senza fili".
  
È consigliabile consultare il capitolo 8 "Gestione della soluzione per reti LAN senza fili protette". In questo capitolo sono incluse informazioni essenziali per garantire l'esecuzione dell'infrastruttura RADIUS in un ambiente protetto e affidabile.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Riferimenti
  
Questa sezione contiene rimandi a informazioni supplementari importanti e ad altro materiale attinente al contenuto di questo capitolo.
  
-   La sezione "Servizio di Autenticazione Internet" della documentazione di Windows Server 2003 disponibile all'URL seguente:
  
    <http://technet.microsoft.com/en-us/library/cc759100.aspx> (in inglese).
  
-   Per ulteriori informazioni sulla distribuzione di IAS, vedere il capitolo "Deploying IAS" del *Windows Server 2003 Deployment Kit* disponibile all'URL seguente:
  
    [http://go.microsoft.com/fwlink/?LinkId=4716](http://go.microsoft.com/fwlink/?linkid=4716) (in inglese).
  
-   Per ulteriori informazioni sulla programmazione di IAS mediante l'utilizzo dell'interfaccia Oggetti dati server, vedere la pagina "Server Data Objects" su MSDN disponibile all'URL seguente:
  
    [http://msdn.microsoft.com/en-us/library/bb960722(VS.85).aspx](http://msdn.microsoft.com/en-us/library/bb960722(vs.85).aspx) (in inglese).
  
-   Per ulteriori informazioni sulla registrazione di IAS e RADIUS, vedere la sezione "Remote Access Logging" nella documentazione di IAS disponibile all'URL seguente:
  
    <http://technet.microsoft.com/en-us/library/cc786043.aspx> (in inglese).
  
-   Per ulteriori informazioni sul supporto Pocket PC per la riconnessione rapida PEAP, vedere l'articolo 827824, "FIX: Wireless Clients Cannot Connect When the PEAP Fast Reconnect Authentication Option is Turned On" della Microsoft Knowledge Base disponibile all'URL seguente:
  
    <http://support.microsoft.com/default.aspx?scid=kb;en-us;827824> (in inglese).
  
-   Per ulteriori informazioni sulla configurazione di supporti RADIUS specifici per i punti di accesso, vedere la pagina "Vendor-Specific Attributes" nella documentazione di IAS disponibile all'URL seguente:
  
    <http://technet.microsoft.com/en-us/library/cc782608.aspx> (in inglese).
  
-   Per ulteriori informazioni sulla distribuzione delle reti WLAN, vedere il capitolo "Deploying a Wireless LAN" del *Windows Server 2003 Deployment Kit* disponibile all'URL seguente:
  
    <http://technet.microsoft.com/en-us/library/cc780901.aspx> (in inglese).
  
-   Per ulteriori informazioni sulla tecnologia senza fili Windows XP, vedere il white paper *Windows XP Wireless Deployment Technology and Component Overview* disponibile all'URL seguente:
  
    <http://technet.microsoft.com/en-us/library/bb457015.aspx> (in inglese).
  
**Scarica la soluzione completa**
  
[Protezione delle reti LAN senza fili con PEAP e password](http://go.microsoft.com/fwlink/?linkid=23481)
  
[](#mainsection)[Inizio pagina](#mainsection)
