---
TOCTitle: Rilevamento del Servizio di registrazione
Title: Rilevamento del Servizio di registrazione
ms:assetid: 'bbeb00bd-04e0-4df6-8615-76aa8125b620'
ms:contentKeyID: 18824750
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747737(v=WS.10)'
---

Rilevamento del Servizio di registrazione
=========================================

Il primo server RMS di cui viene eseguito il provisioning in un insieme di strutture deve connettersi al servizio di Enrollment Microsoft per registrarsi e ottenere un certificato concessore di licenze server. Per acquisire l'URL del servizio di Enrollment, il programma di installazione di RMS invia una richiesta UDDI al [sito Web Microsoft UDDI](http://go.microsoft.com/fwlink/?linkid=14794) (http://go.microsoft.com/fwlink/?LinkId=14794). I server successivi di cui viene eseguito il provisioning all'interno del cluster di certificazione principale non richiedono certificati concessori di licenze server perché condividono la configurazione del primo server di certificazione principale.
