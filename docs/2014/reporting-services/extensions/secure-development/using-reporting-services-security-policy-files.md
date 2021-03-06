---
title: Using Reporting Services Security Policy Files (Uso di file di criteri di sicurezza di Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- CodeGroup elements
- configuration files [Reporting Services]
- code access security [Reporting Services], security policies
- security policies [Reporting Services]
- security configuration files [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: 2280fff6-3de7-44b1-87da-5db0ec975928
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ee7ba55e48f4704c912e92a4d8352e7c891c06b6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989680"
---
# <a name="using-reporting-services-security-policy-files"></a>Utilizzo di file di criteri di sicurezza di Reporting Services
  In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] le informazioni sui criteri di sicurezza dei componenti sono archiviate in tre file di configurazione che vengono copiati nel file system durante l'installazione. Questi file possono contenere una combinazione di criteri di sicurezza per uso interno e definiti dall'utente per gli assembly del codice in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. I tre file di configurazione corrispondono alle tre componenti di entità a protezione diretta [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]: Finestra di anteprima di server di report e del servizio Windows, l'applicazione Web gestione Report e progettazione Report.  
  
> [!NOTE]  
>  In Progettazione report sono disponibili due modalità di anteprima, ovvero la scheda di anteprima e la finestra popup di anteprima visualizzate quando il Progetto report viene avviato in modalità **DebugLocal**. La scheda **Anteprima** non è un componente a protezione diretta e non applica alcuna impostazione dei criteri di sicurezza. La finestra di anteprima consente di simulare le funzionalità del server di report e pertanto dispone di un file di configurazione di criteri che l'utente o un amministratore deve modificare per utilizzare assembly ed estensioni personalizzati in Progettazione report.  
  
 I file di configurazione dei criteri di sicurezza contengono informazioni sulle classi di sicurezza, alcuni set di autorizzazioni denominati predefiniti e i gruppi di codice per gli assembly di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. I file di configurazione dei criteri di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sono simili al file Security.config che determina la gerarchia dei gruppi di codice e i set di autorizzazioni associati al computer e i criteri a livello aziendale in [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Il percorso di questo file è C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config.  
  
## <a name="policy-files-in-reporting-services"></a>File di criteri di Reporting Services  
 Nella tabella seguente vengono elencati i file di configurazione dei criteri di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], i percorsi (presupponendo un'installazione predefinita) e le rispettive funzioni.  
  
|Nome file|Percorso (installazione predefinita)|Descrizione|  
|---------------|---------------------------------------|-----------------|  
|rssrvpolicy.config|C:\Programmi\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer|File di configurazione dei criteri del server di report. Questi criteri di sicurezza influiscono principalmente sulle espressioni del report e sugli assembly personalizzati dopo che un report è stato distribuito in un server di report. Questo file di criteri influisce inoltre sulle estensioni per i dati personalizzati, il recapito e il rendering e sulle estensioni di sicurezza distribuite nel server di report.|  
|rsmgrpolicy.config|C:\Programmi\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager|File di configurazione dei criteri di Gestione report. Questi criteri di sicurezza influiscono su tutti gli assembly che estendono Gestione report; ad esempio estensioni dell'interfaccia utente della sottoscrizione per il recapito personalizzato.|  
|rspreviewpolicy.config|C:\Programmi\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies|File di configurazione autonomo dei criteri di anteprima di Progettazione report. Questi criteri di sicurezza influiscono sugli assembly personalizzati e sulle espressioni del report utilizzate nei report durante l'anteprima e lo sviluppo. Questi criteri influiscono inoltre su estensioni personalizzate, ad esempio estensioni per l'elaborazione dei dati, distribuite in Progettazione report.|  
  
## <a name="modifying-configuration-files"></a>Modifica dei file di configurazione  
 Le impostazioni di configurazione sono specificate come elementi o attributi XML. Se si conoscono il linguaggio XML e i file di configurazione, è possibile utilizzare un editor di testo o di codice per modificare le impostazioni definibili dall'utente. I file di configurazione della sicurezza contengono informazioni sulla gerarchia dei gruppi di codice e sui set di autorizzazioni associati a un livello di criteri in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Si consiglia di utilizzare lo strumento di configurazione di .NET Framework (Mscorcfg.msc) o lo strumento Criteri di sicurezza dall'accesso di codice (Caspol.exe) per modificare innanzitutto i criteri di sicurezza nel file Security.config, in modo che le modifiche dei criteri corrispondono agli elementi di configurazione XML validi per i file di criteri. Dopo avere eseguito questa operazione, è possibile tagliare e incollare i nuovi gruppi di codice e i nuovi set di autorizzazioni dal file Security.config a quello di criteri per il componente cui vengono aggiunte le autorizzazioni per il codice.  
  
> [!IMPORTANT]  
>  Prima di apportare qualsiasi modifica, è necessario eseguire il backup dei file di configurazione dei criteri.  
  
 L'utilizzo di questo approccio consente di realizzare due obiettivi. Innanzitutto è possibile utilizzare uno strumento di visualizzazione per compilare i gruppi di codice e i set di autorizzazioni per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Questa operazione risulta più semplice rispetto alla definizione di elementi di configurazione XML. In secondo luogo, si ottiene la certezza di non danneggiare i file di configurazione dei criteri di sicurezza con elementi XML e attributi in formato non valido. Per ulteriori informazioni sull'utilità Criteri di sicurezza dall'accesso di codice, vedere Utilizzo di file di criteri di sicurezza di Reporting Services in MSDN.  
  
 Prima di modificare i file di configurazione dei criteri, si consiglia di leggere tutte le informazioni disponibili in questi sezione e negli argomenti correlati. La modifica della configurazione dei criteri in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] può avere un impatto significativo in termini di sicurezza sulle modalità in cui i componenti di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] eseguono moduli di codice esterno.  
  
## <a name="placement-of-codegroup-elements-for-extensions"></a>Posizione di elementi CodeGroup per le estensioni  
 La posizione degli elementi CodeGroup in un file di criteri di sicurezza è importante. Per le estensioni e gli assembly personalizzati sviluppati, è consigliabile che i gruppi di codice personalizzati vengano posizionati direttamente sotto la voce esistente per l'appartenenza URL "$CodeGen$/*", come indicato nell'esempio seguente:  
  
```  
<CodeGroup  
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust">  
    <IMembershipCondition   
        class="UrlMembershipCondition"  
        version="1"  
        Url="$CodeGen$/*"  
    />  
</CodeGroup>  
<CodeGroup   
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust"  
    Name="MyCustomCodeGroup"  
    Description="Code group for my custom extension">  
        <IMembershipCondition class="UrlMembershipCondition"  
        version="1"  
        Url="C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\bin\MyAssembly.dll"  
        />  
</CodeGroup>  
```  
  
 È possibile aggiungere gruppi di codice aggiuntivi uno dopo l'altro.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui criteri di sicurezza](understanding-security-policies.md)  
  
  
