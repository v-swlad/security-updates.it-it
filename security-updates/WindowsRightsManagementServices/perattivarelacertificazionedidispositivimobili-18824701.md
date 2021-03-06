---
TOCTitle: Per attivare la certificazione di dispositivi mobili
Title: Per attivare la certificazione di dispositivi mobili
ms:assetid: '93ec088e-9056-4c3c-bd97-1173fb194578'
ms:contentKeyID: 18824701
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747603(v=WS.10)'
---

Per attivare la certificazione di dispositivi mobili
====================================================

Per eseguire questa procedura, è necessario avere effettuato l'accesso locale al sito Web Amministrazione con un account utente di dominio che faccia parte del gruppo Administrators nel computer in cui si sta effettuando l'accesso. La procedura può essere inoltre eseguita dai membri del gruppo Domain Admins. Per garantire maggiore protezione, eseguire la procedura utilizzando **Esegui come**.

Questa procedura è applicabile solo con il cluster di certificazione principale.

Per utilizzare questa procedura, è necessario aver già creato un gruppo di utenti contenente gli account degli utenti del dispositivo mobile che utilizzano il contenuto protetto con RMS.

Attivazione della certificazione di dispositivi mobili
------------------------------------------------------

#### Per attivare la certificazione di dispositivi mobili

1.  Sul server di certificazione principale, aprire un browser per file system e passare alla cartella &lt;system drive&gt;:\\Inetpub\\wwwroot\\\_wmcs\\Certification.

2.  Per attivare i dispositivi mobili per ricevere i certificati per account con diritti (RAC, Rights Account Certificates), fare clic con il pulsante destro del mouse sul file MobileDeviceCertification.asmx, quindi su **Proprietà**.

3.  Nella scheda **Sicurezza**, fare clic su **Aggiungi** e aggiungere il gruppo creato per questa categoria di utenti e il **gruppo di servizi RMS**.

4.  Nell'elenco **Autorizzazioni** dei gruppi, selezionare la casella di controllo **Consenti** sia per le autorizzazioni di **lettura** che per quelle di **lettura ed esecuzione**, quindi fare clic su **OK**.
