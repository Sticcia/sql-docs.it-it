---
title: Creare un avviso del database di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 67aaf5ab44e5584fc50851dd797ad7cbc62f3ffc
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-a-sql-server-database-alert"></a>Creare un avviso del database di SQL Server
  È possibile utilizzare Monitoraggio di sistema per creare un avviso da generare quando viene raggiunto un valore soglia specificato per un contatore di Monitoraggio di sistema. In risposta all'avviso, Monitoraggio di sistema avvia un'applicazione, ad esempio un'applicazione personalizzata programmata per gestire la condizione dell'avviso. Ad esempio, è possibile creare un avviso che viene generato quando il numero di deadlock supera un determinato valore.  
  
 È inoltre possibile definire avvisi utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per altre informazioni, vedere [Avvisi](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef).  
  
 Per altre informazioni sull'uso di Monitoraggio di sistema per impostare un avviso del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Impostazione di un avviso del database di SQL Server &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  