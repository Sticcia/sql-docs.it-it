---
title: "Abilitare e disabilitare la funzionalità RDL Sandboxing | Documenti Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5619e9f-ec5b-4376-9b34-1f74de6fade7
caps.latest.revision: 9
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2a435c6f6b5dc2d9df676f504837393d448820a4
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="enable-and-disable-rdl-sandboxing"></a>Abilitare e disabilitare la funzionalità RDL Sandboxing
  La caratteristica RDL (Report Definition Language) Sandboxing consente di rilevare e limitare l'utilizzo di tipi specifici di risorse in base a singoli tenant in un ambiente in cui più tenant utilizzano una sola Web farm di server di report. Un esempio di questo tipo è rappresentato dai servizi di hosting in cui è possibile gestire una sola Web farm di server di report utilizzati da più tenant e probabilmente da società diverse. L'amministratore del server di report può abilitare questa caratteristica per ottenere gli obiettivi seguenti:  
  
-   Limitare le dimensioni delle risorse esterne. Le risorse esterne includono immagini, file con estensione xslt e dati mappa.  
  
-   Al momento della pubblicazione del report, limitare i tipi e i membri utilizzati nel testo dell'espressione.  
  
-   Al momento dell'elaborazione del report, limitare la lunghezza del testo e le dimensioni del valore restituito per le espressioni.  
  
 Quando RDL Sandboxing è abilitato, sono disabilitate le caratteristiche seguenti:  
  
-   Codice personalizzato nel  **\<codice >** elemento di una definizione di report.  
  
-   Modalità di compatibilità con le versioni precedenti di RDL per gli elementi di report personalizzati di [!INCLUDE[ssRSversion2005](../../includes/ssrsversion2005-md.md)] .  
  
-   Parametri denominati nelle espressioni.  
  
 In questo argomento viene descritto ciascun elemento di \< **rdlsandboxing è**> elemento nel file RSReportServer. config. Per altre informazioni su come modificare questo file, vedere [Modificare un file di configurazione di Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md). Attività dei record del log di traccia del server correlata alla caratteristica RDL Sandboxing. Per altre informazioni sui log di traccia, vedere [Log di traccia del servizio del server di report](../../reporting-services/report-server/report-server-service-trace-log.md).  
  
## <a name="example-configuration"></a>Configurazione di esempio  
 L'esempio seguente mostra le impostazioni e i valori di esempio per il \< **rdlsandboxing è**> elemento nel file RSReportServer. config.  
  
```  
<RDLSandboxing>  
   <MaxExpressionLength>5000</MaxExpressionLength>  
   <MaxResourceSize>5000</MaxResourceSize>  
   <MaxStringResultLength>3000</MaxStringResultLength>  
   <MaxArrayResultLength>250</MaxArrayResultLength>  
   <Types>  
      <Allow Namespace=”System.Drawing” AllowNew=”True”>Bitmap</Allow>  
      <Allow Namespace=”TypeConverters.Custom” AllowNew=”True”>*</Allow>  
   </Types>  
   <Members>  
      <Deny>Format</Deny>  
      <Deny>StrDup</Deny>  
   </Members>  
</RDLSandboxing>  
```  
  
## <a name="configuration-settings"></a>Impostazioni di configurazione  
 Nella tabella seguente sono contenute le informazioni sulle impostazioni di configurazione. Le impostazioni sono elencate nell'ordine in cui vengono visualizzate nel file di configurazione.  
  
