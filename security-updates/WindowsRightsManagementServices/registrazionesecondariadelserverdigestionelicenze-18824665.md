---
TOCTitle: Registrazione secondaria del server di gestione licenze
Title: Registrazione secondaria del server di gestione licenze
ms:assetid: '7bc63397-9186-464c-8824-867038adce9b'
ms:contentKeyID: 18824665
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747640(v=WS.10)'
---

Registrazione secondaria del server di gestione licenze
=======================================================

I server licenze vengono registrati automaticamente durante il provisioning, con un processo chiamato registrazione secondaria. Tuttavia, durante l'aggiunta di un nuovo server a un cluster di server licenze, la registrazione secondaria del nuovo server non avviene in modo esplicito, poiché utilizza il certificato concessore di licenze server e il database di configurazione del cluster.

Anziché inviare la richiesta di registrazione secondaria al servizio di Enrollment Microsoft, il server licenze la invia al server di certificazione principale. La richiesta di registrazione secondaria per il server licenze è identica alla richiesta di registrazione per il server di certificazione principale.

Quando riceve la richiesta di registrazione secondaria, il server di certificazione principale verifica che la richiesta sia formulata correttamente, quindi restituisce una catena di certificati contenente la catena certificato concessore di licenze del server di certificazione principale, oltre a un certificato firmato dal server di certificazione principale. Il certificato contiene la chiave pubblica del server, firmata con la chiave privata del server di certificazione principale. Esso garantisce al server licenze il diritto di emettere licenze d'uso e di pubblicazione.

Il certificato concessore di licenze server è valido per un anno. Il periodo di validità decorre dalla data di rilascio del certificato. Alla scadenza del periodo di validità il certificato può essere rinnovato. I certificati e le licenze rilasciati dal server sono validi per sette anni. Il periodo di validità decorre dalla data di rilascio del certificato o della licenza.

Per impostazione predefinita, il servizio necessario per l'elaborazione di una richiesta di registrazione secondaria nel server di certificazione principale, SubEnrollService.asmx, è configurato in modo da negare tutti gli accessi. Prima di che le richieste possano essere elaborate, è necessario modificare l'elenco DACL, in modo da consentire l'accesso all'amministratore di RMS.
