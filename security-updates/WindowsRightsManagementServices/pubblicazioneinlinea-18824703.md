---
TOCTitle: Pubblicazione in linea
Title: Pubblicazione in linea
ms:assetid: '962c4e83-cf34-4c61-9589-31d24b0299fb'
ms:contentKeyID: 18824703
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747694(v=WS.10)'
---

Pubblicazione in linea
======================

Nella figura riportata di seguito viene illustrato il processo di pubblicazione in linea.

![](images/Cc747694.897e47b6-fffe-4b11-bc9f-be58539b9f19(WS.10).gif "Processo di pubblicazione online")

Il processo di pubblicazione in linea include i passaggi seguenti:

1.  L'autore del contenuto crea un documento e utilizza l'applicazione abilitata per RMS per specificare gli utenti e assegnare diritti e condizioni al contenuto.
2.  L'applicazione abilitata per RMS genera una chiave del contenuto simmetrica, quindi invia la richiesta per una licenza di pubblicazione al server certificati o al server licenze. La richiesta include la chiave del contenuto e le impostazioni per l'uso.
3.  Il server licenze genera la licenza di pubblicazione, crittografa la chiave del contenuto con la chiave pubblica del server, quindi restituisce la licenza di pubblicazione all'applicazione abilitata per RMS.
4.  L'applicazione crittografa il file con la chiave del contenuto ed esegue il binding della licenza di pubblicazione al file.
5.  L'applicazione abilitata per RMS sul computer dell'utilizzatore del contenuto invia una richiesta che contiene il certificato per account con diritti dell'utilizzatore al server RMS che ha emesso la licenza di pubblicazione, per richiedere una licenza d'uso per il documento.
6.  Il server RMS convalida le credenziali dell'utente. Se la convalida dell'utente avviene correttamente, viene generata una licenza d'uso che è quindi restituita all'applicazione abilitata per RMS sul computer dell'utilizzatore del contenuto.
7.  L'applicazione abilitata per RMS apre il documento e concede i diritti utente in base ai parametri definiti nella licenza d'uso.
