---
TOCTitle: 'Capitolo 12: Conclusioni'
Title: 'Capitolo 12: Conclusioni'
ms:assetid: '9ee5a237-9151-4292-bf4e-4156df16d739'
ms:contentKeyID: 20200883
ms:mtpsurl: 'https://technet.microsoft.com/it-it/library/Dd536284(v=TechNet.10)'
---

Pericoli e contromisure
=======================

### Capitolo 12: Conclusioni

In questa Guida sono illustrate le contromisure di protezione più significative disponibili in Microsoft Windows Server 2003 con SP1 e Microsoft Windows XP Professional con SP2. Molte delle impostazioni consigliate possono essere gestite creando un modello di protezione e importandolo in un oggetto Criteri di gruppo (GPO) collegato all'unità organizzativa padre (OU, Organizational Unit) del server membro. Altre invece possono essere implementate configurando le sezioni dei modelli amministrativi (ADM, Administrative Template) dei criteri di gruppo. Alcune procedure, tuttavia, non possono essere applicate mediante i criteri di gruppo. Per questo motivo, nella Guida viene spigato come configurare alcune impostazioni manualmente.

### Ulteriori informazioni

-   Per ulteriori informazioni sulla protezione e la privacy in ambito Microsoft, vedere la pagina [Security](http://www.microsoft.com/security) (in inglese) all'indirizzo www.microsoft.com/security.

-   Per ulteriori informazioni sulle indicazioni autorevoli per la protezione di Microsoft, consultare [Elenco di controllo delle procedure consigliate](http://www.microsoft.com/technet/security/secnews/articles/enterprisesecbp.mspx) all'indirizzo www.microsoft.com/technet/security/secnews/articles/enterprisesecbp.msp.

-   Per informazioni sulle "[10 regole fondamentali della protezione](http://www.microsoft.com/technet/archive/community/columns/security/essays/10imlaws.mspx)", vedere www.microsoft.com/technet/archive/community/columns/security/essays/10imlaws.mspx (in inglese).

-   Per ulteriori informazioni sulla protezione di [Windows Server 2003](http://www.microsoft.com/technet/security/prodtech/windowsserver2003.mspx), vedere www.microsoft.com/technet/security/prodtech/windowsserver2003.mspx (in inglese).

-   Per ulteriori informazioni su come delegare l'amministrazione del servizio di directory Active Directory, consultare "[Design Considerations for Delegation of Administration in Active Directory](http://www.microsoft.com/technet/prodtechnol/windows2000serv/technologies/activedirectory/plan/addeladm.mspx)” (in inglese) all'indirizzo www.microsoft.com/technet/prodtechnol/windows2000serv/technologies/activedirectory/
    plan/addeladm.mspx.

-   Per ulteriori informazioni sugli attacchi di rete più diffusi, vedere "[Common Types of Network Attacks](http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/cnet/cndb_ips_ddui.mspx?mfr=true)" (in inglese), estratto da *Windows*  *2000 Server Resource Kit*, disponibile in linea all'indirizzo:http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/
    en-us/cnet/cndb\_ips\_ddui.asp.

-   Per ulteriori informazioni su come irrobustire lo stack TCP/IP di Windows Server 2003, consultare l'articolo della Microsoft Knowledge Base "[Rendere più forte lo stack TCP/IP rispetto ad attacchi di tipo "denial of service" in Windows Server 2003](http://support.microsoft.com/kb/324270/it)" all'indirizzo http://support.microsoft.com/kb/324270/it.

-   Per ulteriori informazioni su come aumentare la protezione delle impostazioni per le applicazioni Windows Sockets, vedere l'articolo della Microsoft Knowledge Base "[Server Internet non disponibile a causa di attacchi SYN](http://support.microsoft.com/?scid=142641)" all'indirizzo http://support.microsoft.com/?kbid=142641.

-   Per ulteriori informazioni sulla posizione dei file .adm, consultare l'articolo della Microsoft Knowledge Base "[Posizione di file ADM (modello amministrativo) in Windows](http://support.microsoft.com/kb/228460/it)" all'indirizzo http://support.microsoft.com/kb/228460/it.

-   Per ulteriori informazioni sui Criteri di gruppo, compreso un elenco dei percorsi e dei valori di tutte le impostazioni memorizzate nel Registro di sistema disponibili per tutte le versioni di Windows, consultare “[Group Policy Settings Reference for Windows Server 2003 with Service Pack 1](http://www.microsoft.com/downloads/details.aspx?familyid=7821c32f-da15-438d-8e48-45915cd2bc14)” (in inglese) all'indirizzo www.microsoft.com/downloads/details.aspx?FamilyId=7821C32F-DA15-438D-8E48-45915CD2BC14.

-   Per ulteriori informazioni sull'architettura di base per la creazione, la modifica e l'esecuzione dei modelli di protezione, consultare "[How Security Settings Extension Works](http://technet.microsoft.com/en-us/library/cc785052.aspx)" (in inglese) all'indirizzo http://www.microsoft.com/technet/prodtechnol/windowsserver2003/library/TechRef/
    f546e58e-8473-4985-a05d-0b038dea4a9f.mspx. L'articolo contiene informazioni dettagliate sull'archiviazione dei criteri di gruppo, sulle precedenze e su come alcune impostazioni persistono anche quando un particolare criterio di gruppo non viene più applicato a un computer, spesso definito come ‘contrassegno permanente'.

-   Per ulteriori informazioni su come personalizzare l'interfaccia utente dell'Editor di configurazione della protezione, consultare l'articolo della Microsoft Knowledge Base “[Come aggiungere le impostazioni di Registro di sistema personalizzato a Editor di configurazione della protezione](http://support.microsoft.com/kb/214752/it)” all'indirizzo http://support.microsoft.com/kb/214752/it.

-   Per ulteriori informazioni sulla creazione di modelli amministrativi personalizzati in Windows, consultare l'articolo della Microsoft Knowledge Base “[How to: Creare modelli amministrativi personalizzati in Windows 2000](http://support.microsoft.com/kb/323639/it)” all'indirizzo http://support.microsoft.com/kb/323639/it.

-   Per ulteriori informazioni su come assicurare che le impostazioni di livello di autenticazione di LAN Manager più sicure collaborino su reti miste Windows 2000 e Windows NT 4.0, consultare l'articolo della Microsoft Knowledge Base "[I problemi di autenticazione in Windows 2000 con NTLM 2 livellano sopra 2 in un dominio di Windows NT 4.0](http://support.microsoft.com/kb/305379/it)" all'indirizzo http://support.microsoft.com/kb/305379/it.

-   Per ulteriori informazioni sui livelli di compatibilità del LAN Manager, vedere l'articolo della Microsoft Knowledge Base "[Possibili incompatibilità tra client, servizi e programmi quando si modificano le impostazioni di protezione e le assegnazioni diritti utente](http://support.microsoft.com/kb/823659/it)" all'indirizzo http://support.microsoft.com/kb/823659/it.

-   Per ulteriori informazioni sull'autenticazione NTLMv2, vedere l'articolo della Microsoft Knowledge Base "[Attivazione dell'autenticazione NTLM 2](http://support.microsoft.com/kb/239869/it)" all'indirizzo http://support.microsoft.com/kb/239869/it.

-   Per ulteriori informazioni sulle impostazioni predefinite per i servizi di Windows Server 2003, vedere la pagina [Default settings for services](http://technet.microsoft.com/en-us/library/cc785922.aspx) (in inglese) all'indirizzo www.microsoft.com/resources/documentation/windowsserv/2003/standard/proddocs/en-us/sys\_srv\_default\_settings.asp.

-   Per ulteriori informazioni sulla distribuzione delle smart card per Windows Server 2003, vedere la pagina [Windows Server 2003 Smart Card](http://technet.microsoft.com/en-us/library/cc783579.aspx) (in inglese) su Microsoft TechNet all'indirizzo www.microsoft.com/technet/prodtechnol/windowsserver2003/technologies/smrtcard.mspx.

-   Per ulteriori informazioni sui criteri di controllo di Windows Server 2003, vedere la pagina [Auditing Policy](http://www.microsoft.com/technet/prodtechnol/windowsserver2003/library/serverhelp/6847e72b-9c47-42ab-b3e3-691addac9f33.mspx) (in inglese) all'indirizzo www.microsoft.com/technet/prodtechnol/windowsserver2003/library/ServerHelp/
    6847e72b-9c47-42ab-b3e3-691addac9f33.mspx.

-   Per ulteriori informazioni sulle assegnazioni dei diritti utente per Windows Server 2003, vedere la pagina [User Rights Assignment](http://technet.microsoft.com/library/cc780182.aspx) (in inglese) all'indirizzo www.microsoft.com/resources/documentation/windows/
    xp/all/proddocs/en-us/uratopnode.mspx.

-   Per ulteriori informazioni su come ripristinare le impostazioni di protezione predefinite a livello locale, consultare l'articolo della Microsoft Knowledge Base “[How to: Reimpostare le opzioni di protezione predefinite](http://support.microsoft.com/kb/313222/it)” all'indirizzo http://support.microsoft.com/kb/313222/it.

-   Per ulteriori informazioni su come ripristinare le impostazioni di protezione predefinite negli oggetti dei criteri di gruppo integrati del dominio, consultare l'articolo della Microsoft Knowledge Base “[Reimpostazione dei diritti utente nei criteri di gruppo di dominio predefiniti in Windows Server 2003](http://support.microsoft.com/kb/324800/it)” a http://support.microsoft.com/kb/324800/it.

-   Per ulteriori informazioni sulla protezione per i vari sistemi operativi Windows, consultare "[*Microsoft Windows Security Resource Kit*](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/auth_eap.mspx)". Per informazioni sull'acquisto del libro, visitare il sito Microsoft Press all'indirizzo www.microsoft.com/MSPress/books/6418.asp.

-   Per ulteriori informazioni su [Office XP Resource Kit](http://www.microsoft.com/office/ork/xp/default.htm), o per scaricare gli [strumenti di Office Resource Kit](http://www.microsoft.com/office/orkarchive/xpddl.htm), visitare i siti www.microsoft.com/office/ork/xp/default.htm e www.microsoft.com/office/ork/xp/appndx/appc00.htm (in inglese).

**Download**

[Scaricare la Guida a pericoli e contromisure](http://go.microsoft.com/fwlink/?linkid=15160)

**Notifiche di aggiornamento**

[Iscriversi per ottenere aggiornamenti e nuove versioni](http://go.microsoft.com/fwlink/?linkid=54982)

**Commenti e suggerimenti**

[Inviare commenti o suggerimenti](mailto:secwish@microsoft.com?subject=guida%20a%20pericoli%20e%20contromisure)

[](#mainsection)[Inizio pagina](#mainsection)
