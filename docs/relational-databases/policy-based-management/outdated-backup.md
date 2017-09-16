---
title: Backup obsoleto | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94f220565078ceddac2aa43eb8e88f9895c27e9d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="outdated-backup"></a>Backup obsoleto
  Questa regola consente di controllare se per un database siano disponibili backup recenti. La pianificazione di backup frequenti è importante per la protezione dei database dalla perdita di dati dovuta a errori diversi. La frequenza più appropriata per il backup dei dati dipende dal modello di recupero del database, dalle esigenze aziendali relative alla possibile perdita di dati e dalla frequenza con cui viene aggiornato il database. In un database aggiornato di frequente, l'esposizione alla perdita di dati aumenta piuttosto rapidamente tra i backup.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 È consigliabile eseguire backup sufficientemente frequenti per proteggere i database dalla perdita di dati.  
  
 Il modello di recupero con registrazione minima e il modello di recupero con registrazione completa richiedono entrambi il backup dei dati. Per entrambi i modelli, è possibile aggiungere ai backup completi backup differenziali per ridurre in modo efficiente il rischio di perdita di dati.  
  
 Per un database che utilizza il modello di recupero con registrazione completa, è consigliabile eseguire frequenti backup del log. Per un database di produzione che contiene dati molto importanti, è in genere consigliabile eseguire backup del log ogni quindici minuti.  
  
> [!NOTE]  
>  Il metodo consigliato per la pianificazione dei backup è un piano di manutenzione del database.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Backup e ripristino di database di sistema &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
 [Creare un backup differenziale del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [Creazione di un backup completo del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
 [Backup di log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  