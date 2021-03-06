---
title: Configurare le credenziali archiviate per l'aggiornamento dati PowerPivot (PowerPivot per SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73ee3f7f86203f4fa0ac2e4da86fecee0e2b4cf5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680451"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a>Configurare le credenziali archiviate per l'aggiornamento dati PowerPivot (PowerPivot per SharePoint)
  I processi di aggiornamento dati PowerPivot possono essere eseguiti in qualsiasi account utente di Windows purché venga creata un'applicazione di destinazione nel servizio di archiviazione sicura per archiviare le credenziali che si desidera utilizzare. Analogamente, se si desidera fornire un account di accesso al database diverso da quello utilizzato per importare originariamente i dati in PowerPivot per Excel, è possibile eseguire il mapping di queste credenziali a un'applicazione di destinazione del servizio di archiviazione sicura, quindi specificare quell'applicazione di destinazione in una pianificazione dell'aggiornamento dati.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
 Dopo avere seguito le istruzioni in questo argomento, si sarà in grado di utilizzare l'opzione relativa alle credenziali seguente nella pagina della pianificazione dell'aggiornamento dati PowerPivot:  
  
 ![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")  
  
 In questo argomento viene illustrato come impostare nomi utente e password utilizzati per l'aggiornamento dati PowerPivot in una farm di SharePoint 2010. Prima di poter eseguire questi passaggi, è necessario abilitare il servizio di archiviazione sicura e generare una chiave master. Per altre informazioni, vedere [aggiornamento dati PowerPivot con SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
 [Configurare un account di Windows per l'aggiornamento dei dati](#configAny)  
  
 [Configurare un account predefinito per l'accesso alle origini dati esterne o di terze parti](#config3rd)  
  
 Se hai problemi di configurazione o tramite l'aggiornamento dei dati, vedere la [risoluzione dei problemi di aggiornamento dati PowerPivot](https://go.microsoft.com/fwlink/?LinkID=223279) pagina su wiki di TechNet per le soluzioni possibili.  
  
##  <a name="configAny"></a> Configurare un account di Windows per l'aggiornamento dei dati  
 Quando un utente di SharePoint definisce una pianificazione dell'aggiornamento dati, deve specificare l'identità utente con la quale verrà eseguito l'aggiornamento dati. Le possibilità includono la selezione dell'account di aggiornamento dati automatico PowerPivot, l'immissione dell'account utente di dominio di Windows o l'immissione di un altro account utente di Windows valido per l'aggiornamento dati. I passaggi riportati in questa sezione riguardano l'ultima opzione: immissione di un altro account utente di Windows.  
  
 È opportuno scegliere questo approccio quando si desidera avere un'alternativa all'utilizzo dell'account di aggiornamento dati PowerPivot automatico (disponibile a tutti gli utenti di PowerPivot in SharePoint) o delle credenziali del proprietario della cartella di lavoro. È ad esempio possibile rendere disponibile una serie di account di aggiornamento dati a diversi workgroup per agevolare le attività di controllo e gestione dell'aggiornamento dati al livello organizzativo.  
  
> [!IMPORTANT]  
>  Gli utenti e le applicazioni che utilizzano l'applicazione di destinazione e le credenziali che contiene devono essere elencati come membri dell'applicazione. È necessario aggiungere l'identità di ogni applicazione del servizio PowerPivot che utilizzerà l'applicazione di destinazione, l'account di Windows in uso e gli account utente o gruppo delle persone che specificheranno questa applicazione di destinazione nelle pianificazioni dell'aggiornamento dati. È possibile specificare tutti questi account quando si crea l'applicazione di destinazione. Se non si conoscono tutti gli account utente e gruppo che richiederanno l'accesso a questa applicazione, sarà possibile aggiungerli in un secondo momento dopo la creazione dell'applicazione di destinazione.  
  
 La configurazione delle credenziali archiviate per l'aggiornamento dati è suddivisa in quattro parti:  
  
-   Creare un'applicazione di destinazione in cui archiviare le credenziali.  
  
-   Concedere autorizzazioni di collaborazione all'account.  
  
-   Concedere le autorizzazioni di lettura dell'account per accedere alle origini dati esterne durante l'aggiornamento dati.  
  
-   Verificare che l'aggiornamento dati funzioni quando si specifica l'applicazione di destinazione nella pianificazione dell'aggiornamento dati.  
  
### <a name="step-1-create-a-target-application"></a>Passaggio 1: Creare un'applicazione di destinazione  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic su **Secure Store Service**.  
  
3.  In Gestione applicazioni di destinazione, fare clic su **New**.  
  
4.  In ID applicazione di destinazione digitare una stringa di testo. La stringa deve essere univoca, ma semplice da ricordare. Gli utenti devono digitare questa stringa nelle pagine di pianificazione dell'aggiornamento dati ogni volta che desiderano utilizzare le credenziali archiviate in questa applicazione.  
  
5.  In Nome visualizzato immettere un nome descrittivo. Questo nome viene utilizzato solo a scopo di visualizzazione, non viene utilizzato per specificare l'applicazione di destinazione nella pianificazione dell'aggiornamento dati.  
  
6.  In Posta elettronica contatto digitare l'indirizzo di posta elettronica.  
  
7.  Nel tipo di applicazione di destinazione, selezionare **gruppo**.  
  
    > [!IMPORTANT]  
    >  La scelta di un tipo di account gruppo è necessaria perché consente di specificare tutti gli account servizio e utente che richiedono l'accesso alle credenziali. Per ogni richiesta, il servizio di sistema PowerPivot verifica se il richiedente è un membro dell'applicazione di destinazione.  
  
8.  Ignorare l'URL della pagina dell'applicazione di destinazione. Non verrà utilizzato dall'aggiornamento dati PowerPivot.  
  
9. Scegliere **Avanti**.  
  
10. Nel **specificare i campi di credenziali per l'applicazione di destinazione Store sicura** pagina, accettare i valori predefiniti. I tipi e i nomi dei campi devono essere Nome utente Windows e Password Windows.  
  
11. Scegliere Avanti.  
  
12. In Amministratori dell'applicazione di destinazione specificare gli account utente di dominio di Windows degli utenti di SharePoint che devono disporre dell'accesso di amministratore per le impostazioni dell'applicazione di destinazione, ad esempio la possibilità di aggiungere o rimuovere account dall'elenco Membri.  
  
13. In Membri aggiungere gli account utenti e gruppi seguenti:  
  
    1.  Per l'utente che crea l'applicazione, aggiungere l'account utente di Windows all'elenco Membri.  
  
    2.  Aggiungere l'identità del pool di applicazioni dell'applicazione del servizio PowerPivot in modo che le credenziali vengano recuperate quando è pianificata l'esecuzione dell'aggiornamento dati. Per visualizzare l'identità del pool di applicazioni, passare a **Gestisci applicazioni di servizio**, selezionare l'applicazione di servizio PowerPivot facendo clic sullo spazio vuoto accanto al nome (viene selezionata la riga) e quindi fare clic su **proprietà**. L'account di sicurezza visualizzato in questa pagina è l'account da aggiungere come membro dell'applicazione di destinazione.  
  
    3.  Aggiungere gli account utente e gruppo di Windows che includeranno questa applicazione di destinazione nelle pianificazioni degli aggiornamenti dati.  
  
14. Fare clic su **OK**.  
  
15. Selezionare l'applicazione di destinazione appena creata, fare clic sulla freccia verso il basso e selezionare **impostare le credenziali.**  
  
16. In Proprietario credenziali si noti che l'elenco dei proprietari di credenziali è di sola lettura. Gli account che detengono la proprietà delle credenziali sono i membri dell'applicazione di destinazione. Per aggiungere o rimuovere un proprietario di credenziali, è necessario aggiungere o rimuovere account dall'elenco Membri dell'applicazione di destinazione.  
  
     In Nome utente di Windows e Password di Windows digitare le credenziali dell'account utente di Windows che verrà utilizzato per eseguire l'aggiornamento dati.  
  
17. Fare clic su **OK**.  
  
###  <a name="bkmk_grant"></a> Passaggio 2: Concedere le autorizzazioni di collaborazione all'account  
 Prima di poter utilizzare le credenziali archiviate, è necessario assegnare all'account le autorizzazioni di collaborazione per tutte le cartelle di lavoro di PowerPivot per le quali viene utilizzato. Questo livello di autorizzazione è necessario per aprire la cartella di lavoro da una libreria, quindi per salvarla di nuovo nella libreria dopo aver aggiornato i dati.  
  
 L'assegnazione di autorizzazioni è un passaggio effettuato dall'amministratore della raccolta siti. Le autorizzazioni di SharePoint possono essere assegnate a livello della raccolta siti radice o a qualsiasi livello inferiore, inclusi singoli documenti ed elementi. La modalità di impostazione delle autorizzazioni varierà a seconda del relativo livello di granularità necessario. Nei passaggi seguenti verrà illustrato un approccio di concessione delle autorizzazioni.  
  
1.  In un sito di SharePoint in Azioni sito fare clic su **autorizzazioni sito**.  
  
2.  Fare clic su **Concedi autorizzazioni**.  
  
3.  In Seleziona utenti digitare il nome dell'account utente di dominio di Windows specificato nell'applicazione di destinazione.  
  
4.  In Concedi autorizzazioni selezionare **concedere agli utenti autorizzazioni direttamente**.  
  
5.  Selezionare **collaborazione**, quindi fare clic su **OK**.  
  
###  <a name="bkmk_dbread"></a> Passaggio 3: Concessione di autorizzazioni di lettura per accedere alle origini dati esterne utilizzate nell'aggiornamento dati  
 Durante l'importazione di dati in una cartella di lavoro di PowerPivot, le connessioni a dati esterni spesso si basano su connessioni trusted o connessioni rappresentate in cui viene utilizzata l'identità dell'utente corrente per connettersi all'origine dati. Questi tipi di connessioni funzionano solo quando l'utente corrente dispone dell'autorizzazione di lettura per i dati che importa.  
  
 In uno scenario di aggiornamento dati, la stessa stringa di connessione utilizzata per importare i dati viene ora riutilizzata per aggiornare i dati. Se nella stringa di connessione si presuppone l'utente corrente, ad esempio è incluso Integrated_Security=SSPI, il servizio di sistema PowerPivot passerà l'identità utente specificata nell'applicazione di destinazione come utente corrente. Questa connessione potrà essere stabilita solo se l'account dispone delle autorizzazioni di lettura per l'origine dati esterna.  
  
 Per questo motivo, è necessario concedere all'account le autorizzazioni di sola lettura per tutte le origini dati esterne utilizzate durante l'aggiornamento dati.  
  
 Un amministratore delle origini dati utilizzate nell'organizzazione può creare un account di accesso e assegnare le autorizzazioni necessarie. In caso contrario, è necessario contattare i proprietari dei dati e fornire le informazioni sull'account. Assicurarsi di specificare l'account utente di dominio di Windows di cui è possibile eseguire il mapping all'applicazione di destinazione. Si tratta dell'account specificato nel "passaggio 1: Creare un'applicazione di destinazione"in questo argomento.  
  
###  <a name="bkmk_verify"></a> Passaggio 4: Verificare la disponibilità dell'account nelle pagine di configurazione di aggiornamento dati  
  
1.  Aprire una pagina di configurazione dell'aggiornamento dati per una cartella di lavoro pubblicata che contiene dati PowerPivot. Per istruzioni su come aprire la pagina, vedere [pianificare un aggiornamento dei dati &#40;PowerPivot per SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
2.  Verificare che il **connettersi utilizzando le credenziali salvate in Secure Store Service (SSS) per accedere all'origine dati** opzione è abilitata nella pagina di configurazione dell'aggiornamento dati e quindi immettere il nome dell'applicazione di destinazione.  
  
3.  Selezionare il **aggiorna anche appena possibile** casella di controllo, quindi fare clic su **OK**.  
  
4.  Nella raccolta che contiene la cartella di lavoro, selezionare la cartella di lavoro, fare clic sulla freccia giù visualizzata a destra e quindi selezionare **Gestisci aggiornamento dati PowerPivot**. Potrebbe essere necessario attendere alcuni minuti se il processo di aggiornamento dati restituisce una grande quantità di dati.  
  
 Se si verifica un errore, è possibile fare clic su **configura pianificazione** nei dati di aggiornare la pagina della cronologia per provare credenziali diverse. Potrebbe inoltre essere necessario analizzare le informazioni di connessione dell'origine dati nella cartella di lavoro originale per visualizzare la stringa di connessione utilizzata durante l'aggiornamento dati. Nella stringa di connessione vengono fornite informazioni sul percorso del server e sul database che è possibile utilizzare per risolvere il problema.  
  
 Per altre informazioni sulla risoluzione dei problemi, vedere [risoluzione dei problemi di aggiornamento dati PowerPivot](https://go.microsoft.com/fwlink/p/?LinkID=223279) su Wiki di TechNet.  
  
##  <a name="config3rd"></a> Configurare un account predefinito per l'accesso alle origini dati esterne o di terze parti  
 I server di database vengono spesso forniti con propri metodi di autenticazione. Se si dispone di una cartella di lavoro di PowerPivot che richiede credenziali di database per accedere a un'origine dati esterna durante un aggiornamento dati, è possibile creare un ID dell'applicazione di destinazione per le credenziali, quindi specificare l'applicazione di destinazione nella sezione Origini dati della pagina di aggiornamento dati pianificato.  
  
 Questo passaggio è necessario solo se si desidera fornire agli utenti un'opzione di override delle credenziali del database già incorporate nella cartella di lavoro di PowerPivot.  
  
 Questo passaggio funziona solo se la stringa di connessione include già un nome utente e una password. Si noti che solo raramente la stringa di connessione contiene credenziali, pertanto la possibilità di utilizzare questa opzione è alquanto limitata. Nella maggior parte dei casi, la stringa di connessione contiene unicamente ID utente e password se si utilizza l'autenticazione del database per la connessione all'origine dati. Per altre informazioni su come verificare la stringa di connessione per verificare che includa un ID utente e password, vedere la sezione "Concedere autorizzazioni per creare pianificazioni e accedere ai dati esterni" in [aggiornamento dati PowerPivot con SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).  
  
1.  In Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic su **Secure Store Service**.  
  
3.  In Gestione applicazioni di destinazione, fare clic su **New**.  
  
4.  In ID applicazione di destinazione digitare una stringa di testo. La stringa deve essere univoca, ma semplice da ricordare. Gli utenti devono digitare questa stringa nelle pagine di pianificazione dell'aggiornamento dati ogni volta che desiderano utilizzare le credenziali archiviate in questa applicazione.  
  
5.  In Nome visualizzato immettere un nome descrittivo. Questo nome viene utilizzato solo a scopo di visualizzazione, non viene utilizzato per specificare l'applicazione di destinazione nella pianificazione dell'aggiornamento dati.  
  
6.  In Posta elettronica contatto digitare l'indirizzo di posta elettronica.  
  
7.  Nel tipo di applicazione di destinazione, selezionare **gruppo**.  
  
8.  Ignorare l'URL della pagina dell'applicazione di destinazione. Non verrà utilizzato dall'aggiornamento dati PowerPivot.  
  
9. Scegliere **Avanti**.  
  
10. Nel **specificare i campi di credenziali per l'applicazione di destinazione Store sicura** pagina, accettare i valori predefiniti solo se l'origine dati utilizza l'autenticazione di Windows. In caso contrario, scegliere i tipi di campo validi per l'origine dati, quindi modificare i nomi dei campi in base al tipo.  
  
     È ad esempio possibile specificare il nome utente e la password di SQL Server per i nomi dei campi, quindi scegliere Nome utente e Password per i tipi dei campi.  
  
11. Scegliere Avanti.  
  
12. In Amministratori dell'applicazione di destinazione specificare gli account utente di dominio di Windows degli utenti di SharePoint che devono disporre dell'accesso di amministratore per le impostazioni dell'applicazione.  
  
13. In Membri aggiungere gli account utenti e gruppi seguenti:  
  
    1.  Per l'utente che crea l'applicazione, aggiungere l'account utente di Windows all'elenco Membri.  
  
    2.  Aggiungere l'identità del pool di applicazioni di ogni applicazione del servizio PowerPivot che utilizzerà l'applicazione di destinazione per accedere alle relative credenziali archiviate. Per visualizzare l'identità, passare a **Gestisci applicazioni di servizio**, selezionare l'applicazione di servizio PowerPivot facendo clic sullo spazio vuoto accanto al nome (viene selezionata la riga) e quindi fare clic su **proprietà**. L'account di sicurezza visualizzato in questa pagina è l'account da aggiungere come membro dell'applicazione di destinazione.  
  
    3.  Aggiungere gli account utente e gruppo di Windows che includeranno questa applicazione nella sezione origini dati di una pagina di pianificazione dell'aggiornamento dati.  
  
14. Fare clic su **OK**.  
  
15. Selezionare l'applicazione di destinazione appena creata, fare clic sulla freccia verso il basso e selezionare **impostare le credenziali.**  
  
16. Immettere le credenziali che verranno utilizzate per la connessione all'origine dati, ad esempio il nome utente e la password di un accesso di SQL Server.  
  
17. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pianificare un aggiornamento di dati &#40;PowerPivot per SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [Aggiornamento dati PowerPivot con SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
