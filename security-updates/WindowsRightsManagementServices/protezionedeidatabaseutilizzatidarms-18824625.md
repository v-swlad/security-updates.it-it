---
TOCTitle: Protezione dei database utilizzati da RMS
Title: Protezione dei database utilizzati da RMS
ms:assetid: '65802f9a-81bc-4398-968a-00c9b1dca2fa'
ms:contentKeyID: 18824625
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc720285(v=WS.10)'
---

Protezione dei database utilizzati da RMS
=========================================

In RMS, vengono creati e utilizzati tre database caratterizzati da requisiti di protezione diversi, come descritto di seguito.

-   **Servizi di directory**. Tramite questo database, vengono memorizzati nella cache i risultati delle query di appartenenza al gruppo di Active Directory. Poiché questo database include esclusivamente informazioni relative ad Active Directory, non sono necessarie ulteriori impostazioni di protezione tranne quelle configurate automaticamente durante il provisioning di RMS.
-   **Registrazione attività**. Le informazioni presenti in questo database sono più delicate rispetto a quelle del database dei servizi di directory, in quanto la loro divulgazione potrebbe influire sulla privacy degli utenti. Microsoft si è impegnata al massimo per evitare la registrazione di informazioni che consentano l'identificazione personale e per fare in modo che a tutte le informazioni registrate nel database vengano applicate le misure di protezione appropriate. Non sono necessarie ulteriori modifiche alla protezione di questo database, a meno che il database non venga spostato in un altro computer con SQL Server. Se il database viene spostato in un altro server, assicurarsi che al nuovo ambiente vengano applicati gli stessi meccanismi di protezione.
-   **Configurazione**. Questo database rappresenta la risorsa più importante e preziosa nella distribuzione di RMS, oltre alle chiavi private del server. Nel database, sono incluse tutte le informazioni delicate e critiche che necessitano di attenta protezione. Sono presenti tutti i certificati e le chiavi, la chiave privata del server crittografata, a meno che non sia stata utilizzata la crittografia hardware consigliata, e l'hash della password della chiave privata, oltre alle informazioni di configurazione.

Quando, tramite RMS, viene creato il database di configurazione, vengono impostate le autorizzazioni che consentono di limitare l'accesso e assicurare la protezione per il database.

Aumento della protezione del database
-------------------------------------

I passaggi seguenti consentono di aumentare la protezione generale per i database nell'ambiente server e di rete.

-   Eseguire il server database in un computer in cui sia in esecuzione Windows Server 2003. Per impostazione predefinita, questo sistema operativo è maggiormente protetto rispetto a Windows 2000 Server. Sebbene sia possibile bloccare i computer basati su Windows 2000 Server, si tratta di un processo che richiede tempo e la cui esecuzione potrebbe essere soggetta a errori che consentirebbero agli utenti malintenzionati di accedere al database.
-   Limitare l'accesso fisico al server database.
-   Assicurarsi che le autorizzazioni per il database e i DACL nei file del database consentano di limitare l'accesso al solo personale autorizzato. Le autorizzazioni e gli elenchi DACL predefiniti configurati da RMS garantiscono la protezione necessaria. Prestare attenzione quando si modifica una delle impostazioni predefinite.
-   Non eseguire servizi non necessari nel server database, ad esempio Microsoft Internet Information Services (IIS), Accodamento messaggi o Servizi terminal.
-   Non eseguire nel server database altri database se non quelli di RMS.

Proteggere i database di SQL Server configurando SSL o IPsec (Internet Protocol Security) in modo da rendere disponibili canali crittografati. Crittografando le comunicazioni con il database, è possibile evitare che utenti malintenzionati possano acquisire o modificare i dati registrati.

Per ulteriori informazioni sulla configurazione di SSL per SQL Server, vedere il sito Web MSDN all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=17060](http://go.microsoft.com/fwlink/?linkid=17060).

Per ulteriori informazioni sulla configurazione di IPsec per SQL Server 2000, vedere il sito Web MSDN all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=17061](http://go.microsoft.com/fwlink/?linkid=17061).

Per ulteriori informazioni sulla protezione dei sistemi operativi Microsoft Windows Server 2003, consultare la "Guida alla protezione di Windows Server 2003" disponibile nell'area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=36719](http://go.microsoft.com/fwlink/?linkid=36719).
