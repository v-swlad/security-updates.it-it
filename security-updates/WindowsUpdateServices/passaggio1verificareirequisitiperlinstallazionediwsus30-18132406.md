---
TOCTitle: 'Passaggio 1: Verificare i requisiti per l''installazione di WSUS 3.0'
Title: 'Passaggio 1: Verificare i requisiti per l''installazione di WSUS 3.0'
ms:assetid: '912b37d7-021e-4c95-b317-49dd15b4611c'
ms:contentKeyID: 18132406
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc708484(v=WS.10)'
---

Passaggio 1: Verificare i requisiti per l'installazione di WSUS 3.0
===================================================================

In questa guida vengono descritte le procedure per l'installazione di WSUS 3.0. Per i requisiti software e le piattaforme supportate per WSUS 3.0, consultare le note sulla versione ([http://go.microsoft.com/fwlink/?LinkId=71220](http://go.microsoft.com/fwlink/?linkid=71220)) in Windows Server 2003 Service Pack 1 e sistemi operativi Windows Server® 2008.

Requisiti software per l'installazione di WSUS 3.0 in Windows Server 2003 Service Pack 1
----------------------------------------------------------------------------------------

Per installare WSUS 3.0 in Windows Server 2003 Service Pack 1, nel computer deve essere installato quanto segue. Se uno di questi aggiornamenti richiede il riavvio del server al termine dell'installazione, è necessario riavviare il server prima dell'installazione di WSUS 3.0.

