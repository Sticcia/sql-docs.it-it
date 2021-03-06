---
title: Opzione di configurazione del server optimize for ad hoc workloads | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ee3dc240d56e3ca9de53e65e08541097dedd6600
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818381"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>ottimizzare per l'opzione di configurazione del server dei carichi di lavoro a hoc
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'opzione **optimize for ad hoc workloads** consente di migliorare l'efficienza della cache dei piani per carichi di lavoro che contengono molti batch ad hoc a uso singolo. Quando questa opzione viene impostata su 1, alla prima compilazione di un batch il [!INCLUDE[ssDE](../../includes/ssde-md.md)] archivia un piccolo stub del piano compilato nella cache dei piani, anziché il piano compilato completo. In questo modo si riducono le richieste di memoria evitando che la cache dei piani si riempia con piani compilati che non vengono riutilizzati. 
  
  Poiché grazie allo stub del piano compilato il [!INCLUDE[ssDE](../../includes/ssde-md.md)] riconosce che il batch ad hoc è stato compilato in precedenza e ha archiviato solo uno stub del piano compilato, quando il batch viene nuovamente richiamato (compilato o eseguito), il [!INCLUDE[ssDE](../../includes/ssde-md.md)] compila il batch, rimuove lo stub del piano compilato dalla cache dei piani e aggiunge il piano compilato completo alla cache dei piani. 
  
 Lo stub del piano compilato è uno dei cacheobjtype visualizzato nella vista del catalogo sys.dm_exec_cached_plans. Dispone di handle SQL e del piano univoci. Lo stub del piano compilato non ha un piano di esecuzione associato e l'esecuzione di query per l'handle del piano non restituisce uno showplan XML.  
  
 [ Il flag di traccia 8032 ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) ripristina i parametri dei limiti di cache all'impostazione RTM di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] che consente, in generale, di aumentare le dimensioni delle cache. Usare questa impostazione quando le voci della cache riutilizzate di frequente non rientrano nella cache e quando l'opzione di configurazione server Ottimizza per carichi di lavoro ad hoc non riesce a risolvere il problema della cache dei piani.  
  
> [!WARNING]  
>  Il flag di traccia 8032 può provocare prestazioni ridotte se cache di grandi dimensioni rendono disponibile meno memoria per altri consumer di memoria, ad esempio il pool di buffer.  

## <a name="recommendations"></a>Indicazioni
Evitare la presenza di un numero elevato di piani a uso singolo nella cache dei piani. Una causa comune di questo problema è la definizione non coerente dei tipi di dati o dei parametri di query. Questo è vero specificamente per la lunghezza delle stringhe ma è applicabile a qualsiasi tipo di dati che dispone di una lunghezza massima, una precisione o una scala. Se ad esempio un parametro con nome @Greeting viene passato come nvarchar(10) in una chiamata e come nvarchar(20) nella chiamata seguente, vengono creati piani separati per ogni dimensione del parametro. Se una query include diversi parametri e questi non sono definiti in modo coerente quando vengono chiamati, è possibile che per ogni query esista un numero elevato di piani di query. È possibile che esistano piani per ogni combinazione di tipi di dati dei parametri di query e lunghezze.

Se il numero di piani a utilizzo singolo occupa una parte significativa della memoria di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in un server OLTP e questi piani sono piani ad-hoc, usare questa opzione server per ridurre l'utilizzo della memoria con questi oggetti.
Per trovare il numero di piani a uso singolo memorizzati nella cache, eseguire la query seguente:

```sql
SELECT objtype, cacheobjtype, 
  AVG(usecounts) AS Avg_UseCount, 
  SUM(refcounts) AS AllRefObjects, 
  SUM(CAST(size_in_bytes AS bigint))/1024/1024 AS Size_MB
FROM sys.dm_exec_cached_plans
WHERE objtype = 'Adhoc' AND usecounts = 1
GROUP BY objtype, cacheobjtype;
```

> [!IMPORTANT]
> L'impostazione dell'opzione **optimize for ad hoc workloads** su 1 influisce solo sui nuovi piani, mentre non si applica ai piani già presenti nella cache dei piani.
> Per influire immediatamente sui piani di query già memorizzati nella cache, è necessario cancellare il contenuto della cache dei piani usando [ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) oppure riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>Vedere anche  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
