---
title: sp_datatype_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/25/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_datatype_info_TSQL
- sp_datatype_info
dev_langs:
- TSQL
helpviewer_keywords:
- sp_datatype_info
ms.assetid: 045f3b5d-6bb7-4748-8b4c-8deb4bc44147
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3eadc5efc471f44998abddc596f1acc5c6e378ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62506965"
---
# <a name="spdatatypeinfo-transact-sql"></a>sp_datatype_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Restituisce informazioni sui tipi di dati supportati nell'ambiente corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_datatype_info [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @data_type = ] data_type` È il numero di codice per il tipo di dati specificato. Per ottenere un elenco di tutti i tipi di dati, omettere questo parametro. *data_type* viene **int**, con un valore predefinito è 0.  
  
`[ @ODBCVer = ] odbc_version` È la versione di ODBC utilizzata. *odbc_version* viene **tinyint**, con un valore predefinito è 2.  
  
## <a name="return-code-values"></a>Valori restituiti  
 None  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|Tipo di dati che dipende dal sistema di gestione di database (DBMS).|  
|DATA_TYPE|**smallint**|Codice per il tipo di dati ODBC a cui viene eseguito il mapping di tutte le colonne di tale tipo.|  
|PRECISION|**int**|Precisione massima del tipo di dati nell'origine dati. Per i tipi di dati per cui la precisione non è applicabile, viene restituito NULL. Il valore restituito per la colonna PRECISION è in base 10.|  
|LITERAL_PREFIX|**varchar(** 32 **)**|Carattere o caratteri che precedono il nome di una costante, Ad esempio, una virgoletta singola (**'**) per i tipi di carattere e 0x per i dati binari.|  
|LITERAL_SUFFIX|**varchar(** 32 **)**|Carattere o caratteri che seguono il nome di una costante, Ad esempio, una virgoletta singola (**'**) per i tipi di carattere e nessuna virgoletta per i dati binari.|  
|CREATE_PARAMS|**varchar(** 32 **)**|Descrizione dei parametri di creazione per questo tipo di dati, Ad esempio, **decimale** "precision, scale", viene **float** è NULL, e **varchar** "max_length".|  
|NULLABLE|**smallint**|Specifica se i valori Null sono supportati.<br /><br /> 1 = I valori Null sono supportati.<br /><br /> 0 = I valori Null non sono supportati.|  
|CASE_SENSITIVE|**smallint**|Specifica se viene rispettata la distinzione tra maiuscole e minuscole.<br /><br /> 1 = In tutte le colonne di questo tipo viene rispettata la distinzione tra maiuscole e minuscole (per le regole di confronto).<br /><br /> 0 = In tutte le colonne di questo tipo non viene rispettata la distinzione tra maiuscole e minuscole.|  
|SEARCHABLE|**smallint**|Specifica la funzionalità di ricerca del tipo di colonna.<br /><br /> 1 = Non è possibile eseguire ricerche in questo tipo di colonna.<br /><br /> 2 = È possibile eseguire ricerche con LIKE.<br /><br /> 3 = È possibile eseguire ricerche con WHERE.<br /><br /> 4 = È possibile eseguire ricerche con WHERE o LIKE.|  
|UNSIGNED_ATTRIBUTE|**smallint**|Specifica se il tipo di dati include o meno il segno.<br /><br /> 1 = Tipo di dati senza segno.<br /><br /> 0 = Tipo di dati con segno.|  
|MONEY|**smallint**|Specifica la **denaro** tipo di dati.<br /><br /> 1 = **denaro** tipo di dati.<br /><br /> 0 = non un' **denaro** tipo di dati.|  
|AUTO_INCREMENT|**smallint**|Specifica l'incremento automatico.<br /><br /> 1 = Incremento automatico abilitato.<br /><br /> 0 = Incremento automatico disabilitato.<br /><br /> NULL = Attributo non applicabile.<br /><br /> In un'applicazione è possibile inserire valori in una colonna cui è associato questo attributo, ma non è possibile aggiornare i valori della colonna. Fatta eccezione per il **bit** tipo di dati, AUTO_INCREMENT è valido solo per i tipi di dati che appartengono a esatti e numerici categorie dei tipi di dati numerici approssimati.|  
|LOCAL_TYPE_NAME|**sysname**|Versione localizzata del nome del tipo di dati dipendente dall'origine dati. In francese, ad esempio, DECIMAL è DECIMALE. Se il nome localizzato non è supportato dall'origine dati, viene restituito NULL.|  
|MINIMUM_SCALE|**smallint**|Scala minima del tipo di dati nell'origine dati. Se a un tipo di dati è associata una scala fissa, le colonne MINIMUM_SCALE e MAXIMUM_SCALE contengono entrambe lo stesso valore. Se la scala non è applicabile, viene restituito NULL.|  
|MAXIMUM_SCALE|**smallint**|Scala massima del tipo di dati nell'origine dati. Se la scala massima non viene definita separatamente nell'origine dati, ma viene invece definita come corrispondente al valore della precisione massima, questa colonna contiene lo stesso valore della colonna PRECISION.|  
|SQL_DATA_TYPE|**smallint**|Valore del tipo di dati SQL visualizzato nel campo TYPE del descrittore. Questa colonna è uguale alla colonna DATA_TYPE, tranne per il **data/ora** e ANSI **intervallo** i tipi di dati. Questo campo restituisce sempre un valore.|  
|SQL_DATETIME_SUB|**smallint**|**Data/ora** o ANSI **intervallo** sottocodice se il valore di SQL_DATA_TYPE è SQL_DATETIME o SQL_INTERVAL. Per i dati di tipi diversi da **data/ora** e ANSI **intervallo**, questo campo è NULL.|  
|NUM_PREC_RADIX|**int**|Numero di bit o di cifre per il calcolo del numero massimo che può contenere una colonna. Nel caso di tipi di dati numerici approssimati, questa colonna contiene il valore 2 per indicare diversi bit. Nel caso di tipi di dati numerici esatti, questa colonna contiene il valore 10 per indicare diverse cifre decimali. Negli altri casi la colonna è NULL. L'applicazione può calcolare il numero massimo che è possibile immettere nella colonna tramite la combinazione di precisione e radice.|  
|INTERVAL_PRECISION|**smallint**|Valore dell'intervallo di precisione iniziale se *data_type* viene **intervallo**; in caso contrario, NULL.|  
|USERTYPE|**smallint**|**usertype** valore dalla tabella systypes.|  
  
## <a name="remarks"></a>Note  
 sp_datatype_info corrisponde a SQLGetTypeInfo in ODBC. I risultati restituiti vengono ordinati in base a DATA_TYPE e quindi in base alla precisione del mapping del tipo di dati al tipo di dati SQL ODBC corrispondente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente recupera le informazioni per il **sysname** e **nvarchar** tipi di dati specificando il *data_type* valore `-9`.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info -9;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database le Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
