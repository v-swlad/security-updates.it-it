---
TOCTitle: Informazioni generali sul sistema RMS
Title: Informazioni generali sul sistema RMS
ms:assetid: 'cbd14635-e17e-42b8-9fd8-6fdce42ffe07'
ms:contentKeyID: 18824776
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747671(v=WS.10)'
---

Informazioni generali sul sistema RMS
=====================================

Questo argomento contiene informazioni sul modo in cui i servizi Web di RMS e la tecnologia del client RMS operano congiuntamente in un sistema RMS.

La tabella che segue elenca i tipi di server che fanno parte di una distribuzione di RMS e ne descrive le funzioni. Per informazioni dettagliate sulla distribuzione, vedere "Distribuzione di un sistema RMS" in questa documentazione.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Server o cluster</th>
<th style="border:1px solid black;" >Funzione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Di certificazione principale</td>
<td style="border:1px solid black;">Esegue i seguenti servizi RMS:
<ul>
<li><strong>Registrazione secondaria</strong>. Esegue la registrazione secondaria dei server licenze.<br />
<br />
</li>
<li><strong>Proxy di attivazione</strong>. Agisce da proxy Internet per le richieste dei client relative a archivi protetti e certificati computer RMS.<br />
<br />
</li>
<li><strong>Certificazione</strong>. Emette i certificati per account con diritti.<br />
<br />
</li>
<li><strong>Pubblicazione</strong>. Rilascia licenze di pubblicazione.<br />
<br />
</li>
<li><strong>Gestione delle licenze</strong>. Rilascia licenze d'uso.<br />
<br />
</li>
</ul>
Ogni distribuzione deve includere almeno un server o un cluster di certificazione principale. In ogni insieme di strutture di Active Directory deve essere presente un solo cluster di certificazione principale.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Licenze (facoltativo)</td>
<td style="border:1px solid black;">Esegue i seguenti servizi RMS:
<ul>
<li><strong>Pubblicazione</strong>. Rilascia licenze di pubblicazione.<br />
<br />
</li>
<li><strong>Gestione delle licenze</strong>. Rilascia licenze d'uso.<br />
<br />
</li>
</ul>
I server licenze spesso vengono distribuiti allo scopo di supportare singoli reparti oppure delegare richieste di licenza dal cluster di certificazione principale. I server licenze sono facoltativi.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Server database, ad esempio SQL Server</td>
<td style="border:1px solid black;"><ul>
<li>Esegue la configurazione, la registrazione delle attività e i database dei servizi di directory di RMS.<br />
<br />
</li>
<li>Memorizza i certificati per account con diritti nel database di configurazione del cluster di certificazione principale.<br />
<br />
</li>
</ul></td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Controller di dominio e catalogo globale</td>
<td style="border:1px solid black;"><ul>
<li>Esegue l'autenticazione degli utenti e servizi di directory.<br />
<br />
</li>
<li>Memorizza la posizione di rilevamento dei servizi del cluster di certificazione principale.<br />
<br />
</li>
</ul></td>
</tr>
</tbody>
</table>
 

In, RMS i servizi di registrazione e attivazione di Microsoft vengono impiegati per fornire un elemento principale della catena di trust al sistema. Per ulteriori informazioni, vedere "[Gerarchia di trust di RMS](https://technet.microsoft.com/2d44182f-a653-4383-aba1-dade53f7cf9a)" più avanti in questo argomento.

Il seguente diagramma illustra i differenti componenti di un sistema RMS, mostrandone i rispettivi ruoli. Le frecce rappresentano le richieste e le risposte scambiate tra i diversi componenti.

![](images/Cc747671.29138741-d45c-459b-8ead-b9bc3f708dd5(WS.10).gif "Componenti del sistema RMS")

Per ulteriori informazioni su ciascun componente, vedere "[Componenti software di RMS](https://technet.microsoft.com/e38a840e-f390-48fd-8354-50108a64f5ca)" più avanti in questo argomento.
