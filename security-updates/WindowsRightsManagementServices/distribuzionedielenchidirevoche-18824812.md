---
TOCTitle: Distribuzione di elenchi di revoche
Title: Distribuzione di elenchi di revoche
ms:assetid: 'e331338b-66d4-45e4-8d3f-acccf2302ac4'
ms:contentKeyID: 18824812
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747702(v=WS.10)'
---

Distribuzione di elenchi di revoche
===================================

Per implementare le revoche, è necessario distribuire gli elenchi di revoche. Gli elenchi di revoche specificano il contenuto, le applicazioni, gli utenti o altre entità che sono state revocate. È possibile distribuire sia elenchi di revoche aziendali che elenchi di revoche creati da Microsoft.

Distribuzione di elenchi di revoche aziendali
---------------------------------------------

Per utilizzare un modello di criteri per i diritti con un elenco di revoche, è necessario rendere tale elenco disponibile per i computer client dell'organizzazione. Per informazioni sulla creazione degli elenchi di revoca, vedere “Implementazione delle revoche” precedentemente in questo argomento.

Per distribuire un elenco di revoche aziendale, attenersi alla seguente procedura.

1.  Copiare il file dell'elenco di revoche in un server Web accessibile. Poiché gli utenti potrebbero utilizzare i contenuti protetti al di fuori dell'organizzazione, al percorso specificato devono potere accedere tutti gli utenti, sia dall'interno che dall'esterno della rete.
    La distribuzione del file dell'elenco di revoche ai computer client potrebbe richiedere una certa quantità di tempo. Per questo motivo, l'elenco di revoche potrebbe non essere disponibile nel computer degli utenti quando questi tentano di aprire un documento per il quale tale elenco è necessario. Se l'elenco di revoche non è presente nel computer client, può essere scaricato tramite l'applicazione abilitata per RMS dall'ubicazione specificata nella licenza d'uso.
    È consigliabile creare uno script tramite il quale l'elenco di revoche venga automaticamente firmato e copiato sul sito Web ogni giorno. In tal modo, gli utenti non si troveranno a non potere utilizzare un contenuto a causa di un elenco di revoche non aggiornato. Per uno script di esempio, vedere “Utilizzo dello strumento per la firma degli elenchi di revoche” precedentemente in questo argomento.
2.  Nel modello di criteri per i diritti, specificare un intervallo di aggiornamento maggiore di zero per l'elenco di revoche aziendale. In questo modo, l'elenco di revoche non verrà considerato come facoltativo. Se si prevede di aggiornare l'elenco raramente, ad esempio solo nel caso di violazione della protezione, è possibile impostare tale condizione di aggiornamento con un intervallo esteso e quindi utilizzare uno script o le impostazioni di protezione per inviare l'elenco di revoche nei computer client quando necessario. Per informazioni sugli intervalli di aggiornamento, vedere “Definizione dei criteri di revoca” precedentemente in questo argomento. Per ulteriori informazioni sulla configurazione dei modelli di criteri per i diritti, vedere "Creazione e modifica dei modelli di criteri per i diritti", più avanti in questo argomento.
3.  Nel modello di criteri per i diritti, specificare l'URL in cui è disponibile l'elenco di revoche.
4.  In alternativa, è possibile distribuire l'elenco di revoche nei computer client tramite un metodo automatico, ad esempio Criteri di gruppo o Systems Management Server (SMS).

Distribuzione di elenchi di revoche Microsoft
---------------------------------------------

Se si desidera che dal client Servizi Rights Management venga utilizzato un elenco di revoche Microsoft, è necessario distribuire l'elenco nei computer client. Nel presente argomento viene descritto come distribuire un elenco di revoche Microsoft negli scenari seguenti:

-   L'organizzazione desidera distribuire sia il proprio elenco di revoche che l'elenco Microsoft.
-   L'organizzazione desidera distribuire soltanto l'elenco di revoche Microsoft.

Quando un elenco di revoche viene pubblicato da Microsoft, è possibile scaricarlo dalle posizioni seguenti:

