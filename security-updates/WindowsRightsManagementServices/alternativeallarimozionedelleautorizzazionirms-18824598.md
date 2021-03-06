---
TOCTitle: Alternative alla rimozione delle autorizzazioni RMS
Title: Alternative alla rimozione delle autorizzazioni RMS
ms:assetid: '4d32f35e-997d-4d10-ab66-efe217e853f7'
ms:contentKeyID: 18824598
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc720268(v=WS.10)'
---

Alternative alla rimozione delle autorizzazioni RMS
===================================================

Se si è ancora in fase di pianificazione dell'uso di RMS nella propria organizzazione, ma è necessario interrompere l'utilizzo di alcuni server RMS per qualsiasi motivo, è opportuno valutare l'utilizzo delle seguenti alternative alla rimozione delle autorizzazioni.

**Impostazione di un dominio di pubblicazione trusted**

Tutte le informazioni protette con RMS sono crittografate con la chiave privata del server RMS. Un dominio di pubblicazione trusted permette di importare la chiave privata di un server RMS in un altro server RMS. Questo fornisce a un server RMS la capacità di emettere licenze d'uso a fronte delle licenze di pubblicazione create da un diverso server RMS. Una volta esportata la chiave, il provisioning del server può essere annullato e si può disinstallare il server.

**Impostazione di un gruppo di utenti con privilegi avanzati**

Se il contenuto protetto con RMS non può essere aperto in quanto non esiste alcun utente che disponga di diritti per il contenuto, è possibile concedere al gruppo di utenti con privilegi avanzati il controllo completo su tutto il contenuto protetto con RMS, pubblicato da quel server. I membri del gruppo di utenti con privilegi avanzati dispongono di diritti completi per tutte le licenze d'uso emesse dal server o dal cluster RMS in cui è configurato il gruppo stesso. Di conseguenza, i membri di questo gruppo possono decrittografare qualsiasi file con contenuto protetto e rimuoverne la protezione. I membri di questo gruppo possono, ad esempio, rimuovere la protezione dai file che sono stati pubblicati da un ex dipendente per consentirne la pubblicazione e la gestione da parte di un nuovo proprietario.

Nel gruppo di utenti con privilegi avanzati non viene automaticamente incluso alcun membro, neppure gli amministratori. Tale gruppo deve esistere in Active Directory come gruppo di distribuzione, con l'attributo dell'indirizzo di posta elettronica identico al nome del gruppo, nel formato "*nome\_gruppo*@*nome\_dominio*.com." Il nome del gruppo deve corrispondere esattamente all'attributo dell'indirizzo di posta elettronica, inoltre prevede la distinzione tra maiuscole e minuscole.
