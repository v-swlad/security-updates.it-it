---
TOCTitle: 'FAQ - RMS: Problematiche relative alla protezione'
Title: 'FAQ - RMS: Problematiche relative alla protezione'
ms:assetid: 'ff433834-79aa-481f-bd39-3393be12a26f'
ms:contentKeyID: 18824844
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747757(v=WS.10)'
---

FAQ - RMS: Problematiche relative alla protezione
=================================================

FAQ - Problematiche relative alla protezione di RMS
---------------------------------------------------

-   [Qual è l'account utente con privilegi avanzati?](#bkmk_43)
-   [RMS è una soluzione per la protezione?](#bkmk_44)
-   [Quali meccanismi sono disponibili per impedire ai destinatari di far scorrere all'indietro l'orologio del proprio computer per estendere l'accesso a un documento protetto con RMS dopo che la licenza d'uso è scaduta?](#bkmk_45)
-   [È possibile che i membri del gruppo Domain Admins possano leggere i documenti destinati a qualcun altro nel dominio di appartenenza?](#bkmk_46)
-   [Sapendo che ogni archivio protetto può autenticare ogni certificato o licenza di pubblicazione generata all'interno del sistema, come se provenisse da un servizio registrato presso Microsoft, contro quali minacce si ottiene protezione?](#bkmk_47)
-   [Se qualcuno riesce ad aprire un documento utilizzando un attacco di forza bruta, questo permette l'apertura di altri documenti con la stessa chiave?](#bkmk_48)
-   [A causa delle limitazioni sulle esportazioni di tecnologie di crittografia, esistono parti delle chiavi esposte al di fuori dall'organizzazione che le ha distribuite?](#bkmk_49)
-   [Come si impedisce ad aggressori malintenzionati di attivare da una postazione remota la funzionalità di rimozione della autorizzazioni?](#bkmk_50)
-   [Un utente può catturare schermate di contenuto protetto con RMS?](#bkmk_51)
-   [Gli amministratori che eseguono il backup dei file correlati a RMS possono accedere al contenuto protetto con RMS?](#bkmk_52)
-   [Il file di scambio utilizzato da Windows contiene in qualche momento il contenuto non crittografato, lasciando potenzialmente "aperto" il contenuto?](#bkmk_53)
-   [È possibile limitare il numero degli amministratori che possono accedere alle funzionalità amministrative di RMS?](#bkmk_54)
-   [RMS può proteggere singoli documenti non appena vengono creati, sul disco rigido dell'utente o su una cartella condivisa?](#bkmk_55)
-   [Aprendo un file, il file Autosave e i file Temp sono crittografati?](#bkmk_56)
-   [Quando si riceve posta elettronica protetta con RMS, sembra che sia presente un allegato. Si riesce a salvare l'allegato anche se la posta non può presumibilmente essere salvata. Si è verificato un problema con RMS?](#bkmk_562)

<span id="BKMK_43"></span>
#### Qual è l'account utente con privilegi avanzati?

RMS supporta un gruppo di utenti con privilegi avanzati che ha il controllo completo su tutto il contenuto protetto con RMS. I membri del gruppo di utenti con privilegi avanzati dispongono di diritti completi per tutte le licenze d'uso emesse dal cluster RMS in cui è configurato il gruppo. Di conseguenza, i membri di questo gruppo possono decrittografare qualsiasi file protetto e rimuoverne la protezione. I membri del gruppo possono, ad esempio, rimuovere la protezione dai file pubblicati da un ex dipendente per consentirne la pubblicazione e la gestione da parte di un nuovo proprietario.

<span id="BKMK_44"></span>
#### RMS è una soluzione per la protezione?

No, RMS non è una soluzione per la protezione. Quando si utilizza con un'applicazione abilitata per RMS, come Office 2007, può essere considerato una "soluzione per l'imposizione di criteri". Se non è autorizzato a visualizzare i dati, l'utente potrebbe utilizzare un attacco di forza bruta per tentare di decifrare la crittografia. La crittografia è affidabile, ma può essere decifrata come tutti gli schemi di crittografia software. Tuttavia, se l'utente ha il diritto di visualizzare i dati, potrebbe copiarli a mano o catturarne un'immagine digitale per fornire le informazioni a utenti non autorizzati.

<span id="BKMK_45"></span>
#### Quali meccanismi sono disponibili per impedire ai destinatari di far scorrere all'indietro l'orologio del proprio computer per estendere l'accesso a un documento protetto con RMS dopo che la licenza d'uso è scaduta?

RMS rileva se l'orologio di un sistema client viene fatto scorrere all'indietro o in avanti e impedisce all'utente di accedere al contenuto. Inoltre, RMS rileva se esiste una differenza di orario misurabile tra il server e il client RMS.

<span id="BKMK_46"></span>
#### È possibile che i membri del gruppo Domain Admins possano leggere i documenti destinati a qualcun altro nel dominio di appartenenza?

I membri del gruppo Domain Admins possono leggere il contenuto protetto di un account utente se sono membri del gruppo di utenti RMS con privilegi avanzati oppure se impersonano l'account dell'utente. Poiché i componenti del gruppo Domain Admins hanno il controllo sugli account utente del dominio, non esiste alcun modo per attenuare i rischi relativi a uno scenario in cui un membro del gruppo Domain Admins non è affidabile.

Secondo le procedure ottimali, è necessario aggiungere i membri del gruppo Domain Admins al gruppo degli utenti con privilegi avanzati solo se devono poter accedere al contenuto protetto con RMS. Quando viene concessa una licenza di pubblicazione a un membro del gruppo di utenti con privilegi avanzati, nel registro degli eventi dell'applicazione del server RMS viene registrato un ID evento 49. L'ID evento 49 segnala **"È stata concessa una licenza d'uso a un utente appartenente al gruppo di utenti con privilegi avanzati. L'utente dispone dell'indirizzo di posta elettronica seguente: &lt;Alias utenti&gt;"** dove **Alias utenti** viene sostituito con l'account di posta elettronica dell'utente.

Come accade con altri gruppi utilizzati per limitare l'accesso alle risorse, è necessario definire gli allarmi ed eseguire controlli della protezione per cercare di impedire che qualcuno si unisca senza autorizzazione al gruppo degli utenti con privilegi avanzati.

<span id="BKMK_47"></span>
#### Sapendo che ogni archivio protetto può autenticare ogni certificato o licenza di pubblicazione generata all'interno del sistema, come se provenisse da un servizio registrato presso Microsoft, contro quali minacce si ottiene protezione?

Senza poter verificare l'integrità dei certificati, un utente potrebbe falsificare un certificato per account con diritti (RAC) emesso per un altro utente e ottenere una licenza d'uso per il contenuto oppure creare un'applicazione che rimuova la protezione da un documento.

<span id="BKMK_48"></span>
#### Se qualcuno riesce ad aprire un documento utilizzando un attacco di forza bruta, questo permette l'apertura di altri documenti con la stessa chiave?

Ogni porzione di contenuto protetto con RMS è crittografata con una chiave simmetrica diversa, generata in modo casuale. Quindi, la chiave di ogni documento è univoca e inutile per decrittografare altri documenti.

<span id="BKMK_49"></span>
#### A causa delle limitazioni sulle esportazioni di tecnologie di crittografia, esistono parti delle chiavi esposte al di fuori dall'organizzazione che le ha distribuite?

Le applicazioni firmate nella directory principale di Microsoft sono soggette alla directory principale di firma delle chiavi Microsoft, ma da quel momento in poi, nessun'altra chiave viene divulgata da Microsoft o dalla distribuzione di un cliente.

<span id="BKMK_50"></span>
#### Come si impedisce ad aggressori malintenzionati di attivare da una postazione remota la funzionalità di rimozione della autorizzazioni?

L'aggressore avrebbe bisogno delle credenziali di un account utente con diritti amministrativi per il cluster RMS. Per impostazione predefinita, l'interfaccia di gestione RMS è disponibile solo localmente sul server RMS. Mantenendo queste condizioni, mantenendo disabilitato Remote Desktop Protocol (RDP) e proteggendo fisicamente il server, il rischio di protezione risulterà attenuato.

<span id="BKMK_51"></span>
#### Un utente può catturare schermate di contenuto protetto con RMS?

Se i diritti di RMS sono impostati in modo da non consentire la copia, RMS disabilita la combinazione di tasti Alt+PrtSc di Windows. Tuttavia, in un ambiente con desktop non gestiti, un utente potrebbe utilizzare prodotti non Microsoft per catturare il contenuto.

<span id="BKMK_52"></span>
#### Gli amministratori che eseguono il backup dei file correlati a RMS possono accedere al contenuto protetto con RMS?

No, possono eseguire il backup ma non possono ottenere l'accesso.

<span id="BKMK_53"></span>
#### Il file di scambio utilizzato da Windows contiene in qualche momento il contenuto non crittografato, lasciando potenzialmente "aperto" il contenuto?

Una volta che il client RMS invia il contenuto decrittografato all'applicazione, questo potrebbe essere visualizzato nel file di scambio. Parte delle raccomandazioni per lo sviluppo di applicazioni RMS nel Software Development Kit (SDK) dei Rights Management Services (RMS) includono le operazioni necessarie per evitare l'evenienza, ma questo compito grava comunque sull'applicazione abilitata per RMS.

<span id="BKMK_54"></span>
#### È possibile limitare il numero degli amministratori che possono accedere alle funzionalità amministrative di RMS?

Sì, è possibile creare un diverso gruppo RMS Admin in Active Directory, aggiungervi utenti e creare quindi l'elenco di controllo di accesso appropriato (ACL) per le pagine di amministrazione. Ad esempio, la configurazione predefinita degli ACL della pagina Web di amministrazione RMS specifica che alla pagina delle impostazioni di protezione può accedere solo l'utente che ha eseguito il provisioning del server.

<span id="BKMK_55"></span>
#### RMS può proteggere singoli documenti non appena vengono creati, sul disco rigido dell'utente o su una cartella condivisa?

Benché RMS possa essere utilizzato per proteggere i documenti memorizzati nel computer locale di un utente, resta da preferire Crittografia file system (EFS). EFS protegge i documenti in modo trasparente, mentre RMS richiede l'intervento manuale (un paio di clic del mouse) per proteggere un documento.

<span id="BKMK_56"></span>
#### Aprendo un file, il file Autosave e i file Temp sono crittografati?

Sì, tutti i file temporanei sono crittografati.

<span id="BKMK_562"></span>
#### Quando si riceve posta elettronica protetta con RMS, sembra che sia presente un allegato. Si riesce a salvare l'allegato anche se la posta non può presumibilmente essere salvata. Si è verificato un problema con RMS?

No. Questo è un comportamento previsto. L'allegato che si vede è il messaggio crittografato prima che il client RMS lo abbia decrittografato. È ancora protetto con RMS e non può essere salvato dopo essere stato decrittografato.
