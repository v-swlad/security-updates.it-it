---
TOCTitle: Protezione di client remoti e computer portatili
Title: Protezione di client remoti e computer portatili
ms:assetid: 'bd780478-d723-4873-b19b-79d5377b993f'
ms:contentKeyID: 20213226
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc875832(v=TechNet.10)'
---

Protezione di client remoti e computer portatili
================================================

##### In questa pagina

[](#elaa)[Introduzione](#elaa)
[](#ekaa)[Prima di iniziare](#ekaa)
[](#ejaa)[Service Pack e aggiornamenti rapidi](#ejaa)
[](#eiaa)[Virus e worm](#eiaa)
[](#ehaa)[Adware e spyware](#ehaa)
[](#egaa)[Punti di ripristino](#egaa)
[](#efaa)[Firewall personale](#efaa)
[](#eeaa)[Protezione dei file](#eeaa)
[](#edaa)[Password complesse](#edaa)
[](#ecaa)[Protezione delle reti wireless](#ecaa)
[](#ebaa)[Connessioni VPN](#ebaa)
[](#eaaa)[Informazioni correlate](#eaaa)

### Introduzione

In questo documento vengono descritte le funzionalità che consentono di proteggere computer portatili e remoti che eseguono il sistema operativo Microsoft Windows XP Professional.

Gli utenti possono connettersi a Internet da una grande varietà di luoghi in tutto il mondo, ad esempio hotel e abitazioni private, attraverso cavi di rete tradizionali o reti wireless. In molti aeroporti, bar e vaste aree metropolitane è disponibile il servizio Internet mediante reti wireless. L'utente di un computer portatile ha la possibilità di connettersi a Internet, esplorare siti Web complessi e connettersi alla rete dell'organizzazione a cui appartiene utilizzando una rete privata virtuale (VPN, Virtual Private Network). I rischi potenziali derivanti da codice dannoso, tra cui virus, worm e trojan horse, sono una minaccia concreta. I rischi non riguardano solo i portatili: qualsiasi computer infetto o violato può costituire l'origine di un'infezione in grado di estendersi ad altri computer di una piccola rete aziendale.

È necessario adottare alcune precauzioni per ridurre i rischi connessi all'utilizzo di computer remoti e portatili. Alcune di queste precauzioni, o funzionalità di protezione, coincidono con le misure da attivare nelle workstation. Gli utenti mobili devono prendere in considerazione più minacce. Esiste inoltre il rischio concreto di perdita, danno o furto del portatile stesso.

In questo documento sono fornite informazioni sulle funzionalità di protezione che una piccola azienda può utilizzare per ridurre i rischi a cui sono esposti gli utenti di computer portatili e remoti. Sono inoltre inclusi riferimenti ad altri documenti correlati che contengono istruzioni dettagliate per proteggere i computer.

#### Obiettivo del documento

Scopo del documento è di consentire l'approfondimento degli strumenti e delle funzionalità per la protezione di client remoti e computer portatili che vi sono descritti. Al termine della lettura sarà inoltre possibile verificare il livello di protezione fornito.

[](#mainsection)[Inizio pagina](#mainsection)

### Prima di iniziare

Prima di applicare i suggerimenti contenuti in questo documento, è consigliabile leggere le informazioni seguenti.

#### Credenziali necessarie

Nel documento si fa spesso riferimento alla necessità di utilizzare un account con privilegi per l'esecuzione di alcune attività, account che deve essere membro del gruppo Administrators locale nella workstation. Solo un account con questo livello di autorizzazione nella workstation è in grado di concedere a un altro account l'appartenenza al gruppo Administrators locale. Per gli account con meno privilegi verranno visualizzati avvisi di tipo "Accesso negato".

#### Windows Live OneCare

Con Windows Live OneCare è possibile usufruire di apposite funzionalità per proteggere i computer client da attacchi di rete. A ogni funzionalità sono associati componenti specifici nel Pannello di controllo. Nel Centro sicurezza PC Windows sono raccolte molte di queste funzioni ma il servizio è tuttavia basato su alcuni programmi software di terze parti.

Il misuratore di integrità di Windows OneCare fornisce un'indicazione chiara e continua del livello generale della protezione e delle prestazioni del computer. Se viene rilevata la possibilità di migliorare l'integrità del computer, viene visualizzata automaticamente l'azione da intraprendere e fornita una semplice procedura.

I servizi Windows OneCare Antivirus, Windows OneCare Firewall, Windows OneCare Backup e Tune-up sono sempre attivi e svolgono costantemente un'azione di monitoraggio. Ogni servizio è configurato per l'aggiornamento automatico e consente di proteggere il computer dalle minacce più recenti. È consigliabile installare e utilizzare Windows Live OneCare per raccogliere una famiglia di strumenti in un'unica console o interfaccia utente.

Se oltre a Windows Live OneCare viene anche utilizzato Defender, si avrà a disposizione una grande quantità di strumenti per la gestione dell'integrità e della protezione del computer.

Per ulteriori informazioni, visitare il sito Web [Windows Live OneCare](http://www.windowsonecare.com/) all'indirizzo www.windowsonecare.com/ (in inglese).

#### Approccio alla protezione

Per proteggere i computer portatili e remoti dagli attacchi, è consigliabile non fare affidamento su un'unica funzionalità di protezione. Un approccio a più livelli ammette gli errori garantendo nel contempo un certo livello di protezione. I portatili sono particolarmente esposti a furto e perdita. Oltre a funzionalità in grado di fornire ulteriori livelli di protezione per tutti i computer con Windows XP Professional, in questo articolo sono inclusi altri livelli di protezione dei file utili nel caso il portatile venga sottratto per accedere alle informazioni che vi sono contenute.

[](#mainsection)[Inizio pagina](#mainsection)

### Service Pack e aggiornamenti rapidi

Il Centro sicurezza PC costituisce un modo semplice per gestire gli aggiornamenti della protezione per la grande famiglia di sistemi operativi e altre applicazioni Microsoft, ad esempio Microsoft Office.

Per configurare il Centro sicurezza PC per il download automatico e l'installazione degli aggiornamenti in base alle esigenze, eseguire la procedura seguente. Sarà in tal modo possibile gestire gli aggiornamenti rapidi della protezione senza doverli applicare manualmente.

1.  Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.

2.  Nel Pannello di controllo fare clic su **Centro sicurezza PC** (illustrato nella figura seguente).

    [![](images/Cc875832.SRCPC01(it-it,TechNet.10).gif "SRCPC01.GIF")](https://technet.microsoft.com/it-it/cc875832.srcpc01_big(it-it,technet.10).gif)

3.  Fare clic sull'opzione **Aggiornamenti automatici** (illustrata nella figura seguente).

    [![](images/Cc875832.SRCPC02(it-it,TechNet.10).gif "SRCPC02.GIF")](https://technet.microsoft.com/it-it/cc875832.srcpc02_big(it-it,technet.10).gif)

4.  Selezionare l'opzione **Automatico (impostazione consigliata)** (illustrata nella figura seguente) e specificare una frequenza per il download e l'installazione degli aggiornamenti automatici. Avere cura di impostare un orario in cui il computer è in esecuzione.

    ![](images/Cc875832.SRCPC03(it-it,TechNet.10).gif "SRCPC03.GIF")

5.  Specificata la frequenza, fare clic su **OK**.

[](#mainsection)[Inizio pagina](#mainsection)

### Virus e worm

I virus informatici sono programmi software ideati deliberatamente per interferire con il funzionamento dei computer. Sono in grado di registrare, danneggiare o eliminare dati e di diffondersi in altri computer e attraverso Internet, spesso rallentando i processi e provocando altri problemi.

Anche i virus informatici, esattamente come quelli che affliggono gli esseri umani, da Ebola alla banale influenza, hanno livelli di gravità estremamente diversi essendo in grado di creare piccoli problemi o di distruggere il sistema. Si evolvono inoltre continuamente e possono assumere forme diverse. Tuttavia, adottando opportune misure preventive e acquisendo alcune informazioni di base, è possibile ridurre significativamente l'esposizione al rischio riducendone l'impatto.

È possibile proteggere i dati e le applicazioni contenuti nel computer utilizzando software antivirus e tenendolo aggiornato. Esistono vari programmi antivirus che è possibile installare per proteggere gli utenti di Windows dai virus. Prima dell'installazione accertarsi che sussistano i requisiti di sistema per tali programmi. Nel valutare il programma antivirus da acquistare, prendere in considerazione le funzionalità seguenti:

-   Servizio in tempo reale per il controllo e la prevenzione degli attacchi dei virus.

-   Aggiornamenti automatici delle firme dei virus.

-   Analisi e pulitura a richiesta e pianificate.

È possibile visualizzare l'elenco dei [Partner antivirus di Microsoft](http://www.microsoft.com/athome/security/viruses/wsc/it/flist.mspx) all'indirizzo http://www.microsoft.com/athome/security/viruses/wsc/it/flist.mspx.

[](#mainsection)[Inizio pagina](#mainsection)

### Adware e spyware

Lo spyware è spesso associato a programmi software per la visualizzazione di pubblicità (definiti adware) o per la rilevazione di informazioni personali o sensibili. Ciò non significa che tutti i programmi software pubblicitari o tali da rilevare le attività in linea degli utenti siano dannosi. È ad esempio possibile sottoscrivere un servizio musicale gratuito accettando tuttavia di ricevere annunci pubblicitari mirati. Se le condizioni vengono comprese e accettate, l'accordo è del tutto legittimo. È inoltre possibile accettare che l'azienda rilevi le attività in linea per individuare gli annunci pubblicitari da visualizzare.

Altri tipi di software indesiderato possono apportare modifiche fastidiose al computer tali da provocarne il rallentamento o l'arresto anomalo. Questi programmi sono in grado di modificare la pagina iniziale o la pagina di ricerca del browser Web o di aggiungere componenti al browser non necessari o non desiderati complicando inoltre il ripristino delle impostazioni originali del computer. Questi tipi di programmi indesiderati sono spesso denominati spyware.

Windows Defender (Beta2) è una tecnologia di protezione che consente di proteggere gli utenti di Windows da spyware e altro software potenzialmente dannoso. È possibile individuare e rimuovere le applicazioni spyware conosciute eventualmente presenti nel computer per ridurne gli effetti negativi, ovvero la diminuzione delle prestazioni, la visualizzazione di fastidiose finestre pubblicitarie popup, le modifiche indesiderate alle impostazioni Internet e l'utilizzo non autorizzato di informazioni riservate. La protezione costante aumenta la sicurezza dell'esplorazione di Internet sorvegliando oltre 50 dei modi in cui lo spyware può accedere ai computer. I membri della community SpyNet, diffusa in tutto il mondo, svolgono un ruolo fondamentale nel determinare quali programmi sospetti vengono classificati come spyware e i ricercatori Microsoft sviluppano rapidamente metodi per contrastare queste minacce; gli aggiornamenti vengono scaricati automaticamente nel PC che, quindi, è sempre aggiornato.

È possibile scaricare [Windows Defender](http://www.microsoft.com/italy/athome/security/spyware/software/default.mspx) all'indirizzo http://www.microsoft.com/italy/athome/security/spyware/software/default.mspx. La versione corrente è la Beta 2. Il nome del file è WindowsDefender.msi e le sue dimensioni sono pari a circa 5,5 MB. Il nome del file e le dimensioni potrebbero variare in seguito al rilascio della versione definitiva.

Per installare Windows Defender (Beta 2) dopo il download, eseguire la procedura seguente.

1.  Al termine del download di Windows Defender (Beta 2), verrà visualizzata la finestra di dialogo seguente. Fare clic su **Esegui**.

    ![](images/Cc875832.SRCPC04(it-it,TechNet.10).gif "SRCPC04.GIF")

2.  Verrà visualizzata la schermata **Welcome to the Installation Wizard for Windows Defender** (Installazione guidata di Windows Defender) seguente. Fare clic su **Avanti**.

    ![](images/Cc875832.SRCPC05(it-it,TechNet.10).gif "SRCPC05.GIF")

3.  Verrà visualizzata la schermata **Windows Defender License Agreement** (Contratto di licenza per Windows Defender), illustrata nella figura seguente. Leggere le condizioni del contratto.

    Per continuare l'installazione, è necessario selezionare **I accept the terms in the license agreement** (Accetto i termini del contratto di licenza) e fare clic su **Avanti**.

    ![](images/Cc875832.SRCPC06(it-it,TechNet.10).gif "SRCPC06.GIF")

4.  Nella schermata **Help protect Windows** (Protezione di Windows), illustrata nella figura seguente, selezionare **Use recommended settings** (Usa impostazioni consigliate). Fare clic sul pulsante **Privacy Statement** (Informativa sulla privacy), se lo si desidera, quindi fare clic su **Avanti**.

    ![](images/Cc875832.SRCPC07(it-it,TechNet.10).gif "SRCPC07.GIF")

5.  Nella schermata **Setup Type** (Tipo di installazione), illustrata nella figura seguente, selezionare **Complete** (Completa) e fare clic su **Avanti**.

    ![](images/Cc875832.SRCPC08(it-it,TechNet.10).gif "SRCPC08.GIF")

6.  Nella schermata **Ready to Install Windows Defender** (Installazione di Windows Defender) che verrà visualizzata, fare clic su **Install** (Installa) per avviare l'installazione.

    ![](images/Cc875832.SRCPC09(it-it,TechNet.10).gif "SRCPC09.GIF")

7.  Al termine dell'installazione, verrà visualizzata la schermata **Windows Defender Installation Complete** (Installazione di Windows Defender completata).

    Verificare che l'opzione **Check for updated definitions and run a quick scan now** (Verifica la disponibilità di definizioni aggiornate ed esegui un'analisi veloce) sia selezionata, quindi fare clic su **Fine**.

    **Nota**   Per l'esecuzione di questo passaggio è necessaria la connessione Internet.

    ![](images/Cc875832.SRCPC10(it-it,TechNet.10).gif "SRCPC10.GIF")

8.  Nella schermata seguente fare clic sul pulsante **Check for Updates** (Controlla aggiornamenti) per ottenere aggiornamenti recenti.

    [![](images/Cc875832.SRCPC11(it-it,TechNet.10).gif "SRCPC11.GIF")](https://technet.microsoft.com/it-it/cc875832.srcpc11_big(it-it,technet.10).gif)

Per ulteriori dettagli e informazioni sulle funzionalità avanzate di Windows Defender (Beta 2), visitare il sito Web [Windows Defender (Beta 2)](http://www.microsoft.com/italy/athome/security/spyware/software/default.mspx) all'indirizzo http://www.microsoft.com/italy/athome/security/spyware/software/default.mspx.

[](#mainsection)[Inizio pagina](#mainsection)

### Punti di ripristino

Un sistema operativo e le relative applicazioni possono subire danni per varie cause. In Windows XP Professional è possibile riportare un client portatile o remoto a un punto di ripristino funzionante noto. Questi punti di ripristino vengono talvolta salvati automaticamente nei sistemi operativi prima del verificarsi di alcuni eventi.

Per ulteriori informazioni, vedere [How to ‘undo’ a big mistake in Windows](http://www.microsoft.com/smallbusiness/resources/technology/business_software/how_to_undo_a_big_mistake_in_windows.mspx) all'indirizzo www.microsoft.com/smallbusiness/resources/technology/business\_software/how\_to\_
undo\_a\_big\_mistake\_in\_windows.mspx.

[](#mainsection)[Inizio pagina](#mainsection)

### Firewall personale

Un firewall è un sistema di protezione che agisce come una barriera fra una rete e l'esterno. In Windows XP SP2 è incluso Windows Firewall, un software dal funzionamento pressoché analogo in ogni computer client.

Windows Firewall è preinstallato in Windows XP Professional SP2 e presenta numerose possibilità di configurazione. È attivato per impostazione predefinita e facilita la protezione contro attacchi di rete. Windows Live OneCare, inoltre, esegue il monitoraggio di Windows Firewall costituendo un'unica console per il controllo dello stato di protezione globale del computer. Nel prosieguo di questo documento verrà illustrato come modificare le impostazioni di Windows Firewall utilizzando il Centro sicurezza PC Windows, disponibile nel Pannello di controllo.

**Nota**   Windows Firewall non sostituisce le funzionalità di un firewall di rete. La rete Windows è attivata ed è possibile eseguire alcune operazioni nonostante Windows Firewall, ovvero comunicare con altri computer di rete, stampare e accedere a risorse di rete. È tuttavia consigliabile utilizzare un firewall di rete per proteggere le porte aperte nell'esecuzione di queste funzioni.

Per informazioni sulla soluzione del firewall di rete Microsoft, vedere la pagina [Microsoft Internet Security and Acceleration Server](http://www.microsoft.com/italy/isaserver/default.mspx) all'indirizzo www.microsoft.com/italy/isaserver/default.mspx.

#### Configurazione delle impostazioni generali di Windows Firewall

Le impostazioni generali di Windows Firewall consentono di configurare le opzioni seguenti:

-   **Attivato** (impostazione consigliata).

-   **Disattivato** (impostazione non consigliata). La disattivazione di Windows Firewall rende il computer più vulnerabile ai danni provocati da virus, worm o intrusi.

1.  Per aprire il Centro sicurezza PC Windows, fare clic sul pulsante **Start** e scegliere **Panello di controllo**. Verrà visualizzata la schermata seguente.

    [![](images/Cc875832.SRCPC12(it-it,TechNet.10).gif "SRCPC12.GIF")](https://technet.microsoft.com/it-it/cc875832.srcpc12_big(it-it,technet.10).gif)

2.  Nella sezione **Scegliere una categoria** fare clic su **Centro sicurezza PC**. Verrà visualizzata la schermata **Centro sicurezza PC Windows**, illustrata nella figura seguente.

    [![](images/Cc875832.SRCPC13(it-it,TechNet.10).gif "SRCPC13.GIF")](https://technet.microsoft.com/it-it/cc875832.srcpc13_big(it-it,technet.10).gif)

#### Notifiche di configurazione

Per impostazione predefinita, Windows Firewall visualizza una finestra di dialogo di notifica ogni volta che viene bloccato un tentativo di comunicazione con un altro computer. Questa finestra di dialogo è simile alla schermata illustrata nella figura seguente:

![](images/Cc875832.SRCPC14(it-it,TechNet.10).gif "SRCPC14.GIF")

Nella finestra di dialogo viene indicato il programma bloccato e viene data la possibilità di scegliere se consentirne l'esecuzione. Le opzioni disponibili sono le seguenti:

-   **Continua a bloccare**. Scegliere questa opzione per impedire connessioni non autorizzate al programma da Internet o dalla rete.

-   **Sblocca**. Scegliere questa opzione per inserire il programma nell'elenco di eccezioni di Windows Firewall.

-   **Richiedi in seguito**. Scegliere questa opzione se non è possibile decidere se bloccare o sbloccare il programma. L'opzione mantiene bloccato il programma per maggiore protezione. Il messaggio verrà nuovamente visualizzato al successivo blocco del programma.

Per ulteriori informazioni sulle funzionalità avanzate, vedere la pagina [Informazioni su Windows Firewall](http://www.microsoft.com/italy/windowsxp/using/security/internet/sp2_wfintro.mspx.) all'indirizzo www.microsoft.com/italy/windowsxp/using/security/internet/sp2\_wfintro.mspx.

[](#mainsection)[Inizio pagina](#mainsection)

### Protezione dei file

In Windows XP Professional e in altri sistemi operativi Microsoft è utilizzato il file system NTFS, che presenta una maggiore tolleranza di errore rispetto ai file system FAT (Fat Allocation Table) precedenti. In NTFS sono inoltre disponibili controlli di accesso a livello di file e la tecnologia Crittografia file system (EFS, Encrypting File System). Per la realizzazione di portatili con Windows XP Professional, è consigliabile utilizzare solo il file system NTFS per formattare il disco rigido.

#### NTFS

NTFS v5 è un file system più avanzato rispetto a FAT8, FAT16, FAT32 e persino a NTFS v4. NTFS è più indicato per la risoluzione di errori minori del disco e unito a un utilizzo corretto di Crittografia file system (EFS) è particolarmente adatto ai computer portatili.

**Nota**   Per impostazione predefinita un utente esperto che effettua l'attacco e che accede a un disco rigido formattato con NTFS o con i file system della famiglia FAT è in grado di superare le funzionalità di protezione NTFS se la Crittografia file system (EFS) non è attivata. Anche nel caso in cui EFS sia attivato, chi effettua l'attacco potrà sempre riuscire a violare un portatile perduto in cui è installato Windows XP Professional.

È possibile convertire una partizione FAT di Windows XP Professional esistente in una partizione NTFS per conseguire un maggior livello di stabilità e protezione. La procedura è descritta nella pagina [How to Convert FAT Disks to NTFS](http://technet.microsoft.com/en-us/library/bb456984.aspx) nel sito Web Microsoft all'indirizzo www.microsoft.com/technet/prodtechnol/winxppro/maintain/convertfat.mspx (in inglese). Poiché tuttavia alcuni programmi precedenti potrebbero non essere eseguiti in un volume NTFS, è consigliabile informarsi sui requisiti correnti del software prima di eseguire la conversione.

**Nota**   Eseguire sempre il backup dei file importanti prima di passare da un file system a un altro.

#### EFS

EFS è disponibile solo nei file system NTFS, non nei file system FAT. La crittografia è il processo di codifica dei file finalizzato a impedire l'accesso non autorizzato. I file e le cartelle crittografati possono essere utilizzati esattamente come qualsiasi altro file o cartella.

Esistono vari modi per implementare EFS, ma la determinazione di criteri di recupero a livello locale in un computer portatile o in desktop remoto può essere un errore. I criteri di recupero locali consentono a un tecnico esperto di accedere a file e directory crittografati con la tecnologia EFS. Una funzionalità di recupero eseguita a livello di dominio è in grado di fornire un file system più sicuro.

Per ulteriori informazioni sulle funzionalità avanzate, vedere [Protecting Data by Using EFS to Encrypt Hard Drives](http://www.microsoft.com/technet/security/smallbusiness/topics/cryptographyetc/protect_data_efs.mspx) nel sito Web Microsoft all'indirizzo www.microsoft.com/technet/security/
smallbusiness/topics/cryptographyetc/protect\_data\_efs.mspx (in inglese).

**Nota**   Non è possibile comprimere e codificare i file contemporaneamente.

#### Backup di file

Il backup garantisce la disponibilità dei file nel caso in cui si verifichino problemi in computer portatili o remoti. Può trattarsi semplicemente dell'eliminazione accidentale di file ma anche, più gravemente, del furto deliberato di un piccolo portatile. Il backup periodico dei file è un metodo di protezione di dati importanti economico e preventivo.

Per informazioni su come eseguire il backup e il ripristino dei file in Windows XP Professional, vedere l'articolo della Microsoft Knowledge Base "[How to: Utilizzare l'utilità Backup per il backup di file e cartelle nel computer](http://support.microsoft.com/kb/308422)" all'indirizzo http://support.microsoft.com/kb/308422.

[](#mainsection)[Inizio pagina](#mainsection)

### Password complesse

Uno dei più diffusi problemi di protezione è costituito da password vulnerabili. Una password deve essere sufficientemente complessa per poter proteggere i file e i computer con cui viene utilizzata. Una password complessa è in grado di evitare la violazione di qualsiasi computer. I programmi software per l'identificazione delle password sono comuni e di facile utilizzo.

Per informazioni dettagliate sulla creazione di password complesse, vedere [Selecting Secure Passwords](http://www.microsoft.com/smallbusiness/support/articles/select_sec_passwords.mspx) nel sito Web Microsoft all'indirizzo www.microsoft.com/smallbusiness/support/articles/select\_sec\_passwords.mspx (in inglese).

[](#mainsection)[Inizio pagina](#mainsection)

### Protezione delle reti wireless

I computer client remoti e portatili sono vulnerabili agli attacchi in qualsiasi punto quando è attivata la scheda di rete wireless. È consigliabile disattivare le schede di rete wireless quando non vengono utilizzate.

Prima di collegarsi a una nuova rete wireless, è opportuno prestare particolare attenzione ad alcune considerazioni. Alcune reti wireless che si annunciano automaticamente non sono affatto sicure. Le funzionalità descritte in questo articolo consentono di proteggere le workstation e i portatili con Windows XP Professional dagli attacchi durante la connessione a tali reti ma la regola aurea delle reti wireless consiste nello stabilire la connessione solo a reti note.

Per aumentare la protezione delle reti wireless remote, ad esempio in ambienti domestici, vedere [Configuring Windows XP IEEE 802.11 Wireless Networks for the Home and Small Business](http://technet.microsoft.com/en-us/library/bb457016.aspx) nel sito Web Microsoft TechNet all'indirizzo www.microsoft.com/technet/prodtechnol/winxppro/maintain/wifisoho.mspx (in inglese).

[](#mainsection)[Inizio pagina](#mainsection)

### Connessioni VPN

Una rete privata virtuale (VPN, Virtual Private Network) è un modo sicuro per connettere un computer remoto o portatile da una rete all'altra, solitamente via Internet. Questa tecnologia consente a un utente di Windows che utilizza un portatile di connettersi a una rete da un hotel o da un bar e di connettersi in modo protetto ai computer della rete in ufficio.

Le piccole aziende potrebbero essere tentate di stabilire connessioni non VPN via Internet per fornire la connettività remota. È consigliabile utilizzare una rete privata virtuale (VPN) anziché una connessione Internet non sicura. L'utilizzo di connessioni non sicure espone le reti domestiche e di piccole aziende a rischi inutili.

Quando si utilizzano connessioni VPN via Internet, è importante accertarsi che la soluzione VPN impedisca la connessione contemporanea a un'altra rete. Questa funzionalità infatti rimuove un percorso diretto da una rete a un'altra, che malware o pirati informatici potrebbero sfruttare.

[](#mainsection)[Inizio pagina](#mainsection)

### Informazioni correlate

Per ulteriori informazioni su firewall, aggiornamenti ai computer e programmi antivirus, consultare la documentazione seguente:

-   [Proteggi il tuo PC](http://www.microsoft.com/italy/athome/security/protect/windowsxpsp2/default.mspx), nel sito Web Microsoft all'indirizzo www.microsoft.com/italy/athome/security/protect/windowsxpsp2/Default.mspx.

-   Articolo [5-Minute Security Advisor - The Road Warrior's Guide to Laptop Protection](http://www.microsoft.com/technet/archive/community/columns/security/5min/5min-205.mspx), nel sito Web Microsoft TechNet all'indirizzo www.microsoft.com/technet/
    archive/community/columns/security/5min/5min-205.mspx (in inglese).

-   Articolo “Network Ports Used by Key Microsoft Server Products” contenuto nel [Security Guidance Kit](http://www.microsoft.com/downloads/details.aspx?familyid=c3260bd0-2ebb-4496-ad07-7e9d55d0ef1f&displaylang=en), disponibile nell'Area download Microsoft all'indirizzo www.microsoft.com/downloads/details.aspx?FamilyID=c3260bd0-2ebb-4496-ad07-7e9d55d0ef1f&displaylang=en (in inglese).

-   Articolo [Port Numbers](http://www.iana.org/assignments/port-numbers), nel sito Web dell'associazione IANA (Internet Assigned Numbers Authority) all'indirizzo www.iana.org/assignments/port-numbers (in inglese).

-   [Managing Windows XP Service Pack 2 Features Using Group Policy – Windows Firewall](http://technet.microsoft.com/en-us/library/bb878159.aspx), nel sito Web Microsoft TechNet all'indirizzo www.microsoft.com/technet/
    prodtechnol/winxppro/maintain/mangxpsp2/mngwfw.mspx (in inglese).

Per ulteriori informazioni sulla protezione di Windows XP SP2, consultare le risorse seguenti:

-   Aggiornamento della [*Windows XP Security Guide*](http://go.microsoft.com/fwlink/?linkid=35309), disponibile nell'Area download Microsoft all'indirizzo http://go.microsoft.com/fwlink/?linkid=35309 (in inglese).

-   [Funzionalità modificate in Microsoft Windows XP Service Pack 2 Parte 2: Tecnologie di protezione della rete](http://technet.microsoft.com/en-us/library/bb457156.aspx), nel sito Web Microsoft TechNet all'indirizzo http://www.microsoft.com/technet/prodtechnol/winxppro/it/maintain/sp2netwk.mspx.

Per informazioni su come determinare lo stato di protezione della rete, consultare le risorse seguenti:

-   [Microsoft Baseline Security Analyzer](http://www.microsoft.com/technet/security/tools/mbsahome.mspx), nel sito Web Microsoft TechNet all'indirizzo www.microsoft.com/technet/security/tools/mbsahome.mspx (in inglese).

Per conoscere le definizioni dei termini correlati alla protezione, consultare la risorsa seguente:

-   [Microsoft Security Glossary](http://go.microsoft.com/fwlink/?linkid=35468), disponibile nel sito Web Microsoft all'indirizzo http://go.microsoft.com/fwlink/?LinkId=35468 (in inglese).

**Download**

[Download della guida Protezione di client remoti e computer portatili](http://go.microsoft.com/fwlink/?linkid=70393)

[](#mainsection)[Inizio pagina](#mainsection)
