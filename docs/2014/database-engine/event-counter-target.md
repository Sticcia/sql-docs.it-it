---
title: Destinazione contatore degli eventi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- synchronous event counter target [SQL Server extended events]
- targets [SQL Server extended events], synchronous event counter target
ms.assetid: 342e08d1-dcca-4a71-ae64-cb61b55b85bc
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f701ff8a1648a3f90f7e04c71f159081ac7a3da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780905"
---
# <a name="event-counter-target"></a>Destinazione del contatore degli eventi
  La destinazione del contatore degli eventi conta tutti gli eventi generati durante una sessione di eventi estesi. Utilizzando la destinazione del contatore degli eventi, è possibile ottenere informazioni sulle funzionalità del carico di lavoro senza aggiungere l'overhead di un'intera raccolta di eventi. Questa destinazione non include parametri personalizzabili.  
  
## <a name="adding-the-target-to-a-session"></a>Aggiunta della destinazione a una sessione  
 Per aggiungere la destinazione del contatore degli eventi a una sessione di eventi estesi, è necessario includere l'istruzione seguente quando si crea o modifica una sessione eventi:  
  
```  
ADD TARGET package0.event_counter  
```  
  
## <a name="reviewing-the-target-output"></a>Analisi dell'output di destinazione  
 Per esaminare l'output dalla destinazione del contatore degli eventi, è possibile usare la query seguente, sostituendo *session_name* con il nome della sessione eventi:  
  
```  
SELECT name, target_name, CAST(xet.target_data AS xml)  
FROM sys.dm_xe_session_targets AS xet  
JOIN sys.dm_xe_sessions AS xe  
   ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'session_name'  
```  
  
 Nell'esempio seguente viene illustrato il formato di output della destinazione del contatore degli eventi.  
  
```  
<CounterTarget truncated = "0">  
  <Packages>  
    <Package name = "[package name]">  
      <Event name = "[event name]" count = "[number]" />  
    </Package>  
  </Packages>  
</CounterTarget>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Destinazioni degli eventi estesi di SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
