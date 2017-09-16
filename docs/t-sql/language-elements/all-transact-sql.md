---
title: TUTTE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
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
f1_keywords:
- ALL_TSQL
- ALL
dev_langs:
- TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fd1b250a30b83a3b014384aafee6c40ff4f1a5a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Confronta un valore scalare con un set di valori a colonna singola.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>Argomenti  
 *scalar_expression*  
 È qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Operatore di confronto.  
  
 *sottoquery*  
 Sottoquery che restituisce un set di risultati a colonna singola. Il tipo di dati della colonna restituita deve essere il tipo di dati stesso come il tipo di dati di *scalar_expression*.  
  
 Istruzione SELECT con restrizioni, in cui la clausola ORDER BY e la parola chiave INTO non sono consentite.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 Restituisce TRUE se il confronto specificato è TRUE per tutte le coppie (*scalar_expression***,***x)*, quando *x* è un valore di set di colonna singola. in caso contrario restituisce FALSE.  
  
## <a name="remarks"></a>Osservazioni  
 TUTTI richiede il *scalar_expression* deve essere confrontato con ogni valore viene restituito dalla sottoquery. Ad esempio, se la sottoquery restituisce i valori 2 e 3, *scalar_expression* < = ALL (sottoquery) restituisce TRUE per un *scalar_expression* di 2. Se la sottoquery restituisce i valori 2 e 3, *scalar_expression* = ALL (sottoquery) restituisce false, perché alcuni dei valori della sottoquery (il valore 3) non soddisfano i criteri dell'espressione.  
  
 Per le istruzioni che richiedono il *scalar_expression* per deve essere confrontato a un solo valore restituito dalla sottoquery, vedere [alcune &#124; I &#40; Transact-SQL &#41; ](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 Le informazioni contenute in questo sono rilevanti per l'utilizzo dell'opzione ALL con una sottoquery. TUTTE possono essere utilizzate anche con [unione](../../t-sql/language-elements/set-operators-union-transact-sql.md) e [selezionare](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una stored procedure che determina se tutti i componenti di un oggetto specificato `SalesOrderID` nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database può essere prodotti nel numero di giorni specificato. Nell'esempio viene utilizzata una sottoquery per creare un elenco contenente i numeri corrispondenti ai valori di `DaysToManufacture` per tutti i componenti della colonna `SalesOrderID` specifica e viene quindi verificato che tutti i valori di `DaysToManufacture` siano maggiori del numero di giorni specificato.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 Per testare la procedura, eseguirla utilizzando il valore `SalesOrderID 49080`, a cui sono associati un componente che richiede `2` giorni e due componenti che richiedono 0 giorni. La prima istruzione, di seguito, soddisfa i criteri, mentre la seconda no.  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>Vedere anche  
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Ad esempio &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  
