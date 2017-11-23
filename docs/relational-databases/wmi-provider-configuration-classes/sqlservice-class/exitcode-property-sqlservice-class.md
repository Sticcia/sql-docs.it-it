---
title: "Proprietà ExitCode (classe SqlService) | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ExitCode Property (SqlService Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f464d5134d0424b23086170e88054878543ff121
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="exitcode-property-sqlservice-class"></a>Proprietà ExitCode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Ottiene o imposta il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] codice di errore Win32 che definisce i problemi verificati durante l'avvio e arresto del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.ExitCode [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore **uint32** che specifica il codice di uscita.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà è impostata su ERROR_SERVICE_SPECIFIC_ERROR (1066) quando l'errore è univoco al servizio rappresentato da questa classe. Tramite il servizio questo valore viene impostato su NO_ERROR in fase di esecuzione e di nuovo al termine.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  