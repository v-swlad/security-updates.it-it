---
TOCTitle: Problemi di amministrazione RMS
Title: Problemi di amministrazione RMS
ms:assetid: '97013c08-d3fa-4ea0-8914-995b6c97f900'
ms:contentKeyID: 18824714
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747605(v=WS.10)'
---

Problemi di amministrazione RMS
===============================

Dopo che è stato eseguito con successo il provisioning sul server RMS, si potrebbero incontrare problemi durante la gestione quotidiana di RMS. Le informazioni contenute nelle seguenti sezioni possono essere utili per aiutare a risolvere alcuni di questi problemi.

Appare il messaggio "Server SQL inesistente o accesso negato" quando si cerca di aprire il sito Web di amministrazione RMS
--------------------------------------------------------------------------------------------------------------------------

Se RMS è stato installato utilizzando una nuova installazione di SQL Server 2005 come server di database, il servizio SQL Server potrebbe non essere avviato. In SQL Server 2005 il servizio MSSQLSERVER non è configurato in modo da avviarsi automaticamente quando viene avviato il server. Se si è riavviato SQL Server dopo l'installazione di RMS e non si è configurato questo servizio in modo da riavviarsi automaticamente, RMS non sarà in grado di funzionare e sarà accessibile solo la pagina Amministrazione globale RMS.

Dopo avere avviato il servizio MSSQLSERVER è necessario riavviare IIS dal server RMS per ripristinare le funzionalità di RMS.

Impossibilità di completare il processo di registrazione fuori linea
--------------------------------------------------------------------

Se il file di richiesta registrazione è incompleto o è stato modificato prima dell'invio al sito Web EnrollService, è impossibile completare la registrazione fuori linea. Il file di richiesta registrazione potrebbe essere stato danneggiato da un programma dannoso, da un errore dell'utente o da un errore del sistema.

A seconda delle informazioni mancanti, il sito Web EnrollService potrebbe comunque accettare il file e restituire un certificato concessore di licenze server o potrebbe rifiutare di accettare il file di richiesta e visualizzare un errore.

Se viene restituito un certificato concessore di licenze server, rispecchierà le omissioni o i danneggiamenti presenti nel file di richiesta registrazione e RMS visualizzerà un errore quando si cercherà di importare il certificato.

Se non si è in grado di completare il processo di registrazione, controllare che il computer dotato di connessione Internet sia esente da virus, riesportare il file di richiesta registrazione dal server RMS, quindi utilizzare un supporto diverso per trasportarlo sul computer dotato di connessione Internet. Se si rileva nuovamente l'errore si dovrebbe contattare Microsoft Product Support Services.

I file di registrazione non vengono creati
------------------------------------------

Il servizio di registrazione RMS richiede il servizio di Accodamento messaggi (noto anche come MSMQ) e l'accesso database di registrazione. Se i file di registrazione non vengono creati, questo potrebbe significare che i componenti non sono stati configurati correttamente o che le comunicazioni fra i componenti sono interrotte.

Eseguire un test per assicurarsi che il server RMS e il server di database siano connessi alla rete. Se lo sono, utilizzare le seguenti procedure per esaminare i prerequisiti del servizio di registrazione RMS e assicurarsi che tutte le dipendenze software siano configurate correttamente.

Per prima cosa, verificare che la configurazione di Accodamento messaggi sia corretta. Accodamento messaggi deve essere installato e Integrazione in Active Directory deve essere attivata.

**Per verificare che Accodamento messaggi sia stato installato e configurato correttamente**
1.  Nel **Pannello di controllo**, fare clic su **Installazione applicazioni**, quindi fare clic su **Installazione componenti di Windows** per aprire **Aggiunta guidata componenti di Windows**.

2.  In **Aggiunta guidata componenti di Windows**, selezionare la casella di controllo **Server applicazioni**, quindi fare clic su **Dettagli**.

3.  Selezionare la casella di controllo **Accodamento messaggi** e fare clic su **Dettagli**.

4.  Se la casella di controllo **Integrazione in Active Directory** è selezionata, passare al test successivo per verificare che Accodamento messaggi sia in esecuzione. Se la casella di controllo non è selezionata, continuare a eseguire i passaggi da 5 a 9.