-   Microsoft Internet Information Services (IIS) 6.0.
-   Aggiornamento per Servizio trasferimento intelligente in background (BITS) 2.0 e WinHTTP 5.1 Windows Server 2003. Per scaricare il software, visitare il sito Web Area download Microsoft ([http://go.microsoft.com/fwlink/?LinkID=47251](http://go.microsoft.com/fwlink/?linkid=47251)).
-   Package ridistribuibile di Microsoft .NET Framework versione 2.0 (x86). Per scaricare il software, visitare il sito Web Area download Microsoft ([http://go.microsoft.com/fwlink/?LinkID=68935](http://go.microsoft.com/fwlink/?linkid=68935)). (Anche per le piattaforme a 64 bit, visitare il sito Web Area download Microsoft \[[http://go.microsoft.com/fwlink/?LinkID=70637](http://go.microsoft.com/fwlink/?linkid=70637)\].)
-   Microsoft Report Viewer Redistributable 2005. Per ottenere il software, visitare il sito Web Area download Microsoft [http://go.microsoft.com/fwlink/?LinkID=70410](http://go.microsoft.com/fwlink/?linkid=70410)).
-   Microsoft Management Console 3.0 per Windows Server 2003 (KB907265). Per scaricare il software, visitare il sito Web Area download Microsoft ([http://go.microsoft.com/fwlink/?LinkID=70412](http://go.microsoft.com/fwlink/?linkid=70412)). (Anche per le piattaforme a 64 bit, visitare il sito Web Area download Microsoft \[[http://go.microsoft.com/fwlink/?LinkID=70638](http://go.microsoft.com/fwlink/?linkid=70638)\].)

Requisiti software per l'installazione di WSUS 3.0 in Windows Server 2008
-------------------------------------------------------------------------

Per installare WSUS 3.0 Windows Server 2008, è necessario disporre di un computer in cui è installato il software seguente. Se uno di questi aggiornamenti richiede il riavvio del server al termine dell'installazione, è necessario riavviare il server prima dell'installazione di WSUS 3.0.

-   Microsoft Internet Information Services (IIS) 7,0. Assicurarsi che i seguenti componenti siano attivati:
    -   Autenticazione Windows
    -   ASP.NET
    -   Compatibilità di gestione con 6.0
    -   Compatibilità metabase IIS
-   Microsoft Report Viewer Redistributable 2005. Per scaricare il software, visitare il sito Web Area download Microsoft [http://go.microsoft.com/fwlink/?LinkID=70410](http://go.microsoft.com/fwlink/?linkid=70410)).
-   Microsoft SQL Server™ 2005 Service Pack 1. Per scaricare il software, visitare il sito Web Area download Microsoft [http://go.microsoft.com/fwlink/?LinkID=66143](http://go.microsoft.com/fwlink/?linkid=66143)).

Gli aggiornamenti di .NET Framework 2.0 e BITS 2.0 sono disponibili in Windows Server 2008 come parte del sistema operativo.

Requisiti di spazio su disco
----------------------------

Per l'installazione di WSUS 3.0, il file system del server deve soddisfare i requisiti seguenti:

-   La partizione di sistema e la partizione in cui WSUS 3.0 è installato devono essere formattate con il file system NTFS.
-   Per la partizione di sistema è consigliabile disporre di almeno 1 GB di spazio disponibile.
-   Sono necessari almeno 20 GB di spazio disponibile per il volume in cui viene archiviato il contenuto di WSUS; è consigliabile disporre di 30 GB di spazio disponibile.
-   È consigliabile disporre di almeno 2 GB di spazio disponibile nel volume in cui viene installato Windows® Internal Database.

Requisiti di installazione solo per la console
----------------------------------------------

Con WSUS 3.0 è ora possibile installare la console di amministrazione WSUS in sistemi remoti separati dal server WSUS. Le installazioni della sola console possono essere eseguite sui seguenti sistemi operativi:

-   Windows Server® 2008
-   Windows Vista®
-   Windows Server 2003 Service Pack 1
-   Windows XP Service Pack 2

I prerequisiti software per l'installazione della sola console sono i seguenti

-   Package ridistribuibile di Microsoft .NET Framework versione 2.0 (x86), disponibile nell'Area download Microsoft ([http://go.microsoft.com/fwlink/?LinkId=68935](http://go.microsoft.com/fwlink/?linkid=68935)). Per le piattaforme a 64 bit, visitare accedere a package ridistribuibile di Microsoft .NET Framework versione 2.0 (x64) ([http://go.microsoft.com/fwlink/?LinkId=70637](http://go.microsoft.com/fwlink/?linkid=70637)).
-   Microsoft Management Console 3.0 per Windows Server 2003 (KB907265), disponibile nell'Area download Microsoft ([http://go.microsoft.com/fwlink/?LinkId=70412](http://go.microsoft.com/fwlink/?linkid=70412)). Per le piattaforme a 64 bit, accedere a Microsoft Management Console 3.0 per Windows Server 2003 x64 Edition (KB907265) ([http://go.microsoft.com/fwlink/?LinkId=70638](http://go.microsoft.com/fwlink/?linkid=70638)).
-   Microsoft Report Viewer Redistributable 2005, disponibile nell'Area download Microsoft ([http://go.microsoft.com/fwlink/?LinkId=70410](http://go.microsoft.com/fwlink/?linkid=70410)).

Requisiti di Aggiornamenti automatici
-------------------------------------

Aggiornamenti automatici è il componente client di WSUS 3.0. Per Aggiornamenti automatici non sono necessari requisiti hardware particolari ad eccezione della connessione alla rete. È possibile utilizzare Aggiornamenti automatici con WSUS 3.0 nei computer che eseguono uno dei sistemi operativi seguenti:

-   Microsoft Windows Vista.
-   Windows Server® 2008.
-   Microsoft Windows® Server 2003, tutte le versioni e tutti i Service Pack.
-   Microsoft Windows XP Professional, Service Pack 1 o Service Pack 2.
-   Microsoft Windows 2000 Professional Service Pack 4, Windows 2000 Server Service Pack 4 oppure Windows 2000 Advanced Server Service Pack 4.

Autorizzazioni
--------------

È necessario concedere le seguenti autorizzazioni del disco agli utenti specificati per le directory specificate:

1.  Il gruppo predefinito Utenti o l'account NT Authority\\Servizio di rete (in Windows Server 2003) deve disporre dell'autorizzazione di lettura per la cartella radice sull'unità in cui si trova la directory del contenuto di WSUS. Se tale autorizzazione manca, i download BITS non verranno eseguiti.
2.  L'account NT Authority\\Servizio di rete deve disporre dell'autorizzazione "Controllo completo" per la directory del contenuto di WSUS, in genere &lt;SystemDriver&gt;:WSUS\\WsusContent. Tale autorizzazione viene impostata durante l'installazione del server WSUS al momento della creazione della directory, ma alcuni software di protezione potrebbero reimpostarla. Se tale autorizzazione manca, i download BITS non verranno eseguiti.
3.  L'account NT Authority\\Servizio di rete deve disporre dell'autorizzazione "Controllo completo" per le seguenti cartelle per consentire la corretta visualizzazione dello snap-in Amministrazione di WSUS:
    -   %windir%\\Microsoft .NET\\Framework\\v2.0.50727\\Temporary ASP.NET Files
    -   %windir%\\Temp

Per ulteriori informazioni sull'impostazione delle autorizzazioni, vedere DCPROMO non conserva le autorizzazioni per alcune cartelle IIS all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=76332](http://go.microsoft.com/fwlink/?linkid=76332).
