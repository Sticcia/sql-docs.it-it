---
title: Configurare l'opzione di configurazione del server remote data archive | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 528a76ce80fdace23f76b2b221165f190a5ead5d
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>Configurare l'opzione di configurazione del server remote data archive
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Usare l'opzione **remote data archive** per specificare se i database e le tabelle nel server possono essere abilitati per l'estensione. Per ulteriori informazioni, vedere [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md).  
  
 L'opzione **remote data archive** può avere i valori seguenti.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|0|I database e le tabelle nel server non possono essere abilitati per l'estensione.|  
|1|I database e le tabelle nel server possono essere abilitati per l'estensione.|  
  
 L'esecuzione di **sp_configure** per impostare il valore dell'opzione **remote data archive** richiede autorizzazioni sysadmin o serveradmin.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente visualizza per prima l'impostazione corrente dell'opzione **remote data archive** . L'esempio abilita quindi l'opzione **remote data archive** impostandone il valore su 1.  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 Per disabilitare l'opzione, impostare il valore su 0.  
  
## <a name="see-also"></a>Vedere anche  
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Estensione database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
