---
TOCTitle: 'Passaggio 2: Installare WSUS nel server'
Title: 'Passaggio 2: Installare WSUS nel server'
ms:assetid: 'f593532c-e92e-47f3-914a-38a6c2519e94'
ms:contentKeyID: 18132662
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc708622(v=WS.10)'
---

Passaggio 2: Installare WSUS nel server
=======================================

Dopo avere verificato i requisiti per l'installazione, è possibile installare WSUS. È necessario accedere al server in cui si desidera installare WSUS utilizzando un account membro del gruppo Administrators locale. Solo i membri di tale gruppo possono installare WSUS.

Nelle procedure seguenti vengono utilizzate le opzioni di installazione predefinite di WSUS per Windows Server 2003 che includono l'installazione di Windows SQL Server 2000 Desktop Engine (WMSDE) come software di database di WSUS, l'archiviazione locale degli aggiornamenti e l'utilizzo del sito Web predefinito IIS nella porta 80. Per informazioni sulle opzioni di installazione personalizzate, ad esempio l'utilizzo di un sistema operativo diverso, di un altro software di database o di un sito Web con un numero di porta personalizzato, vedere il white paper “Deploying Microsoft Windows Server Update Services” (informazioni in lingua inglese).

**Per installare WSUS in Windows Server 2003**
1.  Fare doppio clic sul file di installazione **WSUSSetup.exe**.

    | ![](images/Cc708622.note(WS.10).gif)Nota                                                                                                                                                               |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | La versione più recente di WSUSSetup.exe è disponibile nel [sito Web Microsoft](http://go.microsoft.com/fwlink/?linkid=47374) relativo a Windows Server Update Services all'indirizzo http://go.microsoft.com/fwlink/?LinkId=47374. |

2.  Nella pagina iniziale della procedura guidata fare clic su **Avanti**.

3.  Leggere attentamente i termini del Contratto di Licenza Microsoft, fare clic su **Accetto i termini del Contratto di Licenza Microsoft** e quindi su **Avanti**.

4.  Nella pagina **Selezione origine aggiornamenti** è possibile specificare l'origine degli aggiornamenti per i client. Se si seleziona la casella di controllo **Archivia aggiornamenti in locale**, gli aggiornamenti vengono archiviati nel server di WSUS ed è possibile selezionare una posizione di archiviazione nel file system. Se gli aggiornamenti non vengono archiviati in locale, i computer client si connettono a Microsoft Update per scaricare gli aggiornamenti approvati.

    Mantenere le opzioni predefinite e fare clic su **Avanti**.

    ![](images/Cc708622.fa6ac6a6-6814-4b7e-96e8-e08af5e534b8(WS.10).gif)

5.  Nella pagina **Opzioni database** è possibile selezionare il software utilizzato per gestire il database di WSUS. Per impostazione predefinita, il programma di installazione di WSUS consente di installare WMSDE se il computer utilizzato esegue Windows Server 2003.

    Se WMSDE non è disponibile, è necessario fare in modo che WSUS utilizzi un'istanza di SQL Server facendo clic su **Usa un server di database esistente nel computer** e digitando il nome dell'istanza nella casella **Selezione nome istanza SQL server**. Per ulteriori informazioni sui software di database che possono essere utilizzati oltre a WMSDE, vedere il white paper “Deploying Microsoft Windows Server Update Services” (informazioni in lingua inglese).

    Mantenere le opzioni predefinite e fare clic su **Avanti**.

    ![](images/Cc708622.bc0b73ad-b338-437c-a3c7-0299e819840d(WS.10).gif)

6.  Nella pagina **Selezione sito Web** è possibile specificare il sito Web che verrà utilizzato da WSUS. In questa pagina sono inoltre elencati due URL importanti in base alla selezione, ovvero l'URL al quale i computer client di WSUS punteranno per scaricare gli aggiornamenti e l'URL della console WSUS che consentirà di configurare WSUS.

    Se nella porta 80 è già configurato un sito Web, potrebbe essere necessario creare il sito Web di WSUS in una porta personalizzata. Per ulteriori informazioni sull'esecuzione di WSUS in una porta personalizzata, vedere il white paper “Deploying Microsoft Windows Server Update Services” (informazioni in lingua inglese).

    Mantenere l'opzione predefinita e fare clic su **Avanti**.

    ![](images/Cc708622.64ed7643-a050-4f54-bf9f-04cf7931adc0(WS.10).gif)

7.  Nella pagina **Impostazioni mirroring aggiornamenti** è possibile specificare il ruolo di gestione per il server di WSUS. Se si tratta del primo server di WSUS nella rete o se si desidera implementare una topologia di gestione distribuita, ignorare questa pagina.

    Se invece si desidera implementare una topologia di gestione centralizzata e questo non è il primo server di WSUS nella rete, selezionare la casella di controllo e digitare il nome di un server di WSUS aggiuntivo nella casella **Nome server**. Per ulteriori informazioni sui ruoli di gestione, vedere il white paper “Deploying Microsoft Windows Server Update Services” (informazioni in lingua inglese).

    Mantenere l'opzione predefinita e fare clic su **Avanti**.

    ![](images/Cc708622.f26e09d5-983c-418d-8511-8960850403ef(WS.10).gif)

8.  Nella pagina **Inizio installazione di Microsoft Windows Server Update Services** verificare le selezioni e fare clic su **Avanti**.

    ![](images/Cc708622.20de7d09-3d30-4867-9253-6f353dd1923d(WS.10).gif)

9.  Se nella pagina finale della procedura guidata viene confermato il completamento dell'installazione, fare clic su **Fine**.
