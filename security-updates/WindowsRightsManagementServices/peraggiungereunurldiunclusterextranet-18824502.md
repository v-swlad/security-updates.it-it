---
TOCTitle: Per aggiungere un URL di un cluster Extranet
Title: Per aggiungere un URL di un cluster Extranet
ms:assetid: '12c83186-ce9e-4100-bbd1-d87a885331c7'
ms:contentKeyID: 18824502
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc720193(v=WS.10)'
---

Per aggiungere un URL di un cluster Extranet
============================================

Per eseguire questa procedura, è necessario avere effettuato l'accesso locale al sito Web di amministrazione con un account utente di dominio che faccia parte del gruppo Administrators nel computer in cui si sta effettuando l'accesso. La procedura può essere inoltre eseguita dai membri del gruppo Domain Admins. Per garantire maggiore protezione, eseguire la procedura utilizzando **Esegui come**.

Per visualizzare la pagina **Amministrazione globale**, fare clic su **Start**, scegliere **Tutti i programmi**, quindi **Windows RMS** e infine **Amministrazione di Windows RMS**.

Assicurarsi di registrare l'URL nel proprio DNS (Domain Name System), quindi verificarne il funzionamento e la disponibilità nella rete Extranet. Se per i file dei servizi Web è stato abilitato il protocollo SSL, per l'URL del cluster è necessario specificare HTTPS.

Se si aggiunge un URL cluster Extranet a un server RMS già in uso, è necessario ottenere nuovi certificati concessori di licenze client dagli attuali client RMS in modo da consentire l'accesso al cluster Extranet per la gestione delle licenze.

Aggiunta dell'URL di un cluster Extranet
----------------------------------------

#### Per aggiungere un URL di un cluster Extranet

1.  Visualizzare la pagina **Amministrazione globale** e fare clic su **Amministra RMS in questo sito Web** accanto al sito Web in cui si desidera aggiungere un URL di un cluster Extranet.

2.  Nell'area **Collegamenti per l'amministrazione,** fare clic su **Impostazioni URL cluster Extranet**.

3.  Nell'area **URL cluster Extranet,** specificare l'URL che gli utenti esterni devono utilizzare per l'acquisizione delle licenze. È inoltre possibile selezionare HTTP o HTTPS.

4.  Scegliere **Invia**.
