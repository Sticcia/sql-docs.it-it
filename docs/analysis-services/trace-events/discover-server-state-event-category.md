---
title: Individuare la categoria di eventi dello stato di Server | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Discover Server State event category
- server state events [Analysis Services]
- discover server state events
- event classes [Analysis Services], discover server state
ms.assetid: b62ebf66-d090-4f74-8c83-11ed518b2018
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bc94790d8903fa644bd79fa9328c60a781b62d4b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discover-server-state-event-category"></a>Individuazione stato del server - categoria di eventi
  La categoria di eventi Individuazione stato del server include le classi di evento descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Server State Discover Begin|33|Raccoglie tutti gli eventi di inizio individuazione dello stato del server XMLA dall'avvio della traccia.|  
|Server State Discover Data|34|Raccoglie tutti gli eventi di dati di individuazione dello stato del server XMLA dall'avvio della traccia. Tali eventi acquisiscono il contenuto della risposta alla richiesta di individuazione.|  
|Server State Discover End|35|Raccoglie tutti gli eventi di fine individuazione dello stato del server XMLA dall'avvio della traccia.|  
  
 Per informazioni sulle colonne associate a ogni classe di evento degli eventi query, vedere [Colonne di dati degli eventi di individuazione dello stato del server](../../analysis-services/trace-events/discover-server-state-events-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  