---
title: Eliminare il log di un passaggio di processo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- deleting job step logs
- logs [SQL Server], jobs
- removing job step logs
ms.assetid: ee20c6cd-0258-4550-bdb0-71e86a0fb330
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 945c403a44f2b0c2cf2d691a1bcfda6cc96d422b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62523744"
---
# <a name="delete-a-job-step-log"></a>Delete a Job Step Log
  In questo argomento viene illustrato come eliminare un log dei passaggi di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare un log dei passaggi di processo di SQL Server Agent mediante:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Il log di output dei passaggi di processo eliminati viene eliminato automaticamente.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È possibile modificare solo i processi di cui si è proprietari, a meno che non si appartenga al ruolo predefinito del server **sysadmin** .  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>Per eliminare un log dei passaggi di processo di SQL Server Agent  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Espandere il nodo **SQL Server Agent**e il nodo **Processi**; fare clic con il pulsante destro del mouse sul processo che si vuole modificare e scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà processo** eliminare il passaggio di processo selezionato.  
  
##  <a name="TSQL"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-job-step-log"></a>Per eliminare un log dei passaggi di processo di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- removes the job step log for step 2 in the job Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobsteplog  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 2;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_delete_jobsteplog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql).  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 Utilizzare i metodi `DeleteJobStepLogs` della classe `Job` utilizzando un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere[SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
```  
-- Uses PowerShell to delete all job step log files that have ID values larger than 5.  
$srv = new-object Microsoft.SqlServer.Management.Smo.Server("(local)")  
$jb = $srv.JobServer.Jobs["Test Job"]  
$jb.DeleteJobStepLogs(5)  
```  
  
  
