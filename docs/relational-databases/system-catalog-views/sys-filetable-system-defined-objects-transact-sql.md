---
title: Sys. filetable_system_defined_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d18b3c20a78c4f819827a389a3811946bfef33ce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660759"
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene un elenco degli oggetti definiti dal sistema correlati a tabelle FileTable. Contiene una riga per ogni oggetto definito dal sistema.  
  
 Quando si crea una tabella FileTable, vengono creati contemporaneamente anche gli oggetti correlati, quali vincoli e indici. Non è possibile modificare o eliminare questi oggetti, che verranno eliminato solo all'eliminazione della tabella FileTable stessa.  
  
 Per altre informazioni sugli oggetti FileTable, vedere [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
|colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto definito dal sistema correlato a una tabella FileTable.<br /><br /> Fa riferimento all'oggetto nel **Sys. Objects**.|  
|**parent_object_id**|**int**|ID oggetto della tabella FileTable padre.<br /><br /> Fa riferimento all'oggetto nel **Sys. Objects**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare, modificare e rilasciare FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Gestire tabelle FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
