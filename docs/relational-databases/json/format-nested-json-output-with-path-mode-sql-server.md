---
title: "Formattare l'output JSON annidato con la modalità PATH (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: 12dfc255364a410de1ad5c75f3abf38155d6d70f
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Formattare l'output JSON annidato con la modalità PATH (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Per mantenere il controllo completo sull'output della clausola **FOR JSON**, specificare l'opzione **PATH**.  
  
La modalità**PATH** consente di creare oggetti wrapper e annidare proprietà complesse. I risultati vengono formattati sotto forma di matrice di oggetti JSON.  
  
L'alternativa prevede l'uso dell'opzione **AUTO** per formattare l'output automaticamente in base alla struttura dell'istruzione **SELECT**.
 -   Per altre informazioni sull'opzione **AUTO**, vedere [Formattare automaticamente l'output JSON con la modalità AUTO](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md) .
 -   Per una panoramica di entrambe le opzioni, vedere [Formattare i risultati delle query in formato JSON con FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
 
Di seguito sono riportati alcuni esempi della clausola **FOR JSON** con l'opzione **PATH** . Per formattare risultati annidati, usare nomi di colonna separati da punti oppure query annidate, come illustrato negli esempi seguenti. Per impostazione predefinita, i valori null non vengono inclusi nell'output **FOR JSON**.  

## <a name="example---dot-separated-column-names"></a>Esempio: nomi di colonna separati da punti  
La query seguente formatta le prime cinque righe della tabella `Person` di AdventureWorks come JSON.  

La clausola **FOR JSON PATH** usa l'alias o il nome di colonna per determinare il nome della chiave nell'output JSON. Se un alias contiene punti, l'opzione PATH crea oggetti annidati.  

 **Query**  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON PATH   
```  
  
 **Risultato**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sanchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  
   
## <a name="example---multiple-tables"></a>Esempio: più tabelle  
Se nella query si fa riferimento a più tabelle, **FOR JSON PATH** annida ogni colonna usando il relativo alias. La query seguente crea un oggetto JSON per ogni coppia (OrderHeader,OrderDetails) unita in join nella query. 
  
 **Query**  
  
```sql  
SELECT TOP 2 SalesOrderNumber AS 'Order.Number',  
        OrderDate AS 'Order.Date',  
        UnitPrice AS 'Product.Price',  
        OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH   
```  
  
 **Risultato**  
  
```json  
[{
    "Order": {
        "Number": "SO43659",
        "Date": "2011-05-31T00:00:00"
    },
    "Product": {
        "Price": 2024.9940,
        "Quantity": 1
    }
}, {
    "Order": {
        "Number": "SO43659"
    },
    "Product": {
        "Price": 2024.9940
    }
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>Altre informazioni sul supporto JSON integrato in SQL Server  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere i [post del blog sul supporto JSON integrato](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure redatti da Jovan Popovic, Microsoft Program Manager.

## <a name="see-also"></a>Vedere anche  
 [Clausola FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
