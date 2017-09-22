---
title: Operatori (Transact-SQL) composta | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators
- compound operators, described
ms.assetid: 5072fe91-02d3-42a7-831f-756eff714a17
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2e5fde8cd4265359722f33400d834b0a301718ef
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="compound-operators-transact-sql"></a>Operatori composti (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gli operatori composti consentono di eseguire alcune operazioni e impostano un valore originale sul risultato dell'operazione. Ad esempio, se una variabile @x è uguale a 35, quindi @x + = 2 accetta il valore originale di @x, aggiungere 2 e set @x nuovo valore (37).  
  
 In [!INCLUDE[tsql](../../includes/tsql-md.md)] sono disponibili i seguenti operatori composti:  
  
|Operatore|Collegamento a ulteriori informazioni|Azione|  
|--------------|------------------------------|------------|  
|+=|[+ = &#40; Aggiungi EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/add-equals-transact-sql.md)|Aggiunge una quantità al valore originale e imposta il valore originale sul risultato.|  
|-=|[-= &#40; Sottrarre EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/subtract-equals-transact-sql.md)|Sottrae una quantità dal valore originale e imposta il valore originale sul risultato.|  
|*=|[&#42; = &#40; Moltiplicare EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/multiply-equals-transact-sql.md)|Moltiplica una valore per una quantità e imposta il valore originale sul risultato.|  
|/=|[&#40; dividere EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)|Divide un valore per una quantità e imposta il valore originale sul risultato.|  
|%=|[Modulo EQUALS &#40; Transact-SQL &#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)|Divide un valore per una quantità e imposta il valore originale sul modulo.|  
|&=|[& = &#40; AND bit per bit uguale &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)|Esegue un'operazione con AND bit per bit e imposta il valore originale sul risultato.|  
|^=|[^ = &#40; Bit per bit esclusivo EQUALS &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)|Esegue un'operazione con OR esclusivo bit per bit e imposta il valore originale sul risultato.|  
|&#124;=|[&#124; = &#40; OR bit per bit uguale a &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)|Esegue un'operazione con OR bit per bit e imposta il valore originale sul risultato.|  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
expression operator expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *espressione*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno qualsiasi dei dati di tipi della categoria numerica.  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'argomento con la priorità più alta. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni, vedere gli argomenti correlati a ogni operatore.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti vengono illustrate le operazioni composte.  
  
```  
DECLARE @x1 int = 27;  
SET @x1 += 2 ;  
SELECT @x1 AS Added_2;  
  
DECLARE @x2 int = 27;  
SET @x2 -= 2 ;  
SELECT @x2 AS Subtracted_2;  
  
DECLARE @x3 int = 27;  
SET @x3 *= 2 ;  
SELECT @x3 AS Multiplied_by_2;  
  
DECLARE @x4 int = 27;  
SET @x4 /= 2 ;  
SELECT @x4 AS Divided_by_2;  
  
DECLARE @x5 int = 27;  
SET @x5 %= 2 ;  
SELECT @x5 AS Modulo_of_27_divided_by_2;  
  
DECLARE @x6 int = 9;  
SET @x6 &= 13 ;  
SELECT @x6 AS Bitwise_AND;  
  
DECLARE @x7 int = 27;  
SET @x7 ^= 2 ;  
SELECT @x7 AS Bitwise_Exclusive_OR;  
  
DECLARE @x8 int = 27;  
SET @x8 |= 2 ;  
SELECT @x8 AS Bitwise_OR;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  