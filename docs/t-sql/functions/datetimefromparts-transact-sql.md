---
title: DATETIMEFROMPARTS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATETIMEFROMPARTS_TSQL
- DATETIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEFROMPARTS function
ms.assetid: 6008148b-bf75-4c98-9392-68a89fa0711c
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79bddc120ba326e625525098bbe58cf098795108
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="datetimefromparts-transact-sql"></a>DATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Restituisce un **datetime** valore per la data e ora specificate.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DATETIMEFROMPARTS ( year, month, day, hour, minute, seconds, milliseconds )  
```  
  
## <a name="arguments"></a>Argomenti  
*anno*  
Espressione intera che specifica un anno.
  
*mese*  
Espressione intera che specifica un mese.
  
*giorno*  
Espressione intera che specifica un giorno.
  
*ora*  
Espressione intera che specifica le ore.
  
*minuto*  
Espressione intera che specifica i minuti.
  
*secondi*  
Espressione intera che specifica i secondi.
  
*millisecondi*  
Espressione intera che specifica i millisecondi.
  
## <a name="return-types"></a>Tipi restituiti
**datetime**
  
## <a name="remarks"></a>Osservazioni  
**DATETIMEFROMPARTS** restituisce un oggetto completamente inizializzato **datetime** valore. Se gli argomenti non sono validi, viene generato un errore. Se gli argomenti obbligatori sono Null, viene restituito un valore Null.
  
Questa funzione può essere eseguita in modalità remota in server con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e versioni successive, ma non in server con versioni precedenti a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Esempi  
  
```sql
SELECT DATETIMEFROMPARTS ( 2010, 12, 31, 23, 59, 59, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.000  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT DATETIMEFROMPARTS ( 2010, 12, 31, 23, 59, 59, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[DateTime &#40; Transact-SQL &#41;](../../t-sql/data-types/datetime-transact-sql.md)
  
  

