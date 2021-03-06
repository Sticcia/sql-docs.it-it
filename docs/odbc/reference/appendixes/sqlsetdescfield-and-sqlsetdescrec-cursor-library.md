---
title: SQLSetDescField and SQLSetDescRec (libreria di cursori) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b390df48e676290696ae8080c8f671fd0e37bad8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298273"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField and SQLSetDescRec (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzarla nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che utilizzano attualmente questa funzionalità. Microsoft consiglia di usare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo dei **SQLSetDescField** e **SQLSetDescRec** funzioni della libreria di cursori. Per informazioni generali su queste funzioni, vedere [funzione SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) e [funzione SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Esegue la libreria di cursori **SQLSetDescField** quando viene chiamato per restituire il valore dei campi impostati per colonne di segnalibri:  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 La libreria di cursori esegue chiamate a **SQLSetDescRec** per una colonna del segnalibro.  
  
 Quando si lavora con un'API ODBC 2. *x* driver, la libreria di cursori restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer) quando **SQLSetDescField** oppure **SQLSetDescRec** viene chiamato per impostare il SQL_DESC_OCTET_ Campo di lunghezza per il record di segnalibro di un ARD su un valore non è uguale a 4. Quando si lavora con un'applicazione ODBC 3*x* driver, la libreria di cursori consente il buffer essere di qualsiasi dimensione.  
  
 Esegue la libreria di cursori **SQLSetDescField** quando viene chiamato per restituire il valore del campo SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE o SQL_DESC_ROW_STATUS_PTR. Questi campi possono essere restituiti per ogni riga, non solo la riga di segnalibro.  
  
 La libreria di cursori non viene eseguito **SQLSetDescField** modificare qualsiasi campo del descrittore diversi dai campi indicati in precedenza. Se un'applicazione chiama **SQLSetDescField** per impostare qualsiasi altro campo durante il caricamento della libreria di cursori, la chiamata viene passata al driver.  
  
 La libreria di cursori supporta la modifica in modo dinamico i campi SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR e SQL_DESC_OCTET_LENGTH_PTR di qualsiasi riga di un descrittore riga dell'applicazione (dopo una chiamata a **SQLExtendedFetch**, **SQLFetch**, o **SQLFetchScroll**). Il campo SQL_DESC_OCTET_LENGTH_PTR può essere modificato in un puntatore null solo a disassocia il buffer di lunghezza per una colonna.  
  
 La libreria di cursori non supporta la modifica del campo SQL_DESC_BIND_TYPE un APD o ARD quando un cursore è aperto. Il campo SQL_DESC_BIND_TYPE può essere modificato solo dopo che il cursore viene chiuso e prima dell'apertura di un nuovo cursore. Gli unici campi del descrittore che la libreria di cursori supporta la modifica quando è aperto un cursore sono SQL_DESC_ARRAY_STATUS_PTR SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR e SQL_DESC_ROWS_PROCESSED_ PTR.  
  
 La libreria di cursori non supporta la modifica il campo SQL_DESC_COUNT del ARD dopo **SQLExtendedFetch** oppure **SQLFetchScroll** è stato chiamato e prima che il cursore è stato chiuso.
