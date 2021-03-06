---
title: MSSQLSERVER_14420 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5c2818c322749672c514cd9d392b61b580d40e88
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869903"
---
# <a name="mssqlserver14420"></a>MSSQLSERVER_14420
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14420|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum14420|  
|Testo del messaggio|Per il database primario per il log shipping %s.%s è impostato un valore soglia per il backup di %d minuti e tale database non ha eseguito un'operazione di backup del log da %d minuti. Controllare le informazioni nel log dell'agente e del server di monitoraggio distribuzione log.|  
  
## <a name="explanation"></a>Spiegazione  
 Il log shipping non è stato sincronizzato entro la soglia per il backup. La soglia per il backup corrisponde al numero di minuti consentiti tra processi di backup della distribuzione dei log prima che venga generato un avviso. Questo messaggio non indica necessariamente un problema relativo al log shipping, ma potrebbe indicare uno dei problemi seguenti:  
  
-   Il processo di backup non è in esecuzione. La mancata esecuzione del processo può dipendere da diverse cause. È ad esempio possibile che il servizio SQL Server Agent nell'istanza del server primario non sia in esecuzione, che il processo sia disabilitato oppure che la pianificazione del processo sia stata modificata.  
  
-   Si è verificato un errore relativo al processo di backup. L'errore relativo al processo può dipendere da diverse cause. È ad esempio possibile che il percorso della cartella di backup non sia valido, che il disco sia pieno o che vi siano altri motivi che causano errori nell'istruzione BACKUP.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per risolvere il problema che ha causato la visualizzazione di questo messaggio:  
  
-   Verificare che il servizio SQL Server Agent sia in esecuzione per l'istanza del server primario e che il processo di backup del database primario sia abilitato e pianificato per l'esecuzione a intervalli appropriati.  
  
-   È possibile che si sia verificato un errore relativo al processo di backup nel server primario. In questo caso, esaminare la cronologia processo del processo di backup per individuarne la causa.  
  
-   È possibile che il processo di backup del log shipping, che viene eseguito nell'istanza del server primario, non sia in grado di connettersi all'istanza del server di monitoraggio per aggiornare la tabella **log_shipping_monitor_primary**. L'errore potrebbe essere causato da un problema di autenticazione tra l'istanza del server di monitoraggio e l'istanza del server primario.  
  
-   È possibile che la soglia di avviso per il backup non sia corretta. In una situazione ideale, la soglia è impostata su un valore pari ad almeno tre volte la frequenza del processo di backup. Se si cambia la frequenza del processo di backup dopo aver configurato e reso operativo il log shipping, sarà necessario aggiornare di conseguenza la soglia di avviso per il backup.  
  
-   Quando l'istanza del server di monitoraggio passa alla modalità offline e quindi torna alla modalità online, la tabella **log_shipping_monitor_primary** non viene aggiornata con i valori correnti prima dell'esecuzione del processo del messaggio di avviso. Per aggiornare le tabelle di monitoraggio con i dati più recenti del database primario, eseguire **sp_refresh_log_shipping_monitor** nell'istanza del server primario.  
  
-   Nell'istanza del server primario o di monitoraggio la data o l'ora non è corretta. Questo problema può causare la generazione di messaggi di avviso. È possibile che in uno dei due server sia stata modificata la data o l'ora di sistema.  
  
    > [!NOTE]  
    >  Fusi orari diversi per le due istanze del server non dovrebbero invece costituire un problema.  
  
## <a name="see-also"></a>Vedere anche  
 [log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)   
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)   
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
