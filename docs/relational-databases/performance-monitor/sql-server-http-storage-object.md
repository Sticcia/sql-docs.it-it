---
title: HTTP_STORAGE_OBJECT di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: f863259a12be7ef2346ddfa333b79c95a920d2fe
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380462"
---
# <a name="sql-server-http-storage"></a>SQL Server, archiviazione HTTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto prestazione **SQLServer:HTTP Storage** è costituito dai contatori delle prestazioni per il monitoraggio di un account di archiviazione di Microsoft Azure. Con la funzionalità [File di dati di SQL Server in Microsoft Azure](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) è possibile archiviare i file di database nei BLOB di archiviazione di Windows Azure. Questo oggetto prestazione considera ogni account di archiviazione Windows Azure come unità diversa.  
  
|Nome contatore|Descrizione|  
|------------------|-----------------|  
|**Byte medi/lettura**|Numero medio di byte trasferiti dalla risorsa di archiviazione HTTP per operazione di lettura.|  
|**Byte medi/trasferimento**|Numero medio di byte trasferiti dalla risorsa di archiviazione HTTP durante le operazioni di lettura o scrittura.|  
|**Byte medi/scrittura**|Numero medio di byte trasferiti dalla risorsa di archiviazione HTTP per operazione di scrittura.|  
|**Microsec. medi/lettura**|Numero medio di microsecondi impiegati per effettuare ogni operazione di lettura dalla risorsa di archiviazione HTTP.|  
|**Microsec. medi/lettura completamento**|Numero medio di microsecondi impiegati da HTTP per completare la lettura nella risorsa di archiviazione.| 
|**Microsec. medi/trasferimento**|Numero medio di microsecondi impiegati per effettuare ogni operazione di trasferimento nella risorsa di archiviazione HTTP.|  
|**Microsec. medi/scrittura**|Numero medio di microsecondi impiegati per effettuare ogni operazione di scrittura nella risorsa di archiviazione HTTP.|  
|**Microsec. medi/scrittura completamento**|Numero medio di microsecondi impiegati da HTTP per completare la scrittura nella risorsa di archiviazione.|  
|**Operazioni di I/O su risorsa di archiviazione HTTP non riuscite/sec**|Numero di richieste di scrittura non riuscite inviate alla risorsa di archiviazione HTTP al secondo.| 
|**Nuovi tentativi di I/O su risorsa di archiviazione HTTP/sec**|Numero di richieste di nuovi tentativi inviate alla risorsa di archiviazione HTTP al secondo.|  
|**I/O in attesa su risorsa di archiviazione HTTP**|Numero totale di operazioni di I/O in attesa di invio su una risorsa di archiviazione HTTP.|  
|**Byte letti/sec**|Quantità di dati trasferiti dalla risorsa di archiviazione HTTP al secondo durante le operazioni di lettura.|  
|**Letture/sec**|Numero di operazioni di lettura al secondo sulla risorsa di archiviazione HTTP.|  
|**Totale byte/sec**|Quantità di dati trasferiti dalla risorsa di archiviazione HTTP al secondo durante le operazioni di lettura o scrittura.|  
|**Trasferimenti/sec**|Numero di operazioni di lettura e scrittura al secondo sulla risorsa di archiviazione HTTP.|  
|**Byte scritti/sec**|Quantità di dati trasferiti dalla risorsa di archiviazione HTTP al secondo durante le operazioni di scrittura.|  
|**Scritture/sec**|Numero di operazioni di scrittura al secondo sulla risorsa di archiviazione HTTP.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
