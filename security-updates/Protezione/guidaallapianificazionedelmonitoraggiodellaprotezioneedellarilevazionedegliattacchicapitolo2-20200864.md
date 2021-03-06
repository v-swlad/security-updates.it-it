---
TOCTitle: 'Guida alla pianificazione del monitoraggio della protezione e della rilevazione degli attacchi - Capitolo 2'
Title: 'Guida alla pianificazione del monitoraggio della protezione e della rilevazione degli attacchi - Capitolo 2'
ms:assetid: '2f3dc724-b318-4a49-a3f2-1374cb0187e3'
ms:contentKeyID: 20200864
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536265(v=TechNet.10)'
---

Guida alla pianificazione del monitoraggio della protezione e della rilevazione degli attacchi
==============================================================================================

### Capitolo 2 - Strategie di monitoraggio della protezione

Aggiornato: 23 maggio 2005

##### In questa pagina

[](#edaa)[Introduzione](#edaa)
[](#ecaa)[Implementazione del monitoraggio della protezione](#ecaa)
[](#ebaa)[Correlazione degli eventi di controllo della protezione](#ebaa)
[](#eaaa)[Soluzioni di fornitori di software indipendenti (ISV)](#eaaa)

### Introduzione

Nessuna azienda potrebbe pensare di svolgere la propria attività senza sistemi di sicurezza adeguati, ad esempio serrature, sistemi di allarme, videocamere di sorveglianza, recinzioni o, in alcuni casi, personale di sicurezza. Molte aziende, tuttavia, stanno iniziando a comprendere l'importanza di disporre di misure di sicurezza analoghe per la protezione delle risorse di rete dagli attacchi esterni e dalle intrusioni interne.

Sistemi di sicurezza quali videocamere e sensori di movimento consentono di rilevare eventuali tentativi di accesso a un edificio o a un'area riservata. Le organizzazioni, tuttavia, hanno anche la necessità di implementare sistemi in grado di monitorare le risorse di rete e di rilevare eventuali attacchi da parte di utenti malintenzionati. Il monitoraggio della protezione costituisce quindi un fattore estremamente importante per una strategia di protezione della rete efficace.

Nell'agosto 2004 i servizi segreti degli Stati Uniti, in collaborazione con il CERT Coordination Center del Carnegie Mellon University Software Engineering Institute, hanno rilasciato un white paper in cui sono documentati alcuni casi di organizzazioni che sono risultate vulnerabili a tentativi di frode commessi da dipendenti interni. Per ulteriori informazioni, vedere il white paper "[Insider Threat Study: Illicit Cyber Activity in the Banking and Finance Sector](http://www.secretservice.gov/ntac/its_report_040820.pdf)" all'indirizzo http://www.secretservice.gov/ntac/its\_report\_040820.pdf (informazioni in lingua inglese).

Questa minaccia è stata resa ancora più evidente dal sondaggio 2004 E-Crime, a cui hanno partecipato enti governativi e organizzazioni che operano nei settori bancario, finanziario, dell'informazione e delle telecomunicazioni. Questo sondaggio ha rivelato che il 43% degli intervistati ha riscontrato un aumento nel numero dei crimini elettronici e delle intrusioni per acquisizione illecita di dati e che il 70% ha subito almeno un crimine elettronico nell'anno precedente, con un costo totale per tutti gli intervistati di oltre 600 milioni di dollari.

La continua crescita delle normative aziendali, unita alla maggiore consapevolezza delle minacce legate agli utenti malintenzionati, sia interni che esterni, ha contribuito all'aumento delle richieste di implementazione di un sistema di monitoraggio della protezione efficace. Per una pianificazione efficace del monitoraggio della protezione, è necessario conoscere le tecnologie attualmente disponibili per l'implementazione della soluzione. In questo capitolo vengono illustrate le tecnologie Microsoft che rendono possibile il monitoraggio della protezione e consentono di mettere in relazione i registri di protezione a scopo di analisi e archiviazione.

**Nota: **in questo documento viene fatta distinzione tra attacchi interni ed esterni. Per attacco interno si intende un attacco messo in atto da un dipendente, in genere un amministratore. Al contrario, un attacco esterno proviene dall'esterno dell'organizzazione. Sebbene la diffusione di tecnologie di connessione avanzate, ad esempio le reti senza fili, renda possibile agli utenti malintenzionati esterni di sferrare attacchi dall'interno del perimetro della rete, questi sono ancora considerati attacchi esterni.

[](#mainsection)[Inizio pagina](#mainsection)

### Implementazione del monitoraggio della protezione

A partire da Microsoft Windows NT® versione 3.1, gli eventi di protezione vengono memorizzati nell'apposito file registro integrato disponibile in tutte le versioni di Microsoft® Windows®. Questo file è essenziale per il monitoraggio della protezione nelle reti basate su Windows. Sono infatti disponibili utilità e programmi aggiuntivi in grado di mettere in relazione questi eventi registrati e di inserirli in un archivio centrale.

Per la registrazione dei dati di monitoraggio della protezione nel file registro eventi protezione viene utilizzato un formato di database personalizzato. Per visualizzare alcune parti di questo file, ad esempio i nomi dei computer e gli indirizzi IP, è possibile utilizzare un normale editor di testo. Tuttavia, per poter leggere tutte le informazioni contenute nei registri di protezione è necessario utilizzare un apposito programma, ad esempio la console del Visualizzatore eventi. Il file registro eventi protezione (SecEvent.evt) si trova nella directory %systemroot%\\System32\\config. A differenza del registro applicazioni e del registro eventi di sistema, le autorizzazioni predefinite del file system NTFS consentono l'accesso a questo file soltanto ai membri del gruppo Administrators e all'account di sistema.

Nel registro eventi protezione vengono registrati due tipi di evento: le operazioni riuscite e le operazioni non riuscite. Un evento di operazione riuscita indica che un'operazione eseguita da un utente, un servizio o un programma è stata completata correttamente. Un evento di operazione non riuscita indica che un'operazione non è stata completata correttamente. Se ad esempio si attivano i controlli per gli eventi di accesso non riuscito, nel registro eventi protezione verranno registrati tutti i tentativi di accesso non riusciti.

**Nota: **in Microsoft** **Windows Server™ 2003 con Service Pack 1 è possibile configurare livelli di controllo della protezione diversi per utenti differenti. Per ulteriori informazioni su questa funzionalità, vedere il Capitolo 4 "Progettazione della soluzione".

Nella seguente tabella sono elencate le categorie degli eventi di protezione insieme agli eventi registrati da ciascuna categoria.

**Tabella 2.1. Categorie di controllo degli eventi di protezione**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Categoria</th>
<th style="border:1px solid black;" >Effetto</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Eventi di accesso account</td>
<td style="border:1px solid black;">Vengono controllati i tentativi di accesso di un account locale su un computer. Se l'account utente è un account di dominio, questo evento viene riportato anche sul controller di dominio.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Gestione account</td>
<td style="border:1px solid black;">Vengono controllate la creazione, la modifica e l'eliminazione degli account utente e di gruppo, insieme alle operazioni di modifica e di reimpostazione delle password.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Accesso al servizio directory</td>
<td style="border:1px solid black;">Viene controllato l'accesso agli oggetti nel servizio directory Active Directory®.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Eventi di accesso</td>
<td style="border:1px solid black;">Vengono controllati i tentativi di accesso alle workstation e ai server membri.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Accesso agli oggetti</td>
<td style="border:1px solid black;">Vengono controllati i tentativi di accesso a un oggetto, ad esempio un file, una cartella, una chiave del Registro di sistema o una stampante, per il quale sono state definite impostazioni di controllo all'interno del relativo elenco di controllo di accesso di sistema (SACL).</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Modifica dei criteri</td>
<td style="border:1px solid black;">Vengono controllate le modifiche apportate ai criteri di assegnazione dei diritti utente, ai criteri di controllo, ai criteri di account o ai criteri di attendibilità.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Uso dei privilegi</td>
<td style="border:1px solid black;">Vengono controllate tutte le istanze in cui un utente esercita un diritto utente, ad esempio per la modifica dell'ora di sistema.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Tracciato processo</td>
<td style="border:1px solid black;">Viene controllato il comportamento di un'applicazione, ad esempio l'avvio o la chiusura di un programma.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Eventi di sistema</td>
<td style="border:1px solid black;">Vengono controllati gli eventi di sistema relativi al computer, ad esempio l'avvio e la chiusura, nonché gli eventi che influiscono sulla protezione del sistema o sul registro di protezione.</td>
</tr>
</tbody>
</table>
  
Le impostazioni Criteri di controllo in Criteri di gruppo consentono di controllare quali eventi creano voci nei registri di protezione. Il percorso di queste impostazioni è Configurazione computer\\Impostazioni di Windows\\Impostazioni protezione\\Criteri locali. Le impostazioni Criteri di controllo possono essere configurate tramite la console Impostazioni protezione locale oppure a livello di sito, dominio e unità organizzativa tramite Criteri di gruppo e Active Directory.
  
I registri di protezione forniscono una base iniziale adeguata per un monitoraggio della protezione completo. Le impostazioni Criteri di gruppo consentono infatti di configurare in maniera centralizzata i livelli di controllo dei registri di protezione, mentre le impostazioni di protezione predefinite consentono l'accesso ai registri di protezione soltanto agli amministratori. Tuttavia, per il monitoraggio di attacchi distribuiti e l'implementazione dell'analisi legale è necessario un sistema di monitoraggio in grado di mettere in relazione gli eventi di controllo a livello centralizzato.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Correlazione degli eventi di controllo della protezione
  
Per consentire la correlazione degli eventi di controllo della protezione è necessario raccogliere gli eventi di protezione da più computer e collocare tali informazioni in una posizione centrale. Tali informazioni possono essere quindi analizzate dal personale per la protezione allo scopo di individuare eventuali violazioni della protezione o attacchi esterni. Questo archivio può inoltre essere utilizzato come base di partenza per l'analisi legale. In questa sezione vengono illustrati i prodotti Microsoft che possono essere utilizzati per mettere in relazione più registri eventi protezione. Per eseguire queste funzioni è possibile utilizzare anche alcuni prodotti di terze parti.
  
#### Event Comb MT
  
Event Comb MT (multithread) è un componente di Windows Server 2003 Security Guide che consente di analizzare e raccogliere eventi da più registri di eventi su computer diversi. Event Comb MT viene eseguito come applicazione multithread e consente di specificare numerosi parametri relativi all'analisi dei registri di eventi, ad esempio:
  
-   Uno o più ID evento
  
-   Intervalli di ID evento
  
-   Origini evento
  
-   Testo dell'evento specifico
  
-   Durata dell'evento in minuti, ore o giorni
  
In Event Comb sono integrate alcune categorie di ricerca specifiche, ad esempio i blocchi account, che possono essere utilizzate per effettuare una ricerca dei seguenti eventi:
  
-   529: accesso non riuscito (nome utente o password non validi)
  
-   644: blocco automatico di un account utente
  
-   675: preautenticazione non riuscita in un controller di dominio (password non corretta)
  
-   676: richiesta ticket di autenticazione non riuscita
  
-   681: accesso non riuscito
  
Se si desidera effettuare una ricerca per individuare eventuali attacchi nei confronti dell'account Administrator predefinito, è possibile aggiungere l'evento 12294 (superamento del limite di blocchi dell'account) dal registro eventi di sistema. Questo evento è particolarmente importante, poiché il limite di blocchi dell'account non viene applicato all'account Administrator predefinito. Di conseguenza, un utente malintenzionato può effettuare più tentativi per compromettere l'account Administrator predefinito senza che venga attivato il meccanismo di blocco dell'account.
  
**Nota: **l'evento 12294 viene riportato come evento di gestione account di protezione (SAM) nel registro eventi di sistema ma non nel registro di protezione.
  
Event Comb MT consente di salvare gli eventi in una tabella di un database di Microsoft SQL Server™, che può essere quindi utilizzata per l'analisi e l'archiviazione a lungo termine. Per l'accesso alle informazioni nelle tabelle di SQL Server è possibile utilizzare diversi programmi client, ad esempio SQL Query Analyzer, Microsoft Visual Studio® .NET o alcune utilità di terze parti.
  
In Event Comb MT versione 10.0 sono inoltre disponibili opzioni della riga di comando che possono essere utilizzate per la creazione di script, in modo da automatizzare la raccolta di eventi dai registri di protezione a intervalli regolari. Poiché non fornisce alcun tipo di agente di raccolta client né consente di inoltrare automaticamente gli eventi a un archivio centrale, Event Comb MT potrebbe non essere appropriato per tutti gli scenari di individuazione delle minacce.
  
Event Comb MT può essere scaricato gratuitamente dal sito Web [Account Lockout and Management Tools](http://www.microsoft.com/downloads/details.aspx?displaylang=en&familyid=7af2e69c-91f3-4e63-8629-b999adde0b9e) all'indirizzo http://www.microsoft.com/downloads/details.aspx?displaylang=en&familyid=7af2e69c-91f3-4e63-8629-b999adde0b9e (informazioni in lingua inglese).
  
[Windows Server 2003 Security Guide](http://www.microsoft.com/downloads/details.aspx?familyid=8a2643c1-0685-4d89-b655-521ea6c7b4db) è disponibile all'indirizzo http://www.microsoft.com/downloads/details.aspx?FamilyId=8A2643C1-0685-4D89-B655-521EA6C7B4DB (informazioni in lingua inglese).
  
#### Microsoft Operations Manager 2005
  
Microsoft Operations Manager (MOM) consente di monitorare più server all'interno di un'azienda. L'agente MOM raccoglie gli eventi dai registri di eventi e li inoltra al server di gestione MOM, che quindi li inserisce nel database MOM. Con MOM 2005 e versioni successive è possibile raccogliere gli eventi anche da computer in cui non sono in esecuzione agenti MOM.
  
MOM utilizza regole di gestione proprie per individuare i problemi che possono avere impatto sull'efficienza operativa dei server. È possibile comunque definire regole aggiuntive per individuare determinati eventi e, nel caso in cui tali eventi si verifichino, per inviare notifiche immediate tramite posta elettronica, messaggi popup o un avviso a un cercapersone.
  
Sebbene metta a disposizione numerose funzioni utili per il monitoraggio della protezione e la rilevazione degli attacchi, MOM non è stato progettato a questo scopo. È possibile, tuttavia, che nelle versioni future di MOM vengano fornite alcune funzionalità avanzate per la raccolta dei registri di protezione.
  
[](#mainsection)[Inizio pagina](#mainsection)
  
### Soluzioni di fornitori di software indipendenti (ISV)
  
I prodotti Microsoft non forniscono una soluzione end-to-end in grado di coprire tutti gli aspetti legati al monitoraggio della protezione. Di seguito sono indicate le principali lacune che possono essere riscontrate negli attuali prodotti Microsoft:
  
-   Avvisi in tempo reale sui registri eventi.
  
-   Sistemi per la raccolta dei registri eventi protetti.
  
Per colmare queste lacune è possibile utilizzare i seguenti prodotti sviluppati da partner Microsoft (elencati in ordine alfabetico):
  
-   **EventReporter di Adiscon.** EventReporter consente agli amministratori di combinare in un unico ambiente le funzioni per la generazione degli avvisi e dei report sui registri eventi che sono disponibili negli ambienti UNIX e Windows. Questa applicazione supporta il protocollo syslog standard di UNIX per l'integrazione con i sistemi basati su UNIX e il protocollo SMTP (Simple Mail Transfer Protocol) per l'inoltro degli avvisi. In EventReporter è incluso un agente che può essere configurato per raccogliere gli eventi di protezione da più computer, filtrarli e inserirli in un database. A seconda dell'evento di protezione, è possibile quindi inoltrare tali eventi tramite posta elettronica, avviare applicazioni, creare messaggi di rete, e così via. Per ulteriori informazioni su Adiscon EventReporter, visitare il sito Web [EventReporter](http://www.eventreporter.com/) all'indirizzo www.eventreporter.com (informazioni in lingua inglese).
  
-   **GFI LANguard Security Event Log Monitor di GFI.** LANguard Security Event Log Monitor consente di rilevare eventuali tentativi di intrusione mediante l'analisi dei registri eventi e di gestire i registri eventi nell'ambito dell'intera rete. Con questa applicazione è possibile archiviare e analizzare i registri di eventi di tutti i computer nella rete, nonché inviare un avviso in tempo reale per segnalare problemi di protezione, attacchi e altri eventi critici. I registri di eventi possono inoltre essere archiviati in un database centralizzato e vengono forniti regole e report personalizzati per l'analisi legale. Per ulteriori informazioni, visitare il sito Web [GFI LANguard Security Event Log Monitor](http://www.gfi.com/lanselm/) all'indirizzo www.gfi.com/lanselm (informazioni in lingua inglese).
  
-   **Systrack 3 di Lakeside Software, Inc.** Systrack 3 utilizza la funzionalità Event Log Monitor per generare avvisi quasi in tempo reale sui registri eventi. Tale funzionalità analizza periodicamente tutti i registri di eventi in un computer per determinare eventuali variazioni rispetto all'ultima analisi. Systrack 3 filtra qualsiasi nuovo evento rilevato ed esegue automaticamente l'azione appropriata. È possibile utilizzare le impostazioni predefinite di questi filtri, specificarne di nuove oppure utilizzare una combinazione di impostazioni predefinite e di impostazioni definite dall'utente. Gli avvisi sui registri eventi possono essere attivati da specifiche stringhe di caratteri presenti in una qualsiasi delle proprietà degli eventi, ad esempio il nome di un utente o di una workstation. Un evento può anche determinare l'esecuzione di uno script o il riavvio del computer. I filtri possono inoltre generare trap SNMP (Simple Network Management Protocol), messaggi popup di Windows o avvisi da inviare tramite posta elettronica. Per ulteriori informazioni su Systrack 3, visitare il sito Web [Lakeside Software](http://www.lakesidesoftware.com/) all'indirizzo www.lakesidesoftware.com (informazioni in lingua inglese).
  
##### Download
  
[![](images/Dd536265.icon_exe(it-it,TechNet.10).gif)Guida alla pianificazione del monitoraggio della protezione e della rilevazione degli attacchi](http://go.microsoft.com/fwlink/?linkid=41310)
  
[](#mainsection)[Inizio pagina](#mainsection)
