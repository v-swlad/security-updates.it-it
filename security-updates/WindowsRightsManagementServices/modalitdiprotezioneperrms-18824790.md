---
TOCTitle: Modalità di protezione per RMS
Title: Modalità di protezione per RMS
ms:assetid: 'd7792293-5bb2-4232-9d48-e81e87ab6219'
ms:contentKeyID: 18824790
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747686(v=WS.10)'
---

Modalità di protezione per RMS
==============================

RMS utilizza impostazioni di protezione diverse per le tre modalità di esecuzione seguenti:

-   Installazione: i file di RMS vengono installati e configurati.
-   Provisioning: i siti Web, le directory virtuali e i database vengono creati e configurati.
-   Funzionamento normale: alcuni servizi, ad esempio la certificazione degli account, richiedono l'autenticazione, mentre altri, ad esempio l'attivazione del computer, non la richiedono. Alcuni servizi, ad esempio l'amministrazione, sono soggetti a restrizioni, mentre altri, ad esempio la gestione delle licenze, non lo sono.

Nell'ambito di ciascuna modalità, RMS deve poter accedere a differenti risorse per scopi differenti. Inoltre, utilizza account di protezione diversi in base alle operazioni che deve eseguire. I restanti argomenti di questa sezione illustrano la protezione durante l'impiego delle tre modalità, descrivono le operazioni eseguite da RMS e spiegano gli account di protezione utilizzati, oltre alle relative autorizzazioni di accesso.
