---
TOCTitle: Esclusione di applicazioni
Title: Esclusione di applicazioni
ms:assetid: 'b68ae4b2-b9ba-44ae-90cb-c88df600ec86'
ms:contentKeyID: 18824747
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747644(v=WS.10)'
---

Esclusione di applicazioni
==========================

È possibile specificare una versione di un'applicazione abilitata per RMS con la quale devono essere messe a confronto tutte le richieste di licenze. L'esclusione basata sulle applicazioni prevede che ogni licenza d'uso contenga una condizione che preveda che la licenza possa essere associata solo ai contenuti protetti con RMS per i quali è stata emessa, nel caso in cui l'applicazione da cui la licenza è stata richiesta non sia presente nell'elenco delle applicazioni escluse.

Questo metodo può, ad esempio, risultare utile quando in un'organizzazione viene distribuito un aggiornamento per la protezione di un'applicazione. Gli amministratori di sistema possono utilizzare il consueto meccanismo affinché nei computer client venga installato l'aggiornamento per la protezione. È possibile impostare criteri di esclusione delle applicazioni definiti utilizzando le informazioni sulla versione dell'applicazione che sta utilizzando il sito Web Amministrazione. Tramite questo criterio di esclusione da RMS, non vengono emesse licenze per i client in cui sono in esecuzione versioni precedenti del software.

Le applicazioni abilitate per RMS vengono escluse in base al nome del file e al numero di versione. Questa operazione può risultare utile per fare in modo che gli utenti installino una versione più recente e più protetta di un'applicazione non appena questa diventa disponibile. In un'organizzazione potrebbe, ad esempio, essere stata distribuita la versione 1.0.4.2315 di un'applicazione abilitata per RMS. Lo sviluppatore dell'applicazione potrebbe avere rilevato un problema di protezione e, di conseguenza, deciso di rilasciare la versione 1.0.4.4200 per eliminare tale problema. Oltre a implementare la nuova versione dell'applicazione, è possibile definire un criterio di esclusione che impedisca agli utenti di utilizzare i contenuti protetti con una versione precedente dell'applicazione.

Come nel caso degli altri tipi di esclusione, è necessario configurare l'esclusione delle applicazioni in ogni cluster in cui si desidera applicarla.

Quando si applica tale criterio di esclusione nel server, i client non possono utilizzare l'applicazione esclusa per la richiesta e l'associazione di nuove licenze d'uso ai contenuti protetti con RMS. I client potranno tuttavia continuare a utilizzare l'applicazione esclusa per utilizzare i file per i quali è stata precedentemente concessa una licenza.

| ![](images/Cc747644.note(WS.10).gif)Nota                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| In RMS, è necessario specificare la versione dell'applicazione con un formato di quattro cifre separate da punti (\#.\#.\#.\# ). Tuttavia, in alcune applicazioni, la versione viene specificata con numeri di due o tre cifre delimitati da punti. In questo caso, inserire .0 dove necessario per rendere compatibile il numero della versione con il formato richiesto da RMS. |
