---
title: TIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b02eadce149db42ffcf6229ae2cbbc47bc641f1b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2018
ms.locfileid: "53202580"
---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Restituisce un valore **time** per l'ora specificata e con la precisione indicata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Argomenti  
 *hour*  
 Espressione intera che specifica le ore.  
  
 *minute*  
 Espressione intera che specifica i minuti.  
  
 *secondi*  
 Espressione intera che specifica i secondi.  
  
 *fractions*  
 Espressione intera che specifica le frazioni.  
  
 *precisione*  
 Valore letterale intero che specifica la precisione del valore **time** da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 **time(** *precision* **)**  
  
## <a name="remarks"></a>Remarks  
 TIMEROMPARTS restituisce un valore relativo all'ora completamente inizializzato. Se gli argomenti non sono validi, viene generato un errore. Se un parametro è Null, viene restituito Null. Se tuttavia l'argomento *precision* è Null viene generato un errore.  
  
 L'argomento *fractions* dipende dall'argomento *precision*. Se ad esempio *precision* è 7, ogni frazione rappresenta 100 nanosecondi, mentre se *precision* è 3 ogni frazione rappresenta un millisecondo. Se il valore di *precision* è zero, anche il valore di *fractions* deve essere zero. In caso contrario, viene generato un errore.  
  
 Questa funzione può essere eseguita in modalità remota in server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, ma non in server con versioni precedenti a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Esempio semplice senza frazioni di un secondo  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>b. Esempio con frazioni di un secondo  
 L'esempio seguente illustra l'uso dei parametri *fractions* e *precision*:  
  
1.  Se *fractions* ha valore 5 e *precision* ha valore 1, il valore di *fractions* corrisponde a 5/10 di secondo.  
  
2.  Se *fractions* ha valore 50 e *precision* ha valore 2, il valore di *fractions* corrisponde a 50/100 di secondo.  
  
3.  Se *fractions* ha valore 500 e *precision* ha valore 3, il valore di *fractions* corrisponde a 500/1000 di secondo.  
  
```sql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  