5.  Fare clic su **Start**, scegliere **Tutti i programmi**, fare clic su **Windows RMS** e quindi su **Amministrazione di Windows RMS** per aprire la pagina Web Amministrazione globale.

6.  Accanto al sito Web in cui è stato eseguito il provisioning di RMS, selezionare **Rimuovi RMS da questo sito Web** e scegliere **OK**.

7.  Da **Installazione applicazioni** nel **Pannello di controllo**, fare clic su **Installazione componenti di Windows**, fare clic su **Server applicazioni**, quindi fare clic su **Accodamento messaggi**.

8.  Per attivare **Integrazione in Active Directory**, fare clic su **Dettagli**, selezionare la casella di controllo **Integrazione in Active Directory**, quindi fare clic su **OK**.

9.  Aprire la pagina **Amministrazione globale**. Accanto al nome del sito Web in cui si desidera eseguire il provisioning di RMS, selezionare **Effettua il provisioning di RMS in questo sito Web**.

In secondo luogo, verificare che Accodamento messaggi sia in esecuzione sul server.

**Per verificare che Accodamento messaggi sia in esecuzione sul server.**
1.  Nel **Pannello di controllo**, fare clic su **Strumenti di amministrazione**, quindi fare clic su **Servizi**.

2.  Scorrere l'elenco dei servizi finché non si trova il servizio **Accodamento messaggi**.

3.  Nella colonna **Stato**, il servizio dovrebbe essere segnalato come **Avviato**; se non lo è, fare clic con il pulsante destro del mouse sul servizio, quindi fare clic su **Avvia**.

Come terza fase, verificare che il servizio di registrazione attività abbia l'autorizzazione per scrivere eventi nel database di registrazione. Il servizio di registrazione attività di RMS viene eseguito utilizzando l'account di servizio RMS. Verificare che l'account di servizio RMS abbia un accesso valido al server di database e che ad esso siano state concesse le autorizzazioni richieste per consentire la creazione di database e la scrittura di informazioni nei file.

Una volta soddisfatti tutti questi prerequisiti, arrestare e riavviare il servizio di registrazione attività di RMS utilizzando lo snap-in Servizi. Dopo il riavvio del servizio di registrazione RMS, i file di registrazione attività dovrebbero essere creati sul server di database. Se si utilizza SQL Server come server di database, la procedura seguente mostra come verificare che vengano creati i file di registrazione attività.

**Per verificare che i file di registrazione attività vengono creati in SQL Server**
1.  In SQL Server Enterprise Manager, passare al database di registrazione attività, espandere **Database**, quindi espandere il database che include il database di registrazione attività di RMS.

2.  Fare clic sul database di registrazione attività, scegliere **Tabelle**, fare clic con il pulsante destro del mouse su **DRMS\_log\_master** e scegliere **Apri tabella - Visualizza tutte le righe**. Se è in corso la creazione dei file di registro, vengono visualizzati uno o più file.

Ripristino del database di configurazione
-----------------------------------------

RMS non può funzionare senza un database di configurazione funzionante. Se si hanno problemi con il database di configurazione, come un danneggiamento del database o un malfunzionamento del disco rigido sul server di database, è possibile ripristinare le funzionalità di RMS ripristinando un backup del database di configurazione. Per ripristinare il database di configurazione RMS da un backup, sono necessarie le seguenti informazioni:

-   Il nome del backup più recente del database.
-   Il nome del computer su cui sarà ripristinato il database di backup.
-   Il nome dell'account e la password utilizzati originariamente per eseguire il provisioning di RMS.
-   La password originariamente specificata per proteggere software della chiave privata (se è stata utilizzata).

Il ripristino dal database di backup non richiede un nuovo certificato concessore di licenze server o una nuova chiave privata, poiché RMS conserva tutte le impostazioni (ottenute dal database di configurazione di backup).

È possibile ripristinare un database di backup utilizzando la seguente procedura.

**Per ripristinare un database di backup**
1.  Fare clic su **Start**, scegliere **Tutti i programmi**, fare clic su **Windows RMS** e quindi su **Amministrazione di Windows RMS** per aprire la pagina Web **Amministrazione globale**.

2.  Accanto al sito Web in cui è stato eseguito il provisioning di RMS, selezionare **Rimuovi RMS da questo sito Web** e scegliere **OK**.

