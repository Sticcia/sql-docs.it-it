---
title: Rimuovere operazioni DDL nelle tabelle inserite ed eliminate all'interno di trigger DML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1113b0dd823c2479cff950233d0811f6c017afc9
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582054"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a>Rimuovere le istruzioni DDL eseguite su tabelle inserite ed eliminate all'interno di trigger DML
  Istruzioni data definition language (DDL), ad esempio CREATE INDEX non possono essere eseguite sulle tabelle inserite ed eliminate all'interno di trigger DML. Alcune istruzioni DDL sulle tabelle inserite ed eliminate sono consentite nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere "Utilizzo delle tabelle inserted e deleted" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere le istruzioni DLL eseguite nelle tabelle inserite ed eliminate all'interno di trigger DML.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