|Impostazione|Description|  
|-------------|-----------------|  
|**MaxExpressionLength**|Numero massimo di caratteri consentiti nelle espressioni RDL.<br /><br /> Valore predefinito: 1000|  
|**MaxResourceSize**|Numero massimo di KB consentiti per una risorsa esterna.<br /><br /> Valore predefinito: 100|  
|**MaxStringResultLength**|Numero massimo di caratteri consentiti in un valore restituito per un'espressione RDL.<br /><br /> Valore predefinito: 1000|  
|**MaxArrayResultLength**|Numero massimo di elementi consentiti in un valore restituito della matrice per un'espressione RDL.<br /><br /> Valore predefinito: 100|  
|**Tipi**|Elenco di membri da consentire nelle espressioni RDL.|  
|**Allow**|Tipo o set di tipi da consentire nelle espressioni RDL.|  
|**Spazio dei nomi**|Attributo per **Allow** che è lo spazio dei nomi contenente uno o più tipi applicabili a Value. Questa proprietà supporta la distinzione tra maiuscole e minuscole.|  
|**AllowNew**|Attributo booleano per **Consenti** che controlla se nuove istanze del tipo possono essere creati nelle espressioni RDL o in un RDL  **\<classe >** elemento.<br /><br /> Nota: quando **RDLSandboxing** è abilitato, non è possibile creare nuove matrici in espressioni RDL, indipendentemente dall'impostazione di **AllowNew**.|  
|**Valore**|Valore per **Allow** che è il nome del tipo da consentire nelle espressioni RDL. Il valore **\*** indica che sono consentiti tutti i tipi nello spazio dei nomi. Questa proprietà supporta la distinzione tra maiuscole e minuscole.|  
|**Membri**|Per l'elenco dei tipi inclusi nel  **\<tipi >** elemento, l'elenco dei nomi dei membri che non sono consentiti nelle espressioni RDL.|  
|**Nega**|Nome di un membro non consentito nelle espressioni RDL. Questa proprietà supporta la distinzione tra maiuscole e minuscole.<br /><br /> Nota: quando per un membro è specificato **Deny** , non è consentito alcun membro con questo nome per nessun tipo.|  
  
## <a name="working-with-expressions-when-rdl-sandboxing-is-enabled"></a>Utilizzo delle espressioni con RDL Sandboxing abilitato  
 È possibile modificare la caratteristica RDL Sandboxing per facilitare la gestione delle risorse utilizzate da un'espressione nelle modalità seguenti:  
  
-   Limitare il numero di caratteri utilizzati per un'espressione.  
  
-   Limitare le dimensioni del risultato restituito da un'espressione.  
  
-   Consentire un elenco specifico di tipi che possono essere utilizzati in un'espressione.  
  
-   Limitare l'elenco dei membri in base al nome per l'elenco dei tipi consentiti che possono essere utilizzati in un'espressione.  
  
-   La caratteristica RDL Sandboxing consente di creare un elenco di tipi approvati e un elenco di membri non autorizzati. L'elenco dei tipi approvati viene denominato elenco consentiti mentre l'elenco di membri non autorizzati viene denominato elenco bloccati.  
  
> [!NOTE]  
>  Nella definizione del report, un computer non può conoscere il tipo di ogni istanza di un riferimento all'espressione. Quando si aggiunge un membro all'elenco bloccati, vengono negati tutti i membri con quel nome in tutti i tipi nell'elenco consentiti.  
  
 I risultati dell'espressione RDL vengono verificati in fase di esecuzione. Le espressioni RDL vengono verificate nella definizione del report durante la pubblicazione di quest'ultimo. Monitorare il log di traccia del server di report relativamente alle violazioni. Per altre informazioni, vedere [Report Server Service Trace Log](../../reporting-services/report-server/report-server-service-trace-log.md).  
  
### <a name="working-with-types"></a>Utilizzo dei tipi  
 Quando si aggiunge un tipo all'elenco consentiti, vengono controllati i punti di ingresso seguenti per l'accesso alle espressioni RDL:  
  
-   Membri statici di un tipo.  
  
-   Metodo [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] **New** method.  
  
-   Il  **\<classi >** elemento nella definizione del report.  
  
-   Membri aggiunti all'elenco bloccati per un tipo nell'elenco consentiti.  
  
 L'elenco consentiti non controlla i punti di ingresso seguenti:  
  
-   Set di dati del report. I campi nei set di dati del report restituiti dalle query potrebbero contenere qualsiasi tipo RDL valido.  
  
-   Parametri di report. I valori dei parametri forniti dall'utente potrebbero contenere qualsiasi tipo RDL valido.  
  
