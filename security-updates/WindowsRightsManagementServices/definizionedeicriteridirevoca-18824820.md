---
TOCTitle: Definizione dei criteri di revoca
Title: Definizione dei criteri di revoca
ms:assetid: 'e2fffe9f-def7-439b-a8aa-43f8a065813d'
ms:contentKeyID: 18824820
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747782(v=WS.10)'
---

Definizione dei criteri di revoca
=================================

Per la definizione dei criteri di revoca aziendali, sono necessarie un'analisi e una pianificazione attente in quanto, sebbene l'implementazione delle revoche offra una maggiore protezione dei contenuti, essa potrebbe tuttavia impedire agli utenti l'utilizzo dei contenuti stessi. I criteri di revoche per la distribuzione di RMS possono essere definiti dal sito Web Amministrazione.

Revoche di terze parti
----------------------

Poiché per le singole distribuzioni di RMS il certificato concessore di licenze server del server di certificazione principale viene emesso dal Servizio di Enrollment Microsoft, tale certificato può essere revocato da Microsoft. Tuttavia, il certificato concessore di licenze server verrà revocato da Microsoft solo a seguito di ordinanza da parte di un tribunale.

Oltre al Servizio di Enrollment Microsoft, è possibile specificare una terza parte autorizzata a revocare il certificato concessore di licenze server del server di RMS in uso. Tale terza parte può essere rappresentata da un'entità esterna o da una coppia di chiavi pubbliche o private generate dall'amministratore per conto dell'organizzazione. La chiave privata della terza parte specificata può essere utilizzata per firmare un elenco di revoche che consenta di revocare il certificato concessore di licenze server. La terza parte viene specificata tramite la chiave pubblica relativa durante il provisioning di RMS. I modelli di criteri per i diritti del server possono inoltre essere configurati in modo da consentire a terze parti di revocare contenuti, file manifesti dell'applicazione, licenze e certificati emessi dall'installazione di RMS. Per ulteriori informazioni, vedere “[Creazione e modifica dei modelli di criteri per i diritti](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)”, più avanti in questo argomento.

| ![](images/Cc747782.Important(WS.10).gif)Importante                                                                                                                                     |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Qualora si decida di generare una coppia di chiavi da utilizzare per la revoca del certificato concessore di licenze server del server di certificazione principale, è consigliabile conservarla in un luogo sicuro. |

La revoca di un certificato concessore di licenze server rappresenta una decisione importante, in quanto revocando tale certificato tutti i certificati e le licenze emessi dall'installazione di RMS non sono più validi. Per ulteriori informazioni sulla revoca dei certificati concessori di licenze server, vedere “[Revoca dei certificati concessore di licenze server](https://technet.microsoft.com/8020861d-d196-4431-8282-044675ef5616)”, più avanti in questo argomento.

Valutazione degli effetti degli elenchi di revoche
--------------------------------------------------

Quando viene richiesta la revoca per una determinata parte di contenuto protetto, nel caso venga soddisfatta la condizione specificata, verranno utilizzati e avranno efficacia tutti gli elenchi di revoche registrati nei computer client. È pertanto necessario fare attenzione nell'implementare le revoche, in quanto con l'implementazione nei computer client vengono registrati gli elenchi di revoche, che potrebbero avere un effetto più esteso di quanto non si desideri. Per ulteriori informazioni sulla configurazione di questa opzione, vedere “[Creazione e modifica dei modelli di criteri per i diritti](https://technet.microsoft.com/6014176f-ef71-4d29-b3e3-da129c18563d)”, più avanti in questo argomento.

Bilanciamento tra protezione e utilizzo
---------------------------------------

Quando si specifica un criterio di revoca in un modello di criteri per i diritti, è necessario prendere in considerazione l'esigenza di maggiore protezione dei contenuti mettendola però in relazione con l'eventualità che gli utenti incontrino problemi durante l'utilizzo di tali contenuti, come descritto nell'esempio seguente.

Durante l'impostazione di un elenco di revoche in un modello di criteri per i diritti, per l'elenco viene specificato un intervallo di aggiornamento. Per utilizzare i contenuti pubblicati utilizzando tale modello di criteri per i diritti, è necessario che nel computer dell'utente sia presente un elenco di revoche e che tale elenco non sia precedente all'intervallo di aggiornamento specificato. Se ad esempio l'intervallo di aggiornamento è impostato su 10, l'elenco di revoche deve essere stato creato negli ultimi dieci giorni. Se nel computer client non è presente un elenco di revoche oppure se la data di creazione dell'elenco è precedente all'intervallo di aggiornamento, tramite l'applicazione abilitata per RMS verrà cercato l'elenco di revoche più recente nel percorso specificato nella licenza d'uso. Se un utente non è connesso alla rete, non sarà tuttavia possibile ottenere l'elenco di revoche aggiornato e quindi potrebbe non essere possibile utilizzare il contenuto.

Per limitare il problema, attenersi ai suggerimenti riportati di seguito.

-   Fare attenzione quando si specifica l'intervallo di aggiornamento per un elenco di revoche e assicurarsi che gli utenti possano sempre accedere in modo immediato a un elenco di revoche aggiornato.
-   Mantenere gli elenchi di revoche sotto forma di URL accessibili sia dall'interno che dall'esterno della rete aziendale.
-   Utilizzare Microsoft® Systems Management Server (SMS) o un meccanismo simile per distribuire copie aggiornate degli elenchi di revoche a ogni computer client a intervalli definiti, ad esempio ogni notte.
-   Richiedere la revoca solo per i tipi di documenti maggiormente riservati.
