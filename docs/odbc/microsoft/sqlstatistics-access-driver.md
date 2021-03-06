---
title: SQLStatistics (Driver Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc5a354aeaf186b4baeabd96e7424939fe463bfb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62687124"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (driver Access)
> [!NOTE]  
>  In questo argomento vengono fornite informazioni di accesso specifici del Driver. Per informazioni generali su questa funzione, vedere l'argomento appropriato nel [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|colonna|Commenti|  
|------------|--------------|  
|TABLE_QUALIFIER|Viene restituito il percorso di un file di database per Microsoft Access.<br /><br /> Criteri di ricerca non sono supportata nel *szTableQualifier* argomento.|  
|TABLE_OWNER|In questo articolo, viene restituito NULL perché il nome del proprietario non è supportato.|  
|TABLE_NAME|Nome della tabella non delimitato.<br /><br /> Criteri di ricerca non sono supportata nel *szTableName* argomento.|  
|INDEX_QUALIFIER|Viene sempre restituito NULL.|  
|INDEX_NAME|Indice dipendente.|  
|TYPE|Verranno restituiti solo SQL_TABLE_STAT o SQL_INDEX_OTHER per tipo.|  
|SEQ_IN_INDEX|Indice dipendente.|  
|COLUMN_NAME|Indice dipendente.|  
|COLLATION|Indice dipendente.|  
|CARDINALITY|Restituito solo per Microsoft Access.|  
|PAGES|Viene sempre restituito NULL.|  
  
 Il filtro si basa sull'univocità (la *fUnique* argomento). Il *fAccuracy* parametro viene ignorato.
