---
title: Creare un passaggio di processo di uno script di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2f98dfe69207b90c4564277ad9dc49e0752d087f
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095590"
---
# <a name="create-a-powershell-script-job-step"></a>Create a PowerShell Script Job Step
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento vengono descritte le procedure per la creazione e la definizione di un passaggio di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent mediante il quale viene eseguito uno script di PowerShell in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per creare un passaggio di processo di uno script di PowerShell utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  

## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implementazione della sicurezza di SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  

[!INCLUDE[Freshness](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-powershell-script-job-step"></a>Per creare un passaggio di processo di uno script di PowerShell  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**, creare un nuovo processo oppure fare clic con il pulsante destro del mouse su un processo esistente e quindi scegliere **Proprietà**. Per ulteriori informazioni sulla creazione di un processo, vedere [Creazione di processi](../../ssms/agent/create-jobs.md).  
  
3.  Nella finestra di dialogo **Proprietà processo** fare clic sulla pagina **Passaggi** e quindi su **Nuovo**.  
  
4.  Nella finestra di dialogo **Nuovo passaggio di processo** digitare il nome del passaggio del processo nella casella **Nome passaggio**.  
  
5.  Scegliere **PowerShell** dall'elenco **Tipo**.  
  
6.  Nell'elenco **Esegui come** selezionare l'account proxy con le credenziali che verranno utilizzate dal processo.  
  
7.  Nella casella **Comando** immettere la sintassi dello script di PowerShell che verrà eseguito per il passaggio di processo. In alternativa, è possibile fare clic su **Apri** e selezionare un file contenente la sintassi dello script. Per un esempio di script di PowerShell, vedere di seguito **Utilizzo di Transact-SQL** .  
  
8.  Fare clic sulla pagina **Avanzate** per impostare le opzioni seguenti relative al passaggio di processo: l'azione da eseguire in caso di esito positivo o negativo del passaggio, il numero di tentativi di esecuzione del passaggio che devono essere effettuati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e gli intervalli tra tentativi successivi.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-create-a-powershell-script-job-step"></a>Per creare un passaggio di processo di uno script di PowerShell  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- creates a PowerShell job step that finds the processes
    -- that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_jobstep (Transact-SQL)](https://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per creare un passaggio di processo di uno script di PowerShell**  
  
Usare la classe **JobStep** tramite un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell.  
  
