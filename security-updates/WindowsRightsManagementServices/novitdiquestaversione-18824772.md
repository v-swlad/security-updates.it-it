---
TOCTitle: Novità di questa versione
Title: Novità di questa versione
ms:assetid: 'c68ec6fd-0ff5-467e-85a8-a53b9f089de3'
ms:contentKeyID: 18824772
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747748(v=WS.10)'
---

Novità di questa versione
=========================

Rights Management Services (RMS) con Service Pack 1 (SP1) fornisce il supporto per le funzionalità descritte di seguito.

-   **Registrazione del server RMS senza connettività Internet del server**. Nella versione precedente era necessario connettere il server RMS a Internet per eseguire la registrazione al Servizio di Enrollment Microsoft e ottenere un certificato concessore di licenze server principale. Con RMS SP1, il certificato concessore di licenze server principale deve essere comunque richiesto al Servizio di Enrollment Microsoft, ma la richiesta può essere inoltrata da un altro computer dotato di connettività Internet e il certificato può essere importato sul server RMS dopo il provisioning.
-   **Attivazione autonoma dei client**. Nella versione precedente, i certificati del computer e gli archivi protetti per i computer client dovevano essere scaricati dal Servizio di attivazione Microsoft. Con RMS SP1 non è necessaria una riconnessione al Servizio di attivazione Microsoft.
-   **Supporto per più tipi di client**. In questa versione, il server RMS può essere utilizzato per supportare i client su dispositivi mobili e i servizi server. L'amministratore di un server RMS è in grado di controllare se il server debba fornire una certificazione ai client che cercano di utilizzarne i servizi.
-   **Supporto per modelli multilingue**. Nella versione precedente, i modelli erano basati sull'impostazione della lingua di Internet Explorer. In questa versione, è possibile specificare in che lingua si desidera creare il modello, utilizzando la pagina Web Amministrazione di RMS.
-   **Supporto per autenticazione dei client mediante smart card**. In questa versione, il client RMS può utilizzare le credenziali memorizzate come certificati x.509 nelle smart card per l'autenticazione sul server RMS al fine di ottenere certificati per account con diritti (RAC) e licenze d'uso.
