---
title: I campi e record di diagnostica | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- header records [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], diagnostic records
- ODBC error handling, diagnostic records
- SQLGetDiagField function
- diagnostic records [ODBC]
- errors [ODBC], diagnostic records
- fields [ODBC]
- status information [ODBC]
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 603eb8682b69a5f2abc3cd0f46adbd735de05170
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740021"
---
# <a name="diagnostic-records-and-fields"></a>Campi e record di diagnostica
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  I record di diagnostica sono associati a handle descrittore, di istruzione, di connessione o di ambiente ODBC. Quando una funzione ODBC genera un codice restituito diverso da SQL_SUCCESS o SQL_INVALID_HANDLE, l'handle chiamato dalla funzione presenta record di diagnostica associati che contengono messaggi informativi o di errore. Questi record vengono mantenuti fino a quando non vengono eliminati per effetto di una chiamata a un'altra funzione utilizzando l'handle specifico. Non esiste un limite nel numero di record di diagnostica che possono essere associati a un handle.  
  
 Sono disponibili due tipi di record di diagnostica, ovvero di intestazione e di stato. Il record di intestazione è il record 0, mentre gli eventuali record di stato vengono numerati a partire da 1. I record di diagnostica contengono campi diversi per il record di intestazione e i record di stato. Per i componenti ODBC possono anche essere definiti campi dei record di diagnostica specifici.  
  
 I campi del record di intestazione contengono informazioni generali sull'esecuzione di una funzione, inclusi il codice restituito, il conteggio delle righe, il numero di record di stato e il tipo di istruzione eseguita. Il record di intestazione viene creato sempre, a meno che una funzione ODBC non restituisca SQL_INVALID_HANDLE. Per un elenco completo dei campi del record di intestazione, vedere [SQLGetDiagField](../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md).  
  
 I campi dei record di stato contengono informazioni su errori o avvisi specifici restituiti da Gestione driver ODBC, dal driver o dall'origine dati, quali SQLSTATE, il numero dell'errore nativo, il messaggio di diagnostica, il numero di colonna e il numero di riga. I record di stato vengono creati solo se la funzione restituisce SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA o SQL_STILL_EXECUTING. Per un elenco completo dei campi nei record di stato, vedere **SQLGetDiagField**.  
  
 **SQLGetDiagRec** recupera un singolo record di diagnostica insieme ai relativi ODBC SQLSTATE, numero di errore nativo e i campi di messaggio di diagnostica. Questa funzionalità è simile a ODBC 2. _x_**SQLError** (funzione). La funzione di gestione degli errori più semplice in ODBC 3. *x* consiste nel chiamare ripetutamente **SQLGetDiagRec** inizia con il *RecNumber* parametro impostato su 1 e l'incremento *RecNumber* da 1 fino a **SQLGetDiagRec** restituisce SQL_NO_DATA. Ciò equivale a una ODBC 2. *x* applicazione che chiama **SQLError** fino a quando non restituisce SQL_NO_DATA_FOUND.  
  
 ODBC 3. *x* supporta molte più informazioni di diagnostica a ODBC 2. *x*. Queste informazioni vengono archiviate in altri campi di record di diagnostica recuperati tramite **SQLGetDiagField**.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client contiene i campi di diagnostica specifici del driver che possono essere recuperati con **SQLGetDiagField**. Le etichette di questi campi specifici del driver sono definite in sqlncli.h. Utilizzarle per recuperare lo stato, il livello di gravità, il nome del server, il nome della procedura e il numero di riga di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associati a ogni record di diagnostica. SQLNCLI. h contiene inoltre le definizioni dei codici del driver utilizza per identificare le istruzioni Transact-SQL se un'applicazione chiama **SQLGetDiagField** con *DiagIdentifier* impostato su SQL_DIAG_DYNAMIC_ FUNCTION_CODE.  
  
 **SQLGetDiagField** viene elaborato da Gestione Driver ODBC usando le informazioni sugli errori memorizza nella cache dal driver sottostante. Gestione driver ODBC memorizza nella cache i campi di diagnostica specifici del driver solo una volta stabilita una connessione. **SQLGetDiagField** restituisce SQL_ERROR se viene chiamato per ottenere i campi di diagnostica specifici del driver prima che ha stabilito una connessione è stata completata. Se una funzione di connessione ODBC restituisce SQL_SUCCESS_WITH_INFO, i campi di diagnostica specifici del driver della funzione non sono ancora disponibili. È possibile iniziare a chiamare **SQLGetDiagField** per campi di diagnostica specifici del driver solo dopo avere apportato ODBC un'altra chiamata di funzione dopo la funzione di connessione.  
  
 La maggior parte degli errori segnalati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client può essere diagnosticato in modo efficace utilizzando solo le informazioni restituite da **SQLGetDiagRec**. In alcuni casi, tuttavia, le informazioni restituite dai campi di diagnostica specifici del driver sono importanti per la diagnosi di un errore. Quando si codifica un gestore degli errori ODBC per applicazioni che usano il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client, è consigliabile usare anche **SQLGetDiagField** per recuperare almeno i SQL_DIAG_SS_MSGSTATE e SQL_DIAG_SS_SEVERITY campi specifici del driver. Se un determinato errore può essere generato in diverse posizioni nel codice [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SQL_DIAG_SS_MSGSTATE indica esattamente al supporto tecnico Microsoft il punto in cui è stato generato, fornendo in tal modo un'informazione che in alcuni casi facilita la diagnosi di un problema.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di errori e messaggi](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
