---
TOCTitle: Per specificare il percorso dei modelli di criteri per i diritti
Title: Per specificare il percorso dei modelli di criteri per i diritti
ms:assetid: 'e1bee46d-33db-424f-ba45-1dcedcb883ab'
ms:contentKeyID: 18824822
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747781(v=WS.10)'
---

Per specificare il percorso dei modelli di criteri per i diritti
================================================================

Per eseguire questa procedura, è necessario avere effettuato l'accesso locale al sito Web di amministrazione con un account utente di dominio che faccia parte del gruppo Administrators nel computer in cui si sta effettuando l'accesso. La procedura può essere inoltre eseguita dai membri del gruppo Domain Admins. Per garantire maggiore protezione, eseguire la procedura utilizzando **Esegui come**.

Per visualizzare la pagina **Amministrazione globale**, fare clic su **Start**, scegliere **Tutti i programmi**, quindi **Windows RMS** e infine **Amministrazione di Windows RMS**.

Se i modelli di criteri per i diritti vengono memorizzati in una cartella condivisa e si modifica il percorso della cartella, è necessario copiare manualmente tali modelli dal percorso precedente a quello nuovo.

I modelli di criteri per i diritti vengono inoltre memorizzati nel database di configurazione. Per ulteriori informazioni sulla distribuzione dei modelli di criteri per i diritti, vedere "[Distribuzione dei modelli di criteri per i diritti](https://technet.microsoft.com/ae6fa26f-d744-4ac9-9eb1-728ffab87bfe)", più indietro in questo argomento.

Se si utilizza Microsoft Office 2003 come applicazione abilitata per RMS, il percorso dei modelli di criteri per i diritti viene controllato dalla chiave del Registro `AdminTemplatePath` e il client RMS cercherà di individuare i modelli nella posizione specificata nella chiave del Registro piuttosto che in altre posizioni.

Specifica del percorso dei modelli di criteri per i diritti
-----------------------------------------------------------

#### Per specificare il percorso dei modelli di criteri per i diritti

1.  Visualizzare la pagina **Amministrazione globale** e selezionare **Amministra RMS in questo sito Web** accanto al sito Web in cui si desidera specificare il percorso dei modelli di criteri per i diritti.

2.  Nell'area **Collegamenti per l'amministrazione,** selezionare **Modelli criteri diritti**.

3.  Nell'area **Percorso modello,** specificare l'UNC (Universal Naming Convention) di una cartella condivisa in cui si desidera memorizzare i modelli di criteri per i diritti per il cluster, in base al formato \\\\*nome\_server*\\*nome\_condivisione*. L'account in esecuzione nel pool di applicazioni di **amministrazione** deve disporre delle autorizzazioni di scrittura nella cartella condivisa. Verificare che i modelli siano memorizzati in un percorso di rete accessibile e conforme ai criteri di protezione dell'organizzazione. Le cartelle condivise per i modelli non devono essere create all'interno delle cartelle principali utilizzate da RMS, come ad esempio la cartella Programmi o le cartelle IISRoot.

4.  Scegliere **Salva**.

5.  Dopo avere creato i modelli di criteri per i diritti e averli salvati in questo percorso, è necessario renderli disponibili agli utenti. Per impostazione predefinita, tramite il client RMS, viene eseguita la ricerca dei modelli di criteri per i diritti nel percorso seguente del computer locale:

    %HOMEPATH%\\Local Settings\\Application Data\\Microsoft\\DRM\\templates

    È necessario copiare i modelli di criteri per i diritti dal percorso specificato al passaggio 3 in questo percorso per tutti gli utenti dell'organizzazione che utilizzano RM.
