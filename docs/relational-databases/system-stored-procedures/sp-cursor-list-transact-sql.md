---
title: sp_cursor_list (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_list
- sp_cursor_list_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_list
ms.assetid: 7187cfbe-d4d9-4cfa-a3bb-96a544c7c883
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8c6cef14177e871f35ccd5c84af4a2b28e35aff5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724046"
---
# <a name="spcursorlist-transact-sql"></a>sp_cursor_list (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce gli attributi dei cursori del server aperti per la connessione corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cursor_list [ @cursor_return = ] cursor_variable_name OUTPUT   
     , [ @cursor_scope = ] cursor_scope  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @cursor_return=] *cursor_variable_name*OUTPUT  
 Nome di una variabile di cursore dichiarata. *cursor_variable_name* viene **cursore**, non prevede alcun valore predefinito. Il cursore restituito è di tipo scorrevole, dinamico e di sola lettura.  
  
 [ @cursor_scope= ] *cursor_scope*  
 Specifica il livello dei cursori da segnalare. *cursor_scope* viene **int**e non prevede alcun valore predefinito, i possibili valori sono i seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|1|Restituisce tutti i cursori locali.|  
|2|Restituisce tutti i cursori globali.|  
|3|Restituisce i cursori locali e quelli globali.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 None  
  
## <a name="cursors-returned"></a>Cursori restituiti  
 sp_cursor_list restituisce un report come parametro di output di un cursore [!INCLUDE[tsql](../../includes/tsql-md.md)], anziché come set di risultati. In questo modo i batch, le stored procedure e i trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] possono elaborare l'output una riga alla volta. Non è possibile richiamare direttamente la procedura da funzioni API del database. Il parametro di output del cursore deve essere associato a una variabile di programma, ma le API del database non supportano l'associazione di parametri o variabili del cursore.  
  
 Di seguito è riportato il formato del cursore restituito da sp_cursor_list. Il formato del cursore è analogo a quello restituito da sp_describe_cursor.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|reference_name|**sysname**|Nome utilizzato per fare riferimento al cursore. Se il riferimento al cursore è stato impostato tramite il nome specificato in un'istruzione DECLARE CURSOR, il nome di riferimento corrisponde al nome del cursore. Se il riferimento al cursore è stato impostato tramite una variabile, il riferimento corrisponde al nome della variabile di cursore.|  
|cursor_name|**sysname**|Nome del cursore che deriva da un'istruzione DECLARE CURSOR. Nelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se il cursore è stato creato impostando una variabile di cursore su un cursore **cursor_name** restituisce il nome della variabile di cursore.  Nelle versioni precedenti questa colonna di output restituisce un nome generato dal sistema.|  
|cursor_scope|**smallint**|1 = LOCAL<br /><br /> 2 = GLOBAL|  
|status|**smallint**|Valori restituiti dalla funzione di sistema CURSOR_STATUS:<br /><br /> 1 = Il cursore a cui si fa riferimento tramite il nome o la variabile è aperto. Se il cursore è di tipo insensitive, statico o keyset, il set di risultati contiene almeno una riga. Se invece è dinamico, contiene zero o più righe.<br /><br /> 0 = Il cursore a cui si fa riferimento tramite il nome o la variabile è aperto, ma non contiene righe. I cursori dinamici non restituiscono mai questo valore.<br /><br /> -1 = Il cursore a cui si fa riferimento tramite il nome o la variabile è chiuso.<br /><br /> -2 = Si applica solo alle variabili di cursore. Alla variabile non è assegnato alcun cursore. È possibile che un parametro OUTPUT abbia assegnato un cursore alla variabile, ma la stored procedure ha chiuso il cursore prima di completare l'operazione.<br /><br /> -3 = Non esiste alcun cursore o variabile di cursore con il nome specificato oppure alla variabile non è stato assegnato alcun cursore.|  
|model|**smallint**|1 = Insensitive (o statico)<br /><br /> 2 = Keyset<br /><br /> 3 = dinamica<br /><br /> 4 = Fast forward-only|  
|concorrenza|**smallint**|1 = Di sola lettura.<br /><br /> 2 = Blocchi di scorrimento.<br /><br /> 3 = Ottimistica.|  
|scrollable|**smallint**|0 = Forward-only<br /><br /> 1 = Scorrevole|  
|open_status|**smallint**|0 = Chiuso<br /><br /> 1 = Aperto|  
|cursor_rows|**int**|Numero di righe del set di risultati. Per altre informazioni, vedere [@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md).|  
|fetch_status|**smallint**|Stato dell'ultimo recupero del cursore. Per altre informazioni, vedere [@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md):<br /><br /> 0 = Recupero corretto.<br /><br /> -1 = Recupero non riuscito o non compreso entro i limiti del cursore.<br /><br /> -2 = La riga richiesta è mancante.<br /><br /> -9 = Nessun recupero eseguito sul cursore.|  
|column_count|**smallint**|Numero di colonne nel set di risultati del cursore.|  
|row_count|**smallint**|Numero di righe modificate dopo l'ultima operazione eseguita sul cursore. Per altre informazioni, vedere [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md).|  
|last_operation|**smallint**|Ultima operazione eseguita sul cursore:<br /><br /> 0 = Non è stata eseguita alcuna operazione.<br /><br /> 1 = OPEN<br /><br /> 2 = FETCH<br /><br /> 3 = INSERIMENTO<br /><br /> 4 = UPDATE<br /><br /> 5 = DELETE<br /><br /> 6 = CLOSE<br /><br /> 7 = DEALLOCATE|  
|cursor_handle|**int**|Valore univoco che identifica il cursore nell'ambito del server.|  
  
## <a name="remarks"></a>Note  
 La stored procedure sp_cursor_list consente di creare un elenco dei cursori del server aperti nella connessione e di ottenere una descrizione degli attributi globali di ogni cursore, ad esempio se è scorrevole e aggiornabile. I cursori elencati tramite sp_cursor_list sono i seguenti:  
  
-   I cursori del server [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Cursori API del server aperti da un'applicazione ODBC che viene quindi chiamata SQLSetCursorName per assegnare un nome di cursore.  
  
 Utilizzare sp_describe_cursor_columns per ottenere una descrizione degli attributi del set dei risultati restituito dal cursore. Utilizzare sp_describe_cursor_tables per ottenere un report delle tabelle di base a cui fa riferimento il cursore. stored procedure sp_describe_cursor restituisce le stesse informazioni di sp_cursor_list, ma solo per il cursore specificato.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni di esecuzione vengono assegnate per impostazione predefinita al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aperto un cursore globale e viene utilizzata la stored procedure `sp_cursor_list` per creare un report degli attributi del cursore.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a keyset-driven cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person  
WHERE LastName LIKE 'S%';  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_cursor_list.  
DECLARE @Report CURSOR;  
  
-- Execute sp_cursor_list into the cursor variable.  
EXEC master.dbo.sp_cursor_list @cursor_return = @Report OUTPUT,  
      @cursor_scope = 2;  
  
-- Fetch all the rows from the sp_cursor_list output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_cursor_list.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
