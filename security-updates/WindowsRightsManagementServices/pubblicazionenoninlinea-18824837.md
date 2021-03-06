---
TOCTitle: Pubblicazione non in linea
Title: Pubblicazione non in linea
ms:assetid: 'f6384ed2-f917-442e-aa63-c1394a1c4d06'
ms:contentKeyID: 18824837
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747741(v=WS.10)'
---

Pubblicazione non in linea
==========================

La pubblicazione non in linea differisce dalla pubblicazione in linea nel modo in cui l'applicazione abilitata per RMS acquisisce la licenza di pubblicazione.

Prima di pubblicare contenuto non in linea, l'autore deve acquisire un certificato concessore di licenze client mentre è connesso attraverso la rete al server di certificazione principale.

Il processo di pubblicazione non in linea include i passaggi seguenti:

1.  L'autore crea il documento utilizzando un'applicazione abilitata per RMS, quindi specifica i diritti e le condizioni del contenuto.
2.  Quando l'autore salva il file, il certificato concessore di licenze client consente al computer o alla periferica locale di rilasciare e firmare una licenza di pubblicazione per il file.
    La licenza di pubblicazione contiene due copie della chiave del contenuto, la prima crittografata con la chiave pubblica del certificato concessore di licenze client, l'altra crittografata con la chiave pubblica del server che ha emesso il certificato concessore di licenze. La licenza contiene inoltre l'URL del server. Le due chiavi pubbliche e l'URL sono ricavati dal certificato concessore di licenze client.
3.  Il computer impiega il certificato concessore di licenze client per creare una licenza di proprietario, una speciale licenza d'uso che assegna all'autore il diritto di utilizzare il contenuto protetto con RMS anche quando non è in linea. Il certificato concessore di licenze client utilizza la propria chiave privata per decrittografare la chiave simmetrica del contenuto dalla licenza di pubblicazione e quindi la crittografa nuovamente nella licenza di proprietario.
4.  L'applicazione crittografa il file con la chiave del contenuto ed esegue il binding della licenza di pubblicazione al file. Solo il server RMS che ha emesso la licenza di pubblicazione o un server membro di un dominio di pubblicazione trusted possono emettere licenze in grado di decrittografare questo file.
