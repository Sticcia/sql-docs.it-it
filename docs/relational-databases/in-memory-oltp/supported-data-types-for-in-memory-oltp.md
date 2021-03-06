---
title: Tipi di dati supportati per OLTP in memoria | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8ea1371abfc033c6a19f27d005c3b97f97e6d504
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47657569"
---
# <a name="supported-data-types-for-in-memory-oltp"></a>Tipi di dati supportati per OLTP In memoria
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Questo articolo elenca i tipi di dati che non sono supportati per le funzionalità OLTP In memoria di:  
  
-   Tabelle con ottimizzazione per la memoria  
  
-   Moduli T-SQL compilati in modo nativo  
  
## <a name="unsupported-data-types"></a>Tipi di dati non supportati  
 I tipi di dati indicati di seguito non sono supportati:  
  
||||  
|-|-|-|  
|[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography &#40;Transact-SQL&#41;](../../t-sql/spatial-geography/spatial-types-geography.md)|[geometry &#40;Transact-SQL&#41;](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md)|  
|[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)|[xml &#40;Transact-SQL&#41;](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)|Tipi definiti dall'utente|,|  
  
## <a name="notable-supported-data-types"></a>Tipi di dati supportati rilevanti  
 La maggior parte dei tipi di dati è supportata dalle funzionalità di OLTP In memoria. Di seguito sono riportati alcuni tipi che vale la pena notare in modo esplicito:  
  
|Tipi stringa e binari|Per ulteriori informazioni|  
|-----------------------------|--------------------------|  
|binary e varbinary*|[binary e varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char e varchar*|[char e varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar e nvarchar*|[nchar e nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
Per i precedenti tipi di dati string e binary, a partire da SQL Server 2016:  
  
- Una singola tabella ottimizzata per la memoria può contenere anche diverse colonne di grandi dimensioni, ad esempio `nvarchar(4000)`, anche se il totale delle relative lunghezze sarebbe superiore a quello delle dimensioni fisiche della riga di 8060 byte.  
  
- Una tabella ottimizzata per la memoria può includere colonne di tipo string e binary di lunghezza massima dei tipi di dati, ad esempio `varchar(max)`.  


### <a name="identify-lobs-and-other-columns-that-are-off-row"></a>Identificare le colonne LOB e altre colonne che si trovano all'esterno di righe

A partire da SQL Server 2016, le tabelle ottimizzate per la memoria [supportano colonne all'esterno di righe](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md), che consentono a una singola riga di tabella di superare la dimensione di 8060 byte. L'istruzione Transact-SQL SELECT seguente restituisce tutte le colonne che si trovano all'esterno di righe, per tabelle ottimizzate per la memoria. Tenere presente quanto segue:

- Tutte le colonne chiave di indice vengono archiviate all'interno di righe.
  - Le chiavi di indice non univoche possono ora includere colonne che ammettono valori Null in tabelle ottimizzate per la memoria.
  - Gli indici possono essere dichiarati come UNIQUE in una tabella ottimizzata per la memoria.
- Tutte le colonne LOB vengono archiviate all'esterno di righe.
- Un valore max_length pari a -1 indica una colonna con oggetti LOB.


```sql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


### <a name="other-data-types"></a>Altri tipi di dati


|Altri tipi|Per ulteriori informazioni|  
|-----------------|--------------------------|  
|tipi di tabella|[Variabili di tabella con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di Transact-SQL per OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [Implementazione di SQL_VARIANT in una tabella con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
 [Dimensioni di tabelle e righe per le tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
