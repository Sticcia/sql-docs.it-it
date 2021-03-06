---
title: Rimuovere le istruzioni che modificano oggetti di sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ebc7288bd7c72ce76df69d11c7a9fb0771764fca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856142"
---
# <a name="remove-statements-that-modify-system-objects"></a>Rimuovere le istruzioni che modificano oggetti di sistema
  Sono state rilevate istruzioni che aggiornano il catalogo di sistema. Gli aggiornamenti diretti del catalogo di sistema non sono consentiti. Modificare gli script SQL in modo che utilizzino API ufficiali e documentate.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descrizione  
 Gli aggiornamenti diretti del catalogo di sistema non sono consentiti. Qualsiasi tentativo di eseguire questa operazione restituirà l'errore seguente:  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare gli script SQL in modo che utilizzino API ufficiali e documentate. Ad esempio, usare ALTER DATABASE *database_name* SET EMERGENCY anziché eseguire un'istruzione UPDATE sulle **sysdatabases** tabella di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
