---
title: "Proprietà server (pagina esecuzione) | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 933f3287d8e02df8aeadf93bbd7ce39f20aff268
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="server-properties-execution-page"></a>Proprietà server (pagina Esecuzione)
  Utilizzare questa pagina per impostare un valore di timeout per l'esecuzione dei report. Questo valore si applica a tutti i report elaborati dall'istanza del server di report corrente, ma è possibile modificarlo a livello di singolo report. Il valore specificato deve essere appropriato per tutte le elaborazioni dei report nel server di report, nonché per l'elaborazione delle query nel server di database quando il server di report recupera i dati utilizzati nel report.  
  
 Per aprire questa pagina, avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connettersi a un'istanza del server di report, fare clic con il pulsante destro del mouse sul nome del server di report e scegliere **Proprietà**. Fare clic su **Esecuzione** per aprire la pagina.  
  
## <a name="options"></a>Opzioni  
 **Nessun timeout per l'esecuzione del report**  
 Consente a un server di report di completare l'elaborazione del report senza alcun limite di tempo.  
  
 **La durata dell'esecuzione del report non può superare il numero di secondi seguente**  
 Imposta un vincolo di tempo per l'esecuzione del report. Il periodo di tempo viene calcolato dal momento della richiesta del report. Se il tempo scade prima del completamento dell'elaborazione del report, il processo e ogni query in-process verranno annullati nelle origini dei dati esterne.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare proprietà Server di Report &#40; Management Studio &#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Connettersi a un Server di Report in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Impostare le proprietà di elaborazione di Report](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Impostazione dei valori di timeout per i Report e l'elaborazione di set di dati condiviso &#40; SSRS &#41;](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Server di report in Management Studio F1 Help](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  