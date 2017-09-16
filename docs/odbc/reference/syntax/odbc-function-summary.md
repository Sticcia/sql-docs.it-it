---
title: Riepilogo delle funzioni ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9441a955eaa4a9001b7acd655f7753e32f49e68e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-function-summary"></a>Riepilogo delle funzioni ODBC
Nella tabella seguente elenca le funzioni ODBC, raggruppate per tipo di attività e include la designazione di conformità e una breve descrizione dello scopo di ogni funzione. Per ulteriori informazioni sulle designazioni di conformità, vedere [ODBC e Standard CLI](../../../odbc/reference/odbc-and-the-standard-cli.md). Per ulteriori informazioni sulla sintassi e semantica per ogni funzione, vedere [riferimento all'API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Un'applicazione può chiamare il **SQLGetInfo** funzione per ottenere informazioni di conformità di un driver. Per ottenere informazioni sul supporto per una funzione specifica di un driver, un'applicazione può chiamare **SQLGetFunctions**.  
  
|Attività|Nome funzione|Conformità|Scopo|  
|----------|-------------------|-----------------|-------------|  
|Connessione a un'origine dati|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|Ottiene un handle di ambiente, connessione, istruzione o descrittore.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|Si connette a un driver specifico fornendo il nome di origine dati, l'ID utente e password.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|Si connette a un driver specifico da una stringa di connessione o le richieste che il gestore dei Driver e il driver visualizzare finestre di dialogo di connessione per l'utente.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|Restituisce i livelli successivi di attributi di connessione e valori di attributo valido. Quando è stato specificato un valore per ogni attributo di connessione, si connette all'origine dati.|  
|Ottenere informazioni su un driver e un'origine dati|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|Restituisce l'elenco delle origini dati disponibili.<br /><br /> Restituisce l'elenco dei driver installati e i relativi attributi.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|Restituisce informazioni relative a un'origine dati e i driver specifica.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|Restituisce supportate funzioni del driver.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|Restituisce informazioni sui tipi di dati supportati.|  
|Impostazione e recupero attributi del driver|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|Imposta un attributo di connessione.<br /><br /> Restituisce il valore di un attributo di connessione.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|Imposta un attributo di ambiente.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|Restituisce il valore di un attributo di ambiente.|  
||[Funzione SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|Imposta un attributo di istruzione.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|Restituisce il valore di un attributo di istruzione.|  
|Impostazione e recupero di campi di descrizione|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|Restituisce il valore di un campo singolo descrittore.<br /><br /> Restituisce i valori di più campi di descrizione.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|Imposta un campo di descrizione singolo.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|Imposta più campi di descrizione.|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|Copia informazioni sul descrittore da handle di uno descrittore a altro.|  
|Preparazione di SQL richieste|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|Prepara un'istruzione SQL per un'esecuzione successiva.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|Consente di assegnare spazio di archiviazione per un parametro in un'istruzione SQL.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|Restituisce il nome di cursore associato a un handle di istruzione.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|Specifica un nome di cursore.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|Imposta le opzioni che controllano il comportamento del cursore.|  
|Invio di richieste|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|Esegue un'istruzione preparata.<br /><br /> Esegue un'istruzione.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|Restituisce il testo di un'istruzione SQL convertita dal driver.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|Restituisce la descrizione per un parametro specifico in un'istruzione.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|Restituisce il numero di parametri in un'istruzione.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|Usato in combinazione con **SQLPutData** per fornire dati di parametro in fase di esecuzione. (Utile per i valori di dati di tipo long).|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|Invia o parte di un valore di dati per un parametro. (Utile per i valori di dati di tipo long).|  
|Recupero dei risultati e informazioni sui risultati|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|Restituisce il numero di righe interessate da un'istruzione insert, update o richiesta di eliminazione.<br /><br /> Restituisce il numero di colonne nel set di risultati.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|Descrive una colonna nel set di risultati.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|Vengono descritti gli attributi di una colonna nel set di risultati.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|Assegna la memoria per una colonna di risultati e specifica il tipo di dati.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|Restituisce più righe di risultati.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|Restituisce le righe di risultati scorrevoli.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|Restituisce o parte di una colonna di una riga di un risultato impostato. (Utile per i valori di dati di tipo long).|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|Posiziona un cursore all'interno di un blocco di recupero di dati e consente a un'applicazione per aggiornare i dati nel set di righe o aggiornare o eliminare dati nel set di risultati.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|Esegue le operazioni di inserimento bulk e segnalibro bulk operazioni, incluso l'aggiornamento, eliminazione e il recupero dal segnalibro.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|Determina se sono presenti ulteriori risultati set disponibili e, in caso affermativo, inizializza l'elaborazione di set di risultati successivo.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|Restituisce informazioni diagnostiche aggiuntive (un singolo campo della struttura di dati di diagnostica).|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|Restituisce informazioni diagnostiche aggiuntive (più campi della struttura di dati di diagnostica).|  
|Recupero di informazioni sulle tabelle di sistema dell'origine dati (funzioni di catalogo)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> Apri gruppo|Restituisce un elenco di colonne e i privilegi associati uno o più tabelle.<br /><br /> Restituisce l'elenco di nomi di colonna nelle tabelle specificate.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|Restituisce un elenco di nomi di colonne che costituiscono le chiavi esterne, se presenti per una tabella specificata.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|Restituisce l'elenco di nomi di colonne che costituiscono la chiave primaria per una tabella.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|Restituisce l'elenco di input e i parametri di output, nonché le colonne che costituiscono il set di risultati per le procedure specificate.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|Restituisce l'elenco di nomi di procedure archiviati in un'origine dati specifica.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|Apri gruppo|Restituisce informazioni sui set ottimale di colonne che identifica in modo univoco una riga in una tabella specificata o le colonne che vengono aggiornate automaticamente quando qualsiasi valore nella riga viene aggiornato da una transazione.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|Restituisce le statistiche di una singola tabella e l'elenco di indici associati alla tabella.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|Restituisce un elenco di tabelle e i privilegi associati a ogni tabella.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|Apri gruppo|Restituisce l'elenco dei nomi di tabella archiviata in un'origine dati specifica.|  
|Un'istruzione di terminazione|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|Termina l'elaborazione di istruzione, Elimina i risultati in sospeso e, facoltativamente, libera tutte le risorse associate all'handle di istruzione.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|Chiude un cursore che è stato aperto in un handle di istruzione.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|Annulla l'elaborazione in un'istruzione.|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|Annulla l'elaborazione in un'istruzione o di connessione.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|Esegue il commit o il rollback di una transazione.|  
|Chiusura di una connessione|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|Chiude la connessione.<br /><br /> Rilascia un handle di ambiente, connessione, istruzione o descrittore.|