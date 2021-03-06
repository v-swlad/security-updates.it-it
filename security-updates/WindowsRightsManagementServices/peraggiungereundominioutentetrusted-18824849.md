---
TOCTitle: Per aggiungere un dominio utente trusted
Title: Per aggiungere un dominio utente trusted
ms:assetid: 'ed672e58-6272-4ac0-a434-d1d938037e93'
ms:contentKeyID: 18824849
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747793(v=WS.10)'
---

Per aggiungere un dominio utente trusted
========================================

Per eseguire questa procedura, è necessario avere effettuato l'accesso locale al sito Web di amministrazione con un account utente di dominio che faccia parte del gruppo Administrators nel computer in cui si sta effettuando l'accesso. La procedura può essere inoltre eseguita dai membri del gruppo Domain Admins. Per garantire maggiore protezione, eseguire la procedura utilizzando **Esegui come**.

Per visualizzare la pagina **Amministrazione globale**, fare clic su **Start**, scegliere **Tutti i programmi**, quindi **Windows RMS** e infine **Amministrazione di Windows RMS**.

Aggiunta di un dominio utente trusted
-------------------------------------

#### Per aggiungere un dominio utente trusted

1.  Visualizzare la pagina **Amministrazione globale** e selezionare **Amministra RMS in questo sito Web** accanto al sito Web in cui si desidera aggiungere un dominio utente trusted.

2.  Nell'area **Collegamenti per l'amministrazione,** selezionare **Criteri di trust**.

3.  Nell'area **Domini utenti trusted,** scegliere **Sfoglia**, individuare il certificato concessore di licenze server del dominio utente che si desidera importare per stabilire la relazione di trust e fare doppio clic su tale certificato, quindi scegliere **Aggiungi**.

    Il nome del dominio verrà visualizzato nell'elenco **Domini utenti trusted**.

4.  Per specificare quali domini all'interno del dominio utente trusted sono trusted, fare clic su **Domini trusted** accanto al nome del certificato nell'elenco per aprire la finestra **Domini posta elettronica trusted**.

5.  Selezionare una delle seguenti opzioni di trust.

    -   Selezionare **Considera trusted tutti i domini per la posta elettronica** per specificare come trusted tutti gli account utente che sono membri di tale dominio.
        –oppure-
    -   Selezionare **Considera trusted solo i domini per la posta elettronica specificati**, digitare il nome del dominio da specificare come trusted, ad esempio example.com, e fare clic su **Aggiungi**. In questo modo, il dominio verrà aggiunto all'elenco Domini posta elettronica trusted. Per rimuovere un nome dall'elenco, selezionarlo e scegliere **Rimuovi**. Quando si inserisce un dominio nell'elenco, vengono inclusi anche i relativi sottodomini.

6.  Se si utilizza RMS in un ambiente in cui è necessario espandere l'appartenenza ai gruppi a insiemi di strutture diversi, selezionare la casella di controllo **Considera attendibile la gestione licenze RM per gli identificatori di protezione per questo dominio utenti**.

7.  Al termine, scegliere **Chiudere la finestra e tornare a Criteri di trust**.

Per ulteriori informazioni sull’esecuzione di questa procedura, vedere "[Aggiunta e rimozione di domini utente trusted](https://technet.microsoft.com/7c440b15-01c4-49f1-b43c-00f67f3388c1)", più indietro in questo argomento.
