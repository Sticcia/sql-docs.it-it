---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b11c67740005573d5c48ca80a69758ab19e4d91
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014788"
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Come regola generale, considerare le implicazioni dell'utilizzo di **SQLBindCol** per provocare la conversione dei dati. Le conversioni per associazione sono processi client. Se ad esempio viene recuperato un valore a virgola mobile associato a una colonna di tipo character, nel driver viene eseguita in locale la conversione da float a character quando viene recuperata una riga. La funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT può essere utilizzata per riportare il costo della conversione dei dati nel server.  
  
 Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può restituire più set di righe di risultati in una singola esecuzione dell'istruzione. Ogni set di risultati deve essere associato separatamente. Per ulteriori informazioni sull'associazione di più set di risultati, vedere [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Lo sviluppatore può associare le colonne da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-tipi di dati C specifici usando la *TargetType* valore **SQL_C_BINARY**. Le colonne associate a tipi specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sono portabili. I tipi di dati ODBC C specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiti corrispondono alle definizioni del tipo di DB-Library e gli sviluppatori di DB-Library che si occupano della portabilità delle applicazioni potrebbero sfruttare questa caratteristica.  
  
 Il troncamento dei dati di Reporting è un processo impegnativo per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client. È possibile evitare il troncamento assicurandosi che la larghezza di tutti i buffer di dati associati sia sufficiente per restituire i dati. Per i dati di tipo character, la larghezza deve includere lo spazio per un carattere di terminazione della stringa quando viene utilizzato il comportamento predefinito del driver per la terminazione della stringa. Ad esempio, associa una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** colonna in una matrice dei risultati di cinque caratteri troncamento per ogni valore recuperato. L'associazione della stessa colonna a una matrice di sei caratteri evita il troncamento fornendo un elemento character in cui archiviare il terminatore null. [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) può essere utilizzato per recuperare dati long character e binari senza troncamento.  
  
 Per tipi di dati di valori di grandi dimensioni, se il buffer fornito dall'utente non è sufficientemente grande da contenere l'intero valore della colonna **SQL_SUCCESS_WITH_INFO** viene restituito e i dati della stringa"; viene generato l'avviso "troncamento a destra. Il **StrLen_or_IndPtr** argomento conterrà il numero di caratteri/byte archiviati nel buffer.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Supporto di SQLBindCol per le caratteristiche avanzate di data e ora  
 I valori di colonna risultato dei tipi data/ora vengono convertiti come descritto in [le conversioni da SQL a C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Si noti che per recuperare le colonne time e datetimeoffset relative strutture corrispondenti (**SQL_SS_TIME2_STRUCT** e **valore SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType*deve essere specificato come **SQL_C_DEFAULT** oppure **SQL_C_BINARY**.  
  
 Per altre informazioni, vedere [data e miglioramenti per la fase &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Supporto di SQLBindCol per tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLBindCol** supporta grandi CLR a tipi definiti dall'utente (UDT). Per altre informazioni, vedere [Large CLR User-Defined tipi &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLBindCol Function](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
