---
TOCTitle: 'Espansione dell''infrastruttura di base per supportare il clustering'
Title: 'Espansione dell''infrastruttura di base per supportare il clustering'
ms:assetid: '78f0f2f0-a075-409c-9f46-26eb62d1d05b'
ms:contentKeyID: 18824658
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747567(v=WS.10)'
---

Espansione dell'infrastruttura di base per supportare il clustering
===================================================================

Se si implementano cluster per distribuzioni di grandi dimensioni, assicurarsi che l'infrastruttura sia configurata in modo da supportare i requisiti del clustering. Nei piani di distribuzione si dovrebbero includere i seguenti elementi.

Registrazione DNS
-----------------

Assicurarsi che qualsiasi registrazione DNS eseguita per esporre l'indirizzo IP virtuale alla Extranet esponga l'indirizzo anche all'Intranet.

Se la registrazione DNS non viene eseguita per l'Intranet, la richiesta interna della licenza client non avrà esito Nel caso che sia impossibile modificare le impostazioni DNS, è possibile modificare la tabella host di ciascun server contenuto nel cluster in modo da eseguire il mapping dell'URL del cluster con l'indirizzo IP virtuale del cluster. La registrazione DNS deve essere effettuata prima di eseguire il provisioning del servizio; se il provisioning è già stato eseguito, rimuovere RMS dal server e ripetere il processo di provisioning

Bilanciamento del carico
------------------------

Configurare l'hardware e il software richiesti per abilitare la distribuzione dei server di bilanciamento del carico, il servizio Bilanciamento del carico di rete o il bilanciamento del carico hardware, come appropriato, per distribuire le richieste nel cluster.
