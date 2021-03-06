---
TOCTitle: Backup e ripristino del sistema RMS
Title: Backup e ripristino del sistema RMS
ms:assetid: 'c11f3ac1-e512-402b-bf13-9ff21f5fe745'
ms:contentKeyID: 18824761
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747745(v=WS.10)'
---

Backup e ripristino del sistema RMS
===================================

Quando si esegue una pianificazione per il ripristino del sistema, i piani dovrebbero tener conto degli errori del server di database e dell'interruzione di un server RMS. Qualora si verifichi un'interruzione del server di database, è possibile ripristinare la funzionalità di un cluster o di un server RMS da una copia di backup del database di configurazione. A tale scopo, non è necessario ottenere un nuovo certificato concessore di licenze server o una nuova chiave privata per il server RMS, in quanto questi elementi sono memorizzati nel database di configurazione.

Pianificazione del backup di sistema di RMS
-------------------------------------------

Oltre alla chiave del server, nel database di configurazione sono memorizzati i dati utente, incluse le informazioni sulla chiave pubblica. Per proteggere i dati più importanti relativi alla chiave, eseguire il backup del database di configurazione su un supporto e riporre tale supporto in un luogo sicuro. Poiché il database di configurazione del cluster di certificazione principale varia frequentemente, è consigliabile eseguire regolarmente dei backup. Maggiore è la frequenza con cui vengono aggiunti nuovi utenti all'organizzazione, maggiore è la frequenza con cui è necessario eseguire i backup. Se si esegue il backup del server di certificazione principale, è consigliabile assicurarsi anche di includere nel proprio backup la tabella **sysmessages** del database principale. Se questa tabella non include i messaggi specifici per RMS, il server di certificazione principale non sarà in grado di funzionare e restituirà un errore. Se questa tabella non è nel backup, può essere ricostruita ripetendo il processo di provisioning e utilizzando un database esistente.

Il database di registrazione attività di RMS contiene registrazioni che potrebbero fornire interessanti risoluzioni ai problemi e dati statistici, ma di solito non è critico per un sistema RMS. Il database Servizi Directory è una cache locale del database Active Directory e viene ricreato automaticamente quando si ripristina un sistema RMS. Per definire pianificare l'esecuzione del backup dei database RMS, rivolgersi all'amministratore di SQL Server.

Se per la protezione delle chiavi private di RMS si utilizza un modulo di protezione hardware, eseguire il backup della configurazione di tale modulo. Per ulteriori informazioni sull'esecuzione del backup e sul ripristino della configurazione del modulo di protezione hardware, vedere la documentazione relativa.

| ![](images/Cc747745.note(WS.10).gif)Nota                                                                                                                                                                                                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Se per la crittografia delle chiavi private di RMS si utilizza un provider del servizio di crittografia (CSP, Cryptographic Service Provider) basato su software diverso da quello predefinito, assicurarsi di disporre delle corrette procedure di gestione della chiave organizzativa, ad esempio le procedure di backup e ripristino, per il provider prima del suo uso con RMS. |

Pianificazione del ripristino di un sistema RMS
-----------------------------------------------

Se si ripristina un server di database da un backup, assicurarsi che la versione di RMS in esecuzione sia la stessa versione che era in esecuzione quando è stato creato il backup. Informare gli utenti del sistema RMS che, se hanno iniziato a utilizzare il sistema RMS dopo la data di esecuzione del backup, sarà loro richiesto di ottenere un nuovo certificato di account con diritti. Il risultato è comunque che nessun contenuto protetto verrà perso.

Per ripristinare un singolo server RMS da un cluster, ricostruire il server, reinstallare RMS e quindi unire il server al cluster utilizzando il database esistente. Questa attività non influisce sugli utenti del sistema RMS poiché i server raggruppati in cluster operano come se fossero uno solo.
