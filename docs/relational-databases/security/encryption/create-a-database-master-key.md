---
title: Creare la chiave master di un database | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: aliceku
ms.author: aliceku
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3034dc76a64e25b614b1871247369214199c36b
ms.sourcegitcommit: fa2f85b6deeceadc0f32aa7f5f4e2b6e4d99541c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2019
ms.locfileid: "53997493"
---
# <a name="create-a-database-master-key"></a>Creazione della chiave master di un database
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  In questo argomento viene descritto come creare una chiave master del database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)].
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
È richiesta l'autorizzazione CONTROL per il database.  
  
## <a name="using-transact-sql"></a>Utilizzo di Transact-SQL  
  
### <a name="to-create-a-database-master-key"></a>Per creare la chiave master di un database  
  
1. Scegliere una password per la crittografia della copia della chiave master che verrà archiviata nel database.  
  
2. In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
3. Sulla barra Standard fare clic su **Nuova query**.  
  
4. Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```sql
    -- Creates a database master key for the "AdventureWorks2012" database.   
    -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."  
    USE AdventureWorks2012;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
    GO  
    ```  
  
 Per altre informazioni, vedere [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-master-key-transact-sql.md).  