3.  Ripristinare i file del database di backup relativi al database di configurazione. Se si è eseguito il backup del database di registrazione attività durante la procedura di backup e si vuole mantenere la continuità di dati, ripristinare anche il database di registrazione attività.

    -   Se il sistema viene ripristinato dopo un malfunzionamento totale del sistema, ripristinare il registro utilizzando il backup dello stato del sistema prima di ripristinare i file del database di backup.

4.  Se il database che viene ripristinato è per un unico server di certificazione principale, modificare la seguente chiave del registro di sistema prima di provare a rieseguire il provisioning del servizio:

    -   Su computer in cui è in esecuzione la versione a 32 bit di Windows Server 2003:
        `HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\1.0\`
    -   Su computer in cui è in esecuzione la versione a 64 bit di Windows Server 2003:
        `HKEY_LOCAL_MACHINE\SoftwareWOW6432Node\Microsoft\DRMS\1.0`

    Aggiungere la seguente voce come valore stringa e lasciare vuoto il valore:

    `GicURL`

    Questo sovrascrive la rilevazione mediante Active Directory del server di certificazione principale e permette di accedere alle pagine di provisioning del server di certificazione principale.

5.  Se è stato utilizzato un dispositivo di protezione hardware per proteggere la chiave privata RMS, ripristinare l'intero backup della protezione in modo che le chiavi possano essere recuperate.

6.  Eseguire una delle operazioni seguenti:

    -   Per ripristinare il database per un singolo server piuttosto che per un cluster, fare clic su Effettua il provisioning di RMS in questo sito Web accanto al sito Web in cui si desidera eseguire il provisioning di RMS.
        oppure
    -   Per ripristinare il database per un cluster, fare clic su Aggiungi questo server a un cluster accanto al sito Web in cui si desidera eseguire il provisioning di RMS.

7.  Specificare l'account di servizio di RMS utilizzato inizialmente per eseguire il provisioning del server.

8.  Specificare il database di configurazione di backup (includendo il nome del database e il nome del computer dove risiede il database) che si desidera utilizzare.

9.  Specificare la password utilizzata inizialmente per eseguire il provisioning del server.

10. Scegliere **Invia**.

Il processo di provisioning verrà avviato e sarà rieseguito il provisioning di RMS sul server.

Per ulteriori informazioni, vedere Pianificazione del ripristino del sistema e Backup e ripristino del sistema RMS in Pianificazione di una distribuzione RMS, in questa documentazione.

Password dell'account di servizio di RMS scaduta
------------------------------------------------

Se RMS smette di funzionare, può darsi che la password dell'account di servizio di RMS sia scaduta. Verificare questo problema in Gestione IIS. Se i pool di applicazione RMS sono interrotti e non è possibile riavviarli, la password dell'account di servizio di RMS potrebbe essere scaduta.

Se la password di account di servizio RMS scade, è necessario modificare la password su ogni server RMS che utilizza l'account con la password scaduta, quindi riavviare IIS. Per ulteriori informazioni, vedere "Modifica della password dell'account di servizio di RMS" in "Utilizzo di un server RMS", in questa documentazione.

Ripristino di una precedente installazione RMS
----------------------------------------------

Se l'hardware o il software del server RMS si blocca, è possibile ripristinare un server RMS utilizzando il database di configurazione precedentemente installato per eseguire il provisioning di una nuova istanza del server.

| ![](images/Cc747605.note(WS.10).gif)Nota                                                                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Questa procedura si applica solo se il server che esegue RMS non funziona. Se non funziona il server che esegue il database di configurazione, vedere "Ripristino del database di configurazione", più indietro in questo argomento. Se il server RMS è anche il server di database, sarà necessario ripristinare l'intero server da una copia di backup. |

Utilizzare la seguente procedura per selezionare lo stesso database di configurazione utilizzato per l'installazione originale.

**Per ripristinare una precedente installazione di RMS**
1.  Connettersi al computer che si desidera configurare come server RMS utilizzando un account con privilegi amministrativi. Assicurarsi che in computer soddisfi i requisiti minimi di sistema per RMS. Per ulteriori informazioni su requisiti di sistema per RMS, vedere "Requisiti hardware" per RMS in "Pianificazione di una distribuzione RMS", in questa documentazione.

2.  Se si utilizza un dispositivo di protezione hardware per proteggere le chiavi private RMS, assicurarsi che sia configurato correttamente utilizzando le stesse impostazioni e le stesse misure di protezione che sono state utilizzate con la precedente installazione di RMS.

3.  Installazione di RMS sul computer.

4.  Dopo aver completato l'installazione di RMS, fare clic su **Start**, scegliere **Tutti i programmi**, fare clic su **Windows RMS** e quindi su **Amministrazione di Windows RMS** per aprire la pagina Web **Amministrazione globale**.

5.  Accanto al sito Web in cui si desidera eseguire il provisioning di RMS, selezionare **Aggiungi questo server a un cluster**.

6.  Nell'area **Account di servizio di RMS,** digitare il nome dell'account del servizio RMS nel formato nome\_dominio\\nome\_utente e la password dell'account di servizio di RMS in cui viene eseguito RMS per le operazioni più comuni. Deve trattarsi di un account di dominio.

7.  Nell'area **Database di configurazione**, specificare il nome del server di database e il nome del database di configurazione dell'installazione RMS originale che si desidera recuperare.

8.  Nell'area **Protezione della chiave privata,** selezionare il meccanismo utilizzato dal cluster per la protezione della chiave privata. Se è stata utilizzata la protezione della chiave privata basata su software, specificare la password utilizzata inizialmente per la crittografia della chiave privata al momento del provisioning del cluster.

9.  Scegliere **Invia**.

I client non possono aprire il contenuto protetto con RMS in quanto le autorizzazioni sono scadute
--------------------------------------------------------------------------------------------------

Se le autorizzazioni di un utente sono scadute, l'utente non può utilizzare il contenuto protetto con RMS. Se l'orologio di sistema del server RMS è avanti rispetto all'orologio di sistema del client RMS, un utente potrebbe non essere in grado di utilizzare il contenuto protetto con RMS anche se le autorizzazioni non sono scadute. Poiché l'orologio di sistema dei due computer non è sincronizzato, potrebbe apparire l'errore seguente quando il computer client cerca di aprire il contenuto:

**You do not have permission to open this message because your permission has expired. Do you want to open it using a different set of credential?**

La licenza del client e la licenza del contenuto sono valide, ma la differenza di orario fa in modo che il client interpreti la licenza del contenuto come non valida e restituisca quell'errore all'utente. Questo potrebbe fare in modo che un utente creda di avere un problema con il certificato del proprio account RMS o con i diritti concessi per il documento. Quando che l'orologio del client avrà raggiunto il periodo di validità della licenza del contenuto, l'utente sarà in grado di aprire il contenuto.

Secondo le procedure, si dovrebbe fare in modo che i client e i server del sistema RMS si sincronizzano con lo stesso segnale orario.

Errore "Accesso negato" quando RMS cerca di registrare gli eventi nel registro eventi dell'applicazione
-------------------------------------------------------------------------------------------------------

Per impostazione predefinita, i componenti come RMS che sono eseguiti da una pagina ASP sono creati con l'account IUSR\_COMPUTERNAME. Questo account è un membro del gruppo Guests e i privilegi di protezione necessari per scrivere nel registro eventi dell'applicazione impediscono agli account Guest la scrittura di dati nel registro eventi.

Per aggirare questo problema, è possibile utilizzare l'editor del registro di sistema per modificare la chiave di registro che controlla questo comportamento.

| ![](images/Cc747605.Caution(WS.10).gif)Attenzione                                                                                                                                          |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Apportando modifiche errate al Registro di sistema, è possibile danneggiare seriamente il sistema. Prima di apportare modifiche al Registro di sistema, effettuare il backup dei dati importanti presenti nel computer. |

Impostare la seguente chiave di registro a 0 anziché a 1, quindi riavviare il computer perché le modifiche abbiano effetto.

`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\EventLog\Application`

Nome: `RestrictGuestAccess`

Tipo: `REG_DWORD`

| ![](images/Cc747605.note(WS.10).gif)Nota                        |
|----------------------------------------------------------------------------------------------|
| Questo permette a tutti gli account Guest di scrivere nel registro eventi dell'applicazione. |

Per ulteriori informazioni sulla causa di questo errore, vedere l'articolo sull'attivazione della registrazione dalle pagine ASP nella [Knowledge Base Microsoft](http://go.microsoft.com/fwlink/?linkid=44167).
