---
title: Elemento EventString (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 85e5c89f87a0a6eda0173511f818e047fc0c51c9
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="eventstring-element-dta"></a>Elemento EventString (DTA)
  Specifica il carico di lavoro di uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] direttamente nel file di input XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**Weight**|Facoltativa. Specifica il fattore di ponderazione, o fattore di importanza, della query per l'evento specificato. Per specificare il fattore di ponderazione, utilizzare un tipo di dati **float** . Ad esempio, **Weight**="100.01". Il valore minimo che è possibile specificare per **Weight** è "0".|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Obbligatorio una sola volta se non viene specificato un altro tipo di carico di lavoro. È necessario specificare un elemento figlio **EventString**, **File**o **Database** per l'elemento padre **Workload** , ma è possibile utilizzare un solo tipo. Se ad esempio si specifica un carico di lavoro con l'elemento **EventString** , non sarà possibile specificare anche un carico di lavoro con l'elemento **File** nello stesso file di input XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Workload &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con carico di lavoro inline &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  