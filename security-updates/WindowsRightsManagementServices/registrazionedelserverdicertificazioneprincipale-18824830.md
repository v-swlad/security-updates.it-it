---
TOCTitle: Registrazione del server di certificazione principale
Title: Registrazione del server di certificazione principale
ms:assetid: 'f08bc919-f090-4843-b2ce-b40d558012ce'
ms:contentKeyID: 18824830
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747734(v=WS.10)'
---

Registrazione del server di certificazione principale
=====================================================

La registrazione mediante il servizio di Enrollment Microsoft è necessaria per il primo server presente nella distribuzione di RMS. Questo server, che ricopre il ruolo di server di certificazione principale, può essere registrato automaticamente durante il provisioning, qualora disponga di una connessione a Internet; in alternativa, può essere registrato manualmente se fa parte di una rete locale isolata. Per ulteriori informazioni sulla registrazione manuale di un server, vedere “Per registrare manualmente un server di certificazione principale” in “Gestione di un server RMS” in questa documentazione.

La richiesta di registrazione richiede i parametri di input seguenti:

-   Una chiave pubblica a 1024 bit. Viene impiegata come chiave pubblica di RMS.
-   Versione, nome e URL del server RMS da registrare.

Il Servizio di Enrollment Microsoft utilizza queste informazioni solo per creare il certificato concessore di licenze server e le memorizza solo a scopo di revoca.

Il Servizio di Enrollment Microsoft restituisce una catena di certificati contenente la catena di certificati concessori di licenze del server di registrazione nonché un certificato firmato dal server di registrazione. Il certificato contiene la chiave pubblica del server del server firmata con la chiave privata di registrazione nonché la versione e l'URL del server registrato. Il certificato garantisce al server di certificazione principale il diritto di emettere certificati concessore di licenze server ai server licenze, oltre a quello di emettere certificati per account con diritti, certificati concessore di licenze client e licenze di pubblicazione e d'uso.

Il certificato concessore di licenze server è valido per un anno. Il periodo di validità decorre dalla data di rilascio del certificato. Alla scadenza del periodo di validità il certificato può essere rinnovato. I certificati e le licenze rilasciati dal server sono validi per sette anni. Il periodo di validità decorre dalla data di rilascio del certificato o della licenza.

Le informazioni riguardanti la revoca del certificato vengono aggiunte al certificato concessore di licenze server in base a quanto specificato nella richiesta di registrazione. La chiave pubblica del Servizio di Enrollment Microsoft viene aggiunta al certificato come chiave di revoca. Inoltre, qualora venga specificata una chiave di revoca di terze parti, questa viene anche aggiunta al certificato come chiave di revoca.
