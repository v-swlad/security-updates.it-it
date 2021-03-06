---
TOCTitle: Per attivare la certificazione di servizi server
Title: Per attivare la certificazione di servizi server
ms:assetid: '0ed78c85-7acb-4e3b-a594-613f8ccb5b14'
ms:contentKeyID: 18824516
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc720196(v=WS.10)'
---

Per attivare la certificazione di servizi server
================================================

Per eseguire questa procedura, è necessario avere effettuato l'accesso locale al sito Web di amministrazione con un account utente di dominio che faccia parte del gruppo Administrators. Per garantire maggiore protezione, eseguire la procedura utilizzando **Esegui come**.

Questa procedura è applicabile solo sul cluster principale.

Per utilizzare questa procedura, è necessario avere già creato un gruppo di utenti contenente gli account degli utenti rappresentati dai servizi server durante l'utilizzo del contenuto protetto con RMS.

Abilitazione della certificazione di servizi server
---------------------------------------------------

#### Per attivare la certificazione di servizi server

1.  Accedere al computer come membro del gruppo Administrators locale.

2.  Aprire un browser per file system e passare alla cartella &lt;unità sistema&gt;:\\Inetpub\\wwwroot\\\_wmcs\\Certification.

3.  Per attivare i servizi server per ricevere i certificati per account con diritti (RAC, Rights Account Certificates), fare doppio clic sul file **ServerCertification.asmx**, quindi su Proprietà.

4.  Nella scheda **Sicurezza**, fare clic su **Aggiungi** e aggiungere il gruppo creato per questa categoria di utenti e il **gruppo di servizi RMS**.

5.  Negli elenchi **Autorizzazioni** dei gruppi, selezionare la casella di controllo **Consenti** per le autorizzazioni di **Lettura e& Esecuzione** e fare clic su **OK**.

6.  Ripetere i passaggi 1 - 4 per ogni server del cluster.

| ![](images/Cc720196.note(WS.10).gif)Nota                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Per Microsoft Exchange Server 2007, è necessario aggiungere l'oggetto computer Active Directory di ogni server testa di ponte all'elenco di controllo di accesso discrezionale (DACL, Discretionary Access Control List) di ServerCertification.asmx. Allo stesso modo, per Microsoft Office SharePoint Server 2007, è necessario aggiungere a tale DACL l'oggetto computer Active Directory del server Office SharePoint Server 2007. Si consiglia di aggiungere un gruppo di protezione a questo DACL e aggiungervi gli oggetti computer appropriati. |
