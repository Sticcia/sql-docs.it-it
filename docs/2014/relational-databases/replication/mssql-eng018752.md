---
title: MSSQL_ENG018752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0558ded6ed10284df39270ddeca9d92434daf40e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057544"
---
# <a name="mssqleng018752"></a>MSSQL_ENG018752
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|18752|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|A un database può connettersi un solo agente di lettura log o una sola procedura correlata ai log (sp_repldone, sp_replcmds e sp_replshowcmds) alla volta. Se è stata eseguita una procedura correlata ai log, eliminare la connessione utilizzata per eseguire la procedura oppure eseguire sp_replflush tramite tale connessione prima di avviare l'agente di lettura log o di eseguire un'altra procedura relativa ai log.|  
  
## <a name="explanation"></a>Spiegazione  
 È in corso da parte di più connessioni il tentativo di eseguire una delle procedure seguenti: **sp_repldone**, **sp_replcmds**o **sp_replshowcmds**. Le stored procedure [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) e [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) vengono usate dall'agente di lettura log per trovare e aggiornare le informazioni sulle transazioni replicate in un database pubblicato. La stored procedure [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) viene usata per la risoluzione di alcuni tipi di problemi relativi alla replica transazionale.  
  
 Questo errore viene generato nelle circostanze seguenti:  
  
-   Se l'agente di lettura log di un database pubblicato è in esecuzione e un secondo agente di lettura log tenta l'esecuzione sullo stesso database, per il secondo agente viene generato l'errore, che appare nella cronologia dell'agente.  
  
     In una situazione in cui compaiono più agenti, è possibile che uno di loro sia il risultato di un processo orfano.  
  
-   Se l'agente di lettura log di un database pubblicato viene avviato e un utente esegue **sp_repldone**, **sp_replcmds**o **sp_replshowcmds** sullo stesso database, viene generato l'errore nell'applicazione in cui è stata eseguita la stored procedure (ad esempio **sqlcmd**).  
  
-   Se l'agente di lettura log di un database pubblicato viene avviato e un utente esegue **sp_repldone**, **sp_replcmds**o **sp_replshowcmds** e non chiude la connessione su cui è stata eseguita la procedura, quando l'agente di lettura log tenta di connettersi al database viene generato l'errore.  
  
## <a name="user-action"></a>Azione dell'utente  
 I passaggi seguenti possono contribuire alla risoluzione del problema. Se uno dei passaggi consente l'avvio senza errori dell'agente di lettura log, non è necessario completare i passaggi rimanenti.  
  
-   Verificare nella cronologia dell'agente di lettura log la presenza di eventuali altri errori che potrebbero contribuire a questo errore. Per informazioni sui dettagli di stato e di errore dell'agente di visualizzazione in Monitoraggio replica, vedere [Visualizzare le informazioni ed eseguire attività usando Monitoraggio replica](monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Verificare nell'output di [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) la presenza di numeri di identificazione di processo (SPID) connessi al database pubblicato. Chiudere le connessioni che potrebbero aver eseguito **sp_repldone**, **sp_replcmds**o **sp_replshowcmds**.  
  
-   Riavviare l'agente di lettura log. Per altre informazioni, vedere [Avviare e arrestare un agente di replica &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (metterlo offline oppure online in un cluster) sul server di distribuzione. Se vi è una possibilità che un processo pianificato abbia eseguito **sp_repldone**, **sp_replcmds**o **sp_replshowcmds** da altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , riavviare l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent anche per queste istanze. Per altre informazioni, vedere [Avviare, arrestare o sospendere il servizio SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).  
  
-   Eseguire [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) nel server di pubblicazione sul database di pubblicazione e quindi riavviare l'agente di lettura log.  
  
-   Se l'errore continua a verificarsi, aumentare il livello di dettaglio per la registrazione delle operazioni dell'agente e specificare un file di output per il log. A seconda del contesto dell'errore, in questo modo si potrebbero ottenere ulteriori informazioni sui passaggi che conducono all'errore e/o messaggi di errore aggiuntivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [Agente lettura log repliche](agents/replication-log-reader-agent.md)  
  
  
