---
title: uniqueidentifier (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- uniqueidentifier
- uniqueidentifier_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- globally unique identifiers [SQL Server]
- GUIDs [SQL Server]
ms.assetid: b026035b-f3d2-4d70-989d-3884b4ca0233
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7b627fb357fba635d6aaa74ac4d1cd1c8a2d2295
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2019
ms.locfileid: "56042713"
---
# <a name="uniqueidentifier-transact-sql"></a>uniqueidentifier (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

GUID a 16 byte.
  
## <a name="remarks"></a>Remarks  
È possibile inizializzare una colonna o variabile locale di tipo **uniqueidentifier** su un valore specifico nei modi seguenti:
-   Usando le funzioni [NEWID](../../t-sql/functions/newid-transact-sql.md) o [NEWSEQUENTIALID](../../t-sql/functions/newsequentialid-transact-sql.md).    
-   Tramite la conversione da una costante stringa nel formato *xxxxxxxx*-*xxxx*-*xxxx*-*xxxx*-*xxxxxxxxxxxx*, in cui ogni *x* rappresenta una cifra esadecimale compresa nell'intervallo 0-9 oppure a-f. Ad esempio, 6F9619FF-8B86-D011-B42D-00C04FC964FF è un valore **uniqueidentifier** valido.  
  
Con i valori **uniqueidentifier** è possibile usare gli operatori di confronto. Quando si confrontano gli schemi di bit dei due valori, tuttavia, l'ordinamento non viene implementato. Le uniche operazioni che è possibile eseguire su un valore **uniqueidentifier** sono i confronti (=, <>, \<, >, \<=, >=) e la verifica del valore NULL (IS NULL e IS NOT NULL). Non è possibile utilizzare altri operatori aritmetici. Con il tipo di dati **uniqueidentifier** è possibile usare tutti i vincoli e le proprietà delle colonne, ad eccezione di IDENTITY.
  
Le colonne **uniqueidentifier** vengono usate nella replica transazionale e di tipo merge con sottoscrizioni aggiornabili, per garantire che le righe siano identificate in modo univoco in più copie della tabella.
  
## <a name="converting-uniqueidentifier-data"></a>Conversione del tipo di dati uniqueidentifier  
Per la conversione da un'espressione di caratteri, il tipo **uniqueidentifier** è considerato un tipo di dati carattere ed è pertanto soggetto alle regole di troncamento per la conversione in un tipo di dati carattere. Vale a dire che, se un'espressione di caratteri viene convertita in un tipo di dati carattere di dimensioni diverse, i valori troppo lunghi per il nuovo tipo di dati vengono troncati. Vedere la sezione relativa agli esempi.
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni

I seguenti strumenti e funzionalità non supportano il tipo di dati `uniqueidentifier`:
- PolyBase
- [Strumento di caricamento dwloader](https://msdn.microsoft.com/sql/analytics-platform-system/dwloader) per Parallel Data Warehouse

## <a name="examples"></a>Esempi  
Nell'esempio seguente un valore `uniqueidentifier` viene convertito in un tipo di dati `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Nell'esempio seguente viene illustrato il troncamento dei dati quando il valore è troppo lungo per il tipo di dati in cui avviene la conversione. Poiché la lunghezza del tipo **uniqueidentifier** è limitata a 36 caratteri, i caratteri eccedenti vengono troncati.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[NEWID &#40;Transact-SQL&#41;](../../t-sql/functions/newid-transact-sql.md)  
[NEWSEQUENTIALID &#40;Transact-SQL&#41;](../../t-sql/functions/newsequentialid-transact-sql.md)    
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)
  
  
