---
TOCTitle: 'Passaggio 2: Installare la console di amministrazione o il server di WSUS'
Title: 'Passaggio 2: Installare la console di amministrazione o il server di WSUS'
ms:assetid: '6db6fcb0-c55d-43b9-9b07-4040c6267759'
ms:contentKeyID: 21743046
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd939859(v=WS.10)'
---

Passaggio 2: Installare la console di amministrazione o il server di WSUS
=========================================================================

Dopo aver verificato se il server soddisfa i requisiti minimi di sistema e se si dispone delle autorizzazioni account necessarie, sarà possibile installare Windows Server Upgrade Services 3.0 Service Pack 2 (WSUS 3.0 SP2). Avviare l'installazione di WSUS 3.0 SP2 utilizzando la procedura valida per il tipo di installazione e il sistema operativo in uso (tramite Gestione server o tramite il file WUSSetup.exe).

Se si utilizza Gestione server
------------------------------

**Per avviare l'installazione del server di WSUS 3.0 SP2 mediante Gestione server**
1.  Accedere al server in cui si desidera installare WSUS 3.0 SP2 utilizzando un account membro del gruppo Administrators locale.

2.  Fare clic su **Start**, scegliere **Strumenti di amministrazione**, quindi fare clic su **Gestione server**.

3.  Nel riquadro laterale destro della finestra Gestione server, all'interno della sezione Riepilogo ruoli, fare clic su **Aggiungi ruoli**.

4.  Se viene visualizzata la pagina "Requisiti preliminari", fare clic su **Avanti**.

5.  Nella pagina Selezione ruoli server selezionare **Windows Server Update Services**.

6.  Nella pagina Windows Server Update Services fare clic su **Avanti**.

7.  Nella pagina Conferma selezioni per l'installazione premere **Installa**.

8.  Una volta avviata l'installazione guidata di WSUS 3.0 SP2, ignorare la sezione successiva e vedere la procedura “Per continuare l'installazione di WSUS 3.0 SP2”.

Se si utilizza il file WUSSetup.exe
-----------------------------------

**Per avviare l'installazione del server di WSUS 3.0 SP2 oppure la console di amministrazione WSUS 3.0 SP2 utilizzando il file WUSSetup.exe**
1.  Accedere al server in cui si desidera installare WSUS 3.0 SP2 utilizzando un account membro del gruppo Administrators locale.

2.  Fare doppio clic sul file di installazione **WSUSSetup.exe**.

3.  Una volta avviata l'Installazione guidata di Windows Server Update Services 3.0 SP2, vedere la procedura “Per continuare l'installazione di WSUS 3.0 SP2”.

Utilizzo dell'Installazione guidata di WSUS 3.0 SP2
---------------------------------------------------

L'Installazione guidata di WSUS viene avviata da Gestione server o dal file WUSSetup.exe.

**Per continuare l'installazione di WSUS 3.0 SP2**
1.  Nella pagina iniziale dell'Installazione guidata di Windows Server Update Services 3.0 fare clic su **Avanti**.

2.  Nella pagina Selezione della modalità di installazione selezionare **Installazione server completa inclusiva di console di amministrazione** se nel computer si desidera installare il server di WSUS oppure **Solo console di amministrazione** se si desidera installare solo la console di amministrazione.

3.  Nella pagina Contratto di Licenza Microsoft leggere attentamente i termini del Contratto di licenza, fare clic su **Accetto i termini del Contratto di Licenza Microsoft**, quindi su **Avanti**.

4.  È possibile specificare l'origine degli aggiornamenti per i client nella pagina Selezione origine aggiornamenti dell'Installazione guidata. Per impostazione predefinita, viene selezionata la casella di controllo **Archivia aggiornamenti in locale** in modo tale che gli aggiornamenti vengano archiviati nel server di WSUS nella posizione specificata. Se si deseleziona la casella di controllo **Archivia aggiornamenti in locale**, i client computer otterranno aggiornamenti approvati mediante la connessione a Microsoft Update. Effettuare la selezione e fare clic su **Avanti**.

5.  Nella pagina Opzioni database è possibile selezionare il software utilizzato per gestire il database di WSUS 3.0. Per impostazione predefinita, l'Installazione guidata consente di installare Database interno di Windows.

    Se non si desidera utilizzare Database interno di Windows, fornire un'istanza di SQL Server per l'utilizzo di WSUS selezionando **Usa un server di database esistente nel computer** oppure **Usa un server di database esistente in un computer remoto (nome computer\\nome istanza)**. Digitare il nome dell'istanza nella casella corrispondente. Il nome dell'istanza deve essere indicato come &lt;*nomeServer*&gt;\\&lt;*nomeIstanza*&gt;, dove*nomeServer* è il nome del server e *nomeIstanza* è il nome dell'istanza di SQL. Effettuare la selezione e fare clic su **Avanti**.

6.  Se si sceglie la connessione a SQL Server nella pagina **Connessione all'istanza di SQL Server in corso**, WSUS tenterà di eseguire la connessione all'istanza specificata di SQL Server. Dopo aver stabilito correttamente la connessione fare clic su **Avanti** per continuare.

7.  Nella pagina Selezione sito Web è possibile specificare il sito Web che verrà utilizzato da WSUS. Se si desidera utilizzare il sito Web predefinito sulla porta 80, selezionare **Usa il Sito Web predefinito di IIS esistente**. Se già si dispone di un sito Web sulla porta 80, è possibile creare un sito alternativo sulla porta 8530, selezionando **Crea un sito Web Windows Server Update Services 3.0 SP2**. Fare clic su **Avanti**.

8.  Nella pagina **Inizio installazione di Microsoft Windows Server Update Services** verificare le selezioni e quindi fare clic su **Avanti**.

9.  La pagina finale della procedura di installazione guidata indicherà se l'installazione di WSUS è stata eseguita correttamente. Dopo aver fatto clic su **Fine** verrà avviata la Configurazione guidata.

Passaggio successivo
--------------------

[Passaggio 3: Configurare le connessioni di rete](https://technet.microsoft.com/42a144c5-f08e-4a6e-b360-47ddea77bd24).

Risorse aggiuntive
------------------

[Guida dettagliata a Windows Server Update Services 3.0 SP2](https://technet.microsoft.com/4b504edc-93b3-45b0-a7e8-d0107f1a4442)
