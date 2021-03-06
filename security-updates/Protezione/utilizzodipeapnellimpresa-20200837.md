---
TOCTitle: 'Utilizzo di PEAP nell''impresa'
Title: 'Utilizzo di PEAP nell''impresa'
ms:assetid: '17d96d47-98a4-4aeb-bd22-a721e337ffe5'
ms:contentKeyID: 20200837
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536238(v=TechNet.10)'
---

Protezione delle reti LAN senza fili con PEAP e password
========================================================

### Appendice A: Utilizzo di PEAP nell'impresa

Aggiornato: 2 aprile 2004

Microsoft® ha realizzato due soluzioni per la protezione delle reti locali senza fili(WLAN). Nella prima soluzione *Securing Wireless LANs — a Certificate Services Solution* (in inglese) vengono utilizzati i certificati client per l'autenticazione dei client senza fili. Questa soluzione è indicata principalmente per le organizzazioni di grandi dimensioni. Nella seconda soluzione, *Protezione delle reti LAN senza fili con PEAP e password* (oggetto della presente guida), vengono utilizzati il protocollo PEAP (Protected Extensible Authentication Protocol) e le password per l'autenticazione dei client senza fili. Questa seconda guida è indicata principalmente per le organizzazioni di piccole e medie dimensioni. Non vi sono controindicazioni, tuttavia, all'utilizzo di PEAP e dell'autenticazione con password per proteggere le reti LAN senza fili delle organizzazioni di grandi dimensioni.

In questa appendice viene descritto come utilizzare le sezioni di entrambe le soluzioni per implementare PEAP con password in un'organizzazione di grandi dimensioni. In entrambe le soluzioni vengono utilizzati la stessa architettura e gli stessi componenti tecnici, quindi è relativamente semplice servirsi del contenuto della prima soluzione, commisurato alle imprese di grandi dimensioni, e sostituire i protocolli di autenticazione basati sui certificati con PEAP con password. Lo scopo è fornire alle organizzazioni di grandi dimensioni linee guida specifiche per una soluzione WLAN per grandi organizzazioni, ad esempio in merito alle funzionalità avanzate per la delega amministrativa, alla registrazione RADIUS e alla separazione dei ruoli dei server, che tuttavia contemplano l'impiego dell'autenticazione basata su password per i client senza fili.

Per motivi di brevità, in questa appendice verrà utilizzato il termine "soluzione EAP-TLS" per fare riferimento alla prima soluzione *Securing Wireless LANs — a Certificate Services Solution* e il termine "soluzione PEAP" per fare riferimento alla seconda soluzione *Protezione delle reti LAN senza fili con PEAP e password*. EAP-TLS (Extensible Authentication Protocol-Transport Layer Security) è il nome del protocollo di autenticazione basata sui certificati client utilizzato nella prima soluzione.

### Elementi necessari della soluzione EAP-TLS

