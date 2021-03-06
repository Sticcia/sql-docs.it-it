---
title: Recupero di dati | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3414992c-61c0-4e7d-b509-72517e52c1bb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbc6d4e971a810d581b8ace2de8fd7882171c460
ms.sourcegitcommit: c1105ce638078d2c941cd656b34f78486e6b2d89
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676059"
---
# <a name="retrieving-data"></a>Recupero di dati
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento e negli argomenti di questa sezione viene illustrato il recupero dei dati.  
  
## <a name="sqlsrv-driver"></a>Driver SQLSRV  
Il driver SQLSRV dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] fornisce le seguenti opzioni per il recupero dei dati da un set di risultati:  
  
-   [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)  
  
-   [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)  
  
-   [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)/[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)  
  
> [!NOTE]  
> Quando si usa una delle funzioni elencate, evitare i confronti Null come criterio di uscita dai cicli. Poiché le funzioni **sqlsrv** restituiscono false quando si verifica un errore, il codice seguente potrebbe causare un ciclo infinito in caso di errore in [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md):  
>   
> `/*``This code could result in an infinite loop. It is recommended that`  
>   
> `you do NOT use null comparisons as the criterion for exiting loops,`  
>   
> `as is done here. */`  
>   
> `do{`  
>   
> `$result = sqlsrv_fetch_array($stmt);`  
>   
> `} while( !is_null($result));`  
  
Se la query recupera più set di risultati, è possibile passare al set di risultati successivo con [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md).  
  
A partire dalla versione 1.1 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], è possibile usare [sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md) per verificare se un set di risultati contiene righe.  
  
## <a name="pdosqlsrv-driver"></a>Driver PDO_SQLSRV  
Il driver PDO_SQLSRV dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] offre le seguenti opzioni per il recupero dei dati da un set di risultati:  
  
-   [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md)  
  
-   [PDOStatement::fetchAll](../../connect/php/pdostatement-fetchall.md)  
  
-   [PDOStatement::fetchColumn](../../connect/php/pdostatement-fetchcolumn.md)  
  
-   [PDOStatement::fetchObject](../../connect/php/pdostatement-fetchobject.md)  
  
Se la query recupera più set di risultati, è possibile passare al set di risultati successivo con [PDOStatement::nextRowset](../../connect/php/pdostatement-nextrowset.md).  
  
Per verificare il numero di righe incluse in un set di risultati, specificare un cursore scorrevole ed eseguire una chiamata a [PDOStatement::rowCount](../../connect/php/pdostatement-rowcount.md).  
  
[PDO::prepare](../../connect/php/pdo-prepare.md) consente di specificare un tipo di cursore. È quindi possibile usare [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) per selezionare una riga. Vedere [PDO::prepare](../../connect/php/pdo-prepare.md) per un esempio e altre informazioni.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|---------|---------------|  
|[Recupero di dati come flusso](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)|Fornisce una panoramica sull'uso dei flussi di dati e i collegamenti a specifici casi d'uso.|  
|[Uso dei parametri direzionali](../../connect/php/using-directional-parameters.md)|Descrive l'uso dei parametri direzionali in una chiamata a una stored procedure.|  
|[Specifica di un tipo di cursore e selezione di righe](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)|Viene illustrato come creare un set di risultati con righe cui è possibile accedere in qualsiasi ordine.|  
|[Procedura: Recuperare i tipi di data e ora come stringhe usando il driver SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)|Descrive come recuperare i tipi di data e ora come stringhe usando il driver SQLSRV.|  
|[Procedura: Recuperare i tipi di data e ora come oggetti Datetime PHP usando il driver PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)|Viene descritto come recuperare i tipi di data e ora come oggetti usando il driver PDO_SQLSRV.|  
|[Formattazione delle stringhe decimale con il Driver SQLSRV](../../connect/php/formatting-decimals-sqlsrv-driver.md)|Di seguito viene illustrato come formattare i valori decimali o denaro usando il driver SQLSRV.|  
|[Formattazione delle stringhe decimale con il Driver PDO_SQLSRV](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)|Di seguito viene illustrato come formattare i valori decimali o denaro usando il driver PDO_SQLSRV.|  
  
## <a name="related-sections"></a>Sezioni correlate  
[Procedura: Specificare i tipi di dati PHP](../../connect/php/how-to-specify-php-data-types.md)  
  
## <a name="see-also"></a>Vedere anche  
[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Recupero di dati](../../connect/php/retrieving-data.md)  
  
