---
TOCTitle: 'Pianificazione dell''infrastruttura di server database'
Title: 'Pianificazione dell''infrastruttura di server database'
ms:assetid: 'b12354bd-3143-4d1f-b5aa-450c4550653c'
ms:contentKeyID: 18824742
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747731(v=WS.10)'
---

Pianificazione dell'infrastruttura di server database
=====================================================

Poiché RMS utilizza database e stored procedure per supportare le proprie operazioni, per utilizzare RMS nella propria organizzazione è necessaria un'infrastruttura di database. Il server database può trovarsi sullo stesso server di RMS o su un altro server. Se la propria infrastruttura non dispone di un server database per supportare RMS, è possibile utilizzare Microsoft SQL Server 2000 Desktop Engine (MSDE 2000) Versione A come server database per il test di RMS.

È consigliabile utilizzare Microsoft SQL Server Desktop Engine per supportare i database di RMS solo in ambienti di verifica perché Microsoft SQL Server Desktop Engine non include gli strumenti necessari per gestire e supportare completamente un database a livello di organizzazione. Inoltre, poiché MSDE non supporta connessioni di rete remote, è necessario installarlo sullo stesso server di RMS e non è possibile aggiungere altri server RMS al cluster RMS. Le condizioni per l'utilizzo di Microsoft SQL Server Desktop Engine specificano che è vietato utilizzare gli strumenti client di SQL Server per modificare un database di Microsoft SQL Server Desktop Engine. Questa limitazione impedisce di eseguire il backup e il ripristino del database di configurazione RMS, visualizzare le informazioni di registrazione o modificare direttamente i dati archiviati nel database di configurazione.

Se si prevede di sistemare i database su un server diverso da quello dell'installazione RMS, è necessario utilizzare un prodotto completo per server database, come SQL Server, per fornire il supporto di database. Assicurarsi di assegnare all'account del servizio RMS le autorizzazioni appropriate di lettura, scrittura e creazione dei database che si trovano sul server database utilizzato per supportare RMS.

Sebbene RMS sia progettato e testato per server database con SQL Server 2000 e MSDE e Microsoft non supporti l'utilizzo di RMS insieme a un provider di database diverso da SQL Server 2000 o MSDE, RMS può essere utilizzato su server database con interfacce ADO.NET fornite da Microsoft .NET Framework. Altri fornitori di database, pertanto, potrebbero aver sviluppato dei provider database compatibili con RMS. È possibile utilizzare qualsiasi provider database con RMS a condizione che il server database corrispondente soddisfi i criteri descritti di seguito.

-   Il server database deve essere compatibile con Transact-SQL, utilizzato sia dagli script di inizializzazione RMS che dalle stored procedure RMS.
-   Il server database deve supportare tutte le estensioni specifiche per Microsoft SQL Server.

Il provider database deve poter:

-   Rispondere a richieste di metodo per lo spazio dei nomi di System.Data.SqlClient di .NET Framework.
-   Fornire una funzionalità corrispondente allo spazio dei nomi System.Data.SqlClient.
-   Utilizzare l'autenticazione Windows integrata piuttosto che l'autenticazione SQL.

Se si utilizza RMS in altre configurazioni, contattare il fornitore del database o il provider della soluzione di cui si sta utilizzando il provider database per la distribuzione personalizzata.

| ![](images/Cc747731.Caution(WS.10).gif)Attenzione                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| I database RMS sono tutti creati con il recupero completo abilitato per impostazione predefinita, ma non viene creato alcun processo di backup del registro transazioni. Questa condizione potrebbe causare l'esaurimento dello spazio sul disco rigido e portare a un blocco del server database. Il recupero completo è raccomandato per il database DRMS\_configuration, mentre gli altri database DRMS possono essere configurati in modo da utilizzare un diverso modello di recupero, in base alle esigenze della propria organizzazione. |

In questa sezione, vengono trattati gli argomenti seguenti:

-   [Come stimare la crescita dei database](https://technet.microsoft.com/87652cc2-b886-4797-8d40-356669768089)
-   [Menutenzione del database dei servizi di directory](https://technet.microsoft.com/911a62f2-c1d6-4091-99b0-b53211be27a7)
-   [Manutenzione del database di registrazione attività](https://technet.microsoft.com/de55058b-0d1a-4997-8a45-e14678ddd13f)