-   Membri di un tipo abilitato non inclusi nell'elenco bloccati. Per impostazione predefinita, vengono abilitati tutti i membri di tutti i tipi nell'elenco consentiti. Quando si aggiunge il nome di un membro all'elenco bloccati, vengono negati tutti i membri con quel nome in tutti i tipi nell'elenco consentiti.  
  
 Per abilitare un membro di un tipo ma negare un membro con lo stesso nome per un tipo diverso, è necessario eseguire le operazioni seguenti:  
  
-   Aggiungere un  **\<Deny >** elemento per il nome del membro.  
  
-   Creare un membro proxy con un nome diverso in una classe di un assembly personalizzato per il membro che si desidera abilitare.  
  
-   Aggiungere la nuova classe all'elenco consentiti.  
  
 Per aggiungere funzioni .NET Framework di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] all'elenco degli elementi consentiti, aggiungere i tipi corrispondenti dallo spazio dei nomi Microsoft.VisualBasic all'elenco.  
  
 Per aggiungere le parole chiave tipo di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET Framework all'elenco consentiti, aggiungere il tipo CLR corrispondente all'elenco consentiti. Ad esempio, per usare il [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (parola chiave) di .NET Framework **intero**, aggiungere il seguente frammento XML per il  **\<rdlsandboxing è >** elemento:  
  
```  
<Allow Namespace="System">Int32</Allow>  
```  
  
 Per aggiungere un tipo che ammette valori Null o un tipo generico .NET Framework di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , è necessario eseguire le operazioni seguenti:  
  
-   Creare un tipo proxy per il tipo generico o che ammette valori Null di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET Framework.  
  
-   Aggiungere il tipo di proxy all'elenco consentiti.  
  
 L'aggiunta di un tipo da un assembly personalizzato all'elenco consentiti non concede in modo implicito autorizzazioni di esecuzione sull'assembly. È necessario modificare in modo specifico il file di sicurezza per l'accesso al codice e fornire autorizzazioni di esecuzione all'assembly. Per altre informazioni, vedere [Sicurezza dall'accesso di codice in Reporting Services](../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md).  
  
#### <a name="maintaining-the-deny-list-of-members"></a>Gestione di \<Nega > elenco di membri  
 Quando si aggiunge un nuovo tipo all'elenco consentiti, attenersi all'elenco seguente per determinare quando potrebbe essere necessario aggiornare l'elenco dei membri bloccati:  
  
-   Quando si aggiorna un assembly personalizzato con una versione che introduce nuovi tipi.  
  
-   Quando si aggiungono membri ai tipi nell'elenco consentiti.  
  
-   Quando si aggiorna [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] nel server di report.  
  
-   Quando si aggiorna il server di report a una versione successiva di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Quando si aggiorna un server di report per gestire uno schema RDL successivamente, dal momento che è probabile che nuovi membri siano stati aggiunti ai tipi RDL.  
  
### <a name="working-with-operators-and-new"></a>Utilizzo di operatori e dell'operatore New  
 Per impostazione predefinita, gli operatori di linguaggio .NET Framework di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] sono sempre consentiti, ad eccezione di **New**. Il **New** operatore è controllato dal **AllowNew** attributo la  **\<Consenti >** elemento. Altri operatori di linguaggio, come l'operatore della funzione di accesso alla raccolta predefinito **!**, e le macro di cast .NET Framework di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , come **CInt**, sono sempre consentiti.  
  
 L'aggiunta di operatori, inclusi quelli personalizzati, a un elenco bloccati non è supportata. Per escludere operatori per un tipo, è necessario effettuare le operazioni seguenti:  
  
-   Creare un tipo di proxy che non implementa gli operatori che si desidera escludere.  
  
-   Aggiungere il tipo di proxy all'elenco consentiti.  
  
 Per creare una nuova matrice in un'espressione RDL, creare la matrice in un metodo in una classe definita e aggiungere quella classe all'elenco consentiti.  
  
 Per creare una nuova matrice in un'espressione RDL, è necessario eseguire le operazioni seguenti:  
  
-   Definire una nuova classe e creare la matrice in un metodo in quella classe.  
  
-   Aggiungere la classe all'elenco consentiti.  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Log di traccia del servizio Server di report](../../reporting-services/report-server/report-server-service-trace-log.md)  
  
  