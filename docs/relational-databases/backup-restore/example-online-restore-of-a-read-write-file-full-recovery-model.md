---
title: 'Esempio: Ripristino online di un file di lettura/scrittura (modello di recupero con registrazione completa) | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4be86c808d1af35a04b10c88d5cecdd919416137
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="example-online-restore-of-a-read-write-file-full-recovery-model"></a>Esempio: Ripristino online di un file di lettura/scrittura (modello di recupero con registrazione completa)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Le informazioni contenute in questo argomento interessano i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] basati sul modello di recupero con registrazione completa che includono più file o filegroup.  
  
 In questo esempio un database denominato `adb`, che utilizza il modello di recupero con registrazione completa, contiene tre filegroup. Il filegroup `A` è in lettura/scrittura, mentre i filegroup `B` e `C` sono di sola lettura. Inizialmente, tutti i filegroup sono online.  
  
 Il file `a1` del filegroup `A` è danneggiato e l'amministratore del database decide di ripristinarlo, mantenendo online il database.  
  
> [!NOTE]  
>  Il modello di recupero con registrazione minima non consente il ripristino online di dati di lettura/scrittura.  
  
## <a name="restore-sequences"></a>Sequenze di ripristino  
  
> [!NOTE]  
>  La sintassi di una sequenza di ripristino online è la stessa di una sequenza di ripristino offline.  
  
1.  Ripristino in linea del file `a1`.  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     A questo punto lo stato del file a1 è RESTORING e il filegroup A è offline.  
  
2.  Al termine del ripristino del file, l'amministratore del database esegue un nuovo backup del log per garantire l'acquisizione del punto in cui il file è passato offline.  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  Ripristino online dei backup del log.  
  
     L'amministratore ripristina tutti i backup del log a partire dal backup del file ripristinato fino all'ultimo backup del log (*log_backup3*, eseguito nel passaggio 2). Una volta ripristinato l'ultimo backup, viene recuperato il database.  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     Il file `a1` è ora online.  
  
## <a name="additional-examples"></a>Esempi aggiuntivi  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di alcuni filegroup &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di sola lettura &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di filegroup selezionati &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Esempio: Ripristino online di un file di sola lettura &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristino in linea &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Ripristini a fasi &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Panoramica del ripristino e del recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Applicazione dei backup di log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  