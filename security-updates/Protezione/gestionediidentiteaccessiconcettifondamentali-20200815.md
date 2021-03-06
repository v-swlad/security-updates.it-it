---
TOCTitle: 'Gestione di identità e accessi: Concetti fondamentali'
Title: 'Gestione di identità e accessi: Concetti fondamentali'
ms:assetid: '7eabacbd-a83c-4a87-af14-4591e95050de'
ms:contentKeyID: 20200815
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536215(v=TechNet.10)'
---

Concetti fondamentali
=====================

Aggiornato: 29 agosto 2004

### Riepilogo operativo

In questo documento vengono affrontati i problemi relativi alla gestione di identità e accessi e gli approcci e le tecnologie disponibili per risolverli, dal punto di vista aziendale e del reparto IT. Vengono descritti i concetti di base, la terminologia, le iniziative comuni e i prodotti e le tecnologie Microsoft relative alla gestione di identità e accessi.

Questo documento è il primo della [*Serie Microsoft Gestione di identità e accessi*](http://technet.microsoft.com/it-it/library/dd536198.aspx) disponibile sul sito Web Microsoft.com

#### La sfida per le aziende

La gestione di identità e accessi è diventata più complessa con l'accresciuta importanza assunta dall'utilizzo delle identità digitali nelle modalità di interazione fra utenti e reti informatiche. Le organizzazioni devono poter gestire gli utenti in modo efficace e attento, garantendo loro l'accesso alle risorse della rete. Tuttavia, è raro che le organizzazioni archivino e utilizzino le informazioni sulle identità in un'unica posizione. Reparti, paesi, regioni e divisioni aziendali diversi e una vasta gamma di applicazioni software, oltre che fusioni e acquisizioni, hanno come risultato la proliferazione di servizi directory e archivi di identità specifici di applicazioni e servizi, con conseguente aumento di costi e di complessi problemi di protezione.

Lo sviluppo di un'efficace e coerente strategia di gestione di identità e accessi richiede una comprensione profonda degli approcci e delle tecnologie che è possibile utilizzare per la gestione di molteplici identità digitali. Le organizzazioni e i reparti IT devono implementare approcci sia strategici che a breve termine per il controllo delle identità.

#### I vantaggi per le aziende

Il miglioramento dell'accesso alle risorse della rete e la gestione del ciclo di vita delle identità può offrire significativi vantaggi economici alle organizzazioni. Tra i vantaggi sono inclusi:

-   Riduzione del costo totale di proprietà grazie a efficienza e consolidamento.

-   Miglioramenti della protezione che riducono il rischio di attacchi interni ed esterni.

-   Maggiore accesso alle informazioni da parte di partner, dipendenti e clienti, con conseguente aumento della produttività, della fruibilità e del fatturato.

-   Conformità alle normative, mediante l'implementazione di criteri completi per la protezione, il controllo e l'accesso.

-   Maggiore agilità in occasione di fusioni e acquisizioni.

#### Destinatari della guida

Questo documento è rivolto ad architetti di sistema, professionisti e responsabili IT, nonché a consulenti coinvolti nelle attività di gestione di identità e accessi. È inoltre rivolto ai responsabili dei processi decisionali aziendali interessati alla valutazione degli investimenti per la gestione di identità e accessi.

#### Prerequisiti per i lettori

In questo documento sono riportati i concetti fondamentali della *Serie Microsoft Gestione di identità e accessi*; l'unico prerequisito è disporre di una conoscenza di base dei servizi directory e di protezione utilizzati in diversi ambienti informatici.

[](#mainsection)[Inizio pagina](#mainsection)

### Panoramica

Questo documento è composto da sette capitoli nei quali sono illustrati i concetti fondamentali e la funzionalità della piattaforma Microsoft per la gestione di identità digitali e degli accessi. I capitoli trattano i seguenti argomenti:

[**Capitolo 1: Introduzione**](http://technet.microsoft.com/it-it/library/dd536216.aspx)

Nell'Introduzione vengono riportati un riepilogo operativo, problemi e vantaggi per le aziende, i principali destinatari a cui questo documento è rivolto e una panoramica su ciascun capitolo della Guida.

[**Capitolo 2: Terminologia e iniziative**](http://technet.microsoft.com/it-it/library/dd536217.aspx)

In questo capitolo vengono esaminati i termini fondamentali e i problemi strategici alla base della gestione di identità e accessi. Vengono illustrate le possibili soluzioni per l'integrazione delle identità digitali e gli approcci tecnici e organizzativi per applicarle.

[**Capitolo 3: Tecnologie Microsoft per la gestione di identità e accessi**](http://www.microsoft.com/italy/technet/security/topics/identity/p1fund_2.mspx)

In questo capitolo sono presentati i servizi directory e di protezione di Microsoft® Windows Server™ 2003, Microsoft Windows XP, Microsoft Identity Integration Server 2003 Enterprise Edition (MIIS 2003), Microsoft Passport e di altri prodotti relativi alla gestione di identità e accessi.

Negli altri capitoli vengono illustrati in modo più dettagliato e più specificamente tecnico gli scenari e le tecnologie per la gestione di identità e accessi.

[**Capitolo 4: Servizi directory**](http://technet.microsoft.com/it-it/library/dd536218)

In questo capitolo viene illustrato come il servizio directory Microsoft Active Directory® e Active Directory Application Mode (ADAM) forniscono i servizi LDAP, X.500 e di replica su più master per creare la base di un'infrastruttura efficace per la gestione di identità e accessi.

[**Capitolo 5: Gestione del ciclo di vita delle identità**](http://technet.microsoft.com/it-it/library/dd536219)

In questo capitolo vengono illustrati gli approcci per la gestione degli utenti, delle credenziali e dei diritti acquisiti. Vengono esaminate le tecniche e le tecnologie per l'abilitazione del self-service da parte dell'utente, dell'amministrazione delegata, dell'integrazione e dell'implementazione di identità.

[**Capitolo 6: Gestione degli accessi**](http://www.microsoft.com/italy/technet/security/topics/identity/p1fund_5.mspx)

In questo capitolo vengono illustrati diversi concetti e descritte le tecnologie che li supportano, compreso:

-   autenticazione, Single Sign On e mapping delle credenziali.

-   Autorizzazione mediante il controllo dell'accesso basato sui ruoli e gli elenchi di controllo di accesso.

-   Attendibilità e federazione.

-   Controllo della protezione.

[**Capitolo 7: Applicazioni**](http://technet.microsoft.com/it-it/library/dd536220)

Le organizzazioni devono spesso sviluppare applicazioni interne o acquistare applicazioni per il funzionamento di processi LOB (Line-Of-Business). Tali applicazioni dovranno integrarsi completamente con i servizi directory e di protezione utilizzati dall'organizzazione. In questo capitolo viene illustrato come le applicazioni possono integrarsi con la piattaforma Microsoft per la gestione di identità e accessi e vengono esaminate le tecniche utilizzabili dagli sviluppatori per creare applicazioni personalizzate.

[](#mainsection)[Inizio pagina](#mainsection)