Dal momento che la guida della soluzione EAP-TLS è stata scritta per le organizzazioni di grandi dimensioni, deve essere considerata la guida di riferimento principale. Contiene informazioni di pianificazione, implementazione e operative (ad esempio per l'amministrazione delegata) che riguardano maggiormente le organizzazioni di grandi dimensioni. Dopo la tabella è disponibile un elenco dei capitoli della soluzione EAP-TLS. Per ogni capitolo viene fornita una breve descrizione, in cui è indicato se il contenuto è di rilievo o meno per le linee guida "miste". Viene indicato, inoltre, se al posto delle istruzioni della soluzione EAP-TLS deve essere utilizzato il contenuto della soluzione PEAP.

Nella tabella seguente viene mostrata la correlazione tra i capitoli delle due soluzioni. A causa delle differenze a livello di ambito di applicazione e di utilizzo della tecnologia, non vi è una corrispondenza esatta tra i capitoli.

**Tabella A.1: Corrispondenza tra i capitoli delle soluzioni EAP-TLS e PEAP**

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Soluzione EAP-TLS</th>
<th style="border:1px solid black;" >Soluzione PEAP</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Capitolo 1 Panoramica</td>
<td style="border:1px solid black;">Capitolo 1 Protezione delle reti LAN senza fili con PEAP e password</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 2 Scelta di una strategia di rete senza fili protetta</td>
<td style="border:1px solid black;">Introduzione Scelta di una strategia per la protezione di reti LAN senza fili</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Capitolo 3 Architettura della soluzione di rete LAN senza fili protetta</td>
<td style="border:1px solid black;">Capitolo 2 Pianificazione dell'implementazione della protezione di reti LAN senza fili</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 4 Progettazione dell'infrastruttura a chiave pubblica (PKI)</td>
<td style="border:1px solid black;">Capitolo 2 Pianificazione dell'implementazione della protezione di reti LAN senza fili</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Capitolo 5 Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili</td>
<td style="border:1px solid black;">Capitolo 2 Pianificazione dell'implementazione della protezione di reti LAN senza fili</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 6 Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X</td>
<td style="border:1px solid black;">Capitolo 2 Pianificazione dell'implementazione della protezione di reti LAN senza fili</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;"> </td>
<td style="border:1px solid black;">Capitolo 3 Predisposizione dell'ambiente</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 7 Implementazione dell'infrastruttura a chiave pubblica</td>
<td style="border:1px solid black;">Capitolo 4 Creazione dell'Autorità di certificazione della rete</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Capitolo 8 Implementazione dell'infrastruttura RADIUS per la protezione di reti LAN senza fili</td>
<td style="border:1px solid black;">Capitolo 5 Creazione dell'infrastruttura di protezione per LAN senza fili</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 9 Implementazione della protezione di reti LAN senza fili mediante lo standard 802.1X</td>
<td style="border:1px solid black;">Capitolo 6 Configurazione dei client delle reti LAN senza fili</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Capitolo 10 Introduction to Operations Guide</td>
<td style="border:1px solid black;">Capitolo 8 Gestione della soluzione per reti LAN senza fili protette</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 11 Managing the Public Key Infrastructure</td>
<td style="border:1px solid black;">Capitolo 8 Gestione della soluzione per reti LAN senza fili protette</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Capitolo 12 Managing the RADIUS and WLAN Security Infrastructure</td>
<td style="border:1px solid black;">Capitolo 8 Gestione della soluzione per reti LAN senza fili protette</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Capitolo 13 Guida per i test</td>
<td style="border:1px solid black;">Capitolo 7 Gestione della soluzione per reti LAN senza fili protette</td>
</tr>
</tbody>
</table>
  
Si osservi che la soluzione EAP-TLS è stata strutturata intenzionalmente per mantenere indipendenti fra loro, il più possibile, i componenti dell'infrastruttura a chiave pubblica (PKI, Public Key Infrastructure), di RADIUS e della rete WLAN, allo scopo di consentire il riutilizzo di questi componenti in altre applicazioni. Questo comporta alcune ripetizioni nella soluzione EAP-TLS. Ad esempio, entrambi i capitoli sull'infrastruttura PKI e su RADIUS includono istruzioni di implementazione per i server, perché nelle grandi organizzazioni può accadere che l'installazione dei server CA e IAS venga svolta da gruppi diversi del reparto IT. Inoltre, alcuni dei passaggi logici contenuti nei capitoli sulla progettazione e sull'implementazione possono risultare fuorvianti nel contesto di una soluzione PEAP. Pertanto è necessario leggere l'intera soluzione PEAP per farsi un quadro dell'intero processo, quindi tornare alla soluzione EAP-TLS per reperire informazioni specifiche per la progettazione e l'implementazione.
  
Le sezioni seguenti contengono le descrizioni di come utilizzare i capitoli della soluzione EAP-TLS insieme ai capitoli della soluzione PEAP.
  
#### Capitolo 1 Panoramica
  
Il capitolo 1 contiene una panoramica della soluzione e brevi descrizioni del contenuto di ogni capitolo e appendice della guida. Dal momento che verranno utilizzate principalmente le indicazioni della guida EAP-TLS, è necessario utilizzare il capitolo 1 di tale guida.
  
#### Capitolo 2 Scelta di una strategia di rete senza fili protetta
  
Il contenuto di questo capitolo è molto simile al contenuto dell'introduzione "Scelta di una strategia per la protezione di reti LAN senza fili" della soluzione PEAP. L'introduzione della soluzione PEAP può fungere da prefazione per entrambe le soluzioni, quindi è opportuno utilizzare questa introduzione anziché il capitolo 2 della soluzione EAP-TLS.
  
#### Capitolo 3 Architettura della soluzione di rete LAN senza fili protetta
  
Questo capitolo contiene una panoramica dell'architettura della soluzione per la protezione di reti WLAN basata su certificati. Sono rilevanti tutti gli argomenti seguenti, ad eccezione del primo:
  
-   Descrizione di come funzionano i certificati 802.1X con EAP-TLS. Al suo posto, vedere la descrizione contenuta nel capitolo 2 "Pianificazione dell'implementazione della protezione di reti LAN senza fili" della soluzione PEAP.
  
-   Descrizione dell'organizzazione di destinazione.
  
-   Elenco dei principali criteri di progettazione della soluzione.
  
-   Illustrazione di come vengono utilizzati i vari componenti server in punti diversi dell'organizzazione.
  
-   Descrizione delle modalità di scalabilità della soluzione.
  
-   Esempio di utilizzo di elementi della soluzione per supportare altre applicazioni di rete, quali la protezione di rete cablata 802.1X e le reti private virtuali (VPN).
  
I riferimenti all'Autorità di certificazione possono essere importanti anche per un corretto utilizzo del capitolo successivo.
  
#### Capitolo 4 Progettazione dell'infrastruttura a chiave pubblica (PKI)
  
Questo capitolo contiene una descrizione dettagliata del processo di pianificazione per un'infrastruttura PKI semplice. La soluzione PEAP contiene anche istruzioni per una CA semplice, finalizzata a un solo scopo. Sebbene non sia necessario rilasciare certificati ai client della propria rete WLAN, è comunque consigliabile fare riferimento a questo capitolo per progettare l'infrastruttura PKI. Più grande è l'organizzazione, più è probabile che si debbano adottare certificati diversi da quelli per la semplice autenticazione di rete. Questo capitolo contiene indicazioni utili per progettare un'infrastruttura PKI più robusta e flessibile di quella presentata nella soluzione PEAP.
  
#### Capitolo 5 Progettazione di un'infrastruttura RADIUS per la protezione di reti LAN senza fili
  
Seguire le indicazioni fornite in questo capitolo della soluzione EAP-TLS.
  
#### Capitolo 6 Progettazione della protezione di reti LAN senza fili mediante lo standard 802.1X
  
Seguire le indicazioni fornite in questo capitolo della soluzione EAP-TLS.
  
#### Capitolo 7 Implementazione dell'infrastruttura a chiave pubblica
  
Questo capitolo è di interesse solo se si decide di implementare un'infrastruttura PKI completa, come descritto in precedenza. In caso contrario, seguire il capitolo 4 "Creazione dell'Autorità di certificazione della rete" della soluzione PEAP.
  
#### Capitolo 8 Implementazione dell'infrastruttura RADIUS per la protezione di reti LAN senza fili
  
È necessario seguire le indicazioni fornite in questo capitolo. Per ulteriori informazioni, vedere anche il capitolo 5 "Creazione dell'infrastruttura di protezione per LAN senza fili" della soluzione PEAP.
  
#### Capitolo 9 Implementazione della protezione di reti LAN senza fili mediante lo standard 802.1X
  
Seguire le istruzioni fornite nel capitolo 5 "Creazione dell'infrastruttura di protezione per LAN senza fili" e nel capitolo 6 "Configurazione dei client delle reti LAN senza fili" della soluzione PEAP su come configurare il criterio di accesso remoto per IAS e le impostazioni dell'oggetto Criteri di gruppo per i client. Il capitolo 5 della soluzione PEAP contiene anche informazioni utili sulla configurazione delle impostazioni dei punti di accesso senza fili e script per l'automazione dell'immissione dei client RADIUS e della replica delle impostazioni IAS che non sono disponibili nella soluzione EAP-TLS.
  
#### Capitoli 10, 11 e 12 sull'esercizio della soluzione
  
Seguire le indicazioni fornite in questi capitoli della soluzione EAP-TLS. Inoltre, leggere le informazioni del capitolo 7 "Gestione della soluzione per reti LAN senza fili protette" della soluzione PEAP sulla risoluzione dei problemi delle reti LAN senza fili. Questo capitolo contiene procedure dettagliate e tecniche che completano le procedure dei capitoli della soluzione EAP-TLS.
  
#### Capitolo 13 Guida per i test
  
Applicare il contenuto di questo capitolo. Se è stato deciso di non implementare un'infrastruttura PKI completa come descritto nel capitolo 4 "Progettazione dell'infrastruttura a chiave pubblica (PKI)" della soluzione EAP-TLS, ignorare alcuni test relativi all'infrastruttura PKI di questo capitolo.
  
#### Script
  
Gli script utilizzati nella soluzione PEAP sono stati sviluppati a partire dagli script della soluzione EAP-TLS. Tuttavia, anche se gli script della soluzione PEAP contengono più funzionalità rispetto agli script della soluzione EAP-TLS, non possono essere considerati un soprainsieme perfetto. Gli script della soluzione EAP-TLS contengono, ad esempio, funzioni di monitoraggio della CA più sofisticate. Nella maggior parte dei casi vanno utilizzati gli script forniti nella soluzione PEAP, tuttavia può essere utile installare gli script di entrambe le soluzioni in cartelle distinte e utilizzare gli uni o gli altri a seconda delle necessità del momento. Gli script vengono forniti solo come esempi basilari per illustrare le tecniche, quindi può essere utile modificarli in base alle esigenze della propria organizzazione.
  
**Scarica la soluzione completa**
  
[Protezione delle reti LAN senza fili con PEAP e password](http://go.microsoft.com/fwlink/?linkid=23481)
  
[](#mainsection)[Inizio pagina](#mainsection)