-   I server RMS possono scaricare l'elenco di revoche utilizzando Windows Update.
-   In alternativa, se il server RMS non è connesso a Internet, l'elenco di revoche di Microsoft può essere scaricato anche dall'area download Microsoft.

Se il pacchetto dell'elenco di revoche viene scaricato in un server RMS, viene salvato nella cartella %systemdrive%\\Program Files\\Windows Rights Management Services Revocation List. Se si scarica il pacchetto dell'elenco di revoche in un altro tipo di computer, è possibile selezionare la posizione in cui scaricarlo. Il pacchetto include un file eseguibile, CRL\_Update.exe, che consente di installare tutti gli elenchi di revoche client nell'archivio di licenze del client, nonché un file dell'elenco di revoche, Msrl.xml, che può essere copiato in un sito Web o in cartella pubblica condivisa.

**Per distribuire sia l'elenco di revoche dell'organizzazione che l'elenco Microsoft**
1.  Per distribuire l'elenco di revoche dell'organizzazione, seguire le istruzioni in “[Distribuzione di elenchi di revoche](https://technet.microsoft.com/e331338b-66d4-45e4-8d3f-acccf2302ac4)” precedentemente in questo argomento.

2.  Scaricare il pacchetto dell'elenco di revoche Microsoft e distribuirlo in tutti i computer client dell'organizzazione tramite un metodo, ad esempio Criteri di gruppo o Systems Management Server (SMS). In alternativa, è possibile copiare le voci dall'elenco di revoche Microsoft in quello dell'organizzazione e distribuire soltanto l'elenco di revoche dell'organizzazione.

| ![](images/Cc747702.Caution(WS.10).gif)Attenzione                                                                                                                                                                                                                                                                                                                                              |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft rappresenta un'entità nella catena di trust di tutti i certificati e le licenze emessi da RMS. Un elenco di revoche emesso da Microsoft ha pertanto effetto per tutte le richieste di binding per le quali viene ottenuta una licenza d'uso in base a un modello di criteri per i diritti che richieda l'elenco di revoche aziendale. L'elenco di revoche Microsoft viene inoltre registrato nel computer client. |

**Per distribuire un solo elenco di revoche Microsoft**
1.  Scaricare il pacchetto dell'elenco di revoche Microsoft.

2.  Modificare eventuali modelli di criteri per i diritti esistenti oppure, qualora non ve ne siano, crearne uno che richieda la revoca. Utilizzare la chiave pubblica Microsoft quando si specifica la condizione di revoca.

3.  Impostare l'intervallo di aggiornamento su un valore molto alto, ad esempio 50.000, per fare in modo che un elenco di revoche pubblicato da Microsoft non scada mai. Per le licenze d'uso distribuite, non è pertanto necessaria una nuova versione dell'elenco di revoche Microsoft nel caso in cui non ve ne siano di disponibili.

4.  Copiare il file dell'elenco di revoche in un server Web accessibile. Poiché gli utenti potrebbero utilizzare i contenuti protetti al di fuori dell'organizzazione, al percorso specificato devono potere accedere tutti gli utenti, sia dall'interno che dall'esterno della rete.

5.  È necessario rendere disponibile l'elenco di revoche, in quanto la distribuzione del file dell'elenco di revoche nei computer client potrebbe richiedere una certa quantità di tempo. Per tale motivo, l'elenco di revoche potrebbe non essere presente localmente nel computer di un utente quando questi tenta di aprire un documento con una licenza d'uso che richieda la revoca. Se l'elenco di revoche non è presente nel computer client, può essere scaricato tramite l'applicazione abilitata per RMS dal percorso specificato.

6.  Nel modello di criteri per i diritti, specificare l'URL in cui è disponibile l'elenco di revoche. Per ulteriori informazioni sulla configurazione dei modelli di criteri per i diritti, vedere "[Creazione e modifica dei modelli di criteri per i diritti](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)", più avanti in questo argomento.

7.  In alternativa, è possibile distribuire il pacchetto dell'elenco di revoche nei computer client tramite un metodo, ad esempio Criteri di gruppo o SMS. Gli utenti potranno quindi aprire i contenuti protetti con RMS che richiedono elenchi di revoche, anche qualora non siano connessi alla rete.
