---
title: Uso di set di risultati predefiniti SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d7101cf4775e5280c22cc27ecae009410d231d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62511686"
---
# <a name="using-sql-server-default-result-sets"></a>Utilizzo dei set di risultati predefiniti di SQL Server
  Gli attributi predefiniti del cursore ODBC sono:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Ogni volta che questi attributi sono impostati sui valori predefiniti, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizza un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] set di risultati predefinito. I set di risultati predefiniti possono essere utilizzati per qualsiasi istruzione SQL supportata da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e rappresentano il metodo più efficiente per trasferire un intero set di risultati al client.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] introdotto il supporto per più set di risultati attivi (MARS); le applicazioni possono ora includere più di un set di risultati predefinito attivo per connessione. Per impostazione predefinita, la funzionalità MARS non è abilitata.  
  
 Prima di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], i set di risultati predefiniti non supportavano più istruzioni attive nella stessa connessione. Dopo l'esecuzione di un'istruzione SQL in una connessione, il server non accetta comandi dal client in tale connessione finché non sono state elaborate tutte le righe del set di risultati, ad eccezione di una richiesta per annullare il resto del set di risultati. Per annullare il resto di un set di risultati parzialmente elaborato, chiamare [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) oppure [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) con il *fOption* parametro impostato su SQL_CLOSE. Per completare un set di risultati parzialmente elaborato e verificare la presenza di un altro set di risultati, chiamare [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md). Se un'applicazione ODBC tenta di eseguire un comando su un handle di connessione prima di un set di risultati predefinito è stato completamente elaborato, la chiamata che genera l'errore SQL_ERROR e una chiamata a **SQLGetDiagRec** restituisce:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità di implementazione dei cursori](how-cursors-are-implemented.md)  
  
  
