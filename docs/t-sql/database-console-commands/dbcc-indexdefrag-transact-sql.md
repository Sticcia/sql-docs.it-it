---
title: DBCC INDEXDEFRAG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- INDEXDEFRAG
- DBCC INDEXDEFRAG
- DBCC_INDEXDEFRAG_TSQL
- INDEXDEFRAG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- defragmenting indexes
- DBCC INDEXDEFRAG statement
- leaf level defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
ms.assetid: 3c7df676-4843-44d0-8c1c-a9ab7e593b70
author: pmasl
ms.author: umajay
manager: craigg
ms.openlocfilehash: 8efd6bf4ca5ec7cf4a1ab1699bf1cae5ce33cb08
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685468"
---
# <a name="dbcc-indexdefrag-transact-sql"></a>DBCC INDEXDEFRAG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Deframmenta gli indici della tabella o vista specificata.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] In alternativa, usare [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md).  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC INDEXDEFRAG  
(  
    { database_name | database_id | 0 }   
    , { table_name | table_id | view_name | view_id }   
    [ , { index_name | index_id } [ , { partition_number | 0 } ] ]  
)  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name* | *database_id* | 0  
 Database contenente l'indice da deframmentare. Se si specifica 0, viene utilizzato il database corrente. I nomi dei database devono essere conformi alle regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 *table_name* | *table_id* | *view_name* | *view_id*  
 Tabella o vista contenente l'indice da deframmentare. I nomi delle tabelle e delle viste devono essere conformi alle regole per gli identificatori.  
  
 *index_name* | *index_id*  
 Nome o ID dell'indice da deframmentare. Se viene omesso, l'istruzione deframmenta tutti gli indici della tabella o vista specificata. I nomi degli indici devono essere conformi alle regole per gli identificatori.  
  
 *partition_number* | 0  
 Numero di partizione dell'indice da deframmentare. Se non viene specificato o viene specificato 0, l'istruzione deframmenta tutte le partizioni nell'indice specificato.  
  
 WITH NO_INFOMSGS  
 Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="remarks"></a>Remarks  
L'istruzione DBCC INDEXDEFRAG deframmenta il livello foglia di un indice in modo che l'ordine fisico delle pagine corrisponda all'ordine logico da sinistra a destra dei nodi foglia, con un conseguente miglioramento delle prestazioni di analisi dell'indice.
  
> [!NOTE]  
>  Quando si esegue DBCC INDEXDEFRAG, la deframmentazione dell'indice viene eseguita in modo seriale. Ciò significa che l'operazione su un indice singolo viene eseguita tramite un thread singolo, senza parallelismo. Inoltre, le operazioni eseguite su più indici dalla stessa istruzione DBCC INDEXDEFRAG vengono eseguite su un indice per volta.  
  
L'istruzione DBCC INDEXDEFRAG consente inoltre di compattare le pagine di un indice in base al fattore di riempimento specificato durante la creazione dell'indice. Le pagine vuote create in seguito alla compattazione vengono rimosse. Per altre informazioni, vedere [Specificare un fattore di riempimento per un indice](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).
  
Se un indice si estende su più file, DBCC INDEXDEFRAG deframmenta un file alla volta. Non viene eseguita la migrazione delle pagine da un file all'altro.
  
DBCC INDEXDEFRAG segnala la percentuale di completamento stimata ogni cinque minuti. È possibile arrestare l'istruzione in qualsiasi momento. In questo caso il lavoro completato viene conservato.
  
A differenza di DBCC DBREINDEX e dell'operazione di compilazione degli indici in generale, DBCC INDEXDEFRAG è un'operazione eseguita online. Non mantiene attivi blocchi per un lungo periodo di tempo e di conseguenza non blocca le query o gli aggiornamenti in esecuzione. La deframmentazione di un indice relativamente non frammentato risulta più rapida rispetto alla creazione di un nuovo indice. I tempi di deframmentazione infatti sono correlati al livello di frammentazione. La deframmentazione di un indice molto frammentato può richiedere molto più tempo rispetto alla ricompilazione dell'indice.
  
La deframmentazione viene sempre registrata indipendentemente dal modello di recupero del database impostato. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md). La deframmentazione di un indice molto frammentato può generare un log molto maggiore di quello generato per una creazione di indice a registrazione completa. Dato tuttavia che la deframmentazione viene eseguita come una serie di transazioni brevi, se si eseguono backup del log frequenti o si imposta il modello di recupero su SIMPLE, non è necessario un log molto esteso.
  
## <a name="restrictions"></a>Restrictions  
DBCC INDEXDEFRAG sposta le pagine foglia dell'indice. Pertanto, se un indice è intercalato con altri indici sul disco, l'esecuzione di DBCC INDEXDEFRAG su quell'indice non rende contigue tutte le pagine foglia dell'indice. Per migliorare il raggruppamento delle pagine, è necessario ricompilare l'indice.
Non è possibile utilizzare DBCC INDEXDEFRAG per deframmentare gli indici seguenti:
-   Un indice disabilitato.  
-   Un indice con blocco di pagina impostato su OFF.  
-   Un indice spaziale.  
  
