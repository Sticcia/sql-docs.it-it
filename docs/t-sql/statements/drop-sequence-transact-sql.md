---
title: SEQUENZA DROP (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SEQUENCE
- DROP_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SEQUENCE statement
- sequence number object, dropping
ms.assetid: c25772d3-61af-4aa7-b58b-a6f67a793e3d
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d7247c5e809c8e26fbd17dc01e8c2f624a170ff
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-sequence-transact-sql"></a>DROP SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Rimuove un oggetto sequenza dal database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP SEQUENCE [ IF EXISTS ] { [ database_name . [ schema_name ] . | schema_name. ]    sequence_name } [ ,...n ]  
 [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale la sequenza solo se esiste già.  
  
 *database_name*  
 Nome del database in cui è stato creato l'oggetto sequenza.  
  
 *schema_name*  
 Nome dello schema a cui appartiene l'oggetto sequenza.  
  
 *sequence_name*  
 Nome della sequenza da eliminare. Il tipo è **sysname**.  
  
## <a name="remarks"></a>Osservazioni  
 Dopo la generazione di un numero, un oggetto sequenza non ha una relazione continua con il numero generato, pertanto l'oggetto sequenza può essere eliminato, anche se il numero generato è ancora in uso.  
  
 È possibile eliminare un oggetto sequenza mentre una stored procedure o un trigger vi fa riferimento, perché non è associato a schema. Non è possibile eliminare un oggetto sequenza se vi si fa riferimento come valore predefinito in una tabella. Nel messaggio di errore verrà indicato l'oggetto che fa riferimento alla sequenza.  
  
 Per elencare tutti gli oggetti sequenza nel database, eseguire l'istruzione seguente.  
  
```  
SELECT sch.name + '.' + seq.name AS [Sequence schema and name]   
    FROM sys.sequences AS seq  
    JOIN sys.schemas AS sch  
        ON seq.schema_id = sch.schema_id ;  
GO  
```  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER o CONTROL per lo schema.  
  
### <a name="audit"></a>Controllo  
 Per controllare **DROP SEQUENCE**, monitoraggio di **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso un oggetto sequenza denominato `CountBy1` dal database corrente.  
  
```  
DROP SEQUENCE CountBy1 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [CREATE SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [VALORE successivo per &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Numeri di sequenza](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
