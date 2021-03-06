---
title: Analizzare deadlock con SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- process nodes [SQL Server Profiler]
- Profiler [SQL Server Profiler], deadlocks
- deadlocks [SQL Server], identifying cause
- resource nodes [SQL Server Profiler]
- graphs [SQL Server Profiler]
- SQL Server Profiler, deadlocks
- events [SQL Server], deadlocks
- edges [SQL Server Profiler]
ms.assetid: 72d6718f-501b-4ea6-b344-c0e653f19561
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca1882faa9c61536d1ef025058322f141beedafd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63316332"
---
# <a name="analyze-deadlocks-with-sql-server-profiler"></a>Analizzare deadlock con SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] consente di identificare la causa di un deadlock. I deadlock si verificano in caso di dipendenza ciclica tra due o più thread o processi per alcuni set di risorse in SQL Server. Tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], è possibile creare una traccia che registra, riproduce e visualizza gli eventi deadlock da analizzare.  
  
 Per tracciare gli eventi deadlock, aggiungere la classe di evento **Deadlock graph** a una traccia. Questa classe di evento consente di popolare la colonna di dati **TextData** nella traccia con dati XML sul processo e gli oggetti coinvolti nel deadlock. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] può estrarre il documento XML in un file XML del deadlock (con estensione xdl) visualizzabile in un secondo momento in SQL Server Management Studio. È possibile configurare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per estrarre gli eventi **Deadlock graph** in un singolo file contenente tutti gli eventi **Deadlock graph** oppure in file distinti. È possibile eseguire l'estrazione in uno dei modi seguenti:  
  
-   Durante la configurazione della traccia, con la scheda **Impostazioni estrazione eventi** . Si noti che questa scheda non viene visualizzata a meno che non si selezioni l'evento Deadlock graph nella scheda **Selezione eventi** .  
  
-   Con il comando **Estrai eventi di SQL Server** del menu **File** .  
  
-   Per estrarre e salvare singoli eventi è anche possibile fare clic con il pulsante destro del mouse su un evento specifico e scegliere **Estrai dati eventi**.  
  
## <a name="deadlock-graphs"></a>Grafici di deadlock  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usano per descrivere un deadlock un grafico che contiene i nodi dei processi, i nodi delle risorse e archi che rappresentano le relazioni tra i processi e le risorse. Nella tabella seguente vengono descritti i componenti di questi grafici:  
  
 Nodo di processo  
 Un thread che esegue un'attività, ad esempio INSERT, UPDATE o DELETE.  
  
 Nodo di risorsa  
 Un oggetto di database, ad esempio una tabella, un indice o una riga.  
  
 Arco  
 Una relazione tra un processo e una risorsa. Un arco di tipo `request` viene generato quando un processo è in attesa di una risorsa. Un arco di tipo `owner` viene generato quando una risorsa è in attesa di un processo. Nella descrizione dell'arco è inclusa la modalità di blocco, Ad esempio, **modalità: X**.  
  
## <a name="deadlock-process-node"></a>Nodo di processo del deadlock  
 In questo tipo di grafico, il nodo del processo contiene informazioni sul processo. Nella tabella seguente vengono illustrati i componenti di un processo.  
  
|Componente|Definizione|  
|---------------|----------------|  
|ID processo server|Identificatore di processo del server (SPID). Identificatore assegnato dal server al processo proprietario del blocco.|  
|ID batch server|Identificatore del batch server (SBID).|  
|ID contesto esecuzione|Identificatore del contesto di esecuzione (ECID). ID del contesto di esecuzione di un thread specifico associato a un valore SPID specifico.<br /><br /> ECID = {0,1,2,3, *...n*}, dove 0 rappresenta sempre il thread principale o padre e {1,2,3, *...n*} rappresenta i thread secondari.|  
|Priorità deadlock|Priorità dei deadlock per il processo. Per altre informazioni sui possibili valori, vedere [SET DEADLOCK_PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-deadlock-priority-transact-sql).|  
|Log utilizzato|Quantità di spazio del log utilizzata dal processo.|  
|ID proprietario|ID transazione per i processi che utilizzano transazioni e che sono in attesa in un blocco.|  
|Descrittore transazione|Puntatore al descrittore della transazione che descrive lo stato della transazione.|  
|Buffer di input|Buffer di input del processo corrente. Consente di definire il tipo di evento e l'istruzione eseguita. I valori possibili includono:<br /><br /> **Lingua**<br /><br /> **RPC**<br /><br /> **Nessuno**|  
|.|Tipo di istruzione. I valori possibili sono:<br /><br /> **NOP**<br /><br /> **SELECT**<br /><br /> **UPDATE**<br /><br /> **INSERT**<br /><br /> **DELETE**<br /><br /> **Unknown**|  
  
## <a name="deadlock-resource-node"></a>Nodo di risorsa del deadlock  
 In un deadlock, due processi sono in attesa ognuno di una risorsa mantenuta dall'altro processo. In un grafico di deadlock, le risorse sono visualizzate come nodi di risorsa.  
  
  
