---
title: Guida di riferimento alla configurazione Web (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- web configuration file [Master Data Services]
ms.assetid: b8cc9a35-97ab-4fe0-ab4b-c07f13d9793a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ee3582e7de37b99cd7f665f563e789259954b722
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65478478"
---
# <a name="web-configuration-reference-master-data-services"></a>Guida di riferimento alla configurazione Web (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] usa un file Web.config per le impostazioni di configurazione che consentono a Internet Information Services (IIS) di ospitare il servizio Web e l'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Questo file Web.config si trova nella cartella WebApplication nel percorso di installazione [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Per altre informazioni sul percorso e le autorizzazioni, vedere [Autorizzazioni per file e cartelle &#40;Master Data Services&#41;](folder-and-file-permissions-master-data-services.md).  
  
## <a name="webconfig-elements"></a>Elementi di Web.Config  
 Il file Web.config contiene un elemento [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] personalizzato, **\<masterDataServices>**, oltre agli elementi di configurazione IIS, .NET Framework, ASP.NET e Windows Communication Foundation (WCF) standard. Nella tabella seguente vengono descritti gli elementi inclusi nel file Web.config.  
  
|Elemento di configurazione|Descrizione|  
|---------------------------|-----------------|  
|`masterDataServices`|Elemento Custom. Connette il servizio Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] a un database di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|`connectionStrings`|Elemento ASP.NET. Per altre informazioni, vedere [Elemento connectionStrings (schema delle impostazioni ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178347) in MSDN Library.|  
|`system.web`|Elemento ASP.NET. Per altre informazioni, vedere [Elemento system.web (schema delle impostazioni ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178348) in MSDN Library.|  
|`startup`|Elemento .NET Framework. Per altre informazioni, vedere [\<Elemento> startup](https://go.microsoft.com/fwlink/?LinkId=178349) in MSDN Library.|  
|`runtime`|Elemento .NET Framework. Per altre informazioni, vedere [\<Elemento > runtime](https://go.microsoft.com/fwlink/?LinkId=178350) in MSDN Library.|  
|`system.codedom`|Elemento .NET Framework. Per altre informazioni, vedere [\<Elemento> system.codedom](https://go.microsoft.com/fwlink/?LinkId=178351) in MSDN Library.|  
|`system.web.extensions`|Elemento ASP.NET. Per altre informazioni, vedere [Elemento system.web.extensions (schema delle impostazioni ASP.NET)](https://go.microsoft.com/fwlink/?LinkId=178352) in MSDN Library.|  
|`system.webServer`|Gruppo di sezioni che contiene gli elementi IIS. Per altre informazioni, vedere [system.webServer Section Group \[IIS 7 Settings Schema\]](https://go.microsoft.com/fwlink/?LinkId=178353) (Gruppo di sezioni system.webServer (schema delle impostazioni IIS 7)) in MSDN Library.|  
|`system.serviceModel`|Elemento WCF. Per altre informazioni, vedere [\<system.serviceModel>](https://go.microsoft.com/fwlink/?LinkId=178354) in MSDN Library.|  
|`system.diagnostics`|Elemento .NET Framework. Per altre informazioni, vedere [\<Elemento> system.diagnostics](https://go.microsoft.com/fwlink/?LinkId=178355) in MSDN Library.|  
|`appSettings`|Elemento ASP.NET. Per altre informazioni, vedere [Elemento appSettings (schema delle impostazioni generali)](https://go.microsoft.com/fwlink/?LinkId=178356) in MSDN Library.|  
  
## <a name="masterdataservices-element"></a>Elemento masterdataservices  
 L'elemento **\<masterDataServices>** è un elemento personalizzato usato per connettere un servizio Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] a un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
### <a name="syntax"></a>Sintassi  
  
```  
<masterDataServices>  
   <instance virtualPath="path" siteName="name" connectionName="name" serviceName="name" />  
</masterDataServices>  
```  
  
### <a name="elements-and-attributes"></a>Elementi e attributi  
  
|Elemento|Descrizione|  
|----------|-----------------|  
|`instance`|Elemento figlio. Contiene gli attributi che specificano le informazioni per la stringa di connessione al database e al servizio Web.|  
|`virtualPath`|Attributo. Specifica il percorso virtuale del servizio e dell'applicazione Web di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Corrisponde al `path` attributo del  **\<applicazione >** elemento sotto il  **\<sito >** elemento nel file ApplicationHost. config IIS.|  
|`siteName`|Attributo. Specifica il nome del sito che ospita il servizio e l'applicazione Web di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Corrisponde al `name` attributo del  **\<site >** elemento sotto  **\<siti >** nel file ApplicationHost. config IIS.|  
|`connectionName`|Attributo. Specifica il nome della connessione da utilizzare. Corrisponde al `name` attributo del  **\<aggiungere >** elemento sotto il  **\<connectionStrings >** in Web. config.|  
|`serviceName`|Attributo. Specifica il nome del servizio Web. Corrisponde al `name` attributo del  **\<servizio >** elemento sotto il  **\<services >** in Web. config.|  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un servizio denominato MDS1 nel sito di Contoso e nel percorso /MDS mediante una stringa di connessione specificata da MDSDB.  
  
```  
<masterDataServices>  
   <instance virtualPath="/MDS" siteName="Contoso" connectionName="MDSDB" serviceName="MDS1" />  
</masterDataServices>  
```  
  
  
