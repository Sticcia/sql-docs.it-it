---
title: SCHEMA_ID (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_ID
- SCHEMA_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], schemas
- schemas [SQL Server], IDs
- SCHEMA_ID function
- IDs [SQL Server], schemas
- default schema IDs
ms.assetid: c8e34df5-3eea-459f-ae40-050909ce9fda
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e364abf5b75159600715be0a4823ba8fce847e2
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="schemaid-transact-sql"></a>SCHEMA_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce l'ID dello schema associato a un nome di schema.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
SCHEMA_ID ( [ schema_name ] )   
```  
  
## <a name="arguments"></a>Argomenti  
  
|Nome|Definizione|  
|----------|----------------|  
|*schema_name*|Nome dello schema. *schema_name* è un **sysname**. Se *schema_name* viene omesso, SCHEMA_ID restituirà l'ID dello schema predefinito del chiamante.|  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
 Verrà restituito NULL se *schema_name* non è uno schema valido.  
  
## <a name="remarks"></a>Osservazioni  
 SCHEMA_ID restituisce gli ID degli schemi di sistema e degli schemi definiti dall'utente. SCHEMA_ID può essere chiamato in un elenco di selezione, in una clausola WHERE e dovunque è consentita un'espressione.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-default-schema-id-of-a-caller"></a>A. Restituzione dell'ID di schema predefinito di un chiamante  
  
```  
SELECT SCHEMA_ID();  
GO  
```  
  
### <a name="b-returning-the-schema-id-of-a-named-schema"></a>B. Restituzione dell'ID di uno schema denominato  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SCHEMA_ID('HumanResources');  
GO   
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-default-schema-id-of-a-caller"></a>C. Restituzione dell'ID di schema predefinito di un chiamante  
  
```  
SELECT SCHEMA_ID();  
```  
  
### <a name="d-returning-the-schema-id-of-a-named-schema"></a>D. Restituzione dell'ID di uno schema denominato  
  
```  
SELECT SCHEMA_ID('dbo');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [SCHEMA_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/schema-name-transact-sql.md)   
 [Schemas &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)  
  
  

