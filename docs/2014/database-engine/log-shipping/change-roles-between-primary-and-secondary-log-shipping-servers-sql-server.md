---
title: Modificare i ruoli tra i server primario e secondario per il log shipping (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], role changes
- secondary data files [SQL Server], roles changed between
- primary databases [SQL Server]
- initial role changes [SQL Server]
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: 2d7cc40a-47e8-4419-9b2b-7c69f700e806
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 08467118608db6b222bea2a41351eac951449a16
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62774565"
---
# <a name="change-roles-between-primary-and-secondary-log-shipping-servers-sql-server"></a>Modificare i ruoli tra i server primario e secondario per il log shipping (SQL Server)
  Dopo aver eseguito il failover di una configurazione per il log shipping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su un server secondario, è possibile configurare il database secondario per operare come database primario. Sarà quindi possibile scambiare il database primario e quello secondario in base alle proprie esigenze.  
  
## <a name="performing-the-initial-role-change"></a>Esecuzione della modifica iniziale del ruolo  
 La prima volta che si desidera eseguire il failover al database secondario e impostarlo come nuovo database primario, è necessario eseguire alcuni passaggi specifici. Dopo avere eseguito tali passaggi iniziali, sarà possibile scambiare i ruoli tra database primario e secondario in modo semplice.  
  
1.  Eseguire manualmente il failover dal database primario a un database secondario. Eseguire il backup del log delle transazioni attive nel server primario con l'opzione NORECOVERY. Per altre informazioni, vedere [Failover su un database secondario per il log shipping &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md).  
  
2.  Disabilitare il processo di backup per il log shipping nel server primario originale e i processi di copia e ripristino nel server secondario originale.  
  
3.  Nel database secondario, che si desidera impostare come nuovo database primario, configurare il log shipping usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Configurare il log shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md). Eseguire i passaggi seguenti:  
  
    1.  Per la creazione di backup, usare la stessa condivisione creata per il server primario originale.  
  
    2.  Quando si aggiunge il database secondario, nella casella **Database secondario** della finestra di dialogo **Impostazioni database secondario** immettere il nome del database primario originale.  
  
    3.  Nella finestra di dialogo **Impostazioni database secondario** selezionare **No, il database secondario è già inizializzato**.  
  
4.  Se il monitoraggio del log shipping era abilitato nella relativa configurazione precedente, riconfigurare il monitoraggio per controllare la nuova configurazione per il log shipping.  Eseguire i comandi riportati di seguito, sostituendo *database_name* con il nome del database in uso:  
  
    1.  **Nel nuovo server primario**  
  
         Eseguire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] riportate di seguito:  
  
        ```  
        -- Statement to execute on the new primary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_secondary_database @secondary_database = N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
    2.  **Nel nuovo server secondario**  
  
         Eseguire le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] riportate di seguito:  
  
        ```  
        -- Statement to execute on the new secondary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_primary_database @database=N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
## <a name="swapping-roles"></a>Scambio di ruoli  
 Dopo avere completato i passaggi descritti in precedenza per la modifica iniziale dei ruoli, è possibile scambiare i ruoli tra il database primario e quello secondario eseguendo i passaggi indicati in questa sezione. Per modificare i ruoli, eseguire la procedura seguente:  
  
1.  Portare online il database secondario, eseguendo il backup del log delle transazioni nel server primario con l'opzione NORECOVERY.  
  
2.  Disabilitare il processo di backup per il log shipping nel server primario originale e i processi di copia e ripristino nel server secondario originale.  
  
3.  Abilitare il processo di backup per il log shipping nel server secondario, ovvero il nuovo server primario, e i processi di copia e ripristino nel server primario, ovvero il nuovo server secondario.  
  
> [!IMPORTANT]  
>  Se si modifica un database secondario in database primario per offrire a utenti e applicazioni un sistema più coerente, potrebbe essere necessario ricreare alcuni o tutti i metadati del database, ad esempio account di accesso e processi, nell'istanza del nuovo server primario. Per altre informazioni, vedere [Gestione dei metadati quando si rende disponibile un database in un'altra istanza del server &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Failover su un database secondario per il log shipping &#40;SQL Server&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [Gestione di account di accesso e di processi dopo un cambio di ruolo &#40;SQL Server&#41;](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e stored procedure relative al log shipping](log-shipping-tables-and-stored-procedures.md)  
  
  
