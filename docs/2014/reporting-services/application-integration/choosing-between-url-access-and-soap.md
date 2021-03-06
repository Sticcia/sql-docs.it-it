---
title: Scelta tra accesso con URL e SOAP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], vs. URL access
- Report Server Web service, application integration
- URL access [Reporting Services], vs. SOAP
- Web service [Reporting Services], application integration
ms.assetid: bccdc243-4366-4ce5-8e63-3dd6c463fa52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 070d37a1e6ca210694d16ab593e9de40882611f5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192986"
---
# <a name="choosing-between-url-access-and-soap"></a>Scelta tra accesso con URL e SOAP
  L'integrazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni personalizzate può risultare complessa. La complessità non è tuttavia dovuta al modello di programmazione o alle API, ma alle numerose modalità di integrazione disponibili. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è stato progettato interamente come piattaforma di sviluppo e, in quanto tale, offre flessibilità di programmazione. Alla flessibilità è associata l'esigenza di prendere decisioni importanti relativamente all'integrazione delle funzionalità di navigazione e gestione dei report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni aziendali esistenti.  
  
 ![Scenari di programmazione di Reporting Services](../../../2014/reporting-services/media/bk-ext-04.gif "Reporting Services, gli scenari di programmazione")  
La programmazione in Reporting Services supporta un'ampia gamma di scenari.  
  
 Esistono due modi per integrare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni personalizzate: Accesso con URL e l'API SOAP di Reporting Services. La modalità da utilizzare dipende da diversi fattori. In alcuni casi, l'integrazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni aziendali personalizzate richiede l'utilizzo sia dell'accesso con URL che di SOAP. È necessario porsi le domande seguenti:  
  
-   Quali tipi di funzionalità di creazione di report aziendali sono necessari? È necessario disporre di un modo semplice per avviare e navigare tra i report oppure sono necessarie caratteristiche di gestione del server di report più avanzate per la soluzione aziendale personalizzata?  
  
-   In quale tipo di ambiente operano in genere gli utenti? L'applicazione aziendale è un'applicazione Web o un'applicazione Windows? Con quanta facilità gli utenti finali possono passare da un ambiente Win32 a un ambiente Web? Quale tipo di controllo è necessario sull'ambiente in cui i report vengono eseguiti e gestiti?  
  
 Dopo aver risposto alle domande precedenti, è possibile scegliere come integrare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nella propria infrastruttura IT. In genere, l'accesso con URL è preferibile per la visualizzazione e la navigazione di singoli report. L'accesso con URL consente di navigare tra i report in modo semplice e rapido senza l'overhead del servizio Web. L'accesso con URL, inoltre, è attualmente l'unica tecnica di programmazione che utilizza la versione completa del Visualizzatore HTML per la navigazione dei report, che include la barra degli strumenti dei report. L'accesso con URL garantisce inoltre prestazioni migliori rispetto a SOAP in quanto consente di ignorare il marshalling delle richieste SOAP da e verso il server. Negli scenari di integrazione in cui è necessario poter accedere in modo rapido e semplice ai report con gli strumenti predefiniti di visualizzazione e navigazione, l'accesso con URL rappresenta la scelta migliore.  
  
> [!NOTE]  
>  L'accesso con URL al server di report supporta il Visualizzatore HTML e la funzionalità estesa della barra degli strumenti dei report. L'API SOAP non supporta questo tipo di report visualizzabile. Se si esegue il rendering dei report utilizzando SOAP, è necessario progettare e sviluppare una barra degli strumenti dei report personalizzata.  
  
 Per altre informazioni sulla barra degli strumenti dei report, vedere [Visualizzatore HTML e barra degli strumenti dei report](../html-viewer-and-the-report-toolbar.md).  
  
 Per altre informazioni sull'accesso tramite URL, vedere [l'accesso con URL &#40;SSRS&#41;](../url-access-ssrs.md).  
  
 L'accesso con URL è utile per la visualizzazione dei report, ma non fornisce le funzionalità di gestione degli spazi dei nomi e dei report che possono essere essenziali per qualsiasi scenario aziendale di creazione di report. In questo caso, è consigliabile utilizzare le ampie e ricche funzionalità dell'API SOAP di Reporting Services. Con l'API SOAP è possibile gestire e distribuire report, creare pianificazioni, configurare le proprietà del server, gestire lo spazio dei nomi del server di report, creare sottoscrizioni e altro ancora. L'API SOAP espone il set completo di funzionalità di gestione in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. L'API SOAP può consentire inoltre la visualizzazione e la navigazione dei report tramite il metodo <xref:ReportExecution2005.ReportExecutionService.Render%2A> dell'API. La visualizzazione dei report tramite l'API SOAP non consente tuttavia l'abilitazione delle funzionalità di visualizzazione predefinite della barra degli strumenti dei report, né la gestione automatica dell'interattività dei report fornita dall'accesso con URL.  
  
 Per altre informazioni sull'API SOAP di Reporting Services, vedere [Servizio Web ReportServer](../report-server-web-service/report-server-web-service.md).  
  
 Nella maggior parte dei casi, l'accesso con URL e le chiamate SOAP sono entrambi necessari per soddisfare le esigenze in materia di creazione di report. SOAP viene utilizzato durante la connessione iniziale al database del server di report e la visualizzazione dell'elenco di report disponibili in un'interfaccia utente, mentre l'accesso con URL viene utilizzato per l'effettivo accesso e la navigazione dei singoli report.  
  
 Per un esempio di uso dell'accesso con URL in combinazione con il servizio Web per offrire funzionalità di creazione di report integrate, vedere [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Esempi del prodotto SQL Server Reporting Services).  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione di Reporting Services nelle applicazioni](../../../2014/reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Integrazione di Reporting Services tramite SOAP](../application-integration/integrating-reporting-services-using-soap.md)   
 [Integrazione di Reporting Services tramite l'accesso con URL](../application-integration/integrating-reporting-services-using-url-access.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
