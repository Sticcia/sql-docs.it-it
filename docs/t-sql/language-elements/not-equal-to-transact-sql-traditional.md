---
title: '&lt;&gt; (diverso da) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- <>
- <>_TSQL
- Not Equal To
- Not Equal
- <>(Not Equal To)
- NOT
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- not equal to operator (<>)
- <> (not equal to operator)
ms.assetid: 34cf9b38-d589-4be9-925a-116e224609a0
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0850c14d67ee64c18b8e44a26e74bab4ab45a4fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760309"
---
# <a name="not-equal-to-transact-sql---traditional"></a>Diverso da (Transact SQL) - tradizionale
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Confronta due espressioni (operatore di confronto). Quando si confrontano due espressioni diverse da Null, il risultato è TRUE se il valore dell'operando di sinistra è diverso dal valore di quello di destra. In caso contrario il risultato è FALSE. Se uno o entrambi gli operandi sono NULL, vedere l'argomento [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression <> expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida. È necessario che il tipo di dati di entrambe le espressioni possa essere convertito in modo implicito. La conversione dipende dalle regole di [precedenza dei tipi di dati](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using--in-a-simple-query"></a>A. Uso di <> in una query semplice  
 Nell'esempio seguente vengono restituite tutte le righe nella tabella `Production.ProductCategory` che non dispongono di un valore in `ProductCategoryID` uguale a 3 o 2.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductCategoryID, Name  
FROM Production.ProductCategory  
WHERE ProductCategoryID <> 3 AND ProductCategoryID <> 2;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ProductCategoryID Name  
----------------- --------------------------------------------------  
1                 Bikes  
4                 Accessories  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori di confronto &#40;Transact-SQL&#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