DBCC INDEXDEFRAG non è utilizzabile con le tabelle di sistema.
  
## <a name="result-sets"></a>Set di risultati  
DBCC INDEXDEFRAG restituisce il set di risultati seguente (i valori possono variare) se un indice viene specificato nell'istruzione (a meno che non sia specificato WITH NO_INFOMSGS):
  
```sql
Pages Scanned Pages Moved Pages Removed  
------------- ----------- -------------  
359           346         8  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
Il chiamante deve essere proprietario della tabella o membro del ruolo predefinito del server **sysadmin** o dei ruoli predefiniti del database **db_owner** e **db_ddladmin**.
  
## <a name="examples"></a>Esempi  
### <a name="a-using-dbcc-indexdefrag-to-defragment-an-index"></a>A. Utilizzo di DBCC INDEXDEFRAG per deframmentare un indice  
Nell'esempio seguente vengono deframmentate tutte le partizioni dell'indice `PK_Product_ProductID` nella tabella `Production.Product` del database `AdventureWorks`.
  
```sql  
DBCC INDEXDEFRAG (AdventureWorks2012, 'Production.Product', PK_Product_ProductID);  
GO  
```  
  
### <a name="b-using-dbcc-showcontig-and-dbcc-indexdefrag-to-defragment-the-indexes-in-a-database"></a>b. Utilizzo di DBCC SHOWCONTIG e DBCC INDEXDEFRAG per deframmentare gli indici di un database  
 Nell'esempio seguente viene illustrato un metodo semplice per deframmentare tutti gli indici di un database il cui livello di frammentazione è superiore alla soglia massima specificata.  
  
```sql  
/*Perform a 'USE <database name>' to select the database in which to run the script.*/  
-- Declare variables  
SET NOCOUNT ON;  
DECLARE @tablename varchar(255);  
DECLARE @execstr   varchar(400);  
DECLARE @objectid  int;  
DECLARE @indexid   int;  
DECLARE @frag      decimal;  
DECLARE @maxfrag   decimal;  
  
-- Decide on the maximum fragmentation to allow for.  
SELECT @maxfrag = 30.0;  
  
-- Declare a cursor.  
DECLARE tables CURSOR FOR  
   SELECT TABLE_SCHEMA + '.' + TABLE_NAME  
   FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_TYPE = 'BASE TABLE';  
  
-- Create the table.  
CREATE TABLE #fraglist (  
   ObjectName char(255),  
   ObjectId int,  
   IndexName char(255),  
   IndexId int,  
   Lvl int,  
   CountPages int,  
   CountRows int,  
   MinRecSize int,  
   MaxRecSize int,  
   AvgRecSize int,  
   ForRecCount int,  
   Extents int,  
   ExtentSwitches int,  
   AvgFreeBytes int,  
   AvgPageDensity int,  
   ScanDensity decimal,  
   BestCount int,  
   ActualCount int,  
   LogicalFrag decimal,  
   ExtentFrag decimal);  
  
-- Open the cursor.  
OPEN tables;  
  
-- Loop through all the tables in the database.  
FETCH NEXT  
   FROM tables  
   INTO @tablename;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
-- Do the showcontig of all indexes of the table  
   INSERT INTO #fraglist   
   EXEC ('DBCC SHOWCONTIG (''' + @tablename + ''')   
      WITH FAST, TABLERESULTS, ALL_INDEXES, NO_INFOMSGS');  
   FETCH NEXT  
      FROM tables  
      INTO @tablename;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE tables;  
DEALLOCATE tables;  
  
-- Declare the cursor for the list of indexes to be defragged.  
DECLARE indexes CURSOR FOR  
   SELECT ObjectName, ObjectId, IndexId, LogicalFrag  
   FROM #fraglist  
   WHERE LogicalFrag >= @maxfrag  
      AND INDEXPROPERTY (ObjectId, IndexName, 'IndexDepth') > 0;  
  
-- Open the cursor.  
OPEN indexes;  
  
-- Loop through the indexes.  
FETCH NEXT  
   FROM indexes  
   INTO @tablename, @objectid, @indexid, @frag;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   PRINT 'Executing DBCC INDEXDEFRAG (0, ' + RTRIM(@tablename) + ',  
      ' + RTRIM(@indexid) + ') - fragmentation currently '  
       + RTRIM(CONVERT(varchar(15),@frag)) + '%';  
   SELECT @execstr = 'DBCC INDEXDEFRAG (0, ' + RTRIM(@objectid) + ',  
       ' + RTRIM(@indexid) + ')';  
   EXEC (@execstr);  
  
   FETCH NEXT  
      FROM indexes  
      INTO @tablename, @objectid, @indexid, @frag;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE indexes;  
DEALLOCATE indexes;  
  
-- Delete the temporary table.  
DROP TABLE #fraglist;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)
  
  

