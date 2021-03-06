---
title: Funzione SQLSetConfigMode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b40da961e3e659bf4cd3e3692b4674399bce47a6
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537207"
---
# <a name="sqlsetconfigmode-function"></a>Funzione SQLSetConfigMode
**Conformità**  
 Versione introdotta: ODBC 3.0  
  
 **Riepilogo**  
 **SQLSetConfigMode** imposta la modalità di configurazione che indica se la voce ini Elenca i valori DSN è nelle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Argomenti  
 *wConfigMode*  
 [Input] La modalità di configurazione del programma di installazione (vedere "Commenti"). Il valore in *wConfigMode* può essere:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLSetConfigMode** FALSO, restituisce un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* i valori che possono essere restituiti da **SQLInstallerError** e illustra ognuna nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Descrizione|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Sequenza di parametri non validi|Il *wConfigMode* argomento non conteneva ODBC_USER_DSN, ODBC_SYSTEM_DSN o ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene utilizzata per impostare in cui la voce ini Elenca i valori DSN è nelle informazioni di sistema. Se *wConfigMode* è ODBC_USER_DSN, il DSN è un DSN utente e la funzione legge dalla voce ini in HKEY_CURRENT_USER. Se si tratta ODBC_SYSTEM_DSN, il DSN è un DSN di sistema e la funzione legge dalla voce ini in HKEY_LOCAL_MACHINE. Se si tratta ODBC_BOTH_DSN, viene eseguito un tentativo di HKEY_CURRENT_USER e in caso contrario, viene utilizzato HKEY_LOCAL_MACHINE.  
  
 Questa funzione non influisce **SQLCreateDataSource** e **SQLDriverConnect**. La modalità di configurazione deve essere impostata quando un driver legge il Registro di sistema chiamando **SQLGetPrivateProfileString** o la scrittura nel Registro di sistema chiamando **SQLWritePrivateProfileString**. Le chiamate a **SQLGetPrivateProfileString** e **SQLWritePrivateProfileString** usare la modalità di configurazione per sapere quale parte del Registro di sistema su cui operare.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** deve essere chiamato solo quando necessario; se la modalità è impostata in modo non corretto, il programma di installazione ODBC potrebbe non riuscire funzionare correttamente.  
  
 **SQLSetConfigMode** apporta una modifica diretta del Registro di sistema della modalità di configurazione. Si tratta di oltre il processo di modifica la modalità di configurazione da una chiamata a **SQLConfigDataSource**. Una chiamata a **SQLConfigDataSource** imposta la modalità di configurazione per distinguere i DSN di sistema e utente quando si modifica un DSN. Prima della restituzione, **SQLConfigDataSource** BOTHDSN Reimposta la modalità di configurazione.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Creazione di un'origine dati|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|La connessione a un'origine dati tramite una finestra di dialogo o stringa di connessione|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Recuperare la modalità di configurazione|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
