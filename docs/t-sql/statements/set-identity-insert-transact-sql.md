---
title: SET IDENTITY_INSERT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET IDENTITY_INSERT
- SET_IDENTITY_INSERT_TSQL
- IDENTITY_INSERT_TSQL
- IDENTITY_INSERT
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY_INSERT option
- SET IDENTITY_INSERT statement
- identity values [SQL Server], explicit values
- identity columns [SQL Server], explicit values
ms.assetid: a5dd49f2-45c7-44a8-b182-e0a5e5c373ee
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9725d774075f21fc86d5276c91ed281fa34eba7d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-identityinsert-transact-sql"></a>SET IDENTITY_INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Consente l'inserimento di valori espliciti nella colonna Identity di una tabella.  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET IDENTITY_INSERT [ database_name . [ schema_name ] . ] table { ON | OFF }  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database contenente la tabella specificata.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella.  
  
 *table*  
 Nome di una tabella contenente una colonna Identity.  
  
## <a name="remarks"></a>Osservazioni  
 La proprietà IDENTITY_INSERT può essere impostata su ON per una sola tabella di una sessione. Se in una tabella tale proprietà è già impostata su ON e viene eseguita un'istruzione SET IDENTITY_INSERT ON per un'altra tabella, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza un messaggio di errore per segnalare che la proprietà SET IDENTITY_INSERT è già impostata su ON e indicata la tabella per la quale l'opzione è impostata.  
  
 Se il valore immesso è maggiore del valore Identity corrente per la tabella, il nuovo valore viene utilizzato automaticamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come valore Identity corrente.  
  
 L'opzione SET IDENTITY_INSERT viene impostata in fase di esecuzione, non in fase di analisi.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve essere il proprietario della tabella o deve disporre dell'autorizzazione ALTER per la tabella.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella contenente una colonna Identity e viene illustrato come tramite l'impostazione di `SET IDENTITY_INSERT` sia possibile completare un'interruzione nella sequenza di valori Identity generata da un'istruzione `DELETE`.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create tool table.  
CREATE TABLE dbo.Tool(  
   ID INT IDENTITY NOT NULL PRIMARY KEY,   
   Name VARCHAR(40) NOT NULL  
);  
GO  
-- Inserting values into products table.  
INSERT INTO dbo.Tool(Name)   
VALUES ('Screwdriver')  
        , ('Hammer')  
        , ('Saw')  
        , ('Shovel');  
GO  
  
-- Create a gap in the identity values.  
DELETE dbo.Tool  
WHERE Name = 'Saw';  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
  
-- Try to insert an explicit ID value of 3;  
-- should return a warning.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
-- SET IDENTITY_INSERT to ON.  
SET IDENTITY_INSERT dbo.Tool ON;  
GO  
  
-- Try to insert an explicit ID value of 3.  
INSERT INTO dbo.Tool (ID, Name) VALUES (3, 'Garden shovel');  
GO  
  
SELECT *   
FROM dbo.Tool;  
GO  
-- Drop products table.  
DROP TABLE dbo.Tool;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENTITY &#40;proprietà&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)   
 [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
