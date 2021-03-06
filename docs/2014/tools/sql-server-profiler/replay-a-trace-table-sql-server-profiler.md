---
title: Riprodurre una tabella di traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e80a18cef595ae3543aba8a656aca9267607e38
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240483"
---
# <a name="replay-a-trace-table-sql-server-profiler"></a>Riprodurre una tabella di traccia (SQL Server Profiler)
  La funzionalità di riproduzione è la capacità di aprire una traccia salvata e riprodurla nuovamente. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] include un motore di riproduzione a thread multipli in grado di simulare le connessioni utente e l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La funzionalità di riproduzione risulta utile per la risoluzione dei problemi a livello di applicazione o di processo. Quando si identifica il problema e si implementano le correzioni adeguate, eseguire nell'applicazione o nel processo la traccia con cui è stato rilevato il possibile problema. Riprodurre quindi la traccia originale e confrontare i risultati.  
  
 Per consentire la riproduzione è necessario acquisire classi di evento specifiche oltre alle classi di evento che si desidera monitorare. Questi eventi vengono acquisiti per impostazione predefinita se si usa il modello di traccia **TSQL_Replay** . Per altre informazioni, vedere [Requisiti per la riproduzione](replay-requirements.md).  
  
### <a name="to-replay-a-trace-table"></a>Per riprodurre una tabella di traccia  
  
1.  Aprire una tabella di traccia contenente le classi di eventi necessarie per la riproduzione.  
  
2.  Scegliere **Avvia** dal menu **Riproduci**e connettersi all'istanza del server in cui si vuole riprodurre la traccia.  
  
3.  Specificare **Server di riproduzione** nella scheda **Opzioni di base di riproduzione** della finestra di dialogo **Configurazione riproduzione**. Fare clic su **Cambia** per modificare il server visualizzato nella casella **Server di riproduzione** .  
  
4.  È facoltativamente possibile selezionare una delle destinazioni seguenti in cui salvare la riproduzione:  
  
    -   **Salva nel file** che consente di specificare un file in cui salvare la riproduzione.  
  
    -   **Salva nella tabella**che consente di specificare una tabella di database in cui salvare la riproduzione.  
  
5.  Selezionare **Riproduci gli eventi nell'ordine in cui sono stati inseriti nella traccia**oppure **Riproduci gli eventi usando più thread**. Nella tabella seguente viene spiegata la differenza tra queste impostazioni.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |**Riproduci gli eventi nell'ordine in cui sono stati inseriti nella traccia**|Gli eventi vengono riprodotti nell'ordine in cui sono stati inseriti nella traccia. Questa opzione consente il debug.|  
    |**Riproduci gli eventi usando più thread**|Vengono utilizzati più thread per riprodurre i vari eventi, indipendentemente dalla sequenza. Questa opzione consente di ottimizzare le prestazioni.|  
  
6.  Selezionare **Visualizza risultati di riproduzione** per visualizzare la riproduzione quando si verifica.  
  
7.  Se si vuole, è possibile fare clic sulla scheda **Opzioni avanzate di riproduzione**per configurare le opzioni seguenti:  
  
    -   Per riprodurre tutti gli ID dei processi server (SPID), selezionare **Riproduci SPID di sistema**.  
  
    -   Per limitare la riproduzione ai processi appartenenti a uno specifico SPID, selezionare **Riproduci un solo SPID**. Digitare lo SPID nella casella **SPID da riprodurre**.  
  
    -   Per riprodurre gli eventi che si sono verificati in un determinato periodo di tempo, selezionare **Limite di tempo per la riproduzione**. Impostare i valori di data e ora in **Ora inizio**e **Ora fine**per specificare il periodo di tempo da includere nella riproduzione.  
  
    -   Per controllare la modalità di gestione dei processi da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante la riproduzione, configurare le **Opzioni Health Monitor**.  
  
## <a name="see-also"></a>Vedere anche  
 [Autorizzazioni necessarie per l'esecuzione di SQL Server Profiler](sql-server-profiler.md)   
 [Riprodurre le tracce](replay-traces.md)   
 [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
