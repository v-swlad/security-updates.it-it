---
TOCTitle: Riepilogo dei certificati e delle licenze RMS
Title: Riepilogo dei certificati e delle licenze RMS
ms:assetid: '637ccfca-318e-4346-85b5-0945b058fb9c'
ms:contentKeyID: 18824624
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Cc747595(v=WS.10)'
---

Riepilogo dei certificati e delle licenze RMS
=============================================

La tabella che segue elenca i certificati e le licenze utilizzate da RMS. Questi vengono illustrati dettagliatamente nei rimanenti argomenti della sezione.

###  

 
<table style="border:1px solid black;">
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th style="border:1px solid black;" >Certificato o licenza</th>
<th style="border:1px solid black;" >Scopo</th>
<th style="border:1px solid black;" >Contenuto</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="border:1px solid black;">Certificati concessori di licenze server</td>
<td style="border:1px solid black;">Il certificato concessore di licenze server rilasciato ai server licenze assegna il diritto di rilasciare:
<ul>
<li>Licenze di pubblicazione<br />
<br />
</li>
<li>Licenze d'uso<br />
<br />
</li>
<li>Certificati concessori di licenze client<br />
<br />
</li>
<li>Modelli di criteri per i diritti<br />
<br />
</li>
</ul>
Il certificato concessore di licenze server rilasciato al cluster di certificazione principale assegna il diritto di rilasciare:
<ul>
<li>Certificati per account con diritti ai client<br />
<br />
</li>
<li>Certificati concessori di licenze server ai server licenze<br />
<br />
</li>
</ul></td>
<td style="border:1px solid black;">Il certificato concessore di licenze server rilasciato a un server licenze contiene la chiave pubblica del server licenze.
Il certificato concessore di licenze server rilasciato al server di certificazione principale contiene la chiave pubblica del server di certificazione principale.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Certificati concessori di licenze client</td>
<td style="border:1px solid black;">Concedono all'utente i diritti necessari per pubblicare contenuto protetto con RMS senza essere connessi alla rete aziendale.</td>
<td style="border:1px solid black;">Contengono la chiave pubblica del certificato e la chiave privata del certificato crittografata con la chiave pubblica dell'utente che ha richiesto il certificato. Inoltre, contengono la chiave pubblica del server che ha rilasciato il certificato.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Certificati computer RMS</td>
<td style="border:1px solid black;">Identificano un computer o un dispositivo considerato attendibile dal sistema RMS.</td>
<td style="border:1px solid black;">Contengono la chiave pubblica del computer attivato. La chiave privata corrispondente è contenuta nell'archivio protetto del computer.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Certificati per account con diritti</td>
<td style="border:1px solid black;">Identificano un utente nel contesto di un computer o una periferica specifica.</td>
<td style="border:1px solid black;">Contengono la chiave pubblica dell'utente e la chiave privata dell'utente crittografata con la chiave pubblica del computer attivato.</td>
</tr>
<tr class="odd">
<td style="border:1px solid black;">Licenze di pubblicazione</td>
<td style="border:1px solid black;">Specificano i diritti validi per il contenuto protetto con RMS.</td>
<td style="border:1px solid black;">Contengono la chiave del contenuto simmetrica per la decrittrografazione del contenuto, il quale viene crittografato mediate la chiave pubblica del server che ha emesso la licenza.</td>
</tr>
<tr class="even">
<td style="border:1px solid black;">Licenze d'uso</td>
<td style="border:1px solid black;">Specificano i diritti validi per il contenuto protetto con RMS nel contesto di uno specifico utente autenticato.</td>
<td style="border:1px solid black;">Contengono la chiave simmetrica per la decrittografia del contenuto, crittografata con  la chiave pubblica dell'utente.</td>
</tr>
</tbody>
</table>
