---
title: Modificare le applicazioni per prevedere valori bigint da sysperfinfo. cntr_value | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 835e5fae4717748664affef9491ea1f7eeaec8b2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199920"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>Modificare le applicazioni in modo da prevedere valori bigint da sysperfinfo.cntr_value
  sysperfinfo restituisce un `bigint` valore per la colonna cntr_value.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare le applicazioni che utilizzano sysperfinfo per assicurarsi che siano in grado di gestire i valori `bigint` della colonna cntr_value.  
  
> [!NOTE]  
>  sysperfinfo è una vista di compatibilità. È consigliabile utilizzare la vista a gestione dinamica sys.dm_os_performance_counter.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
