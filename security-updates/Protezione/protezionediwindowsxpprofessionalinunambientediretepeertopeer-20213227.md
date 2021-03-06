---
TOCTitle: 'Protezione di Windows XP Professional in un ambiente di rete peer-to-peer'
Title: 'Protezione di Windows XP Professional in un ambiente di rete peer-to-peer'
ms:assetid: '8dbc5935-ec3e-4b06-bc4e-4edf8aace9e2'
ms:contentKeyID: 20213227
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc875837(v=TechNet.10)'
---

Protezione di Windows XP Professional in un ambiente di rete peer-to-peer
=========================================================================

##### In questa pagina

[](#efaa)[Introduzione](#efaa)
[](#eeaa)[Prima di iniziare](#eeaa)
[](#edaa)[Protezione del File System](#edaa)
[](#ecaa)[Windows Firewall](#ecaa)
[](#ebaa)[Aggiornamento delle patch di protezione](#ebaa)
[](#eaaa)[Informazioni correlate](#eaaa)

### Introduzione

Le reti peer-to-peer possono aumentare la produttività agevolando la condivisione delle informazioni e delle risorse di rete. Tuttavia, la possibilità degli utenti di controllare l'accesso ai rispettivi computer può renderli vulnerabili alla perdita, al furto o alla divulgazione involontaria di file. Pertanto, oltre a implementare criteri per i computer aziendali, è consigliabile accertarsi che tutti i dipendenti comprendano le nozioni di base sulle reti peer-to-peer e sulla protezione in ambiente Windows.

La minaccia rappresentata dal malware (worm, virus, trojan horse e spyware) e dai pirati informatici impone di agire immediatamente per bloccare i computer desktop e portatili. Questo documento descrive come implementare misure di protezione per le piccole e medie imprese che utilizzano reti peer-to-peer. Grazie a queste indicazioni è possibile migliorare la protezione dei computer che eseguono Microsoft Windows XP Professional con Service Pack 2 (SP2) senza compromettere l'efficienza e la produttività degli utenti.

#### Scopo del documento

Dopo aver acquisito familiarità con le informazioni contenute nel documento, sarà possibile migliorare la protezione dei gruppi di lavoro peer-to-peer.

[](#mainsection)[Inizio pagina](#mainsection)

### Prima di iniziare

Come per ogni indicazione relativa alla protezione, in quelle fornite in questa guida si è cercato di offrire un giusto equilibrio tra protezione avanzata e utilizzabilità. I consigli forniti nel presente documento funzionano correttamente per le distribuzioni di Windows XP Professional SP2 in un'ampia gamma di ambienti. Tuttavia, prima di implementare tali indicazioni, tenere presente che le informazioni contenute in questo documento non prendono in considerazione tutte le esigenze e configurazioni tipiche di organizzazioni di grandi dimensioni. È inoltre possibile che questa guida non soddisfi completamente le esigenze di protezione specifiche di alcune organizzazioni.

#### Conformità al requisito relativo ai Service Pack

Le indicazioni fornite nel presente documento si applicano unicamente a computer che eseguono Windows XP Professional con SP2 appartenenti a gruppi di lavoro e non a domini. Se SP2 non è installato in un determinato computer oppure in caso di dubbi, è possibile visitare la pagina [Microsoft Update](http://windowsupdate.microsoft.com/) del sito Web Microsoft all'indirizzo http://windowsupdate.microsoft.com ed eseguire l'analisi del computer per individuare gli aggiornamenti disponibili. Se SP2 viene indicato come aggiornamento disponibile, installarlo prima di eseguire le procedure illustrate nel presente documento.

**Nota** L'installazione di SP2 richiede il riavvio del computer.

#### Requisiti amministrativi

È necessario accedere come amministratore o membro del gruppo Administrators per completare le procedure seguenti. Se il computer utilizzato è connesso a una rete, le impostazioni dei criteri di rete possono impedire l'esecuzione di queste procedure.

[](#mainsection)[Inizio pagina](#mainsection)

### Protezione del File System

Il file system determina il modo in cui directory e file sono organizzati nei computer. Esistono vari modi per proteggere il file system dall'accesso, la modifica o l'eliminazione non autorizzati. In questa sezione vengono fornite istruzioni dettagliate per l'esecuzione delle attività seguenti, che consentono di proteggere il file system:

-   Conversione dei file system in NTFS

-   Utilizzo di software antivirus

-   Utilizzo di Windows Defender (Beta 2)

-   Protezione delle condivisioni file

-   Protezione delle cartelle condivise

-   Disattivazione dei servizi non necessari

-   Disattivazione o eliminazione degli account non necessari

#### Conversione dei file system in NTFS

Durante l’installazione di Windows XP, i computer possono essere configurati per utilizzare il file system FAT32 o NTFS.

FAT32 è una tecnologia meno recente, utilizzata da versioni precedenti di Windows. Il file system NTFS è più rapido e sicuro di FAT32 e di molti altri file system obsoleti. Per prestazioni ottimali del sistema operativo, utilizzare NTFS per proteggere tutte le partizioni del file system nel computer. Attenersi alle due procedure seguenti per verificare preliminarmente il tipo di file system del computer locale, quindi, se necessario, convertirlo in NTFS.

**Importante** Prima di convertire una partizione FAT in NTFS, è necessario considerare quanto segue:

-   La conversione è un processo irreversibile: dopo aver convertito una partizione in NTFS, non è più possibile ripristinare il formato FAT se non formattando nuovamente la partizione in questione, il che comporta la cancellazione dei dati contenuti al suo interno. Sarà quindi necessario ripristinare successivamente i dati eliminati utilizzando una copia di backup.

-   Dopo avere convertito un'unità del computer in NTFS, non è più possibile rimuovere Windows XP e tornare a Windows 98 o Windows Millennium Edition (ME).

-   Per effettuare la conversione del file system, Convert.exe richiede una determinata quantità di spazio libero nell'unità: Per ulteriori informazioni a questo proposito, vedere l'articolo della Microsoft Knowledge Base
    [Spazio libero richiesto per la conversione da FAT a NTFS](http://support.microsoft.com/kb/156560) all'indirizzo http://support.microsoft.com/kb/156560.

**Per verificare il tipo di file system del computer**

1.  Fare clic sul pulsante **Start**, quindi scegliere **Risorse del computer**.

2.  Fare clic con il pulsante destro del mouse sulla lettera dell'unità da controllare e scegliere **Proprietà**.

3.  Il tipo di file system dovrebbe essere NTFS, come mostrato nella schermata seguente. In caso contrario, l'utilità Convert.exe consente di eseguire la conversione da FAT16 o FAT32 a NTFS.

    ![](images/Cc875837.XPP2P01(it-it,TechNet.10).gif "XPP2P01.GIF")

Ripetere la procedura per tutte le partizioni sui dischi rigidi del computer. Anche se il file system è stato configurato come FAT32 al momento dell'installazione del sistema operativo, è semplice convertirlo in NTFS per assicurare ulteriore protezione.

Per convertire il file system in NTFS, prendere nota del nome del disco, detto anche etichetta del volume (Unità C nella figura precedente) ed eseguire la procedura illustrata di seguito. La conversione del file system in NTFS garantisce al computer un livello di protezione superiore.

**Per convertire il file system in NTFS**

1.  Fare clic sul pulsante **Start**, scegliere **Esegui**, digitare **cmd**, quindi fare clic su **OK**.

2.  Al prompt dei comandi digitare quanto indicato di seguito, dove *&lt;lettera\_unità&gt;* è l'unità che si desidera convertire, quindi premere INVIO:

    **convert** ***&lt;lettera\_unità&gt;*: /fs:ntfs**

3.  Verrà richiesto di immettere l'etichetta di volume corrente per l'unità. Immettere l'etichetta di volume identificata in precedenza, quindi premere INVIO.

4.  Al termine della conversione, digitare **exit**, quindi premere INVIO per chiudere il prompt dei comandi.

    **Nota**: se si sta tentando di convertire l'unità in cui è installato il sistema operativo, potrebbe essere richiesto di pianificare la conversione al successivo riavvio del computer. In questo caso, digitare **y** e premere INVIO per riavviare il computer.

#### Utilizzo di programmi antivirus

I virus sono programmi che vengono caricati nel computer all'insaputa, o senza l'autorizzazione, dell'utente. I virus e altri tipi di malware sono in circolazione da molto tempo. Oggi i virus possono replicarsi e utilizzare Internet e le applicazioni di posta elettronica per diffondersi in tutto il mondo in meno di un'ora.

I programmi software antivirus sono utili per proteggere il computer da virus, worm e trojan horse noti, nonché da altro codice dannoso. Il software antivirus esegue costantemente la scansione del computer alla ricerca di virus e permette di identificarli e rimuoverli facilmente. L'installazione di un programma antivirus rappresenta solo una soluzione parziale al problema. Per mantenere la protezione di un computer desktop o portatile è essenziale aggiornare regolarmente i file delle firme antivirus.

In molti dei nuovi computer è già installato un programma antivirus. Per mantenerlo aggiornato è tuttavia necessario un abbonamento. Se al momento non si dispone di un abbonamento per questi aggiornamenti, il computer potrebbe essere vulnerabile a nuovi virus.

La familiarità degli utenti con l'utilizzo sicuro della posta elettronica è un altro aspetto importante per prevenire gli attacchi dei virus. Evitare di aprire messaggi di posta elettronica o di utilizzare gli allegati, a meno che non sia nota la fonte dei file e accertarsi che essi vengano sottoposti a scansione da parte del software antivirus prima di essere eseguiti.

Microsoft mette a disposizione Windows Live OneCare, un servizio di manutenzione dei PC che si aggiorna automaticamente e viene eseguito in background. Esso fornisce una protezione costante contro virus, pirati informatici e altre minacce, nonché consente di ottimizzare il computer ed effettuare il backup dei documenti importanti. Per ulteriori informazioni, vedere [Windows Live OneCare](http://www.windowsonecare.com/) all'indirizzo www.windowsonecare.com/ (in inglese).

Per ulteriori informazioni sui fornitori di software antivirus compatibile con Windows XP, consultare la pagina [Elenco di fornitori di software antivirus](http://support.microsoft.com/kb/49500) nel sito Web Microsoft all'indirizzo http://support.microsoft.com/kb/49500.

#### Utilizzo di Microsoft Defender

Windows Defender (Beta2) è una tecnologia di protezione che consente di proteggere gli utenti di Windows da spyware e altro software potenzialmente dannoso. È possibile individuare e rimuovere le applicazioni spyware conosciute eventualmente presenti nel computer per ridurne gli effetti negativi, ovvero la diminuzione delle prestazioni, la visualizzazione di fastidiose finestre pubblicitarie popup, le modifiche indesiderate alle impostazioni Internet e l'utilizzo non autorizzato di informazioni riservate. La protezione costante aumenta la sicurezza dell'esplorazione di Internet sorvegliando oltre 50 dei modi in cui lo spyware può accedere ai computer. I membri della community SpyNet, diffusa in tutto il mondo, svolgono un ruolo fondamentale nel determinare quali programmi sospetti vengono classificati come spyware e i ricercatori Microsoft sviluppano rapidamente metodi per contrastare queste minacce; gli aggiornamenti vengono scaricati automaticamente nel PC che, quindi, è sempre aggiornato.

È possibile scaricare [Windows Defender](http://www.microsoft.com/italy/athome/security/spyware/software/default.mspx) all'indirizzo http://www.microsoft.com/italy/athome/security/spyware/software/default.mspx. La versione corrente è la Beta 2. Il nome del file è WindowsDefender.msi e le sue dimensioni sono pari a circa 5,5 MB. Il nome del file e le dimensioni potrebbero variare in seguito al rilascio della versione definitiva.

#### Protezione delle condivisioni di file

Le condivisioni di file in Windows XP Professional consentono di condividere i file di un disco rigido locale con altri utenti di sistemi Windows. È possibile assegnare un nome condivisione a un'intera directory o cartella e concedere a determinati utenti o gruppi di utenti le autorizzazioni relative al nome in questione. Le condivisioni di file funzionano allo stesso modo indipendentemente dal fatto che la workstation faccia parte di un dominio o di un gruppo di lavoro: in entrambi i casi, è possibile creare condivisioni per consentire agli utenti di altre workstation di accedere a una directory di un disco rigido locale. L'utente di una workstation che esegue Windows XP Professional può assegnare le autorizzazioni relative a queste condivisioni ad account e gruppi locali in entrambe le configurazioni, tuttavia è possibile assegnare l'accesso ad account e gruppi dei servizi directory Active Directory solo se la workstation è membro di Active Directory.

Per impostazione predefinita, le condivisioni vengono create assegnando il controllo completo al gruppo Everyone. Le autorizzazioni devono essere modificate in modo da consentire l'accesso alla condivisione solo agli utenti per i quali è necessario. È inoltre possibile limitare le operazioni che gli account utente o i gruppi di account utente possono effettuare su una determinata condivisione file, autorizzando l'accesso in sola lettura oppure consentendo la creazione, la modifica e l'eliminazione dei file.

La condivisione di file è destinata all'utilizzo in una rete domestica o aziendale protetta da un firewall, ad esempio Windows Firewall (disponibile in Windows XP SP2). Se si è connessi a Internet e non si utilizza un firewall, tenere presente che le condivisioni di file create sono accessibili a tutti gli utenti di Internet.

#### Protezione delle cartelle condivise

Le funzionalità di rete peer-to-peer di Windows consentono di condividere il contenuto del file system con altri computer della rete. Nella procedura seguente si presuppone che siano state condivise una o più cartelle del file system. Modificando una o più impostazioni predefinite del file system, è possibile limitare l'accesso non autorizzato alle condivisioni.

-   Ogni utente che richiede l'accesso alla condivisione dal proprio computer deve disporre di un account utente nella workstation che contiene la condivisione stessa; questo requisito costituisce una limitazione della configurazione delle reti per gruppi di lavoro peer-to-peer. È opportuno limitare il più possibile il numero di computer che contengono directory condivise. Se in ogni workstation sono presenti condivisioni, è necessario che ognuna di esse contenga gli account utente; in questo caso, la gestione della configurazione può diventare complessa.

-   È possibile impostare le autorizzazioni solo per le unità formattate in modo da utilizzare il file system NTFS.

-   Nella procedura seguente viene rimosso il gruppo speciale **Everyone**, che consente l'accesso anonimo e a ogni account utente locale vengono assegnate le autorizzazioni **Lettura** o **Modifica** relative alla cartella condivisa.

    -   **Lettura** consente di elencare i file nonché di aprirli e copiarli dalla condivisione in un altro percorso.

    -   **Modifica** consente di elencare, aggiungere, modificare ed eliminare file.

    Per assegnare l'autorizzazione **Modifica**, è necessario selezionare sia **Modifica** sia **Lettura**. Limitare il numero di utenti che dispongono dell'autorizzazione **Modifica** Non è inoltre consigliabile assegnare il **Controllo completo** della condivisione ad altri account utente. L'opzione **Controllo completo** concede agli utenti non solo le stesse autorizzazioni dell'opzione **Modifica**, ma anche la possibilità di acquisire la proprietà dei file e delle directory e modificare le relative autorizzazioni.

**Per proteggere una cartella condivisa**

1.  Fare clic con il pulsante destro del mouse su una cartella precedentemente condivisa e quindi scegliere **Condivisione e protezione**.

2.  Nella scheda **Condivisione** scegliere **Autorizzazioni**. Verrà visualizzata una schermata simile alla seguente:

    ![](images/Cc875837.XPP2P02(it-it,TechNet.10).gif "XPP2P02.GIF")

3.  Selezionare il gruppo **Everyone**, quindi scegliere **Rimuovi**.

4.  Fare clic su **Aggiungi** per selezionare gli utenti che possono accedere alla cartella.

5.  Nella finestra di dialogo **Seleziona Utenti** **o Gruppi** fare clic su **Tipi di oggetto**.

6.  Deselezionare le caselle di controllo **Identità di protezione incorporate** e **Gruppi**, quindi fare clic su **OK**.

7.  Fare clic su **Avanzate**.

8.  Fare clic su **Trova**.

9.  Fare clic per evidenziare gli utenti a cui concedere l'accesso alla cartella. Dopo aver selezionato gli utenti, fare clic su **OK**.

10. Assegnare quindi a ogni utente nell'elenco delle autorizzazioni il tipo di accesso adeguato. Fare doppio clic su un utente, quindi deselezionare la casella di controllo **Consenti** accanto a **Controllo completo**. Scegliere quindi se attribuire all'utente gli accessi di tipo **Modifica** e **Lettura** o solo **Lettura**.

11. Fare clic su **OK**.

12. Fare di nuovo clic su **OK** per chiudere la finestra di dialogo **Autorizzazioni** per la cartella.

    **Nota**: se le caselle di controllo della finestra di dialogo Autorizzazioni non sono disponibili, le autorizzazioni vengono ereditate dalla cartella superiore.

#### Disattivazione dei servizi non necessari

La disattivazione dei servizi non necessari consente di ridurre le possibilità che una vulnerabilità nota o sconosciuta venga sfruttata. Per disabilitare i servizi, utilizzare Installazione applicazioni nel Pannello di controllo.

Per l'elenco dei servizi e delle rispettive impostazioni, vedere la pagina relativa alle impostazioni predefinite dei servizi nel sito [Microsoft Windows XP Professional Documentation](http://technet.microsoft.com/en-us/library/cc785922.aspx) all'indirizzo www.microsoft.com/resources/documentation/windows/xp/all/proddocs/
en-us/sys\_srv\_default\_settings.mspx?mfr=true (in inglese).

#### Disattivazione o eliminazione degli account utente non necessari

Disattivare o eliminare tutti gli account utente non necessari per ridurre le possibilità di accesso non autorizzato al computer in uso.

**Per disattivare un account**

1.  Fare clic sul pulsante **Start**, quindi scegliere **Pannello di controllo**.

2.  Fare doppio clic su **Account utente**.

3.  Fare clic sulla scheda **Avanzate** e, quindi, sul pulsante **Avanzate**.

4.  Fare clic sul ramo **Utenti**.

5.  Fare doppio clic su un account utente per visualizzare la finestra di dialogo delle proprietà.

6.  Selezionare la casella di controllo **Account disabilitato**.

**Nota**: gli account disabilitati vengono mantenuti, ma l'utente corrispondente non è autorizzato ad accedere. Sono visualizzati nel riquadro dei dettagli **Utenti**, ma sull'icona è presente una X.

**Per eliminare un account**

1.  Eseguire i passaggi da 1 a 4 descritti nella procedura precedente.

2.  Anziché fare doppio clic sull'account, fare clic con il pulsante destro del mouse e scegliere **Elimina**.

    -   Prima di eliminare gli account utente, è opportuno disattivarli: Dopo essersi accertati che la disattivazione dell'account non abbia causato problemi, sarà possibile eliminarlo in tutta sicurezza.

    -   Non è possibile ripristinare gli account utente eliminati.

    -   Non è possibile eliminare gli account Administrator e Guest incorporati.

#### Protezione degli account utente

L'utilizzo di password e la configurazione del blocco degli account consentono di ridurre le possibilità di accesso non autorizzato al computer in uso.

##### Utilizzo delle password

È importante che tutti gli account utente presenti in ogni workstation siano dotati di password. Se non si indica una password, gli utenti possono accedere ai computer utilizzando credenziali altrui.

-   Non utilizzare nelle workstation l'account Guest, che deve essere disattivato.

-   È necessario che ogni utente disponga del proprio account. È preferibile non condividere account e password.

In materia di password, due concetti vengono spesso confusi. Gli account utente possono essere bloccati, normalmente quando si tenta di accedervi utilizzando una password errata per un numero di volte eccessivo. In questo caso, è sufficiente sbloccare l'account senza reimpostare la password, a meno che l'utente non l'abbia dimenticata. Un esempio significativo, e probabilmente il più comune, è quando un utente viene bloccato perché digita la password mentre il tasto BLOC MAIUSC è attivato.

La reimpostazione della password assegna all'account utente una nuova password, normalmente provvisoria, che viene comunicata all'utente per consentirgli di effettuare l'accesso. È preferibile impostare questo tipo di password affinché scada in occasione del primo utilizzo, nel caso l'utente dimentichi di modificarla dopo l'accesso. Imporre a un utente di accedere e creare immediatamente una nuova password assicura che essa sia nota solo all'utente in questione.

**Per sbloccare un account utente**

1.  Fare clic sul pulsante **Start**, quindi scegliere **Pannello di controllo**.

2.  Fare doppio clic su **Account utente**.

3.  Fare clic sulla scheda **Avanzate** e, quindi, sul pulsante **Avanzate**.

4.  Fare clic sul ramo **Utenti**.

5.  Individuare l'account utente bloccato e fare doppio clic su di esso.

6.  Deselezionare la casella di controllo **Account bloccato**, quindi fare clic su **OK**.

**Per impostare o reimpostare una password per un account utente esistente**

1.  Eseguire i passaggi da 1 a 5 descritti nella procedura precedente.

2.  Selezionare l'opzione **Cambiamento obbligatorio password**. Fare clic su **OK**.

3.  Fare clic con il pulsante destro del mouse sull'account in questione e scegliere **Imposta password**. Verrà visualizzato un messaggio di avviso. Prendere nota del possibile impatto prima di continuare.

4.  Dopo avere scelto **Continua**, immettere la password provvisoria in entrambi i campi.

5.  Fare clic su **OK** e comunicare la password provvisoria all'utente.

[](#mainsection)[Inizio pagina](#mainsection)

### Windows Firewall

Windows Firewall è una soluzione basata su host altamente configurabile, fornita con Windows XP Professional SP2. È attivato per impostazione predefinita e facilita la protezione contro attacchi di rete. Windows Live OneCare, inoltre, esegue il monitoraggio di Windows Firewall costituendo un'unica console per il controllo dello stato di protezione globale del computer.

Windows Firewall non è stato progettato per sostituire le funzionalità di un firewall di rete. Esso consente di utilizzare le porte di rete di Windows affinché i gruppi di lavoro peer-to-peer possano comunicare e condividere risorse. Per proteggere la rete è indispensabile disporre di un firewall di rete, mentre Windows Firewall protegge le workstation nelle quali è installato e attivato. Esistono numerosi produttori che offrono firewall per reti di dimensioni da piccole a medie a costi accessibili.

**Per verificare che Windows Firewall non sia disattivato**

1.  Fare clic sul pulsante **Start**, quindi scegliere **Pannello di controllo**.

2.  Fare doppio clic sull'icona di **Windows Firewall**.

3.  Verificare che la voce **Attivato (impostazione consigliata)** sia selezionata.

[](#mainsection)[Inizio pagina](#mainsection)

### Aggiornamento delle patch di protezione

Per mantenere aggiornate le patch di protezione è opportuno abbonarsi ai bollettini Microsoft sulla sicurezza, che vengono inviati tramite posta elettronica. È possibile iscriversi per ricevere i bollettini sulla sicurezza nel sito Web [Microsoft e la sicurezza](http://www.microsoft.com/italy/security/default.mspx) all'indirizzo www.microsoft.com/italy/security/default.mspx. Oltre ai bollettini, sono disponibili numerose tecnologie che consentono di automatizzare la gestione delle patch di protezione.

#### Aggiornamenti automatici

La funzionalità Aggiornamenti automatici in Windows XP individua e scarica automaticamente le patch di protezione più recenti dal sito Web Microsoft. Il servizio può essere configurato in modo da scaricare automaticamente in background le correzioni e quindi richiedere all'utente di installarle al termine del download.

**Per configurare il computer per gli aggiornamenti automatici**

1.  Fare clic sul pulsante **Start**, quindi scegliere **Pannello di controllo**.

2.  Fare doppio clic sull'icona **Aggiornamenti automatici**.

3.  Impostare tutte le workstation Windows XP su **Automatico**. Tenere presente che è possibile configurare la frequenza e l'ora del giorno in cui si desidera che vengano effettuati gli aggiornamenti.

4.  Fare clic su **OK**.

**Nota**: Microsoft rilascia inoltre bollettini sulla sicurezza attraverso il servizio Security Notification Service. Questi bollettini vengono emessi relativamente a tutti i prodotti Microsoft in cui vengono riscontrati problemi di protezione.

[](#mainsection)[Inizio pagina](#mainsection)

### Informazioni correlate

Per ulteriori informazioni sulla protezione di Windows XP, vedere quanto riportato di seguito:

-   [*Guida per la protezione di Windows XP*](http://technet.microsoft.com/it-it/library/cc163061), disponibile per la consultazione e il download nel sito Web Microsoft TechNet all'indirizzo www.microsoft.com/italy/technet/security/prodtech/windowsxp/secwinxp/default.mspx.

Per ulteriori informazioni su argomenti correlati riguardanti la protezione di Windows XP, vedere quanto riportato di seguito:

-   La guida [*Pericoli e contromisure*](http://technet.microsoft.com/it-it/library/dd162275), disponibile per la consultazione e il download nel sito Web Microsoft TechNet all'indirizzo www.microsoft.com/italy/technet/security/topics/serversecurity/tcg/tcgch00.mspx.

**Download**

[Download della guida Protezione di Windows XP Professional in un ambiente di rete peer-to-peer](http://go.microsoft.com/fwlink/?linkid=70393)

[](#mainsection)[Inizio pagina](#mainsection)
