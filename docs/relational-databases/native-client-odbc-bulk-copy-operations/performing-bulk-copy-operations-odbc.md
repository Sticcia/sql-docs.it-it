---
title: Esecuzione di operazioni di copia Bulk (ODBC) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC]
- ODBC, bulk copy operations
- minimally logged operations [SQL Server Native Client]
- bulk copy [ODBC], about bulk copy
ms.assetid: 5c793405-487c-4f52-88b8-0091d529afb3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 98b59d3b5d3c0679ec8fb060b66afa44a38c1262
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013926"
---
# <a name="performing-bulk-copy-operations-odbc"></a>Esecuzione di operazioni di copia bulk (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Lo standard ODBC non supporta direttamente le operazioni di copia bulk [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In caso di connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0 o successiva, il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client supporta le funzioni DB-Library che eseguono operazioni di copia bulk [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa estensione specifica del driver fornisce un percorso di aggiornamento semplice per le applicazioni DB-Library esistenti che utilizzano le funzioni di copia bulk. Il supporto specifico per la copia bulk è disponibile nei file seguenti:  
  
-   sqlncli.h  
  
     Include prototipi della funzione e definizioni costanti per le funzioni di copia bulk. sqlncli.h deve essere incluso nell'applicazione ODBC che esegue le operazioni di copia bulk e deve trovarsi nel percorso di inclusione dell'applicazione quando viene compilato.  
  
-   sqlncli11.lib  
  
     Deve trovarsi nel percorso della libreria del linker e deve essere specificato come un file da collegare. sqlncli11.lib è distribuito con il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Deve essere presente in fase di esecuzione. sqlncli11.dll è distribuito con il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
> [!NOTE]  
>  ODBC **SQLBulkOperations** funzione ha alcuna relazione con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzioni di copia bulk. Per eseguire le operazioni di copia bulk è necessario che le applicazioni utilizzino le funzioni di copia bulk specifiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="minimally-logging-bulk-copies"></a>Registrazione minima delle copie bulk  
 Con un modello di recupero con registrazione completa, tutte le operazioni di inserimento di righe eseguite durante il caricamento bulk vengono registrate in modo completo nel log delle transazioni. In caso di caricamenti di grandi quantità di dati, questo può causare un rapido esaurimento dello spazio disponibile nel log delle transazioni. In determinate condizioni la registrazione minima è consentita. Tale registrazione riduce la possibilità che un'operazione di caricamento bulk riempia lo spazio di log e risulta anche più efficiente della registrazione completa.  
  
 Per informazioni sull'utilizzo della registrazione minima, vedere [Prerequisites for Minimal Logging in Bulk Import](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
## <a name="remarks"></a>Note  
 Quando bcp.exe viene utilizzato in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva, potrebbero essere visualizzati errori nelle situazioni in cui non si presenta alcun errore nelle versioni precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Questo avviene perché nelle versioni successive bcp.exe non esegue più la conversione implicita dei tipi di dati. Nelle versioni precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] bcp.exe converte i dati numerici in un tipo di dati money, se la tabella di destinazione contiene tale tipo di dati. In tale situazione, tuttavia, bcp.exe tronca semplicemente i campi aggiuntivi. A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], se i dati di tipi non corrispondono tra il file e la tabella di destinazione, bcp.exe genererà un errore se sono presenti dati che dovrebbero essere troncati per rientrare nella tabella di destinazione. Per risolvere questo errore, correggere i dati in modo che corrispondano al tipo di dati di destinazione. Se si desidera, è possibile utilizzare il file bcp.exe di una versione precedente a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
  
-   [Uso di file di dati e file di formato](../../relational-databases/native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
-   [Copia bulk da variabili di programma](../../relational-databases/native-client-odbc-bulk-copy-operations/bulk-copying-from-program-variables.md)  
  
-   [Gestione delle dimensioni dei batch di copia bulk](../../relational-databases/native-client-odbc-bulk-copy-operations/managing-bulk-copy-batch-sizes.md)  
  
-   [Copia bulk di dati di tipo text e image](../../relational-databases/native-client-odbc-bulk-copy-operations/bulk-copying-text-and-image-data.md)  
  
-   [Conversione della copia bulk da DB-Library a ODBC](../../relational-databases/native-client-odbc-bulk-copy-operations/converting-from-db-library-to-odbc-bulk-copy.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Informazioni sull'importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
